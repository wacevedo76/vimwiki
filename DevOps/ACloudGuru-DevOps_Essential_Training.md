--------------------------------------------------------------------------------
= acloudguru DevOps path Notes =
--------------------------------------------------------------------------------
== Defining DevOps ==
  DevOps                     | = Dev (Development) + Ops (Operations)
                             |
                             | Different people define DevOps in a variety of ways.
                             |
                             | This definition from Wikipedia is a good starting point
                             |
                             |   "DevOps is a software engineering culture and practice
                             |   aims at unifying software development and software
                             |   operations
                             |
                             |   DevOps aims at shorter development cycles, increased
                             |   deployment frequency, and more dependable releases,
                             |   in close alignment with busines objectives
                             |
--------------------------------------------------------------------------------
== Brief History of DevOps ==
  Agile Software Development | * DevOps grew out of the Agile software development
                             |   movement
                             | * Agile seeks to develop software in small,
                             |   frequent cycles in order to deliver
                             |   functionality to customers quickly andquickly
                             |   respond to chaning busin
                             |
                             | * DevOps and Agile often go hand-in-hand
                             |
  The Timeline of DevOps     | * 2007: Agile software development was gaining
                             |   popularity, but it was also suffering from a
                             |   growing divide between development and operations
                             |
                             | * 2007: Patrick Debois, an enginner with experience
                             |   doing both dev and ops, was doing testing on a
                             |   project and became frustrated by the huge divide
                             |   between dev and ops
                             |
                             | * 2008: Patrick Debois and Andrew Shafer met at the
                             |   Agile2008 Conference in Toronto, Canada. They
                             |   began to start conversations and seek others
                             |   interesten bridging the divide between dev and ops
                             |
                             | * June 23, 2009: John Allspawn and Paul Hammond gave
                             |   a talk to Velocity Conference: "10+ Deploys Per
                             |   Day: Dev and Ops Cooperation at Flickr." Patrick
                             |   was watching vial livestream. People began discussing
                             |   it via twiter.
                             |
                             | * October 30-31 2009: Patrick hosted the first DevOpsDays
                             |   in Ghent, Belgium; a conference for both devs and
                             |   ops engineers. The conversation continued on
                             |   Twitter:#devops
                             |
                             |
                             | * DevOps grew into an organic, grassroots movement
                             |   all over the world and spawned many tools to
                             |   support the practices valued by DevOps
                             |
--------------------------------------------------------------------------------
== Devops Essentials ==
  The Goals of DevOps        | Devops cultures is about collaboration between Dev and Ops
                             |
                             | Under the traditional separations between Dev and Ops
                             |   , Dev and Ops have different and opposing goals.
                             |
                             | * Development -> speed
                             | * Operations  -> Stability
                             |
                             | However, in a devOps culture
                             |   * Dev and Ops are playing on the same team
                             |   * Devn and Ops share the same goals
                             |
                             | These goals include things like:
                             |   * Fast time-to-market (TTM)
                             |   * Few production failures
                             |   * Immediae recovery from failures
                             |
                             | DevOps is a Dev and Ops working together.
                             |
  Why do build automation    | * Build automation is fast - Automation handles
                             |   tasks that would otherwis need to be done manually.
                             |
                             | * Build automation is consistent - The build happens
                             |   the same way every time, removing problems and
                             |   confusion that can happen with manual builds.
                             |
                             | * Buld automation is repeatable - The build can
                             |   be done multiple times with the same result.
                             |   Any version of the source code can always be
                             |   transformed into deployable code in a consistent way.
                             |
                             | * Buld automation is portable - The buld can be done
                             |   the same way on any machine. Anyone on the team
                             |   cab build on their macine, as well as on a shared
                             |   build server. Building code doesn't depend on specific
                             |   people or machines
                             |
                             | * Build automation is more reliable - There will be
                             |   fewer problems caused by bad builds
                             |
  What is Continuous         | * Continuous Intergration(CI): the practive of frequently
  Integration?               |   merging code changes done by developers
                             |
                             | * Traditionally, developers would worl separately, perhaps
                             |   for weeks at a time, and then merge all of their
                             |   work together at the end in one large effort
                             |
                             | * Continuous integration mens merging constantly throughout
                             |   the day, usually with the execution of automated
                             |   tests to detect any problems caused by the merge
                             |
                             | * Merging all the time could be a lot of work, so
                             |   to avoid that it should be automated
                             |
