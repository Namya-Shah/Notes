---
Link:
tags:
  - MLOps
---
# Brief Introduction
## Node and Pod
- A *node* is a simple server, a physical or virtual machine
- A basic component or the smallest unit of kubernetes is a *pod*
	- Abstraction over a container
	- Rather than interacting with the docker images, we work with docker images, we work with the kubernetes layer.
	- Usually meant to run one application container inside
	- We can also run multiple containers inside a pod but it has to have one main application container along with helper containers to use that service.
	- Each *pod* gets its own IP address to communicate between different pods.
	- **Ephemeral** which means that the *pod* can die very easily and when that happens (e.g., the database container ran out of resources/application crashed inside) the pod will die and new one will get created in its place. When that happens it will be assigned new IP address on re-creation.
## Service and Ingress
- A *service* is basically a static IP address that can be attached to each pod so the app will have its own service.
- It is also a **load balancer.**
	- Service will actually catch the request and forward it to whichever pod is least busy.
- **Pros:** The lifecycle of pod and service are not connected. So, even if the pod dies, the service and its ip address will stay.
- **Types:**
	- *External Service*
		- The app that can be accessed through the browser and is accessible by public.
	- *Internal Service*
		- The app (database) that should not be available publicly is referred.
- *External service -> Ingress -> Application Pod*
	- Ingress works as secure transfer protocol for our application
## ConfigMap and Secret
- *ConfigMap* is the external configuration of our application (something like database endpoints/url)
	- Rather than changing one thing and rebuilding and pushing to repo. Just change one configuration and it changes for the whole pod.
> [!IMPORTANT] NOTE
> Don't put credentials into *ConfigMap*
- *Secret* is used to store secret data (credentials) and is not stored in plain text format but in base64 encoded format.
	- Use it as environmental variables or as a properties file.
## Volumes
- It attaches a physical storage on a hard drive to your pod.
- That storage could be either on your local machine (same server node where the pod is running)
- The remote storage (outside of the k8s cluster). It could be on the cloud storage or it could be on your own premise storage which is not part of the k8s cluster.
> [!IMPORTANT]
> K8s doesn't manage data persistence!
- The user or administrator is responsible for backing up of the data, replicating and managing it and making sure its kept on proper hardware.
## Deployment and Stateful Set
- We will define number of replicas of the application we require, that component or that blueprint is called as *deployment*.
- We will not be creating pods but creating deployments because there we can specify how many replicas and also scale up or scale down number of replicas of pods that you need.
- Deployment is another abstraction on top of pods which makes it more convenient to interact with the pods, replicate them and do some other configuration.
- *Databases can't be replicated using deployment, as databases are in a state*
- If we have clones or replicas of the database they would all need to access the same shared data storage.
- We would require a mechanism that manages which pods are currently writing to that storage or which pods are reading from that storage in order to avoid data inconsistencies and that mechanism in addition to replicating feature is offered by another kubernetes component called *stateful set*.
- *Stateful set* is meant specifically for applications like databases such as SQL, MongoDB, elasticsearch and more... should be created using stateful sets and not deployments.
- It is also used to scale up or scale down database pods along with synchronization to avoid data inconsistencies.
- 
# References
---
1. 
