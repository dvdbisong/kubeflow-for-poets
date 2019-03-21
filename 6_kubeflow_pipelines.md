# Kubeflow Pipelines

Table of Contents:
- [Kubeflow Pipelines](#kubeflow-pipelines)
  - [Components of Kubeflow Pipelines](#components-of-kubeflow-pipelines)
  - [Executing a Sample Pipeline](#executing-a-sample-pipeline)

Kubeflow Pipelines is a simple platform for building and deploying containerized machine learning workflows on Kubernetes. Kubeflow pipelines make it easy to implement production grade machine learning pipelines without bothering on the low-level details of managing a Kubernetes cluster.

Kubeflow Pipelines is a core component of Kubeflow and is also deployed when Kubeflow is deployed.

<img src="img/kubeflow-pipelines-dashboard.png" alt="OAuth consent screen." height=90% width=90% />

## Components of Kubeflow Pipelines
A Pipeline describes a Machine Learning workflow, where each component of the pipeline is a self-contained set of codes that are packaged as Docker images. Each pipeline can be uploaded individually and shared on the Kubeflow Pipelines User Interface (UI). A pipeline takes inputs (parameters) required to run the pipeline and the inputs and outputs of each component.

The Kubeflow Pipelines platform consists of:
- A user interface (UI) for managing and tracking experiments, jobs, and runs.
- An engine for scheduling multi-step ML workflows.
- An SDK for defining and manipulating pipelines and components.
- Notebooks for interacting with the system using the SDK.
(Taken from: <a href="https://www.kubeflow.org/docs/pipelines/pipelines-overview/">Overview of Kubeflow Pipelines</a>)

## Executing a Sample Pipeline

1. Click on the name **[Sample] Basic - Condition**.

<img src="img/select-a-simple-pipeline.png" alt="Select a simple pipeline." height=90% width=90% />

2. Click **Start an experiment**.

<img src="img/create-an-experiment.png" alt="Create an experiment." height=90% width=90% />

3. Give the Experiment a Name.

<img src="img/name-experiment.png" alt="Name the experiment." height=90% width=90% />

4. Give the Run Name.

<img src="img/run-experiment.png" alt="Name the run." height=90% width=90% />

5. Click on the **Run Name** to start the Run.

<img src="img/running-pipeline.png" alt="Running pipeline." height=90% width=90% />
