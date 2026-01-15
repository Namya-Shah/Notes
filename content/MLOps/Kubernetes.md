---
Link:
tags:
  - MLOps
---
# Brief Introduction
- Kubernetes, a tool for managing and automating containerized workloads in the cloud.
- Imagine orchestra, all musicians are docker containers, and kubernetes is the conductor.
- Kubernetes is the tool that orchestrate the infrastructure to handle the changing workload.
- It can scale containers across multiple machines and if one fail it knows how to replace it with a new one.
- A system deployed on kubernetes is known as **cluster**.
- The brain of the operation is known as the **control plane**.
- It exposes an API server that can handle both internal and external requests to manage the cluster.
- It also contains its own key value database called **ETCD** used to store important information about running the cluster.
- What it is managing is one or more worker machines called **nodes**.
- Each node is running a **kubelet** which is a tiny application that runs on the machine to communicate back with the main control plane.
- Inside of each node, we have multiple **pods** which is the *smallest deployable unit* in Kubernetes.
- As the workload increases kubernetes can automatically scale horizontally by adding more nodes to cluster. In the process, it takes care of complicated things like networking, secret management, persistent storage and so on.
# Definition
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation, letting you run distributed systems resiliently, with scaling and failover for your application.
# Features
- High availability or no downtime
- Scalability or high performance
- Disaster recovery - backup and restore

# References
---
1. [you need to learn Kubernetes RIGHT NOW!!](https://www.youtube.com/watch?v=7bA0gTroJjw&t=1s)
2. [[Kubernetes Components]]
3. 
