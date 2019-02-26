# Kubernetes (K8s)

When a microservice application is deployed in production, it usually has many running containers that need to be allocated the right amount of resources in response to user demands. Also, there is a need to ensure that the containers are online, running and are communicating with one another. The need to efficiently manage and coordinate clusters of containerized applications gave rise to Kubernetes.

Kubernetes is a software system that addresses the concerns of deploying, scaling and monitoring containers. Hence, it is called a *container orchestrator*.  Examples of other container orchestrators in the wild are Docker Swarm, Mesos Marathon and Hashicorp Nomad.

Kubernetes was built and released by Google as an open-source software, which is now managed by the <a href="https://www.cncf.io/">Cloud Native Computing Foundation (CNCF)</a>. Google Cloud Platform offers a managed Kubernetes services called <a href="https://cloud.google.com/kubernetes-engine/">**Google Kubernetes Engine (GKE)**</a>. <a href="https://aws.amazon.com/kubernetes/">Amazon Elastic Container Service for Kubernetes (EKS)</a> also provides a  managed Kubernetes service.

## Features of Kubernetes
- **Horizontal auto-scaling:** dynamically scales containers based on resource demands.
- **Self-healing:** re-provisions failed nodes in response to health checks.
- **Load balancing:** efficiently distributes requests between replicated containers.
- **Rollbacks and updates:** easily update or revert to a previous container deployment without causing application downtime.
-  **DNS service discovery:** Uses Domain Name System (DNS) to manage container groups.

## Components of Kubernetes
The main components of the Kubernetes engine are the:
- **Master node(s)**: manages the Kubernetes cluster. They may be more than one master node in High Availability mode for fault-tolerance purposes. In this case, only one leads and the others follow.
- **Worker node(s)**: machine(s) that runs containerized applications that are scheduled as pod(s).

The illustration below provides a high overview of the Kubernetes architecture. Later, we'll briefly go through the individual sub-components.

<img src="img/kubernetes_components.png" alt="Kubernetes components." height=90% width=90%/>

### Master Node(s)
- **etcd (distributed key-store):** manages the Kubernetes cluster state. This distributed key-store can be a part of the Master node or external to it. Nevertheless, all master nodes connect to it.
- **api server:** manages all administrative tasks. The `api server` receives commands from the user (kubectl cli,REST or GUI), these commands are executed and the new cluster state is stored in the distributed key-store.
- **scheduler:** schedules work to worker nodes by allocating pods. It is responsible for resource allocation.
- **controller:** ensure that the desired state of the Kubernetes cluster is maintained.

### Worker Node(s)
- **kubelet:**
- **kube-proxy**
- **pod(s):**