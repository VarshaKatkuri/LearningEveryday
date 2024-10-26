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

1.  **Master Node/ Control Plane: **Master node in the k8s architecture takes the responsibility for maintaining the desired state of the k8s cluster. It is responsible for orchestration, and ensures that all the pods are operating as expected. Following are the sub-components of the master plane:
    1. Kube API Server: It is the validator. It is also the communication hub for the k8s cluster and helps navigating information among different master node and worker node components. 
    2. Etcd: Stores data about the nodes, pods, configuration, secrets in the form of key pairs. 
    3. Scheduler: It is the decision maker.  Decides on which node should the user request be processed based on the user requirements. 
    4. Controller Manager: It enables self healing mechanism. Helps in maintaining the state of the cluster.
2. **Worker Nodes: **These are the VMs on which the actual working happens. That is, containers run on the worker nodes. A container or group of containers are encapsulated in a pod and the worker nodes hosts one or more pods on each node. Following the key components of the worker nodes: 
    1. Container Runtime: It is a software that is responsible for running containers withing a pod. 
    2. Kubelet: Kubelet is a primary or principal component that receives information from the control plane node (api server) that runs on each worker node. It ensures that the containers within the pods are running as expected. It is also responsible for the overall health of the node. 
    3. KubeProxy: It enables networking within the node. It allows pods within the nodes to communicate with each other. It is responsible for creating IP table rules that enable pod-to-pod networking. 
![K8S Architecture](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___---figure---ils4qgBcbUxvZmkS0Akyx---figure---_PRGcgIvotH8B0X1WzSpRg.png "K8S Architecture")



Task 1: 

1. Following the [﻿doc](https://kind.sigs.k8s.io/)  install a single node kind cluster on your local machine with Kubernetes version 1.29
```
﻿ kind create cluster --image kindest/node:v1.29.7@sha256:f70ab5d833fca132a100c1f95490be25d76188b053f49a3c0047ff8812360baf --name kind-single-cluster
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___00iw2XgWGDERZ2hVpnvlX.png "image.png")

```
---Get the cluster info
$ kubectl cluster-info --context kind-kind-single-cluster-1
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___ZFJCR1EpQEf3IlJ4W9F8H.png "image.png")

```
--Go inside cluster plane 
$ kubectl get nodes
```
```
--- delete the cluster created in the above step
$ kind delete cluster --name kind-single-cluster-1
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___UxhH4WVn7xq454r-fTSmF.png "image.png")

Task 2: 

Following the same [﻿doc](https://kind.sigs.k8s.io/)  install a multi-node kind cluster on your local machine using the below details:

- **Cluster Name** :- cka-cluster2
- **Nodes**:- 1 Control plane and 3 worker nodes
- **Kubernetes Version** :- 1.30
```
$ kind create cluster --name cka-cluster2 --config config-mn.yml --image kindest/node:v1.30.3@sha256:bf91e1ef2f7d92bb7734b2b896b3dddea98f0496b34d96e37dd5d7df331b7e56
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___Si1MZ-JXV4IuXiwtDU_RO.png "image.png")



Day 3: Pods in Kubernetes

What is a pod? 







Ways to create pod:

1. Imperative Approach: This approach of creating a pod uses the command line interface directly (kubectl) to define and create resources directly rather than writing any config files.  Eg: If we were to create an nginx pod imperatively: 
```
kubectl run --image=nginx pod-nginx
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___xF4xqQfmd9sUK2vzSeSbS.png "image.png")

2.Declarative Approach: The declarative approach of creating a pod requires configuring the requirements for the creation of pod in a yml or json file and then using command line interface to apply the configuration to create a pod. This approach enables a persistent configuration that one can reuse, version control, and manage more easily.

    

Task 2: 

- Create the YAML from the nginx pod created in task 1
```
kubectl run --image=nginx pod-nginx -o yaml > pod-nginx.yml
```
- Update the pod name in the YAML
```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: "2024-10-26T17:20:56Z"
  labels:
    run: pod-nginx
  name: nginx-new #updating the name of the pod to a new name 
  namespace: default
  resourceVersion: "96171"
  uid: c337f4dc-d153-4965-9ba0-9f56d2aa91aa
spec:
  containers:
  - image: nginx
    imagePullPolicy: Always
    name: pod-nginx
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: kube-api-access-g9996
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  preemptionPolicy: PreemptLowerPriority
  priority: 0
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 30
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  volumes:
  - name: kube-api-access-g9996
    projected:
      defaultMode: 420
      sources:
      - serviceAccountToken:
          expirationSeconds: 3607
          path: token
      - configMap:
          items:
          - key: ca.crt
            path: ca.crt
          name: kube-root-ca.crt
      - downwardAPI:
          items:
          - fieldRef:
              apiVersion: v1
              fieldPath: metadata.namespace
            path: namespace
status:
  phase: Pending
  qosClass: BestEffort
```
- Use that YAML to create a new pod with the name nginx-new.
```
kubectl apply -f pod-nginx.yml
```
![image.png](/.eraser/5SbAyc1y0ja2Bw5HOPb1___5xDTFinwA9fr5hUYeqTxN5JwMS42___G6UC44ynoXOhJISck_P45.png "image.png")







<!--- Eraser file: https://app.eraser.io/workspace/5SbAyc1y0ja2Bw5HOPb1 --->