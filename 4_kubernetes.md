# Kubernetes (K8s)

Table of Contents:
- [Kubernetes (K8s)](#kubernetes-k8s)
  - [Features of Kubernetes](#features-of-kubernetes)
  - [Components of Kubernetes](#components-of-kubernetes)
    - [Master Node(s)](#master-nodes)
    - [Worker Node(s)](#worker-nodes)
  - [Writing a Kubernetes Deployment File](#writing-a-kubernetes-deployment-file)
    - [Example of a Service Object](#example-of-a-service-object)
    - [Example of a Deployment Object](#example-of-a-deployment-object)
  - [Deploying Kubernetes on Local Machine using Minikube](#deploying-kubernetes-on-local-machine-using-minikube)
    - [Using `kubectl` to deploy and manage the Kubernetes cluster](#using-kubectl-to-deploy-and-manage-the-kubernetes-cluster)
      - [Overview of Minikube commands:](#overview-of-minikube-commands)
      - [Deploy using `kubectl`](#deploy-using-kubectl)
  - [Deploying Kubernetes on Google Kubernetes Engine](#deploying-kubernetes-on-google-kubernetes-engine)

When a microservice application is deployed in production, it usually has many running containers that need to be allocated the right amount of resources in response to user demands. Also, there is a need to ensure that the containers are online, running and are communicating with one another. The need to efficiently manage and coordinate clusters of containerized applications gave rise to Kubernetes.

Kubernetes is a software system that addresses the concerns of deploying, scaling and monitoring containers. Hence, it is called a *container orchestrator*.  Examples of other container orchestrators in the wild are Docker Swarm, Mesos Marathon and Hashicorp Nomad.

Kubernetes was built and released by Google as an open-source software, which is now managed by the <a href="https://www.cncf.io/">Cloud Native Computing Foundation (CNCF)</a>. Google Cloud Platform offers a managed Kubernetes services called <a href="https://cloud.google.com/kubernetes-engine/">**Google Kubernetes Engine (GKE)**</a>. <a href="https://aws.amazon.com/kubernetes/">Amazon Elastic Container Service for Kubernetes (EKS)</a> also provides a  managed Kubernetes service.

## Features of Kubernetes
- **Horizontal auto-scaling:** dynamically scales containers based on resource demands.
- **Self-healing:** re-provisions failed nodes in response to health checks.
- **Load balancing:** efficiently distributes requests between containers in a pod.
- **Rollbacks and updates:** easily update or revert to a previous container deployment without causing application downtime.
-  **DNS service discovery:** Uses Domain Name System (DNS) to manage container groups as a Kubernetes service.

## Components of Kubernetes
The main components of the Kubernetes engine are the:
- **Master node(s)**: manages the Kubernetes cluster. They may be more than one master node in High Availability mode for fault-tolerance purposes. In this case, only one is the master, and the others follow.
- **Worker node(s)**: machine(s) that runs containerized applications that are scheduled as pod(s).

The illustration below provides a high overview of the Kubernetes architecture. Later, we'll briefly go through the individual sub-components.

<img src="img/kubernetes_components.png" alt="Kubernetes components." height=90% width=90%/>

### Master Node(s)
- **etcd (distributed key-store):** manages the Kubernetes cluster state. This distributed key-store can be a part of the Master node or external to it. Nevertheless, all master nodes connect to it.
- **api server:** manages all administrative tasks. The `api server` receives commands from the user (kubectl cli,REST or GUI), these commands are executed and the new cluster state is stored in the distributed key-store.
- **scheduler:** schedules work to worker nodes by allocating pods. It is responsible for resource allocation.
- **controller:** ensure that the desired state of the Kubernetes cluster is maintained. The desired state is what is contained in a JSON or YAML deployment file.

### Worker Node(s)
- **kubelet:** the `kubelet` agent runs on each worker node. It connects the worker node to the `api server` on the master node and received instructions from it. Ensures the pods on the node are healty.
- **kube-proxy:** it is the Kubernetes network proxy thats runs on each worker node. Listens to the `api server` and forward requests to the appropriate pod. Important for load-balancing.
- **pod(s):** consists of one or more containers that share network and storage resources as well as container runtime instructions. Pods are the smallest deployable unit in Kubernetes.

## Writing a Kubernetes Deployment File
The Kubernetes deployment file defines the desired state for the various Kubernetes objects. Examples of Kubernetes objects are:
- **Pods:** a collection of one or more containers.
- **ReplicaSets:** part of the `controller` in the master node. Specifies the number of replicas of a pod that should be running at any given time. It ensures that the specified number of pods is maintained in the cluster.
- **Deployments:** automatically creates `ReplicaSets`. It is also part of the `controller` in the master node. Ensures that the clusters current state matches the desired state.
- **Namespaces:** partition the cluster into sub-clusters to organize users into groups.
- **Service:** a logical group of Pods with a policy to access them.
  - *ServiceTypes:* specifies the type of Service e.g. `ClusterIP`, `NodePort`, `LoadBalancer`, `ExternalName`. As an example, `LoadBalancer` exposes the service externally using a cloud provider’s load balancer.

Other important tags in writing a Kubernetes Deployment File.
- **spec:** describes the desired state of the cluster.
- **metadata:** contains information of the object.
- **labels:** used to specify attributes of objects as key-value pairs.
- **selector:** used to select a subset of objects based on their label values.

The deployment file is specified as a `yaml` file.

### Example of a Service Object
The snippet is saved in `kubernetes-intro/deployment.yaml`.
```yaml
kind: Service
apiVersion: ebisong.net/tf-jupyter-service
metadata:
  name: tf-jupyter-service
spec:
  selector:
    app: tf-jupyter
  ports:
    - protocol: "TCP"
      # accessible inside cluster
      port: 8888
      # port forward inside the pod
      targetPort: 8888
      # accessible outside cluster
      nodePort: 30002
  type: LoadBalancer
```

### Example of a Deployment Object
The snippet is saved in `kubernetes-intro/deployment.yaml`.
```yaml
apiVersion: ebisong.net/tf-jupyter-deployment
kind: Deployment
metadata:
  name: tf-jupyter-deployment
spec:
  replicas: 5
  template:
    metadata:
      labels:
        app: tf-jupyter
    spec:
      containers:
        - name: tf-jupyter-container
          image: jupyter/tensorflow-notebook
          ports:
            - containerPort: 8888
```

## Deploying Kubernetes on Local Machine using Minikube
Minikube makes it easy to install and run a single-node Kubernetes cluster on a local machine. Go to <a href="https://kubernetes.io/docs/tasks/tools/install-minikube/">https://kubernetes.io/docs/tasks/tools/install-minikube/</a> for instructions on installing Minikube.

1. Install a hypervisor e.g. <a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox</a>.
2. Install Kubernetes Command line interface `kubectl`.
For mac:
```bash
brew install kubernetes-cli
```
Check the installed version:
```bash
kubectl version
```
3. Install Minikube.
For mac:
```bash
brew cask install minikube
```

### Using `kubectl` to deploy and manage the Kubernetes cluster
#### Overview of Minikube commands:
|**Command**|**Description**|
|-|-|
|`minikube status`| Check if Minikube is running.
|`minikube start`| Create local kubernetes cluster.
|`minikube dashboard`| Open Minikube GUI for interacting with the Kubernetes cluster. Append `&` to open in background mode `minikube dashboard &`.
|`minikube ip`| get ip address of Kubernetes cluster.

#### Deploy using `kubectl`

```bash
# create local kubernetes cluster
minikube start
```

```
Starting local Kubernetes v1.13.2 cluster...
Starting VM...

Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Stopping extra container runtimes...
Machine exists, restarting cluster components...
Verifying kubelet health ...
Verifying apiserver health ....
Kubectl is now configured to use the cluster.
Loading cached images from config file.

Everything looks great. Please enjoy minikube!
```

```bash
# list pods
kubectl get pods
```

```
NAME                   READY     STATUS             RESTARTS   AGE
example-job-master-0   1/1       Running            0          20d
example-job-ps-0       0/1       ImagePullBackOff   0          20d
example-job-ps-1       0/1       ImagePullBackOff   0          5m
example-job-worker-0   1/1       Running            0          20d
```

```bash
# navigate to directory with deployment file
cd kubernetes-intro/

# create new resource from yaml file
sudo kubectl create -f deployment.yml
```

## Deploying Kubernetes on Google Kubernetes Engine
ABCD