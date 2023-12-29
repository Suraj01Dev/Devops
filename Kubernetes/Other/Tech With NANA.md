```timestamp-url 
 https://www.youtube.com/watch?v=X48VuDVv0do
 ```


```timestamp 
 05:00
 ```
Three important features of orchestration tools:
- High Availability
- Scalability
- Disaster Recovery


## Different components of K8's

### Pods
- Its the smallest unit of K8's
- Its the abstraction over containers
- Usually 1 application per pod
- Each pod have their own IP and can communicate with each other

![[Pasted image 20231202100327.png]]

```timestamp 
 09:28
 ```
### Service

Pods can be temporary and can die easily, in that case a new pod is created and a new IP is assigned to it. This becomes inconvenient for inter-communication between pods, since a new IP is generated whenever a pod dies. Thus a service component is used to tackle this problem.

- Provides permanent IP address


### Ingress

```timestamp 
 10:45
 ```

Since each pods will have a unique IP and port number. Thus when connecting to a pod it becomes inconvenient to to connect it using the IP and port. This is where Ingress comes in. Whenever we connect to a node, the request first goes to the Ingress component.


### Config Maps and secrets.
This stores the config information and passwords.


```timestamp 
 15:49
 ```
### Volumes
Volumes are used to store the data of the pod, it can be either locally stored or remotely stored.

**k8's don't manage storage explicitly**. Thus the best practice is to manage the storage outside the cluster.


```timestamp 
 16:23
 ```
### Deployment

The deployment is the abstraction for the pods. We can't deploy the pods directly it can only be done through deployment. Deployment is suitable for stateless pods like a web server. For state-full applications such as Databases deployments cannot be used.

**Deployments are like a blueprint for pods**

### Stateful Set

When it comes to deploying stateful applications such as databases, deployment cannot be used **stateful set** should be used.



## Architecture of K8's
### Processes in the worker Node

- `Container runtime`
- `Kubelet`
- `Kubeproxy`

#### Container runtime
This is important for creating containers for the pods.

#### Kubelet
This component is used for creating the pods and communicating between the node and the pods. It also gets the instructions from the master node.


```timestamp 
 26:05
 ```
#### Kubeproxy
**check the timestamp**

### Processes in the Control Node

- `API Server`
- `Scheduler`
- `Controller Manager`
-  `ETCD`

#### API server
This component of the master node is the `entrypoint` into the cluster. The client communicates only with the `API server`. 

Some uses of API server are:
- Creating a new pod
- Creating a new service, etc

#### Scheduler
The scheduler is responsible for creating new pods. The API server after validating the request makes the scheduler to create the pods. The scheduler carefully checks the resources and creates the pods accordingly across the different nodes. 

**The Scheduler only instructs to create the pods, the process is done by the kubelet after getting a request from the scheduler.**


#### Control Manager

The control manager is responsible for monitoring the pods. Whenever a pod dies the control manager communicates with the scheduler to create a new pod.

#### Etcd
This the cluster brain, which all the data related to the cluster in the form of key value pair.


## Frequently used Kubectl commands.

 
```
kubectl get nodes
```

```
kubectl get pods
```

```
kubectl get services
```

```
kubectl get deployments
```

```
kubectl get replicaset
```

```
kubectl logs <pod name>
```

```
kubectl create deployment <name> --image=<image_name>
```

```
kubectl delete deployment <deployment name>
```

```
kubectl get pods -o wide
```

