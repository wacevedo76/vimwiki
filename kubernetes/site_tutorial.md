# Kubernetes - Main site tutorial
## Terms and definitions:
- **etcd**
  Consisten and highly-available key value stroe used as Kubernetes' backing store for all cluster data
 
## Using Minikube to Create a Cluster
### What is a Kubernetes cluster?
- Kubernetes coordinates a highly available custer of computes that are connected to work as a single unit
- Kubernetes automates the distribution and scheduling of application containers across a cluster in a more efficient way.
- Kubernetes is a production-grade, open-source platform that orchestrates the placement (scheduling) and execution of application containers within and across computer clusters

### A kubernetes cluster consists of two types of resources:
- The **Control Plane** coordinates the cluster
  - The Control Plane is responsible for managing the cluster
- **Nodes** are the workers that run applications
  - A node is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster
