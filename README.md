# Kubernetes

Kubernetes is a container orchestration technology

Key features:
1. No downtime
2. Scalability (high scale when more users, low scale when less users)
3. Backup and restore (to the latest stable state after recovery)

Architecture:
1. Atleast one master node
2. Virtual network
3. A few worker nodes(aka kubelets)


Functions:
1. Master node (control panel), It runs critical processes
    1. API server
    2. Control manager
    3. Scheduler
    4. etcd
2. Worker node, each worker node has docker containers for different applications
3. Virtual network make the master node and its worker nodes into one pwoerful system with resources of all the nodes

Size:
1. Master node has less resources (but very important)
2. Worker node has a lot of resources 

Backups:
1. Atleast 2 replicas of a master

Node and Pod:
1. A node has several contai    ners, and ever container is abstracted using a pod (pod is the smalest unit of kubernetes)
2. Each pod has its own IP address
3. Pods are ephemeral, they die if resources are cut, then a new pod will start and a new ip will be allotted
4. A service is a static ip address that can be assigned to each pod, the lifecycle of a pod and service are independent
5. The service abstracts multiple pod ips behind itself, providing a layer of abstraction.
6. The service is further abstracted by something called as ingress

Secret and Configmap and Volume:
1. A Configmap stores key-value pairs that are not confidential
2. A secret stores key-value pairs that are usually very confidential
3. A volume provides ephemeral or persistent data storage to pods

Deployment and stateful states:
1. A Stateless server is the main idea behind the deployment component in kubernetes, a serverless system is
simply a pod that does not retain any data, it depends on external caches, makes load balancing easier
2. A stateful server is the main idea behind the stateful component in kubernetes, its characteristics are 
that it has a unique identity, retains data across restarts using PVs and has an ordered deployment and scaling 
processes

Kubernetes configuration:
1. A YAML or JSON file is accepted by the master node aka control panel and based on the confgs, the api server 
on the master node processes the requests and schedules the workloads across the worker nodes
2. Each config file has 3 parts
    1. Metadata, e.g., component name like nginx-deployment
    2. Specification, e.g., number of replicas
    3. Status, it makes sure that the desired and the actual state matches, i.e., if 2 replicas are asked then 
    there should infact be 2 replcias (managed by etcd)
3. The config files are generally stored in the code repo itself


Minicube:
1. A software that lets you test kubernetes on your local machine
2. 