--------------------------------------------------------------------------------
== Infrastructure as Code (IaC) ==
  What is infrastructure as  | * Infrastructure as Code (IaC): manage and provision
  code?                      |   infrastructure through code and automation
                             |
                             | * With infrastructure as code, instead of doing
                             |   things manually, you use automation and code
                             |   to create and change:
                             |
                             |   * Servers
                             |   * Instances
                             |   * Environments
                             |   * Containers
                             |   * Other infrastructure
                             |
  What does infrastructure   | - Without infrastructure as code you might:
  as code look like?         |   * ssh into a host
                             |   * Issue a series of commands to perform the change
                             |
                             | - With infrastructure as code:
                             |   * Chance some code or configuration files that
                             |     can be used with an automation too to perform
                             |     changes
                             |
                             |   * Commit them to souce control
                             |
                             |   * Use an automation tool to enact the chanes
                             |     defined in the code and/or configuration files
                             |
                             | - With IaC, provisioning new resource and changing
                             |   existing resources are both done through automation
                             |
  Why do infrastructure as   | * Consistency in creation and management of resources -
  code?                      |   The same automation will run he same way every time.
                             |
   * Consistency             | * Reusability - Code can be used to make the same change
   * Reusability             |   consistently across multiple hhosts and can be
   * Scalability             |   used again in the future.
   * Self-documenting        |
   * Simplify the complexity | * Scalability - Need a new instance? You can have
                             |   one configured exactly the same way as  the
                             |   existing instances in minutes (or seconds).
                             |
                             | * Self-documenting - With LaC, changes to infrastructure
                             |   document themselves to a degree. The way a
                             |   server is configured can be viewed in source
                             |   control, rather than being a matter of who
                             |   logged in to the server and did something.
                             |
                             | * Simplify the complexity - Complex infrastructures
                             |   can be  stood up quickly once they are defined
                             |   as code. A group of several interdependent servers
                             |   can be provisioned on demand.
                             |
--------------------------------------------------------------------------------
== Configuration Management ==
  What is Configuration      | * Configuration Management: maintaining a changing
  management?                |   the state of pieces of infrastructure in a
                             |   consistend, maintainable, and stable way
                             |
                             | * Changes always need to happen - configuration
                             |   management is about doing themn in a maintainable
                             |   way
                             |
                             | * Configuration management allows you to minimize
                             |   configuration drift - the small changes that
                             |  accumulate ove rtime and make systems different
                             |  from one another nd harder to manage
                             |
                             | * Infrastructures as Code is very beneficial for
                             |   configuration managment
                             |
  What does configuration    | Here is an Example
  management look like?      | * You need ot upgrade a software package on a
                             |   bunch of servers:
                             |   * Without good configuration management, you
                             |     log on into each server and perform the upgrade.
                             |     However, this can lead to a lot of problems.
                             |     Perhaps one server was missed due to poor
                             |     documentation, or perhaps something doesn't
                             |     while the versions are temporarily mismatched
                             |     between servers, causing a lot of downtime
                             |     while you do the upgrade
                             |
                             |   * With good configuration management, you define
                             |     the new version of the software package in a
                             |     configuration file or tool and automatically
                             |     roll out the change to all of the servers.
                             |
                             | * Configuration management is about managing your
                             |   somewhere outside of the servers themselves
                             |
  Why do configuration       | * Save time - It takes less time to change the configuration.
  management?                |
                             | * Insight - With good configuration management,
  * Save time                |   you can know about the state of all pieces of
  * Insight                  |   large and complex infrastructure
  * Maintainability          |
  * Less configuration drift | * Maintainability - A more maintainable infrastructure
                             |   is easier to change in a stable way.
                             |
                             | * Less configuration drift - It is easier to keep
                             |   a standard configuration across a multitude of hosts
                             |
