--------------------------------------------------------------------------------
= Orchestration =
--------------------------------------------------------------------------------
  == What is Orchestration ==
                             | *Container Orchestration* simply refers to processes
                             | used to manage containers and o automate the
                             | management of containers
                             |
                             | For example:
                             | * I want to start up a set of five ocntainers in production
                             | * I could spin up each container manually.
                             | * or, I could tell and *orchestration tool* like
                             |   *Kubernetes* that I want five containers, and
                             |   let the tool do it.
                             |
                             | For the sake of redundancy, it's a good idea to
                             | spin up my five containers on five different hosts
                             |
                             | The *more complex* my requirements for managing
                             | become, the *more useful* my orchestration tools
                             | become.
                             |
  Another Example:           | In the old days, deployments went like this:
    Zero-Downtime-Deployments|   1. Take he server down for maintenance (it is unavailable to customers)
                             |   2. Perform the deployment
                             |   3. Bring the server back up
                             |
                             | A *zero-downtime deployment* (with containers) goes like this:
                             |   1. Spin up containers running the new code.
                             |   2. When they are fully up, direct user traffic to he new containers
                             |   3. Remoe the old containers running the old code. No downtime for users
                             |
                             | How do you coordinate those steps quickly and efficiently?
                             | *Orchestration tools* can do it for you.
                             |
--------------------------------------------------------------------------------
== What are containers used for? ==
  Containers are great at    | * *Software Portability* - Running software consistently
  accomplishing things like: |   on different machines
                             | * *Isolation* - Keeping individual pieces of software
                             |   separate from one another
                             | * *Scaling* - Increasing or decreasing resources
                             |   allocated to software as needed
                             | * *Automation* - Automating processes to save time and money
                             | * *Efficient Resource Usage* - Containers use resources
                             |   efficiently, which saves money
                             |
--------------------------------------------------------------------------------
== Advantages and Limitations of Containers ==
  Advantages of Containers   | These are a few of the main advantaes of containers:
                             | * The *isolation* and *portability* of VMs.
                             | * More *lightweight* than VMs - Less resource usage
                             | * *Faster* than VMs - Containes can start up in seconds, not minutes
                             | * *Smaller* than VMs - Container images can be measured in megabytes, not gigabytes
                             | * All of these add up to faster and simpler automation.
                             |
  Limitations of Containers  | These are some limitations of containers:
                             | * *Less flexibility* than VMs - You can't run a Windows container on a Linux machine (yet)
                             | * Introduces *new chalenges* around orchestration and automation
                             |
--------------------------------------------------------------------------------
== What is Docker? ==
  Docker                     | *Docker* is primarily a *container runtime*
                             |
                             | This means that Docker is a piece of software that
                             | is designed to implement and support containers
                             |
                             | At its core, Docker allows you to run containerson
                             | systems. It also offers a variety of tools for
                             | creating and managing *containers* and *container images*
                             |
                             | It is currently the industry leader in container runtimes
                             |
--------------------------------------------------------------------------------
== What about other container runtimes? ==
  Container Runtimes         | Docker is not the only option for doing containers
                             |
                             | Here are some other competitive container runtimes:
                             |
      rkt                    | * *rkt*
                             |   Created by CoreOS, "designed with composibility
                             |   and security in mind".
                             |
      containerd             | * *containerd*
                             |   Emphasizes "simplicity, robustness, and portability".
                             |
--------------------------------------------------------------------------------
== What is Kubernetes? ==
  Kubernetes                 | *Kubernetes* is a container orchestration tool
                             |
                             | It allow you to easily build and manage your
                             | continer infrastructure and automation.
                             |
                             | Do you want things like self-healing applications,
                             | automated scaling, and easy automated deployments?
                             | Then you should definately look into Kubernetes
                             |
--------------------------------------------------------------------------------
== What about other orchestration solutions? ==
  Container Orchestration    | Kubernetes is not the only container orchestraion
  Solutions                  | tool
                             |
                             | Here are some other popular ones:
                             | * *Docker Swarm*
                             |   Docker's native container orchestration solution
                             |
                             | * *Marathon*
                             |   Base on Apace Mesos, offers APIs for integrating
                             |   with other tools
                             |
                             | * *Nomad*
                             |   Open source and built by HashiCorp, designed to
                             |   be simple and lightweight
                             |
  Cloud Orchestration        | *Cloud providers* such as Amazon Web Services,
  Solutions                  | Mircosoft Azure, and Google Cloud Platform also
                             | offer built-in orchestration solutions, including
                             | cloud-native Kubernetes implementations
                             |
                             | For example:
                             | * Amazon Elastic Container Service
                             | * Amazon ECS for Kubernetes
                             | * Azure Kubernetes Service
                             | * Google Kubernetes Engine
                             |
