--------------------------------------------------------------------------------
= AWS Certified Cloud Practitioner Exam Notes =
--------------------------------------------------------------------------------
== Cloud Concepts ==
  The six advantages of      | * Trade fixed expense for variable expense
  cloud computing            | * Benefit from massive economies of scale
                             | * Stop guiessing capacity
                             | * Increase speed and agility
                             | * Stop spending money running and maintaining data centers
                             | * Go global in minutes
                             |
    Terms associated         | * Capital Expense (CAPEX)
                             | * Variable expense / Operating expense (OPEX)
                             |
--------------------------------------------------------------------------------
== Cloud Computing Modes ==
 Infrafrastructure as a      | Contains the basic building blocks for cloud IT
 Service (IaaS)              |   Eg. VPC, EC2, EBS
                             |
                             | can be defined as a type of cloud computing which
                             | provides virtualized computing resources over the
                             | internet
                             |
 Platform as a Service (PaaS)| AWS manages the underlying infrastructure
                             |   (usually hardware and operating systems)
                             |   Eg. RDS, EMR, ElasticSearch
                             |
                             | Platform as a service is a complete development
                             | and deployment environment in the cloud, with
                             | resources that enable you to deliver everything
                             | from simple cloud based apps to sophisticated,
                             | cloud enabled enterprise applications.
                             |
 Software as a Service (SaaS)| Completed product that is run and managed by the
 (Serverless Computing)      |   service provider. Mostly referes to end-user
                             |   applications:
                             |     Eg, Web-based email, Office 365, Salesforce.com
                             |
                             | SaaS is a method of software delivery and
                             | licensing n which software is accessed online
                             | via a subscription rather than bought and
                             | installed on individual computers
  Scope of Responsibility    |
  Shared Responsibility Model|
  Terms                      |
    Application and Data     | Application and the data that are taken from users
                             |
    Runtime                  | The environments in which our code runs
                             |
    Middleware               | The interface for our software
                             |
    Operating System         | The operating system that is running on the
                             | virtualization software
                             |
    Virtualization           | With virtualization, we can manage resources,
                             | privacy and security of users using the same
                             | hardware.
                             |
    Servers, storage and     | The hardware that we need and the interconnections
    networking.              | between them
                             |

  On premise is a computing model where all of the necessary components are
  managed by those whom implement.

  IAAS, PASS and SAAS are computing (cloud) models where certain aspects of
  the infrustructure are managed by you, and others are managed by the model's.
  provider.  If an aspect is not included in the model, it means that it is
  managed by the provider and outside the scope of responsibility of the user.

 On Premise          IAAS                PAAS                SAAS
`+----------------+  +----------------+  +----------------+  +----------------+`
`|  Application   |  |  Application   |  |  Application   |  |                |`
`|    Data        |  |    Data        |  |    Data        |  |                |`
`|  Runtime       |  |  Runtime       |  |                |  |                |`
`|  Middleware    |  |  Middleware    |  |                |  |                |`
`|    O/S         |  |    O/S         |  |                |  |                |`
`| Virtualization |  |                |  |                |  |                |`
`|   Servers      |  |                |  |                |  |                |`
`|   Storage      |  |                |  |                |  |                |`
`| Networking     |  |                |  |                |  |                |`
`+----------------+  +----------------+  +----------------+  +----------------+`