--------------------------------------------------------------------------------
== Orchestration ==
  What is Orchestration?     | * Orchestration: automation that supports processes
                             |   and workflows, such as provisioning resources
                             |
                             | * With orchestration, managing a complex infrastructure
                             |   is less like being a builder and more like
                             |   conducting an orchestra
                             |
                             | * Instead of going out and creating a pice of
                             |   infrastructure, the conductor simply signals
                             |   what needs to be done and the orchestra performs it:
                             |
                             |   * The conductor does not need to control every detail
                             |   * The musicians (automation) are able to perform
                             |     their piece with only a little bit of guidance
                             |
  What does Orchestration    | * Here is an example:
  look like?                 |   * A customer requests more resources for a web
                             |     service that is abot to see a heavy increase
                             |     in usage due to a planned marketing effort
                             |
                             |   * Instead of manually standing up new nodes,
                             |     operations engineers use an orchestration to
                             |     request five more nodes to support the service
                             |
                             |   * A few minutes later, the tool has five new nodes
                             |     up and running
                             |
                             | * A much cooler example:
                             |   * A monitoring too detects an increased load on the service
                             |
                             |   * An orchestration tool responds to this by spinning up
                             |     additional resources to handle the load
                             |
                             |   * When the load decreases again, the tool spins the
                             |     additional resources to handle the load
                             |
                             |   * When the load decreases again, the tool spins
                             |     the additional resources back down, freeing them
                             |     up to be used by something else
                             |
                             |   * Al of this happens while the engineer is getting coffee
                             |
  Why do orchestration?      | * Scalability - Resources can bequickly increased
                             |   or decreased to meet changing needs.
  * Scalability              |
  * Stability                | * Stability - Automation tools can automatically
  * Save time                |   respond to fix problems before users see them.
  * Self-service             |
  * Granular insigth into    | * Save time - Certain tasks and workflows can be
    resource usage           |   automaticaly respond to fix problems before users
                             |   see them
                             |
                             | * Save time - Certain tasks and workflows can be
                             |   automated, freeing up engineers' time
                             |
                             | * Granular insight into resouce usage - Orchestration
                             |   Tools give greater insight into how many resources
                             |   are being used by what software, services, or customers.
                             |
--------------------------------------------------------------------------------
== Monitoring ==
  What is Monitoring?        | * Monitoring: The collection and presentation of
                             |   data about the performace and stability of
                             |   services and infrastructure
                             |
                             | * Monitoring tools collect data over things such
                             |   as:
                             |
                             |   * Usage of memory
                             |   * CPU
                             |   * disk i/o
                             |   * Other reources over time
                             |   * Application logs
                             |   * Network traffice
                             |   * etc
                             |
                             | * The collected data is presented in various
                             |   forms, such as charts and graphs, or in the form
                             |  of real-time notifications about problems
                             |
  What does Monitoring look  | * Real-time notifications:
  like?                      |   * Performance on the website is beginning to
                             |     slow down
                             |   * A monitoring tool detects that response times
                             |     are growing
                             |   * An administrator is immediately notified and
                             |     is able to intervene before downtime occurs
                             |
                             | * Postmortem analysis:
                             |   * Something went wrong in production last night
                             |   * It's working now, but we don't know what caused it
                             |   * Luckily, monitoring tools collected a lot of data
                             |     during the outage
                             |   * With that data, developers and operations
                             |     engineers are able to determing the root cause
                             |     (a poorly performing SQL query) and fix it.
                             |
  Why do Monitoring?         | * Fast recovery - The sooner a problem is detected,
                             |
  * Fast recovery            | * Better root cause analysis - The more data you have,
  * Better root cause        |   the easier it is to determine the root cause of a problem
    analysis                 |
  * Visibility across teams  | * Visibility across teams - Good monitoring tools
  * Automated response       |   usefule data to both developers and operations
                             |   people about the perfomance of code in production.
                             |
                             | * Automated response - Monitoring data can be used
                             |   alongside orchestration to provide automated
                             |   responses to events, such as automated recovery
                             |   from failures.
                             |