--------------------------------------------------------------------------------
== Microservises ==
  what are Microservices?    | *Microservices* are a type of application
                             | architecture that involves splitting the application
                             | into a series of small, independent services
                             |
                             | Microservices can be *buit*, *modified*, and *scaled*
                             | seperately, with relatively little impact on one
                             | another.
                             |
  Containers and             | *Containers* excel when it comes to managing a
  Microservices              | large number of small, independent workloads
                             |
                             | Containers and orchestration make it easier to
                             | manages and automate the process of deploying,
                             | scaling, and connecting lost of microserice
                             | instances
                             |
                             | For example, I may have one microservice that needs
                             | *additional resources*. With containers, all I need to
                             | do is create more containers for that service to
                             | handle the load. With *orchestration*, that can even
                             | be done *automatically* and in real time
                             |
--------------------------------------------------------------------------------
== Cloud Transformation ==
  What is                    | *Cloud Transformation* is the process of migrating
   Cloud Transformation?     | your existing IT infrastructure to the cloud.
                             |
                             | Many companies today are making the transition
                             | away from locally-hosted services and toward
                             | services hosted in the cloud
                             |
                             | However, moving your infrastructure into the cloud
                             | can come with challenges.
                             |
                             | Since containers use fewere resource than VMs,
                             | you can save money on cloud resources
                             |
--------------------------------------------------------------------------------
== Automated Scaling ==
  What is Automated Scaling? | *Automated Scaling* refers to automatically provisioning
                             | resources in response to real-time data metrics
                             |
                             | Without automated scaling, you must provision
                             | enough resources to cover your peak resource needs
                             | at all times
                             |
                             | If I need 10 servers to handle my peak usage itmes,
                             | then I need 10 servers all the time
                             |
                             | With *automated scaling*, you can automatically
                             | detect (or even predict) increase in usage. The
                             | automated system creates new servers to handle the
                             | peak usage time then remove those servers wen usage
                             | returns to normal levels
                             |
  Containers and Automated   | *Automated scaling* depends on the ability to spin
  Scaling                    | up new instances *quickly* and *efficiently*.
                             |
                             | Since containers ar small and can start up quickly,
                             | they are ideal for this purpose. This means that if
                             | the system detects and increase in usage, it can
                             | spin up new containers in a few seconds
                             |
                             | This *increases stability* and *reduces costs*.
                             | Your users see less downtime due to the high loads,
                             | and you don't use (and pay for) resources
                             | unnecessarily.
                             |
--------------------------------------------------------------------------------
== Continuous Deployment Pipelines ==
  What is Continuous         | *Continuous Deployment* is the practice of deploying
  Deployment?                | new code automatically and frequently
                             |
                             | Instead of writing new code for months and doing
                             | a big deployment, continuous deployment means
                             | constantly doing many small deployments. Some
                             | companies even do multiple deployments a day
                             |
                             | This allows you to get *new functionality* in front
                             | of customers faster, and it also *reduces the risk*
                             | associated with big deployments containing a large
                             | number of changes
                             |
                             | To maintain *stability* while doing continuous
                             | deployment, it is important to make use of
                             | *automation* to ensure that deployments are
                             | stable and consistent
                             |
  Containers and Continuous  | *Containers* work very well in the context
  Deployment                 | of *continuous deployment*.
                             |
                             | They make it easy to test code in an environment
                             | that is the same as production, because the code
                             | can be automatically tested inside the container
                             | itself.
                             |
                             | An *automation pipeline* for continuous delivery
                             | can automatically build a container image with
                             | the new code, test it, then automatically ship
                             | that same container image to production.
                             |
                             | Because the production environment (the container)
                             | is built right into this automated process, developers
                             | even have the ability to use it for testing and
                             | troubleshooting
                             |