--------------------------------------------------------------------------------
== AWS Global Infrastructure ==
  (Geographic) Regions       |
  Availability Zones         |
  Local Zones                |
  Edge Locations (CloudFront)|
  Wavelength                 |
  Ground Station             |
  Project Kuiper             |
                             |
  AWS Regions                | * An AWS Region is a physical location where AWS
                             |   will host a cluster of data centers
                             | * Within a given Region, these data centers are
                             |   built such that small groups of the larger
                             |   clusters are logically and physically separated
                             |   from each other by a distance that falls within
                             |   100 kilometers of each other
                             | * Each region contains two or more availability zones
                             | * AWS has 22 regions worldwide and increasing
                             |
  AWS's Multi-Region         | AWS's multi-Region strategy enables you (the
  strategy                   | customer) to derive the follwing benefits:
                             | * Identify inrastructure resources closer to your
                             |   end users, where you can host your application
                             |   and reduce network latency
                             | * Identify infrastructure within political and
                             |   national borders to adhere to strict data
                             |   sovereignty and compliance regulations
                             | * Isolate groups of resources from each other to
                             |   allow you to fulfill any failover or DR
                             |   scenarios in j
                             |
  Availability Zone          | * AZs are the logical and physical grouping of
                             |   data centers within a given Region
                             |
                             | * AWS Data Centers are organized into Availability
                             |   Zones
                             |
                             | * Each availability zone is located at low-risk
                             |   locations.
                             |
                             | * There are multiple AZ and each of them is
                             |   separate by geographic regions
                             |
                             | * Each AZ is designed for independent failure zone
                             | * Thus, they are physically separated
                             | * The AZ are interconnected with high speed private links
                             |
  Edge Locations             | * In addition to Regions and AZs, AWS also offers
                             |   Another type of hosting service, called *Edge Locations*.
                             |   These Edge locations also host a the physical
                             |   Server infrastructure, masive amounts of storage
                             |   Devices, and high-bandwidth networking equipment
                             |    In addition, AWS edge computing services provide
                             |   Infrastructure and software that enable data to
                             |   Be processed and analyzed closer to the end customer
                             |   This includes deploying AWS0managed hardware and
                             |   Software to locations outside AWS data centers, and
                             |   Even onto customer-owned devices themselves.
                             |
                             | * With Edge locations, you can cache frequently
                             |   accessed files on servers located closer to users
                             |
                             | * Edge locations are connected to AWS Regions through
                             |   the AWS backbone entwork. This comprises fully redundant
                             |   multiple 100 Gigabit Ethernet parallel fiber connections.
                             |
  Regional Edge Caches       | * Regional Edge Caches have more storage and offer
                             | large cache sizes.
                             |
  CloudFront                 | Amazon's CloudFront is a CDN service designed to
                             | help you create distribution points for your content
                             |  The distribution points are created at thes Edge
                             | Locations in each Region.
                             |
*Global Services*              | Although most services are Region-based, there
                             | are some services that fall under the category of
                             | global services:
                             |
  Identity and Access        | A service offered by AWS to enable you to grant
  Management (IAM)           | access to services and resources in your AWS Account
                             | AWS IAM allows you to create IAM users for your
                             | staff who need to access to those services, define
                             | permissions, configure groups, and set up roles
                             |
  Amazon CloudFront          | A CDN service that allows you to create distribution
                             | points for your content for a specific origin server.
                             |
  Amazon Route 53            | A highly available, scalable, and fully managed
                             | cloud Domain Name System. You can use Route 53 to
                             | register new domain names, configure domain records
                             |  and design global routing policies for various
                             | use cases, such as an active/passive solution for
                             | building a highly available solution.
                             |
  Amazon S3                  | Although Amazon S3 buckets need to be created in
                             | each Region and those buckets are therefore Region
                             | specific, the service itself is presentd as a global
                             | service.
                             |
*On-premises services*         | Although AWS is a publiccloud vendor, they also
                             | provide certain services that are hosted at their
                             | clients' data centers on-premises. On-premises services
                             | are intended to also facilitate a hybrid cloud deployment
                             | solution. whereas other on-premises serices can
                             | be used to help migrate data from local data centers
                             | to the AWS cloud via offline routes where bandwidth
                             | constraints may be an issue.
                             |
  Amazon Snow Family         | These are physical enclosure units that contain
                             | solid-state drives, compute hardware, and networking
                             | components that are shipped to client sites.
                             |
                             | The AWS Snow Family ccomprises of:
                             | * Snowball Edge Devices
                             | * Snow
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
--------------------------------------------------------------------------------
== Deployment Models of the Cloud ==
  Private Cloud              | A private cloud, also known as internal or
                             | corporate cloud, is dedicated to the needs and
                             | goals of a single organization
                             |
                             | It is owned by the company which implemented it.
                             |
                             | This allows the organization to manage their
                             | sensitive data themselves, rather than b a third
                             | party
                             |
                             | These organizations coube be financial
                             | institutions, hospitals, security agencies,
                             | government establishments and so on.
                             |
                             | The private cloud is managed directly in the data
                             | center provided by the organization, in some
                             | other cases, it is provided by a third party
                             | cloud platform like AWS or google cloud platform
                             |
    Advantages               | * It is more secure
                             | * There is more control over all the resources
                             | * Performance level is also high as no resources
                             |   aren't being shared
                             |
  Public Cloud               | They are cloud resources wone and operated by a
                             | third part cloud service provider and they
                             | deliver their services over the internet
                             |
                             | It is a multi tenant environment
                             |
    Advantages               | * Easy access to new technology
                             | * It is cheap (in comparison to the private cloud model)
                             | * Easy to scale globally in a very hsort period of time
                             |
  Hybrid Cloud               | A combination of the private and public cloud
                             |
                             | Companies have the benefit of managing their
                             | sensitive data on premise and also benefit from
                             | different services offered by third party cloud
                             | platforms
                             |
