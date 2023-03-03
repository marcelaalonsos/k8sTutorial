# TUTORIAL NOTES

source: kubernetes.io/docs/tutorials/kubernetes-basics

Kubernetes is an open source platform that uses Containerization to help package software to serve applications (deployment, accessibility, maintenance), enabling them to be released and updated without downtime.

### Kubernetes Clusters

Takes a cluster of computers to work as a single unit. Decouples application from individual machines, into a container. Kubernetes automates the distribution and scheduling of application containers across a cluster.

A Kubernetes cluster consists of:

- Control Plane: manages the cluster
- Nodes: a VM or physical computer that serves as a worker machine. Each node has a Kubelet, which manages the node and communicates with the control plane.
- It should have a minimum of 3 nodes
- The nodes communicate with the control plane using the Kubernetes API

### To know

- Kubernetes doesn't manage data persistance, that has to be storage in the local or remote machine
- Databases can't be replicated via deployment, they need a StatefulSet
- Databases are often hosted outside of Kubernetes cluster

### Configuration

Each configuration file has 3 parts

1. metadata: name
2. specification: atrributes are specific to the kind (deployment or service)
3. status -- but it is automatically created by Kubernetes (desired == actual)