--------------------------------------------------------------------------------
== Self-HealingApplications ==
  What are Self-Healing      | *Self-Healing Applications* are applications that
  Applications?              | are able to automatically detect when something is
                             | broken and automatically take steps to correct the
                             | problem without the need for human involvement
                             |
                             | System administrators will tell you that, in the
                             | past, it was often very ocmmon to have to wake up
                             | in the middle of the night to reboot a server.
                             |
                             | What if an *automated system* could detect a problem
                             | and reboot the server automatically? That's an
                             | example of *self-healing*
                             |
  Containers and Self-Healing| Since *Containers* start up quickly, It's easy
  Applications               | enough to automatically restart them.
                             |
                             | However, containers take the concept of rebooting
                             | the server a step farther.
                             |
                             | Since it is so quick and easy to start up new
                             | containers instances, when something goes wrong
                             | with a container it can often be easily *destroyed*
                             | and *replaced* within a few seconds.
                             |
                             | That means that if something goes wrong, you can
                             | have a brand new, clean, working instance quickly
                             | replace the broken one.
                             |
--------------------------------------------------------------------------------
== Developer Visibility ==
  Developer Visibility       | In more traditional environments, it can be
                             | *difficult* for everyone to get access to a
                             | production system to troubleshoot when something
                             | goes wrong
                             |
                             | That may be due to security concerns, or simply
                             | due to the fact that when something goes wrong,
                             | the first priority is to fix it as quickly as
                             | possible, not to find out why it happened
                             |
                             | Anyone in the organization that does not hae
                             | direct access to a production system has no idea
                             | why code may or may not be working in production
                             |
                             | This leads to the constant refrain, "Well, *it*
                             | *works on my machine*".
                             |
  Containers and Visibility  | With *Containers*, the container _is_ the
                             | the production environment
                             |
                             | This means that anyone can spin up an environment
                             | that is exactly like production, even on their own
                             | laptop.
                             |
                             | Developers (and others) have the ability to test
                             | the node and see exactl how it will behave in
                             | production
                             |
                             | The additional *visibility* offered by containers
                             | can help your organization develop and troubleshoot
                             | code much more efficitently
                             |
--------------------------------------------------------------------------------
== Doing Containers in the Cloud ==
  What is the Cloud?         | *The Cloud* can be an ambiguous term, but it
                             | usually just means "someone elses' computer"
                             |
                             | Instead of running software and hosting services
                             | in your own datacenter, *being in the cloud* means
                             | that you are running software in a romete datacenter
                             | over the internet
                             |
                             | Typically, this means that you pay a *cloud provider*
                             | such as Amazon (AWS), Microsoft (Azure), or Google
                             | (GCP), and thy provide you with servers and resources
                             | with which to run your software
                             |
                             | The term "*cloud*" can also refer to running software
                             | in your own datacenter using the tools and practices
                             | that are associated with the cloud. This is sometimes
                             | called *private cloud*
                             |
  What does it mean to do    | There are many ways to run software in the cloud.
  containers in the Cloud?   | Tis includes running *containers* on servers hosted
                             | by a cloud provider
                             |
                             | Doing containers in the cloud simply means that
                             | you are running containers on servers in the cloud
                             |
                             | Most cloud providers, including *Amazon Web Services*,
                             | *Micronsoft Azure*, and *Google Cloud Plateform*,
                             | provide services which are specifically designed,
                             | around containers, offering you the ability to run
                             | containers in the cloud quickly and easily
                             |
--------------------------------------------------------------------------------
== The benefits of Containers in the Cloud ==
  Why do Containers in the   | Containers are just one way ot run software
  Cloud?                     | in the cloud
                             |
                             | some of the benefits of using containers in the
                             | cloud are:
                             |   * *Regular Benefits of Containers*
                             |     you get all the normal benefits of containers
                             |     in terms of portability, speed, and ease of
                             |     automation
                             |
                             |   * *Save Money*
                             |     Since containers are lightweight and have
                             |     little overhead, they can help save on cloud
                             |     costs. With cloud providers, you only pay for
                             |     resources you use. Use less resources, pay less
                             |
                             |   * *Cloud Platforms Offer Container Support out of the Box*
                             |     Most cloud platforms provide services built
                             |     Specifically for containers
                             |
--------------------------------------------------------------------------------