--------------------------------------------------------------------------------
== Introduction to Cloud Design Principles ==
  * Elasticity
  * Servers and other resources are disposable
  * Automation
  * Design for failure
  * Loose Coupling
  * Parallelism
  * Build security at all layers

  *Think Elastic*              | Elasticity means the ability to increase and
                             | decrease resources as needed. It can be started
                             | with the minimum necessary resources, and as the
                             | application grows, the resources can be scaled as
                             | needed.
                             |
                             | Scaling can be horizontal or vertical.
                             |
    Horizontal Scaling       | Increase in the number of resources (Servers, hard disks)
                             | * Horizontal Scaling is more of a long term solution
                             |
    Vertical Scaling         | Increase the capacity of a given resoure
                             | (increaseing the ram of a server)
                             | * Vertical Scaling is for short term, because
                             | there is a limit on how much the capacity of a
                             | given machine can be increased
                             |
                             |
  *Servers and other resources*| All the resources served through the cloud are
  *are disposable*             | virtualized. This allows for more experimentation
                             | as resources can be used and freed at will
                             |
  *Automoation*                | Since all resources are virtualized, Everything
                             | that can be though of can be automated. With this
                             | we can create a system that can care for itself.
                             | The creating and destruction of servers, restarting
                             | Servers due to error(s), backing up databases,
                             | responding to attacks, self healing and monitoring
                             | can be automated, and respond to feedback from
                             | automation
                             |
  *Design for Failure*         | Assume any part can fail and cater for the
                             | potential failure. Set up automatic recovery and
                             | alerts.
                             |
  *Loose Coupling*             | Complexity grows with the size of the software
                             | we are building. Loose coupling makes it easy to
                             | cope with this complexity as an application can
                             | be seperated into indepedent parts which
                             | interacte with the whole. Meaning that they can
                             | be developed and managed by seperate teams.
                             |
                             | Failure of a part should not be ther failure of
                             | the whole application
                             |
                             | It is important to alwasy implement loose
                             | coupling at the early stage of a project.
                             |
  *Parallelism*                | Parallelism means many things can be handled at
                             | the same time which would save time. An example
                             | of this is request handling, A high load of
                             | requests can be divided between multiple servers.
                             |
  *Build Security in Every*    | Security of the layers that we are managing
  *Layer*                      | should be provided
                             |
                             | For example, in IAAS, security must be provided
                             | for the application, the data in transit and at
                             | rest.
                             |
