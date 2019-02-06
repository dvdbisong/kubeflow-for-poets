# Kubeflow for Poets: A Guide to Containerization of the Machine Learning Production Pipeline

<p align="left">
    <img src="img/docker.png" align="middle" alt="Docker." height=20% width=20%/>&nbsp;&nbsp;
    <img src="img/kubernetes.png" align="middle" alt="Kubernetes." height=20% width=20%/>&nbsp;&nbsp;
    <img src="img/kubeflow.jpg" align="middle" alt="Kubeflow." height=20% width=20%/>&nbsp;&nbsp;
    <img src="img/gcp.png" align="middle" alt="Google Cloud Platform." height=20% width=20%/>&nbsp;&nbsp;
</p>

This repository provides a systematic approach to productionalizing machine learning pipelines with Kubeflow on Kubernetes. Building machine learning models is just one piece of a more extensive system of tasks and processes that come together to deliver a Machine Learning product. Kubeflow makes it possible to leverage the microservices paradigm of containerization to separate modular components of an application orchestrated on Kubernetes. While Kubernetes is platform agnostic, this tutorial will focus on deploying a Machine Learning product on Google Cloud Platform leveraging Google Cloud BigQuery, Google Cloud Dataflow and Google Cloud Machine Learning Engine orchestrated on Google Kubernetes Engine.

## Contents:
The content is arranged as follows:
- <a href="./1_introduction.md">Introduction</a>
- <a href="./2_microservices.md">Microservices Architecture</a>
- <a href="./3_docker.md">Docker</a>
- <a href="./4_kubernetes.md">Kubernetes</a>
- <a href="./5_kubeflow.md">Kubeflow</a>
- <a href="./6_kube_flow_pipelines.md">Kubeflow Pipelines</a>
- <a href="./7_ml_prototype_kubernetes.md">Develop Machine Learning Prototypes on Kubernetes</a>
- <a href="./8_orchestrate_ml_kubeflow.md">Orchestrate Machine Learning Production Flow with Kubeflow Pipelines</a>

## Links:
 - <a href="https://www.docker.com/">Docker</a>
 - <a href="https://kubernetes.io/">Kubernetes</a>
 - <a href="https://github.com/kubeflow/kubeflow">Kubeflow</a>
 - <a href="https://github.com/kubeflow/pipelines">Kubeflow Pipelines</a>
 - <a href="https://cloud.google.com/bigquery/">Google Cloud BigQuery</a>
 - <a href="https://cloud.google.com/dataflow/">Google Cloud Dataflow</a>
 - <a href="https://cloud.google.com/ml-engine/">Google Cloud Machine Learning Engine</a>
 - <a href="https://cloud.google.com/kubernetes-engine/">Google Kubernetes Engine</a>