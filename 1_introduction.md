# Introduction

Machine learning is often and rightly viewed as the use of mathematical algorithms to teach the computer to learn tasks that are computationally infeasible to program as a set of specified instructions. However, the use of these algorithms happen to constitute only a tiny fraction of the overall learning pipeline from an Engineering perspective. Building high-performant and dynamic learning models includes a number of other critical components. These components actually dominate the space of concerns for delivering an end-to-end machine learning product.

A typical machine lerning production pipeline looks like the illustration below.

<img src="img/ml_pipeline.png" align="left" alt="Machine Learning Pipeline."/>

From the above diagram, observe that the process flow in the pipeline is iterative. This repititve pattern is central to machine learning experimentation, design and deployment.

## The Challenge
It is easy to recognize that the pipeline requires a significant amount of development operations for the seamless transition from one component to another when building a learning model. This interoperability of parts has gave rise to Machine Learning Ops, also know as MLOps. The term is coined as an amaglam of Machine Learning and DevOps.

The common way of doing machine learning is to perform all of the experiment and development work in Jupyter notebooks and the model is exported and sent off to the 


<!-- that if overlooked can very much result in a poor or under-performing model. -->