--------------------------------------------------------------------------------
== Availability Zones ==
                             | An Availability Zone (AZ) is one or more discrete
                             | data centes wit redundant power, networking, and
                             | connectivity in an AWS Region
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
                             |
                             |
                             |
                             | * Each AWS Region has multiple physically isolated
                             |   Availability Zones.
                             | * Connected to each other with fast, private fiber-
                             |   optic networking.
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
  Local Zones                | * Clost to large population, industry, and IT
                             |   centers.
                             | * Are an extension of an AWS Region
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
  Edge locations             | Edge locations are AWS data centers designed to
                             | Deliver services with the lowest latency possible.
                             | they are often in major cities
                             |
    Use cases of Edge        | * caching. Delivering content to users faster
    Locations                | * Firewall and DDOS protection
                             | * Leverage AWS global network
                             | * there are over 100 Edge locations which are used
                             |   for the CloudFront Delivery network
                             | * CloudFront CDN cached content at edge locations
                             |   for high performance delivery of content.
                             |
  AWS Wavelength             | * Allows parts of your application to use AWS
                             |   compute and storage services that are embedded
                             |   witin communications service providers' (CSP)
                             |   datacenters at the edge of the 5G network
                             | * This allows developers to low-latency to
                             |   Mobile devices
                             |
  Ground Station             | * Fully managed service that enables customers
                             |   to easily command, control, and downlink from
                             |   satellites.
                             | * Located within the AWS Global Infrastructure
                             |   footprint, Contacts (reservations) are scheduled
                             |   for an antenna to communicate with a satellite
                             |
  Project Kuiper             | * Kuiper Systems LLC is a subsidiary of Amazon.
                             | * Proposed constellation network of Low Earth
                             |   Orbit satellites
                             | * Provide low-latency, high-speed broadband
                             |   connectivity to unserved and underserved
                             |   communities around the world
                             | * Will extend low latency acess to the AWS cloud
                             |   from all areas of the world.
                             |
--------------------------------------------------------------------------------
== Other terms ==
  Virtual Private Cloud (vpc)| * The space within AWS cloud that contain servers
                             |   and will also contain EBS block devices
                             |
  VPC Endpoint               | * The point of contact for storage devices not
                             |   Hosted within the VPC. Examples are: S3 and
                             |   S3 Glacier
                             |

== Serverless Computing ==
                             | Allows you to build and run applications and
                             | services without thinking about servers.
                             | * Also reffered to as Function-as-a-Service (FaaS)
                             |   or Abstracted services.
                             | Examples:
                             |   * Amazon Simple Storage Service (S3) - file storage (bucket)
                             |   * AWS Lambda - running code in the cloud
                             |   * Amazon DynamoDB - nosql database running in the cloud
                             |   * Amazon SNS - Simple Notification Service
                             |

== Cloud Computing Deployment Models ==
  Cloud                      | Fully deployed in the cloud and all parts of
                             | the application run in the cloud.
                             |
  Hybrid                     | A way to connect infrastructure and applications
                             | between cloud-based resources and existing
                             | resources that are not located in the cloud.
                             | Run AWS infrastructure and service on premises
                             | with AWS Outposts
                             |
  On-premise                 | Deploying resources on-premises, using virtualization
                             | and resource management tools, is sometimes called
                             | "private cloud"

== AWS Management Console ==
                             | * Web-based user interface to AWS
                             | * Requires an AWS account
                             | * Monitor costs
                             | * AWS Console Mobile App

== SDK & CLI Access ==
  Software Development Kits  | * Create applications tha tuse AWS services.
                             | * SDKs for Javascript, Nodejs, Java, python
                             |   .NET, PHP, Ruby, Go, C++
                             | * Moble SDKs for Android, iOS, React Native,
                             |   Unity, Xamarin
                             | * Application Programming Interface enables access
                             |   to AWS usig http calls
                             |
  Command Line Interface     | * Control multiple AWS services from the command
                             |   line and automate them through scripts
                             |
  Important URLs             | * aws.amazon.com/certification
                             | * docs.aws.amazon.com
                             | * aws.amazon.com/whitepapers
                             | * aws.amazon.com/products
                             | * aws.amazon.com/new
                             |
