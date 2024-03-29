--------------------------------------------------------------------------------
DevOps
--------------------------------------------------------------------------------
== Platforms ==
  * [[Azure]]
  * [[DevOps/ACloudGuru-DevOps_Essential_Training|acloudguru - DevOps Essential Training]]
  * [[DevOps/ACloudGuru-DevSecOps_Essential_Training|acloudguru - DevSecOps Essential Training]]
  * [[DevOps/ACloudGuru-Jenkins_quick_start|Jenkins Quick Start]]
  * [[DevOps/ACloudGuru-Implementing_a_full_CICD_Pipeline|acloudguru - Implementing a Full CI/CD Pipeline]]
--------------------------------------------------------------------------------
== Concepts ==
  * [[DevOps/Concepts/Orchestration_and_containers|Orchestration and Containers]]
--------------------------------------------------------------------------------
** Agile Principles
  1 - Satisfy the Customer
    Highest priority by delivering valuable software
  2 - Welcome Change
    Harness change for the customer's competitive advantage
  3 - Deliver Frequently
    Deliver working software frequently in as short time as possible
  4 - Work Together
    Business and developers must work together throughout the project
  5 - Trust and Support
    Create a healthy environment that motivates individuals
  6 - Face-to-face conversation
    F2F conversations are an efficient and effective method to convey information
  7 - Working Software
    Delivering functional software is the ultimate way to measure progress
  8 - Sustainable Development
    Establish a repeatable and maintainable development pace
  9 - Continuous Attention
    Right skills and good design to constantly improve the product
  10 - Maintain Simplicity
    Develop just enough to get the job done for right now
  11 - Self-Organizing Teams
    Skilled and motivated team members with decision-making power deliver quality
  12 - Reflect and Adjust
    At regular intervals, the team tunes and adjusts behavior to become more effective
--------------------------------------------------------------------------------
** The Agile Manifesto
  * Individuals & Interactions ofver Processes & Tools
  * Working Software over Comprehensive Documentation
  * Customer Collaboration over Contract Negotiation
  * Responding to Change over Following a Plan
--------------------------------------------------------------------------------
** Agile Project Management
*** Concepts
  * Product Backlog:
    List ordered by priority of the activities, such as features, changes, fixes
    that are required by the application.
  * Issues:
    An issue can be an idea, a user story, discussion, bug ... basically a task
  * Points / Weight:
    Measures the size / complexity of an issue.
  * Sprint:
    Period of time in which specific work has to e completed
*** Roles
  * Scrum Master:
    Serves the team by removing impediments, helping them collaborate and guides the
    product owner.
  * Product Owner:
    Represents or is end user. Owns the backlog and prioritizes items.
  * Development team:
    Team that builds the product through sprints (developers, testers, business analyst)
*** Tools
  * Burn down chart:
    Measures weight to show the remaining work to be done and the progress made.
  * Boards:
    Organizes the activities to be performed in several colums to track work and progress.
    These columns can be customized to the project's needs
    * Agile Project Management Tools:
      * Jira
      * Asana
      * Trello
      * Monday
--------------------------------------------------------------------------------
** DevOps Lifecycle
  `Plan <-----------------------------------------------------|`
  `^ Code    | Continuous Integration                         |`
  `|   Build |                                                |`
  `|     Test        | Continuous Delivery            |       |`
  `|       Release   |          Continuous Deployment |       |`
  `|         Deploy  |                                        |`
  `|           Operate     | Continuous Feedback              |`
  `|------------ Monitor   |__________________________________|`
