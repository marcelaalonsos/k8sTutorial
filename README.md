# NOTES

Kubernetes is an open source platform that uses Containerization to help package software to serve applications (deployment, accessibility, maintenance), enabling them to be released and updated without downtime.

### Kubernetes Clusters

Takes a cluster of computers to work as a single unit. Decouples application from individual machines, into a container. Kubernetes automates the distribution and scheduling of application containers across a cluster.

A Kubernetes cluster consists of:

- Control Plane: manages the cluster
- Nodes: a VM or physical computer that serves as a worker machine. Each node has a Kubelet, which manages the node and communicates with the control plane.
- It should have a minimum of 3 nodes
- The nodes communicate with the control plane using the Kubernetes API

### Hello Minikube

- run minikube start
- run minikube dashboard
- stop proxy by Ctrl + C
- if you don't want to open a web broser run minikube dashboad --url
- use the kubectl create commande to create a Deployment that manages a Pod. The Pod runs a Container based on the provided Docker image
  kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080

- view the deployment
  kubectl get deployment

- view the pod
  kubectl get pods

- view cluster events
  kubectl get events

- view kubectl configuration
  kubectl config view

### Create a Service

To make the hello-node Container accessible from the outside the Kubernetes virtual network, you have to expose the Pod as a Kubernetes Service

- expose the Pod to the publuc internet
  kubectl expose deployment hello-node --type=LoadBalancer --port-8080

-view the services you created
kubectl get services

### Enable addons

- list the current supported addons
  minikube addons list

- enable an addon, for example metrics-server
  minikube addons enable metrics-server

- get the Pod and service you created
  kubectl get pod, svc -n kiube-system

- to disable addon, for example metrics-server
  minikube addons disable metrics-server

### Clean Up

- clean up the resources you created in your cluster:
  kubectl delete service hello-node
  kubeclt delte deployment hello-node

- optionally, stop the Minikube virtual machine:
  minikube stop

- optionally, delete the Minikube VM:
  minikube delete

### Module 1 - Create a Kubernets cluster

- install minikube CLI
- start the cluster by running minikube start
- to interact with Kubernetes, use the kubectl CLI
- check if kubectl is intalled by running kubectl version command
- view cluster details by running kubectl cluster-info
- view nodes, run kubectl get nodes

### Module 2 - Deploy an App using kubectl

- create a Kubernetes Deployment configuration, the control plane schedules the application instances included in that deployment to run on individual nodes in the cluster
- the deployment controller continously monitors the instances, if the node hosting an instance goes down or is deleted, the deployment controller replaces the instance with an instance on another node in the cluster
- it is a self-heing mechanism to address machine failure or maintenance