--------------------------------------------------------------------------------
== Storage Services ==
  Simple Storage Service (S3)| * Designed to store and accesse any type of data
                             |   over the internet
                             | * It is a serverless service
                             | * Think of it as a bucket where you upload data
                             |   content. Theoretical size is unlimited
                             |
  S3 Glacier                 | * Least expensive storage solution, meant for
                             |   long term data archival
                             | * Not as readily accessable as S3, so should
                             |   only be used for Archieval purposes
                             |
  Elastic Block Store (EBS)  | * Low latency block device storage specifically
                             |   meant to attach to servers that are launched
                             |   with Amazon EC2 service - think a mounted
                             |   disk drive
                             |
  Elastic File System (EFS)  | * Network attached storage, allowing multiple
                             |   servers to access the same data source
                             |
  Storage Gateway            | * Enables hybrid storage between on-premise
                             |   environments and the AWS Cloud
                             | * Provides low-latency performance by caching
                             |   frequently used data on premises while storing
                             |   less frequently used data on Cloud storage
                             |   services
                             |
  Snowball (devices)         | * Portable, peta-byte scale, data storage device
                             |   that can be used to migrate large amouts of data
                             |   from on-premises environment over to the AWS
                             |   Cloud.
-- Hybrid Storage Example ------------------------------------------------------
  Using an S3 Bucket as a    | * Large scale data backup can be accomplished with
  disaster recovery solution |   a Snowball Device
                             | * Data syncing can be accomplished with the
                             |   AWS Storage Gateway
                             |
