# Kubeflow

Table of Contents:
- [Kubeflow](#kubeflow)
  - [Working with Kubeflow](#working-with-kubeflow)
  - [Setting-up Kubeflow](#setting-up-kubeflow)

Kubeflow is a platform that is created to enhance and simplify the process of deploying machine learning workflows on Kubernetes. Using Kubeflow, it becomes easier to manage a distributed machine learning deployment by placing components in the deployment pipeline such as the training, serving, monitoring and logging components into containers on the Kubernetes cluster.

The goal of Kubeflow is to abstract away the technicalities of managing a Kubernetes cluster so that a machine learning practitioner can quickly leverage the power of Kubernetes and the benefits of deploying products within a microservices framework. Kubeflow has its history as an internal Google framework for deploying machine learning pipelines on Kubernetes before being open-sourced late 2017.

## Working with Kubeflow
Kubeflow consists of some core components:
- TF Job Operator and Controller: For automatic configuration of master and worker nodes and workload deployment. 
- TF Hub: Instances of JupyterHub for rapid prototyping with Jupyter notebooks.
- Model Server: Platform for deploying Tensorflow models for inference.

## Setting-up Kubeflow