*** Stages
  * Plan Stage:
    * Objectives and requirements added to the backlog
    * Items also added to the backlog per feedback from end users and operations team
    * The teasks from the backlog are added to sprints
    Several issue board & project management tools can be used to track these activities and plan:
      * Gitlab
      * Asana
      * Jira
      * Trello
      * Monday
  ------  Continuous Integration  ----------------------------------------------
  * Code Stage:
    * Code from all the developers gets integrated into a source code repository
    * The repository tool/application is called "Version Control Software" (AKA Source Code Management)
  * Build Stage:
    * A continuous integration pipeline is invoked when code is pushed to the repository
    * Code runs through several tests to identify any bugs, errors, and vulnerabilities
    * If tests pass, code can be reviewed and merged
    Some build stage Tools
      * Maven
      * MS Build
      * Docker
    * Some Testing Tools:
      * Sonar Qube
      * Junit 5
      * PyTest
 -------  Continuous Integration  ----------------------------------------------
          * Commit Early, Commit Often
          * Push code to the repository in the smallest possible size
          * Push code to the repository frequently
        CI Testing:
          * SAST (Security Application Security Testing): Identify any security
            vulnerabilities, erros, and bugs
          * Unit Testing: Make sure code works as expected and make it esiare
            for others to understand and use
          * Code Coverage: Understand what percentage of code is being tested
          * Linting: Make sure code has consistent syntax, formatting, and styling
            to make it easy to read
  ------  CD&D Testing  ----------------------------------------------------------
    * The build is deployed to a staging environment for testting.
    * Several automated tests can be performed, such as load, accessibility, performance, end*to*end, and more.
    * User Acceptance Testing (UAT) can also be set up in this stage.
    Some Testing Tools:
      * Selenium
      * Testcafe
      * Artillery
      * Postman
      * Cypress
      * Cucumber
  ------  CD&D Testing  --------------------------------------------------------
    * Load performanc: Verify how the application works under load
    * Functional testing; Verify that everything works correctly
    * User acceptance testing: Verify if the application meets the customers expectations.
  ------  CD&D Deployment Strategies  ------------------------------------------
  * Release Stage:
    * In this stage, we tag a snapshot of the code with Semantic Versioning.
    * Changes, features, breaking changes, and deprecated features are documented.
    * Release can include artifacts such as binaries and packages.
    Some release Tools:
      * Public package / Container Repositories
      * Git
      * Github
      * Gitlab
      JFrog Artifactory
  ------  CD&D Deployment Strategies  ------------------------------------------
    * Rolling Deployment: Deploy in groups
    * Blue*Green: 2 different environments
    * Canary: Specify a group to deploy to first
  ------  Continuous Delivery & Deployment  ------------------------------------
    * Testing / Production Environments are provisioned and configured
    * Continuous Delivery requires a trigger to deploy the application while in
      Continuous Deployment this is automated
  * Deploy Stage
    * Install our release into the production environment
    * Can be an automated or manual process in the pipeline
    * Several deployment strategies can be used in order to avoid downtime
    Some Deployment Stage Tools:
      * Github Actons
      * Gitlab
      * Azure Devops
      * Jenkins
      * terraform
      * Ansible
      * Puppet
   -----  Continuous Feedback  -------------------------------------------------
  * Operate Stage:
    * Stage where engineers from the Infrastructure and Operations team ensure
      the application runs smoothly
    * Scale infrastructure to meet application demand
    * Troubleshoot and resolve infrastructure issues
    * Document issues to provide feedback for next planning stage
    Some Operations tools
      * AWS
      * Azure
      * Google Cloud
      * Linux
      * Postgre SQL
      * Kubernetes
      * Rancher
  * Monitor Stage:
    * Application Monitoring and logging is used to collect data on the usage,
      performance, errors, and more.
    * Data gathered from this stage is used to provide feedback on the follwoing
      iterations of the DevOps lifecycle.
    Some Monitoring Tools
      * Prometheus
      * Grafana
      * Splunk
      * Elastic Stack
      * Jaeger
  ------  Continuous Feedback  -------------------------------------------------
    * Beginning and end of the Continuous Lifecycle
    * Metrics, Statistics, Analytics and Feedback from the Customer and Teams
      involved are taken into account to continuously improve the product.
--------------------------------------------------------------------------------
** Version Control
*** git-flow model
  - 5 Branch Types:
    * Main
      Production branch
      Contains latest product ready release
    * Hotfix
      Copy of the main branch
      Contains bugfixes
    * Development
      Copy of the main branch
      Contains new features
    * Feature
      Copy of the development Branch
      Branch for each featre
    * Release
      Copy of the Development branch
      Contains latest features ready for release
*** Semantic Versioning
  Package Versions
  `+---------Major `
  `|           - When non-compatible featurs are introduced`
  `|           - When there are breaking change`
  `|   +-----Minor`
  `->3.4.2    - New features`
  `      |     - Compativle with previous version numbersk`
  `      +---Patch`
  `            - A release to fix bugs`
  `            - Should not affect other project or features`
  External Packages
    - Exact Version
      #.#.#
      (1.2.3)
    - Greater than
      >#.#.#
    - Compatible Features
      ^#.#.#
    - Minor Level Fixes
      ~#.#.#
  Pre-Releases
    Alpha < Beta < RC
    - Alpha
      Initial testing release
    - Beta
      Release with Frozen features to fix bugs
    - Release Candidate
      Stable enough to be selected as final release
--------------------------------------------------------------------------------
[[git]]
