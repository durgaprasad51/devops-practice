# Kubernetes Architecture and Cluster Setup

### Kubernetes History

2003-2004	Google develops Borg for internal cluster management
2013	Google builds Omega, an improved successor to Borg
June 2014	Kubernetes is announced by Google at DockerCon
July 2015	Kubernetes v1.0 is released; Google donates K8s to the newly formed Cloud Native Computing Foundation (CNCF)
2016	Kubernetes wins the container orchestration war against Docker Swarm and Apache Mesos
2017	All major cloud providers launch managed Kubernetes services — Amazon EKS, Azure AKS, Google GKE
March 2018	Kubernetes becomes the first CNCF project to graduate, signaling production maturity
2019	Docker Enterprise itself adopts Kubernetes as its default orchestrator
2020	Kubernetes deprecates Docker as a container runtime (in favor of containerd/CRI-O)
2021-2023	Kubernetes matures with stable APIs, Gateway API, and a massive ecosystem
2024-2025	Focus shifts to security, eBPF-based networking, AI/ML workloads, and Wasm support

### Kubernetes wasn’t the only game in town. Three major platforms competed for dominance

**Docker Swarm**
Docker’s built-in orchestration tool. Simple to set up but lacked the advanced features enterprises needed — auto-scaling, rolling updates, and robust networking.

**Apache Mesos**
A powerful distributed systems kernel that could run containers, but was complex to operate and had a steeper learning curve.

**Kubernete**
Google’s entry brought battle-tested patterns from Borg, a declarative API model, an extensible architecture, and — crucially — a vibrant open-source community.

By 2017, the war was effectively over. Kubernetes won because of:

Community — CNCF governance attracted contributions from every major tech company
Extensibility — Custom Resource Definitions (CRDs) let anyone extend K8s
Cloud adoption — Every cloud provider offered managed Kubernetes
Enterprise backing — Red Hat, VMware, Microsoft, and others invested heavily
The CNCF and the Cloud-Native Ecosystem
When Google donated Kubernetes to the Cloud Native Computing Foundation (CNCF) in 2015, it was a strategic move to ensure Kubernetes remained vendor-neutral. The CNCF, part of the Linux Foundation, now oversees a massive ecosystem of cloud-native projects:

Prometheus — Monitoring
Envoy — Service proxy
Helm — Package management
Istio — Service mesh
Argo — GitOps and workflows
containerd — Container runtime
Kubernetes is the gravitational center of this ecosystem.

Why This History Matters
Understanding Kubernetes’ origins helps you recognize:

It’s designed for scale — Born from systems running billions of containers
Declarative model — You tell K8s what you want, not how to do it
Self-healing — Automatic restarts, rescheduling, and replication come from Borg’s DNA
Extensibility — The API-first design lets you build anything on top of K8s
Community-driven — No single vendor controls Kubernetes

**Kubernetes, also known as k8s or kube, is an open source container orchestration platform for scheduling and automating the deployment, management and scaling of containerized applications**

---

### Draw the Kubernetes Architecture


**Control Plane (Master Node):**
- API Server — the front door to the cluster, every command goes through it
- etcd — the database that stores all cluster state
- Scheduler — decides which node a new pod should run on
- Controller Manager — watches the cluster and makes sure the desired state matches reality

**Worker Node:**
- kubelet — the agent on each node that talks to the API server and manages pods
- kube-proxy — handles networking rules so pods can communicate
- Container Runtime — the engine that actually runs containers (containerd, CRI-O)
es down?

---

### Install kubectl

# Linux (amd64)
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

---

** kind (Kubernetes in Docker)**
```bash
# Install kind
# macOS
brew install kind

# Linux
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create a cluster
kind create cluster --name devops-cluster

# Verify
kubectl cluster-info
kubectl get nodes
```

**Option B: minikube**
```bash
# Install minikube

# Linux
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Start a cluster
minikube start

# Verify
kubectl cluster-info
kubectl get nodes
```
---

### Explore Your Cluster


# See cluster info
kubectl cluster-info

# List all nodes
kubectl get nodes

# Get detailed info about your node
kubectl describe node <node-name>

# List all namespaces
kubectl get namespaces

# See ALL pods running in the cluster (across all namespaces)
kubectl get pods -A

Look at the pods running in the `kube-system` namespace:

kubectl get pods -n kube-system

You should see pods like `etcd`, `kube-apiserver`, `kube-scheduler`, `kube-controller-manager`, `coredns`, and `kube-proxy`. 
These are the architecture components running as pods inside the cluster.

---





