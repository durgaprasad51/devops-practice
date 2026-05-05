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
# Run a single Pod
kubectl run my-nginx --image=nginx --port=80

# Check the Pod
kubectl get pods

# Get detailed info
kubectl describe pod my-nginx


### Example of a POD manifest file

```yaml
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


