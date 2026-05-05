# Kubernetes Manifests for Pods
**The Pod is the smallest deployable unit in Kubernetes. It’s not a container — it’s a wrapper around one or more containers that share the same network and storage. Every workload in Kubernetes runs inside a Pod.**

### What is a Pod?
A Pod represents a single instance of a running process in your cluster. It encapsulates:

One or more containers (usually one)
Shared networking — all containers in a Pod share the same IP address and port space
Shared storage — containers can mount the same volumes
Lifecycle — containers in a Pod are co-scheduled and co-located

### Why Pods and Not Just Containers?

Kubernetes doesn’t run containers directly for several important reasons:

Co-location — Some containers need to run together (e.g., a web server and a log shipper)
Shared resources — Containers in a Pod can communicate via localhost and share files
Atomic scheduling — K8s schedules the entire Pod as a unit, not individual containers
Abstraction — Pods provide a runtime-agnostic interface (works with containerd, CRI-O, etc.)

### Using kubectl (Imperative)
```
# Run a single Pod
kubectl run my-nginx --image=nginx --port=80

# Check the Pod
kubectl get pods

# Get detailed info
kubectl describe pod my-nginx
```

### Example of a POD manifest file

```
apiVersion: v1           		 # API version for Pods
kind: Pod                 		 # Resource type   

metadata: 
    name: nginx           		 # Pod name (must be unique in the namespace) 
    labels:           			 # Key-value pairs for organizing and selecting 
      app: nginx
      environment: dev

spec: 
    containers:             		# List of containers in this Pod
    - name: nginx           		# Container name 
      image: nginx:latest    		# Container image 
      ports:
      - containerPort: 80    		# Port the container listens on
      resources:
        requests:            		# Minimum resources guaranteed
          memory: "64Mi"
          cpu: "250m"  
      limits:                 		# Maximum resources allowed
        memory: "128Mi"
          cpu:"500m"  
```
**apply it** =>  kubectl apply -f pod.yaml

**Pod Lifecycle**
```
A Pod goes through several phases during its lifetime:

Pending	=> Pod accepted by the cluster but containers not yet running. Could be waiting for scheduling or image pull.
Running	=> Pod bound to a node. At least one container is running.
Succeeded => All containers terminated successfully (exit code 0). Won’t restart.
Failed	=> All containers terminated. At least one exited with a non-zero code.
Unknown	=> Pod status can’t be determined (usually a node communication issue).
```

###

```
kubectl get pods
kubectl get pod my-nginx -o wide    # Shows node, IP, etc.
```
### Working with pod

```
# View logs
kubectl logs my-nginx

# Follow logs in real-time
kubectl logs -f my-nginx

# View logs for a specific container (multi-container Pod)
kubectl logs my-nginx -c nginx
```
### Execute Commands inside a pod
```
# Open a shell
kubectl exec -it my-nginx -- /bin/bash

# Run a single command
kubectl exec my-nginx -- ls /usr/share/nginx/html

# For multi-container Pods, specify the container
kubectl exec -it my-nginx -c nginx -- /bin/bash
```
### Port forwarding

```
# Forward local port 8080 to Pod port 80
kubectl port-forward my-nginx 8080:80

# Now visit http://localhost:8080 in your browser
```
### Delete a Pod
```
# Delete by name
kubectl delete pod my-nginx

# Delete using the YAML file
kubectl delete -f pod.yaml
```