--------------------------------------------------------------------------------
== Microservices ==
  What are Microservices?    | * Microservices: A microservice architecture breaks
                             |   an application up into a collection of small,
                             |   loosely-coupled services.
                             |
                             | * Traditionally, apps used a monolithic architecture.
                             |   In a monolithic architecture, all features and
                             |   services are part of one large appliation
                             |
                             | * Microservices are small: each microservice
                             |   implements only a small piece of an application's
                             |   overall functionality
                             |
                             | * Microservices are loosely coupled: different
                             |  microservices interact with each other using stable
                             |  and well-defined APIs. This means that they are
                             |  independent of one another
                             |
--------------------------------------------------------------------------------
== Continuous Integration ==
  What does Continuous       | * Continuous integration is ususally done with the
  Integration look like?     |   help of a CI server
                             |
                             | * When a developer commits a code change, the CI
                             |   server sees the change and automatically performs
                             |   a build, also executing automated tests.
                             |
                             | * The occurs multiple times a day.
                             |
                             | * If ther eis any problem with the build, the CI
                             |   server immediately and automatically notifies the
                             |   developers.
                             |
                             | * If anyone commits code that "breaks the build"
                             |   they are responsible for fixing the problem or
                             |   rolling back their changes immediately so that
                             |   other developers can continue working.
                             |
  Why do Continuous          | * Early detection of certain types of bugs - if
                             |   code doesn't compile or an automated test fails,
                             |   the developers are notified and can fix it and
                             |   can fix it immediately. The sooner these bugs
                             |   are detected, the easier tey are to fix?
                             |
                             | * Eliminate the scrable to integrate just before
                             |   a big release - The code is constantly merged,
                             |   so there is no need to do a big merge at the end
                             |
                             | * Makes frequet releases possible - Code is always
                             |   in a stat that can be deplolyed to production
                             |
                             | * Makes continuous testing possible - Sinse the
                             |   code can always be run, QA testers can get their
                             |   hads on it all throughout the development process
                             |   not just at the end
                             |
                             | * Encourages good coding practice - Frequent commits
                             |   encourages simple, modular code.
                             |
--------------------------------------------------------------------------------
== Continuous Delivery and Continuous Deployment ==
  What is Continuous Delivery| * Continuous Delivery (CD): the practice of
                             |   continuously maintaining code in a deployable
                             |   state
                             |
                             | * Regardless of whether or not the decision is
                             |   made to deploy, the code is always in a state
                             |   that is able to be deployed
                             |
                             | * Some use the terms continuous delivery and
                             |   continuous deployment interchangeably, o
                             |   or simply use the abbreviation CD
                             |
  What is Continuous         | * Continuous Deployment: the practice of frequently
  Deployment                 |   deploying small code changes to production
                             |
                             | * Continuous delivery is keeping the coe in a
                             |   deployable state. Continuous deployment is
                             |   actually doing the deployment frequently
                             |
                             | * Some companies that do continuous deployment
                             |   deploy to production multiple times a day
                             |
                             | * There is no standard for how often you should
                             |   deploy, but in general the more foten you
                             |   deploy the better!
                             |
                             | * With continuous deployment, deployments to
                             |   production are routine and commonplace.
                             |   They are not a big, scary event
                             |
--------------------------------------------------------------------------------
== DevOps Tools ==
  Some of the most popular   | Source for learning about DevOps tools
  Tools                      | https:/xebialabs.com/periodic-table-of-devops-tools/
                             |
  Build Automation Tools     | * Build automation - Automated processing of code
                             |   in preparation for deployment
                             |
                             | * What tools you use for build automation usually
                             |   depends on programming language and frameworks
                             |
                             | A few examples:
                             |   * Java - ant, maven, gradle
                             |   * Javascript - npm, Grunt, Gulp
                             |   * Make - widely used in Unix-based systems
                             |   * Packer - build machine images and containers
                             |
  Continuous Integration     | * Continuous Integration - Continuously merging
  Tools                      |   code into a single branch or mainline
                             |
                             | * Continuous Integration tools usually consist
                             |   of a server that integrates with source control
                             |
                             | * When source code is changed, the server responds
                             |   by executing an automated build
                             |
                    Jenkins: | * Open Source - fork of Hudson
                             |
                             | * Widely used
                             |
                             | * Java servlet-based
                             |
                   TravisCI: | * Open Source
                             |
                             | * Built around Github integration
                             |
                             | * Executes builds in clean VMs
                             |
                     Bamboo: | * Enterprise product by Atlassian
                             |
                             | * Out-of-the-box integration with otherAtlassian
                             |   products like JIRA and Confluence
                             |
