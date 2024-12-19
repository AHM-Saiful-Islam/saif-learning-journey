# Kubernetes Documentation

## Introduction
Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. Originally developed by Google, Kubernetes is now maintained by the Cloud Native Computing Foundation (CNCF). It is designed to help manage complex, distributed systems at scale, making it a cornerstone of modern software development.

Official website: [https://kubernetes.io](https://kubernetes.io)

## Key Components

### 1. **Control Plane**
The control plane is responsible for managing the Kubernetes cluster. It consists of the following components:

- **API Server**: Acts as the front-end for the Kubernetes control plane, exposing the Kubernetes API. All cluster interactions pass through this component.
- **etcd**: A consistent and distributed key-value store used to store all cluster data.
- **Scheduler**: Assigns workloads to available nodes based on resource availability and constraints.
- **Controller Manager**: Runs various controllers that regulate the state of the cluster, such as node, replication, and endpoint controllers.
- **Cloud Controller Manager**: Integrates with cloud provider APIs to manage resources like load balancers and storage.

### 2. **Node Components**
Nodes are the worker machines in a Kubernetes cluster, responsible for running containerized applications. Each node contains:

- **Kubelet**: Ensures that containers are running as expected on the node.
- **Kube-proxy**: Manages network rules to allow communication to and from pods.
- **Container Runtime**: Software responsible for running containers, such as Docker, containerd, or CRI-O.

### 3. **Pods**
A pod is the smallest deployable unit in Kubernetes. It encapsulates one or more containers, storage resources, and a network identity.

### 4. **Services**
Services provide stable network endpoints to access pods, enabling communication between components.

### 5. **Deployments**
Deployments manage the lifecycle of applications, providing mechanisms for scaling, rolling updates, and rollbacks.

### 6. **ConfigMaps and Secrets**
These components manage configuration data and sensitive information, allowing separation of configuration from application code.

### 7. **Ingress**
Ingress manages external access to services, often via HTTP and HTTPS, supporting routing, load balancing, and SSL termination.

## Installation

### Prerequisites
- **Operating System**: Linux or macOS (Windows requires WSL2).
- **Command-Line Tools**: `kubectl` (Kubernetes command-line tool), Docker, and a package manager like `brew` or `apt`.

### Installation Steps

1. **Install Kubernetes CLI**:
   ```bash
   # macOS using Homebrew
   brew install kubectl

   # Linux
   sudo apt-get update && sudo apt-get install -y kubectl
   ```

2. **Set up a Local Kubernetes Cluster**:
   - Use Minikube for local development:
     ```bash
     # Install Minikube
     brew install minikube

     # Start a Minikube cluster
     minikube start
     ```
   - Alternatively, use Docker Desktop or Kind (Kubernetes IN Docker).

3. **Verify Installation**:
   ```bash
   kubectl cluster-info
   ```

4. **Deploy a Test Application**:
   ```bash
   kubectl create deployment hello-world --image=k8s.gcr.io/echoserver:1.4
   kubectl expose deployment hello-world --type=NodePort --port=8080
   minikube service hello-world
   ```

### Cloud Installation
For production, use managed Kubernetes services like Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), or Azure Kubernetes Service (AKS).

## Working with Kubernetes

### Deployment Workflow
1. **Define Resources**: Use YAML files to define resources like pods, services, and deployments.
   Example `deployment.yaml`:
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: nginx-deployment
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: nginx
     template:
       metadata:
         labels:
           app: nginx
       spec:
         containers:
         - name: nginx
           image: nginx:1.17.10
           ports:
           - containerPort: 80
   ```

2. **Apply Configuration**:
   ```bash
   kubectl apply -f deployment.yaml
   ```

3. **Monitor Resources**:
   ```bash
   kubectl get pods
   kubectl get services
   ```

4. **Scale Applications**:
   ```bash
   kubectl scale deployment nginx-deployment --replicas=5
   ```

5. **Roll Out Updates**:
   ```bash
   kubectl set image deployment/nginx-deployment nginx=nginx:1.18.0
   ```

### Debugging and Troubleshooting
- View logs: `kubectl logs <pod-name>`
- Debug pods: `kubectl exec -it <pod-name> -- /bin/sh`
- Describe resources: `kubectl describe <resource> <name>`

## Benefits for Developers
- **Scalability**: Automatically scale applications to meet demand.
- **Portability**: Run applications consistently across development, staging, and production.
- **Automation**: Automate deployment, updates, and recovery processes.
- **Observability**: Monitor the health and performance of applications and infrastructure.

## Resources
- Kubernetes Documentation: [https://kubernetes.io/docs](https://kubernetes.io/docs)
- CNCF Kubernetes Landscape: [https://landscape.cncf.io](https://landscape.cncf.io)
- Tutorials: [https://kubernetes.io/docs/tutorials](https://kubernetes.io/docs/tutorials)
- Kubernetes Crash Course for Absolute Beginners: [https://youtu.be/s_o8dwzRlu4?si=hPd1EAqZ2bBKnm6n]

## Conclusion
Kubernetes has revolutionized how we manage and deploy applications in the cloud. By understanding its core components, mastering its workflows, and leveraging its features, developers and organizations can build resilient, scalable, and efficient systems.

