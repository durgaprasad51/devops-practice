# Kubernetes Manifests for Pods
**POD- It smallest unit in the kubernetes. It is like a rapper of container. It has is own and IP address.1 apiVersion: v1

### Example of a POD manifest file

kind: Pod
apiVersion: v1

metadata:
    name: flask-app 
    namespace: flask-app
spec: 
    containers:
    - name: flask-app  
      image: nginx:latest
      ports:
      - containerPort: 80