--------------------------------------------------------------------------------
== Tools for Configuration Management ==
  Configuration Management   | * Configuration Management - Managing and changing
  Tools                      |   the state of pieces of infrastructure in a
                             |   consistent and maintainable way
                             |
                             | * Configuration management tols are a great way |
                             |   to implement infrastructure as code
                             |
                    Ansible: | * Open source
                             |
                             | * Declarative configuration
                             |
                             | * YAML configuration files
                             |
                             | * No control server needed - but Ansible tower
                             |   is available
                             |
                             | * No agents needed, just python and ssh
                             |
                    Puppet:  | * Declarative configuration
                             |
                             | * Manage state through a UI
                             |
                             | * Custom modules use Puppet DSL
                             |
                             | * Pushes changes to clients using a control
                             |   server and agents installed on clients
                             |
                       Chef: | * Procedural configuration
                             |
                             | * Agent/server
                             |
                             | * Uses Chef DSL
                             |
                       Salt: | * Declarative configuration
                             |
                             | * Agent (Minions)/server (master) - but can support agentless
                             |
                             | * Uses YAML
                             |
                             | * Support for event-driven automation
                             |
--------------------------------------------------------------------------------
== Tools for Virtualization and Containerization ==
  Virtualization Tools       | * Virtualization - Managing resource by creating
                             |   virtual machines rather than physical machines
                             |
                             | * Hypervisor - Runs on bare metal and manages
                             |   virtual machines (VMs)
                             |
                             | * Examples:
                             |
                             |   * VMWare ESX and ESXi
                             |
                             |   * Microsoft Hyper-V
                             |
                             |   * Citrix XenServer
                             |
  Containerization           | * Containers - Lightweight, isolated packages
                             |   containing everything needed to run a piece of
                             |   software
                             |
                             | * require fewer resources than VMs - VMs contain
                             |   and entire OS plus virtual versions of all
                             |   hardware
                             |
                             | * Containers have the bare minimum needed to run
                             |   the software
                             |
                             | * Docker - Docker is currently the leading container
                             |   technology
                             |
                             | * Containers are still relatively new but very
                             |   useful for DevOps!
                             |
--------------------------------------------------------------------------------
== Tools for Monitoring ==
  Monitoring Tools           | * Monitoring - Collecting and presenting data about
                             |  the state and performance of applications
                             |
                             | * There are different types of monitoring:
                             |   * Infrastructure monitoring - focuses on things
                             |     related to infrasctucture
                             |       * Examples: CPU, ram
                             |
              Term: (APM) -> |   * Application Performance monitoring(APM) focuses
                             |     on performance and stability of individual parts
                             |     on an application
                             |       * Examples: response time, logs
                             |
  Infrastructure Monitoring  | * SenSu
  Tools                      |   * Designed as a modern replacement for Nagios
                             |   * Server/agent
                             |   * Agents push data to an AMQP broker
                             |
                             | * NewRelic
                             |   * SaaS + agent
                             |   * Wide variety of metrics (also does APM)
                             |
  Application Performanc     | * AppDynamics - Collects data points about applications
  Monitoring Tools           |   and presents it in a centralized dashboard
                             |   * Code-level diagnostics - Able to identify
                             |     performace issues at the code level.
                             |   * Server/agent
                             |
                             | * NewRelic (APM)
                             |
  Aggregation and Analytics  | * Aggregation nand Analytics are about collecting
  Tools                      |   monitoring data and doing something with it
                             |
                             | * Most monitoring tools have some aggregation
                             |   and analytics features
                             |
                             | * Elastic Stack - pump data in a nd quickly
                             |   create viewws to aggregate data and easily
                             |   detect and diagnose problems
