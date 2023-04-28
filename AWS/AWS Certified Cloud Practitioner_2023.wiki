--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
== Certification Track ==
* Foundational
  Six months of funamenta AWS Cloud and industry knowledge
  - AWS Certified Practitioner

* Associate
  One year of experience solving problems and implementing solutions using the
  AWS Cloud
  - Solutions Architect
  - Developer
  - SysOps Administrator

* Professional
  Two years of experience designing, operating, and troubleshooting solutions
  using AWS Cloud
  - Solutions Architect
  - DevOps Engineer

* Specialty
  Technical AWS Cloud experience in the Specialty doman as specified in the
  exam guide
  - Advanced Networking
  - Data Analytics
  - Database
  - Machine Learning
  - Security
  - SAP on AWS

--------------------------------------------------------------------------------
== Fundamentals of Cloud Computing Platform ==
  What is Cloud Computing    | * Cloud computing is the on-demand delivery of
                             |   compute power, database storage, applications,
                             |   and other IT resources
                             |
                             | * Through a cloud services platform with pay-as-you-go
                             |   pricing
                             |
                             | * You can provision exactly the right type and size
                             |   of computing resources you need
                             |
                             | * you can access as many resources as you need,
                             |   almost instantly
                             |
                             | * Simple way to access servers, storage, databases
                             |   and a set of application services
                             |
                             | * Amazon Web Services owns and maintains the
                             |   network-connected hardware required for these
                             |   application services, while you provision and
                             |   use what you need via a web application
                             |
  The Deployment Models of   |
  the Cloud                  |
                             |
    * Private Cloud:         | Cloud sevices used by a single organization, not
                             | exposed to the public.
                             |
                             | * Complete control
                             |
                             | * Security for sensitive application
                             |
                             | * Meet specific busines needs
                             |
                             |   - Rackspace
                             |
    * Public Cloud:          | * Cloud resources owned and operated by a third-
                             |   party cloud service provider delievered over the
                             |   Internet
                             |
                             | * Six advantages of Cloud Computing
                             |
                             |   - Azure
                             |   - Google Cloud
                             |   - AWS
                             |
    * Hybrid Cloud:          | * Keep some servers on premises and extend some
                             |   capabilities to the Cloud
                             |
  The Five Characteristics   | * On-demand self service:
  of Cloud Computing         |   - Users can provision resources and use them
                             |     without human interaction from the service
                             |     provider
                             |
                             | * Broad network access:
                             |   - Resources available over the network, and can
                             |     be acessed by diverse client platforms
                             |
                             | * Multi-tenancy and resource pooling:
                             |   - Multiple customers can share the same
                             |     infrastructure and applications with security
                             |     and privacy
                             |   - Multiple customers are serviced from the same
                             |     physical resources
                             |
                             | * Rapid elasticity and scalability:
                             |   - Automatically and quickly acquire and dispose
                             |     resources when needed
                             |   - Quickly and easily scale based on demand
                             |
                             | * Measured service:
                             |   - Usage is measured, users pay correctly for
                             |     what they have used
                             |
  Six Advantages of Cloud    | * Trade capital expense (CAPEX) for operational
  Computing                  |   expense (OPEX)
                             |   - Pay On-Demand: don't own hardware
                             |   - Reduced Total Cost of Ownership (TCO) &
                             |     Operational Expsnse (OPEX)
                             |
                             | * Benefit from massive economies of scale
                             |   - Prices are reduced as AWS is more efficient
                             |     due to large scale
                             |
                             | * Stop guessing capacity
                             |   - Scale based on actual measured usage
                             |
                             | * Increase speed and agility
                             |
                             | * Stop spending money running and maintaining
                             |   data centers
                             |
                             | * Go global in minutes: leverage the AWS global
                             |   infrastructure
                             |
  Problems solved by the     | * Flexibility: change resource types when needed
  Cloud                      | * Cost-Effectiveness: pay as you go, for what you
                             |   use
                             | * Scalability: accommodate larger loads by making
                             |   hardware stronger or adding additional nodes
                             | * Elasticity: ability to scale out and scale-in
                             |   when needed
                             | * High-availability and fault-tolerance: build
                             |   across data centers
                             | * Agility: reapidly develop, test and launch
                             |   software applications
                             |
  Types of Cloud Computing   | * Infrastructure as a Service (IaaS)
                             |   - Provide building blocks for cloud IT
                             |   - Provides networking, computers, data storage space
                             |   - Highest level of flexibility
                             |   - Easy parallel with traditional on-premises IT
                             |
                             | * Platform as a Service (PaaS)
                             |   - Removes the need for your organization to
                             |     manage the underlying infrastructure
                             |
                             | * Software as a Service (SaaS)
                             |   - Complete product that is run and managed by
                             |     the service provider

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

  Example of Cloud Computing | * Infrastructure as a Service:
  Types                      |   - Amazon EC2 (on AWS)
                             |   - GCP, Azure, Rackspace, Digital Ocean, Linode
                             |
                             | * Platform as a Service:
                             |   - Elastic Beanstalk (on AWS)
                             |   - Heroku, Google App Engine (GCP), Windows Azure (Microsoft)
                             |
                             | * Software as Service:
                             |   - Many AWS services(ex: Rekognition for Machine Learning)
                             |   - Google Apps (Gmail), Dropbox, Zoom
                             |
  Pricing of the Cloud       | AWS has 3 pricing fundamentals, following the
    Quick Overview           | pay-as-you-go pricing model
                             |
                             | * Compute:
                             |   - Pay for compute time
                             |
                             | * Storage:
                             |   - Pay for data stored in the Cloud
                             |
                             | * Data transfer OUT of the Coud:
                             |   - Data transfer IN is free
                             |
                             | * Solved the expensive issue of traditional IT
                             |
  AWS Global Infrastructure  | * AWS Regions
                             | * AWS Availability Zones
                             | * AWS Data Centers
                             | * AWS Edge locations / Points of Presence
                             |
    - AWS Regions            | * AWS has *Regions* all around the world
                             | * A region is a *cluster of data centers*
                             | * Most AWS services are *region-scoped*
                             |
    How to choose an AWS     | * *Compliance* with data governance and legal
    Region?                  |   requirements: data never leaves a region without
                             |   your explicit permission
                             |
                             | * *Proximity* to customers: reduced latency
                             |
                             | * *Available services* within a Region: new services
                             |   and new features aren't available in every Region
                             |
                             | * *Pricing*: pricing varies region to region and is
                             |   transparent in the service pricing page
                             |
    - AWS Availability Zones | * Each region has manyavailability zones
                             |   (usually 3, min is 3, max is 6).
                             |
                             | * Each availability zone (AZ) is one or more
                             |   discrete data centes with redundant power,
                             |   networking, and connectivity
                             |
                             | * They're separate from each other, so that they're
                             |   isolated from disasters
                             |
                             | * They're connected with high bandwidth, ultra-low
                             |   latency networking
                             |
                             | * All Availability zones connected make a region
                             |
    - AWS Points of Presence | * Amazon has 216 Points of Presence (205 Edge
      (Edge Locations)       |   locations & 11 Regional Cached) in 84 cities
                             |   across 42 countries
                             |
    Tour of the AWS Console  | * AWS has Global Services:
                             |   - Identity and Access Management (IAM)
                             |   - Route 53 (DNS service)
                             |   - CloudFront (Content Delivery Network)
                             |   - WAF (Web Application Firewall)
                             |
                             | * Most AWS services are Region-scoped:
                             |   - Amazon EC2 (Infrastructure as a Service)
                             |   - Elastic Beanstalk (Platform as a Service)
                             |   - Lambda (Function as a Service)
                             |   - Rekognition (Software as a Service)
                             |
  Shared Responsibility      |
  Model diagram              |

    `+--------------------------+-------------------------------------------------------------------------------------+`
    `|                          |                                     Customer Data                                   |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|        Customer          |                Platform, Application, Identity & Access Management                  |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|                          |                Operating System, Newtork & Firewall Configuration                   |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|    Responsibility for    |       Client-side data       |  Server-Side Encryption    |   Networking Traffic    |`
    `|  Security 'IN' the cloud | Encryption & Data Integrity  | (File system and/or Data)  | Protection (Encryption, |`
    `|                          |        Authentication        |                            |  Integrity, Identity)   |`
    `+----------------------------------------------------------------------------------------------------------------+`
    `|                          |                                       Software                                      |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|           AWS            |     Compute        |      Storage       |      Database       |     Neworking       |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|                          |                         Hardware/AWS Global Infrastructure                          |`
    `|   Responsibility for     +-------------------------------------------------------------------------------------+`
    `|  Security 'OF' the Cloud |     Compute        |      Storage       |      Database       |     Neworking       |`
    `|                          +-------------------------------------------------------------------------------------+`
    `|                          |        Regions         |       Availability Zones       |       Edge Locations      |`
    `+----------------------------------------------------------------------------------------------------------------+`

