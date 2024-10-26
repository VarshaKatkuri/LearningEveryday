<p><a target="_blank" href="https://app.eraser.io/workspace/5SbAyc1y0ja2Bw5HOPb1" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

Kubernetes is a container orchestration tool that allows the automation of deployment, scaling. It enables load balancing, scaling, rolling updates and other such features. It is an open source container orchestration system that is designed by google. It is self healing and enables declarative state management. It handles complex deployments and ensures high availability and efficiency. 

## Kubernetes Cluster: 
A Kubernetes Cluster is a combination of master and worker machines that enable container orchestration. 

## Why is it called K8S? 
Because there are 8 letters, in between the first letter "K" and the last letter "S". Kubernetes is generally also referred as K8S. 

## How is it different from Docker Swarm? 
Docker Swarm is also a container orchestration tool which enables automation. However, the key difference is that Docker Swarm works on the containers created using Docker only. When compared to the speed, the Docker Swarm is much faster than Kubernetes, as it works on the level of the container. 

## How does K8S work on different container engines? 
K8S architecture contains a key object called "Pod" which enable K8S to work on any type of container engine. 

#### POD is simply a layer of abstraction on top of a container. It is the smallest object on which k8s can work on. Pods deal with working with different kinds of container engines within them.
#  Kubernetes Architecture:
 Key components of the Kubernetes Architecture: 

1.  Master Node/ Control Plane: Master node in the k8s architecture takes the responsibility for maintaining the desired state of the k8s cluster. It is responsible for orchestration, and ensures that all the pods are operating as expected. Following are the sub-components of the master plane:
    1. Kube API Server: It is the validator. It is also the communication hub for the k8s cluster and helps navigating information among different master node and worker node components. 
    2. Etcd: Stores data about the nodes, pods, configuration, secrets in the form of key pairs. 
    3. Scheduler: It is the decision maker.  Decides on which node should the user request be processed based on the user requirements. 
    4. Controller Manager: It enables self healing mechanism. Helps in maintaining the state of the cluster.
2. Worker Nodes: These are the VMs on which the actual working happens. That is, containers run on the worker nodes. A container or group of containers are encapsulated in a pod and the worker nodes hosts one or more pods on each node. Following the key components of the worker nodes: 
    1. Container Runtime: It is a software that is responsible for running containers withing a pod. 
    2. Kubelet: Kubelet is a primary or principal component that receives information from the control plane node (api server) that runs on each worker node. It ensures that the containers within the pods are running as expected. It is also responsible for the overall health of the node. 
    3. KubeProxy: It enables networking within the node. It allows pods within the nodes to communicate with each other. It is responsible for creating IP table rules that enable pod-to-pod networking. 
![K8S Architecture](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___---figure---ITfoX6IHhe1vGnGJ0JM6x---figure---_PRGcgIvotH8B0X1WzSpRg.png "K8S Architecture")







<!--- Eraser file: https://app.eraser.io/workspace/5SbAyc1y0ja2Bw5HOPb1 --->