--------------------------------------------------------------------------------
== EC2 Instance Storage Section ==
  What's an EBS Volume       | * An EBS (Elastic Block Storage) Volume is a
                             |   network drive you can attach to your instances
                             |   while they run
                             | * It allows your instances to persist data, even
                             |   after their termination
                             | * They can only be mounted to one instance at a
                             |   time (at the CCP level)
                             | * They are bound to a specific availability zone
                             | * Anaogy: Think of them asa "network USB stick"
                             | * Free tier: 30GB of free EBS storage of type
                             |   General Purpose (SSD) or Magnetic per month
                             |
  EBS VOlume                 | * It's a network drive (i.e., not a physcial drive)
                             |   * It uses the network to communicate the
                             |     instance, which means there might be a bit of
                             |     latency
                             |   * It can be detached from an EC2 instance and
                             |     attached to another one quickly
                             |
                             | * It's locked to an Availability Zone (AZ)
                             |   * An EBS Volume in us-east-1a cannot be attached to us-east-1b
                             |   * To move a volume across, you first need to snapshot it
                             |
                             | * Have a provisioned capacity (size in GBs, and IOPS)
                             |   * you get billed for all the provisioned capacity
                             |   * You can increase the capacity of the drive over time
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
                             |
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== AWS Database Services ==
  Relational Database Service| * A fully managed database service
  (RDS)                      | * Can launch variations of MySQL (MariaDB or
                             |   Amazon's enterpirse version called: Amazon Aurora,
                             |   PostgreSQL, also Amazon Postgres Aurora, MsSQL
                             |   and Oracle are also available
                             |
                             |
  DynamoDB                   | * AWS's noSQL Database as a service
                             | * Serverless database service
                             |
  Redshift                   | Fully managed, petabyte scale data warehouse based on
                             | Postgresql database engine.
                             |
  ElastiCache                | In-memory data store/cache.
                             | access data from fast, fully managed in-memory caches
                             |
  Database Migration Srvc    | Orchestarts the migration of databases over to AWS
  (DMS)                      | easily and securely. Can also migrated databases from one
                             | type to another
                             |
  Neptune                    | Fast, reliable, fully managed, high performacne graph database
                             | engine optimized for storing billions of relationships.
                             |
--------------------------------------------------------------------------------
== AWS Compute Services ==
  Elastic Compute Cloud      | Provides virtual servers in AWS Cloud
  (EC2)                      |
                             |
  *EC2 Instances Purchasing*   | * On-Demand Instances - short workload, predictable pricing
  *Options*                    |   , pay by second
                             | * Reserved (1 & 3 years)
                             |   * Reserved Instances - long workloads
                             |   * Convertible Reserved Instances - Long workloads with
                             |     flexible instances
                             | * Savings Plans (1 & 3 years) - commitment to an amount of
                             |     usage, long workload
                             | * Spot Instances - short workloads, cheap, can lose instance
                             |   (less reliable)
                             | * Dedicated Hosts - book an entire physical server; control
                             |   instance placement
                             | * Dedicated Instance - no other customer will share your
                             |   hardware
                             | * Capacity Reservations - reserve capacity in a specific AZ
                             |   for any duration
                             |
    *EC2 On-Demand*            | * Pay for what you use:
                             |   * Linux or Windows - billing per second, after the first
                             |     minute
                             |   * All other operating systems - billng per hour
                             | * Has the highest cost but no upfront payment
                             | * No long-term commitment
                             | * Recommended for short-term and un-interrupted workloads,
                             |   where you can't predict how the application will behave
                             |
    *EC2 Reserved Instances*   | * Up to 72% discount compared to On-Demand
                             | * You reserve a specific instance attibutes (Instance Type,
                             |   Region, Tenancy, OS)
                             | * Reservation Period - 1 year (+discount) or 3 years (+++discount)
                             | * Payment Options - No Upfront (+), Partial Upfront (++),
                             |   All Upfront (+++)
                             | * Reserved Instance's Scope - Regional or Zonal (reserve
                             |   capacity in an AZ)
                             | * Recommended for steady-state usage applications (think database)
                             | * You can buy and sell in the Reserved Instance Marketplace
                             |
    *Convertible Reserved*     | * Can change the EC2 instance type, instance family, OS,
    *Instance*                 |   scope and tenancy
                             | * Up to 66% discount
                             |
    *EC2 Savings Plans*        | * Get a discount based on long-term usage (up to 72% - same
                             |   as RIs)
                             | * Commit to a certain type of usage ($10/hour for 1 or 3 years
                             | * Usage beyond EC2 Savings Plans is billed at the On-Demand
                             |   price
                             | * Locked to a specific instance family & AWS region (e.g.,
                             |   M5 in us-east-1
                             | * Flexible across:
                             |   * iNSTANCE sIZE (e.g., m5.xlarge, m5.2xlarge)
                             |   * OS (e.g., Linux, Windows)
                             |   * Tenancy (Host, Dedicated, Default)
                             |
    *EC2 Spot Instance*        | * Can get a discout of up to 90% compared to On-demand
                             | * Instances that you can "lose" at any point of time if
                             |   your max price is less than the current spot price
                             | * The MOSt cost-efficient instances in AWS
                             | * Useful for workloads that are resilient to failure
                             |   * Batch jobs
                             |   * Data analysis
                             |   * Image processng
                             |   * Any distributed workloads
                             |   * Workloads with a flexible start and end time
                             | * *NOT* suitable for critical jobs or databases
                             |
    *EC2 Dedicated Hosts*      | * A physical server with EC2 instance capacity fully
                             |   dedicated to your use
                             | * Allows you address compliance requirements and
                             |   use your exsiting server-bound software
                             |   licenses (per-socket, per-core, per-VM software
                             |   licenses)
                             | * Purchasing Options:
                             |   * On-demand - Pay per second for active Dedicated Host
                             |   * Reserved - 1 or 3 years (No Upgront, Partial Upfront,
                             |     all Upfront
                             | * Useful for software that have complicated licensing model
                             |   (BYOL - Bring Your Own License)
                             | * Or for companies that have strong regulatory or compliance
                             |   needs
                             |
    *EC2 Dedicated Instances*  | * Instances run on hardware that's dedicated to you
                             | * May share hardware with other instances in same account
                             | * No control over instance placement (can move hardware
                             |   after Stop / Start)
                             |
    *EC2 Capacity Reservations*| * Reserve On-Demand instances capacity in a
                             |   specific AZ for any Duration
                             | * You always have access to EC2 capacity when you need it
                             | * No time commitment (create/cancel anytime), no billing discounts
                             | * Combine with Regional Reserved Instances and
                             |   Savings Plans to benefit from billing discounts
                             | * You're charged at On-Demand rate whether you
                             |   run instances or not
                             | * Suitable for short-term, uniterrupted workloads
                             |   the needs to be in a specific AZ
                             |
    *Which purchasing option*  | Using a hotel as an analogy:
    *is right for me*?         | * *On-Demand*: coming and staying in resort
                             |   whenever we like, we pay the full price
                             | * *Reserved*: Like planning ahead and if we plan
                             |   to stay for a long time, we may get a good discount
                             | * *Savings Plan*: pay a certain amount per hour
                             |   for certain period and stay in any room type (
                             |   e.g., King, Suite, Sea View,...)
                             | * *Dedicated Hosts*: we book an entire building of the resort
                             | * *Capacity Reservations*: you book a room for a
                             |   period with full price even if you don't stay
                             |   in it
                             |
  Shared Responsibility      | AWS:
  Model for EC2              |   * Infrastructure (global network security)
                             |   * Isolation on physical hosts
                             |   * Replacing faulty hardware
                             |   * Compliance validation
                             |
                             | User:
                             |   * Security Groups rules
                             |   * Operating-system patches and updates
                             |   * Software and utilities installed on the EC2 instance
                             |   * IAM Roles assigned to EC2 & IAM user access management
                             |   * Data security on your instance
                             |
  EC2 Autoscaling            | Dynamically scale your EC2 Capacity with set thresholds
                             |
  Amazon Lightsail           | An easy method for launching virtual servers running
                             | applications
                             |
  Elastic Container Service  | Highly scaleable, high performance container managment
  (ECS)                      | service (docker containers)
                             |
  AWS Lambda                 | Serverless service - allows you to run code without
                             | a server
                             |
  Elastic Load Balancer      |
                             |
  *EC2 Section - Summary*      |
                             | * EC2 Instance: AMI (OS) + Instance size (CPU + RAM)
                             |   + Storage + security groups + EC2 User Data
                             | * Security groups: Firewall attached to the EC2 instance
                             | * EC2 User Data: Script launched at the first start of an instance
                             | * SSH: Start terminal into our EC2 Instances (port 22)
                             | * EC2 Instance Role: link to IAM roles
                             | * Purchasing Options: On-Demand, Spot, Reserved (
                             |   Standard + Convertible + Scheduled), Dedicated
                             |   Host, Dedicated Instance
                             |
--------------------------------------------------------------------------------
== Networking & Content Delivery ==
  CloudFront                 | Global Content Delivery Network (CDN)
                             |
                             | Let's you provision logically isolated section of the AWS
  Virtual Private Cloud (VPC)| cloud, which lets you deploy self-defined aws services
                             |
  Direct Connect             | High speed dedicated connection to AWS
                             |
  Elastic Load Balancing     | automatically distributes incoming traffic for your application
  (ELB)                      | across multiple EC2 instances and also across multiple
                             | availibility zones
                             |
  Route 53                   | Highly available Domain Name System
                             |
  API Gateway                | fully managed service that allows to create and deploy
                             | APIs at any scale
--------------------------------------------------------------------------------
== Amazon machine Image (AMI) ==
  Amazon Machine Image (AMI) | * AMI are a customization of an EC2 instance
                             |   - You add your own software, configuration,
                             |     operating system, monitoring...
                             |   - Faster boot / configuration time because all
                             |     your software is pre-packaged
                             |
                             | * AMI are built for a *specific region* (and can
                             |   be copied across regions)
                             |
                             | * You can launch EC2 instances from:
                             |   - A Public AMI: AWS provided
                             |   - Your own AMI: you make and maintain them
                             |     yourself
                             |   - An AWS Marketplace AMI: an AMI someone else
                             |     made (and potentially sells)
                             |
  AMI Process (from and EC2  | * Start an EC2 instance and customize it
  instance)                  | * Stop the instance (for data integrity)
                             | * Build an AMI - this will also create EBS snapshot
                             | * Launch instances from other AMIs
                             |
--------------------------------------------------------------------------------
== EC2 Image Builder ==
                             | * Used to automate the creation of Virtual
                             |   Machines or container images
                             | * => Automate the creation, maintain, validate
                             |   and test EC2 AMIs
                             | * Can be run on a schedule (weekly, whenever
                             |   packages are updated, etc...)
                             | * Free service (only pay for the underlying resources)
                             |
                             |
                             | *EC2 Image builder* --create--> *Builder EC2 Instance* --create--> *New AMI* ----> Test EC2 Instance ----> AMI is distribued
                             | `                           Build Components applied                         Test suite is run         (can be multiple regions)`
                             |`                       (customize software on instance)                (is the AMI working, secure?`
                             |
--------------------------------------------------------------------------------