Questions:
  Which Global Infrastructure identity is composed of one or more discrete data
  centers with redundant power, networking, and connectivity, and are used to deploy
  infrastructure? *Availability Zones*

  AWS Regions are composed of? *Three or more Availability Zones*
                             |
--------------------------------------------------------------------------------
== Understanding Core AWS Services ==
  IAM: Users & Groups        | * *IAM* = Identity and Access Management, Global service
                             | * *Root* account created by default, shouldn't be used or shared
                             | * *Users* are people within your organizaition, and can be grouped
                             | * *Groups* only container users, not other groups
                             | * *Users* don't have to belong to a group, and users can beling to multiple groups
                             |
  IAM: Permissions           | * Users or Groups can be assigned JSON documents
                             |   calle policies
                             |
                             | * These policies define the permission of the users
                             |
                             | * In AWS, you apply the *least privilege principle*:
                             |   don't give more permissions than a user needs
                             |
  IAM Policies Structure     | Consists of:
`                             | * `*Version*`: policy language version, alwasy include        | {`
`                             |   "2012-10-17"                                            |     "Version": "2021-10-17",`
`                             | * `*ID*`: an identifier for the policy (optional)             |     "Id": "S3-Account-Permissions",`
`                             | * `*Statement*`: one or more individual statements (required) |     "Statement": [`
`                             |                                                           |         { `
`                             | Statements consists of                                    |             "Sid": "1",`
`                             | * `*Sid*`: an identifier for the statement (optional)         |             "Effect": "Allow",`
`                             | * `*Effect*`: whether the statement allows or denise          |             "Principal": {`
`                             |   access (Allow, Deny)                                    |                 `*"*`AWS": ["arn:aws:iam::123456789012:root"]`
`                             | * `*Principal*`: account/user/role to which this policy       |              },`
`                             |   applied to                                              |              "Action": [`
`                             | * `*Action*`: list of actions this policy allows or denies    |                   "s3:GetObject",`
`                             | * `*Resource*`: list of resources to which the actions        |                   "s3:PutObject"`
`                             |   applied to                                              |              ],`
`                             | * `*condition*`: conditions for when this policy is in        |              "Resource": ["arn:aws:s3:::mybucket/*"]`
`                             |   effect (optional)                                       |         }`
`                             |                                                           |     ]`
`                             |                                                           | }`
                             |
  IAM - Password Policy      | * Strong passwords = higher security for your account
                             | * In AWS, you can setup a password policy:
                             |   - Set a minimum password length
                             |   - Require specific character types:
                             |     * including uppercase letters
                             |     * lowercase letters
                             |     * numbers
                             |     * Non-alphanumeric characters
                             |   - Allow all IAM users to change their own passwords
                             |   - Require users to change their password after some
                             |     time (password expiration)
                             |   - Prevent password re-use
                             |
  Multi Factor Authentication| * Users have access to your account and can possibly
  (MFA)                      |   change configurations or delete resources in your
                             |   AWS account
                             | * you want to protect your Root Accounts and IAM users
                             | * MFA = password you know + security device you own
                             |
  IAM Roles for Services     | An IAM role is an identity you can create that has
                             | specific permissions with credentials that are
                             | valid for short durations. Roles can be assumed by
                             | entities that you trust
                             |
                             | * Some AWS services will need to perform actions on
                             |   your behalf
                             |
                             | * To do so, we weill assign permissions to AWS
                             |   Services with IAM Roles
                             |
                             | * Common roles:
                             |   - EC2 Instance Roles
                             |   - Lambda Function Roles
                             |   - Roles for CloudFormation
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
== Networking Services ==
                             |
--------------------------------------------------------------------------------
== Storage Services ==
                             |
--------------------------------------------------------------------------------
== Database Services ==
                             |
--------------------------------------------------------------------------------
== Devedoper Tools Container Services ==
                             |
--------------------------------------------------------------------------------
== Billing Support Services ==
                             |
--------------------------------------------------------------------------------
== Security Services ==
                             |
--------------------------------------------------------------------------------