--------------------------------------------------------------------------------
== Tools for Orchestration ==
  Orchestration Tools        | * Orchestration - automation that supports processes
                             |   and workflows, such as provisioning resources
                             |
                             | * Lets you do things like:
                             |   * Scale up and scale down applications
                             |   * Auto scale applications based on use
                             |   * Create self-healing systems by spinning down
                             |     unhealthy nodes and replacing them with new ones
                             |
                             | * Docker Swarm:
                             |   * Docker-native
                             |   * Orchestration for Docker containers
                             |
                             | * Kubernetes
                             |   * Open source
                             |   * Orchestration server
                             |   * Manage containerized apps across multiple hosts
                             |
                             | * Zookeeper
                             |   * Open source - Apache foundation
                             |   * Can work alongside Kubernetes
                             |   * Offers a centralized servie registry that
                             |     integrates with orchestration features
                             |
                             | * Terraform:
                             |   * Combines orchestration and infrastructure-as-code
                             |   * Works well with other tools, like Ansible
                             |   * Works well with AWS
                             |   * Integrates with Kubernetes
                             |
--------------------------------------------------------------------------------
== DevOs and the Cloud ==
                             | * DevOps and the Cloud are not the same thing:
                             |   * DevOps - a culture of collaboration between
                             |     Dev and Ops
                             |   * The Cloud - remote servers on the internet
                             |     that offere services in place of locally-hosted
                             |     solutions. "The cloud is someone else's computer"
                             |
                             | * DevOps culture and practices are very useful in
                             |   the world of the cloud
                             |
                             | * DevOps and the Cloud developed alongside each
                             |   other, and many cloud services are built on
                             |   DevOps practices
                             |
                             | * They can also be a tool for DevOps. Many cloud
                             |   services offer features that support DevOps
                             |   practices
                             |
                             | * a traditional stack is a regulare, self-hosted
                             |   data center
                             |
                             | * In a traditional stack, you are responsible for
                             |   every layer of the architecture
                             |
                             | * You provide all of the infrastructure necessary
                             |   to run your apps
                             |
                             | Infrastructure as a Service
                             |   * With infrastructure as a Service (Iaas), someone
                             |     else provides the low-level infrastructure
                             |   * The cloud service provider gives you a bare OS
                             |   * You are responsible for all installation and
                             |      and configuration above the OS level.
                             |
                             |   * Examples
                             |       * Amazon ec2 instances
                             |       * Microsoft Azure VMs and containers
                             |       * Google Compute Engine
                             |
                             | Platform as a Service
                             |
                             |   * With Plaform as a Service (PaaS), everything
                             |   * The cloud service provider gives you a way to
                             |     deploy an app and use databases
                             |   * You are only responsible for managing the app and data
                             |
                             |   * Examples:
                             |     * AWS Elastic Beanstalk
                             |     * Heroku
                             |     * Google App Engine
                             |
                             | Software as a Service
                             |   * With Software as a service (Saas), everything is managed
                             |   * The cloud service provider give you an appliation
                             |     ready for use
                             |   * You are only responsible for using the application
                             |
                             |   * Examples
                             |     * G-mail
                             |     * Microsoft Office 365
                             |
                             | Serverless
                             |   * Serverless is also know as Function as a Service (FaaS)
                             |   * Serverless is different from the traditional
                             |     application architecture
                             |   * Everything is abstracted. YOu deploy small, single-purpose
                             |     functions
                             |   * You pay for the compute resource used by your functions
                             |
                             |   * Examples:
                             |     * AWS Lambda (AWS Serverless Platform)
                             |     * Azure functions
                             |     * Google Cloud Functions
                             |
                             |  Traditional           Iaas Stack         PaaS Stack          Serverless Stack
                             |  Non-Cloud Stack
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `|Application     |  |Application     |  |Application     |  | Functions      |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Data           |  | Data           |  | Data           |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Runtime        |  | Runtime        |  | Runtime        |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Middleware     |  | Middleware     |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| O/S            |  | **IaaS**       |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Virtualization |  | **IaaS**       |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Servers        |  | **IaaS**       |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Storage        |  | **IaaS**       |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `| Network        |  | **IaaS**       |  | **PaaS**       |  | **Serverless** |`
                             |  `+----------------+  +----------------+  +----------------+  +----------------+`
                             |  `                                                            | **Serverless** |`
                             |  `                                                            +----------------+`
                             |
--------------------------------------------------------------------------------
== DevOps and Google Cloud Platform ==
  Google App Engine (PaaS)   | * PaaS - Deploy your code, don't worry about the rest
                             | * Built-in support for microservices
                             | * Out-of-the box autoscaling
                             | * Certain configurations can be considered serverliess
                             |
  Google Compute Engine      | * IaaS - Deploy and orchestrate clusters of VMs on
  (Iaas)                     |   Google's architecture
                             | * Built-in orchestration
                             | * Works with app engine
                             | * Can be managed with other tools like Ansible,
                             |   Salt, Puppet, and Chef
                             |
  Google Cloud Functions     | * Google's FaaS/Serverless solution
  (Serverless/FaaS)          | * Quickly and easily create and deploy FaaS functions
                             |
                             |
  Google Cloud SDK           | * An SDK (Software development kit) for interacting
                             |   with GCP APIs
                             | * Makes it easy to build your own tools and automations
                             |   that interact with GCP
                             |
  Stackdriver (Monitoring)   | * GCP's monitoring solution
                             | * Monitoring, logging, and diagnostics for your
                             |   GCP services
                             | * Also works within AWS
                             |
  Cloud Deployment Manager   | * Declarative configuration for your GCP stack
                             | * IaC and automated deployment
                             | * YAML-based
                             |
  Google Kubernetes Engine   | * Orchestration on GCP with Kubernetes
                             | * Do continuous integration with Jenkins on
                             |   Kubernetes Engine
                             |
--------------------------------------------------------------------------------
== DevOps and Microsoft Azure ==
  MicrosoftAzure DevOps      |
  features                   |
                             |
  Continuous Integration,    | * Visual Studio Team Services - souce control
  Delivery, and Deployment:  |   and CI
                             | * Jenkins - CI for Java apps
                             | * Continuous Deployment Triggers - Automated
                             |   deployment triggers integrated with CI
                             |
  Orchestration:             | * Azure Container Registry - repository of
                             |   container images
                             | * Azure Container Service - Kumbernetes orchestration
                             | * Azure Web Apps - Cloud hosting for web apps
                             |   integrated with DevOps pipeline
                             |
  Monitoring                 | * Azure Application Insigth - APM, diagnostics,
                             |   and analytics. Supports machine learning
                             |
  FaaS/Serverless            | * Azure Functions -autoscaling, serverless functions
                             |   in Azure
                             |
--------------------------------------------------------------------------------
== DevOps and Amazon Web Services ==
  Amazon Web Services Devops |
  Features                   |
                             |
  Amazon EC2                 | * IaaS
  (Elastic Compute Cloud):   | * Easily Scalable
                             | * Full control over your cloud infrastructure
                             | * Inegrates with tons of tools, both AWS and 3rd-party
                             |
  AWS Elastic Beanstalk:     | * PaaS
                             | * Out-of-th-box load balancing and autoscaling
                             | * Can still access underlying AWS resouces with
                             |   full control
                             |
  Continuous integration,    | * AWS CodeBuild - continuous integration
  Delivery, and Deployment   | * AWS CodeDeploy - continuous deployment
                             | * AWS CodePipeline - full code pipeline from build to deploy
                             | * AWS CodeStar - integrates all parts of the
                             |   process with project management tools and JIRA
                             |   issue tracking
                             |
  Infrastructure as Code:    | * CloudFormation - Stack templating engine, YAML or JSON based
                             | * OpsWork - IaC with Chef
                             |
  Serverless/FaaS:           | * AWS Lambda - run serverless functions on AWS
                             |
  Monitoring:                | * Amazon Cloudwatch - track metrics and logs, set
                             |   alarms, and automate responses to monitoring
                             |
DevOps Essentials Certificate of Completion
https://verify.acloud.guru/7AC0C4CDB87D
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
