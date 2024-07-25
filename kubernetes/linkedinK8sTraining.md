## Docker
### Terms 
Container:
  A collection of software processes unified by one namespace,
  with access to an operating system kernel that shares with
  other containers and little to no access between containers

Docker Instance:
  A runtime instance of a Docker image contains three things:
  1. A docker image
  2. An execution environment
  3. A standard set of instructions

1. Docker Engine:
  - Comprised of the runtime and packaging tool
  - Must be installed on the host that run Docker
2. Docker Store:
  - An online cloud service where users can store and share
    Docker images
  - Also known as Docker Hub

Container Benefits for Developers
  Applications are
  1. Portable
  2. Packaged in a standard way

  Deployment is
  1. Easy
  2. Repeatable

  - Automated testing, packaging and integrations
  - Support newer microservice architectures
  - Help alleviate platform compatibility issues

Container Benefits for DevOps
  - Reliable deployments:
    improve speed and frequency of releases
  - Consisten application lifecycle: configure once
    and run multiple times

  Consistent environments
  - No more process differences between dev and
    production environments
  Simple Scaling
  - Fast deployments ease the addition of workers and
    permit workload to grow and shrink for on-demand
    use cases
Allow the Building of Pipelines
  - Containers brin agility to your code
  - help build a continuous integration and deployment
    pipeline
  - Push an IT team to develop, test, and deploy
    applications faster
  - Reason why enterprises have started to adopt
    containers is such a big way

## Kubernetes
## Features 
  Multi-Host Container Scheduling
  - Done by the kube-schedule
  - Assigns pods to nodes at runtime
  - Checks resources, quality of service, policies,
    and user specifications before scheduling
  Scalability and Availability
  - Kubernetes maste can be deployed in a highly
    available configuration

  Scalability (v1.17)
  - Supports 5000 node clusters
  - 150,000 total pods
  - Maximum of 100 pods per node
  - Pods can be horizontally scaled via API

  Flexibility and Modularization
  - Plug-and-play architecture
  - Extend architecture when needed
  - Add-ons: network drivers, service discovery,
    container runtime, visualization, and command

  Registration
  - Seamless nodes register themselves with master

  Service Discovery
  - Automatic detection of services and endpoints via
    DNS or environment variables

  Persistent Storage
  - Much requested and importan feature when working
    with containers
  - Pods can use persistent volumes to store data

  Application Upgrades and Downgrades
  - Upgrades: rolling updates supported
  - Downgrades: rollback are supported

Kubernetes Architecture Overview
Master Node
  - The API Server
  - Scheduler
  - Controller Manager
