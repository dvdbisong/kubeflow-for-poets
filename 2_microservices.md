# Microservies Architecture

The Microservice architecture is an approach for developing and deploying enterprise cloud-native software applications that involve separating the core business capabilities of the application into decoupled components. Each business capability represents some functionality that the application provides as services to the end-user. The idea of Microservices is in contrast to the Monolithic architecture which involves building applications as a composite of its "individual" capabilities.

<img src="img/monolith_vs_microservice.png" align="left" alt="Monolith vs. Microservice Architecture."/>

Microservices interact with each other using Representational state transfer (REST) communications for stateless inter-operability. By stateless, we mean that <a href="https://stackoverflow.com/a/3105337/3353760">"the server does not store state about the client session"</a>. These protocols can be HTTP request/response APIs or an asynchronous messaging queue. This flexibility allows the microservice to easily scale and respond to request even if another microservice fails.

## Advantages of Microservices
- Loosely coupled components make the application fault tolerant.
- Ability to scale-out making each component highly-available.
- Modularity of components makes it easier to extend existing capabilities.

## Challenges with Microservices
- The software architecture increases in complexity.
- Overhead in management and orchestration of microservices. We will, however, see in the next sessions how Docker and Kubernetes work to mitigate this challenge.