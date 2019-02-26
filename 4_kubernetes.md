# Kubernetes (K8s)

When a microservice application is deployed in production, it usually has many running containers that need to be allocated the right amount of resources in response to user demands. Also, there is a need to ensure that the containers are online, running and are communicating with one another. The need to efficiently manage and coordinate clusters of containerized applications gave rise to Kubernetes.

Kubernetes is a software system that addresses the concerns of deploying, scaling and monitoring containers. Hence, it is called a *container orchestrator*.  Examples of other container orchestrators in the wild are Docker Swarm, Mesos Marathon and Hashicorp Nomad.

Kubernetes was built and released by Google as an open-source software, which is now managed by the <a href="https://www.cncf.io/">Cloud Native Computing Foundation (CNCF)</a>. Google Cloud Platform offers a managed Kubernetes services called <a href="https://cloud.google.com/kubernetes-engine/">**Google Kubernetes Engine (GKE)**</a>. <a href="https://aws.amazon.com/kubernetes/">Amazon Elastic Container Service for Kubernetes (EKS)</a> also provides a  managed Kubernetes service.