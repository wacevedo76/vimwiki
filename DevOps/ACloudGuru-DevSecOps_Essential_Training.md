--------------------------------------------------------------------------------
= DevSecOps Essentials =
--------------------------------------------------------------------------------
== Introduction ==
  DevOps and DevSecOps are   | * Process experts and coaches often say that DevOps
  about automation           |   is not about tooling
                             | * Engineers and technologists grow tired of process
                             |   quickly and want real-world examples of how
                             |   processes can be implemented
                             | * Executive stakeholders measure outcomes and
                             |   results when making investments in process
                             |   improvement
                             | * To achieve the goal of DevOps, quality software
                             |   must be developed and deployed faster
                             | * The "Automate everything" mantra of the DevOps
                             |   movement is central to DevSecOps as well
                             |
  DevSecOps Automation       |  `+---------+   Security      +---------+`
                             |  `| Plan    |<---+      /->-- | Deploy  |`
                             |  `+---------+     \    /      +---------+`
                             |  `| Code    |      \__/_      | Operate |`
                             |  `+---------+        / \      +---------+`
                             |  `| Build   |       /   \--<--| Monitor |`
                             |  `+---------+      /          +---------+`
                             |  `| Test    |->---/`
                             |  `+---------+  Integration`
                             |
                             |  DevSecOps can be sued to enforce proper cybersecurity
                             |  practices within an automated DevOps CI/CD pipeline
                             |
                             | DevSecOps Automation involves:
                             |   * Software version control
                             |   * Continuous integration
                             |   * Continuous testing
                             |   * Configuration management and deployment
                             |   * Continuous monitoring
                             |   * Containerization
                             |   * Container orchestration
                             |
  Measuring DevSecOps        | * Deployment frequency (fast and frequent releases)
  Success                    | * Lead time (code to cash cycle)
                             | * Detection of threats, vulnerabilities, and malware
                             | * Mean time to repair and remediation
                             | * Efficiency of rollback and recovery
                             |
--------------------------------------------------------------------------------
== An Overview of DevSecOps ==
  What is DevSecOps?         | * In large corporations, IT departments are generally
                             |   organized by function
                             | * In the past, Development, Security and Operations
                             |   were separate departments
                             | * Development has traditionally been tasked with
                             |   writing software applications
                             | * Operations has traditionally been responsible for
                             |   maintaining the data center of infrastructure
                             | * Security has been the role used to enforce regulatory
                             |   governance and other compliance measures
                             | * DevSecOps is a partmanteau or mashup of Development,
                             |   Security, and Operations.
                             | * It is a process used to help organizations improve
                             |   time-to-market and release software faster
                             |
  Agile Development          | * As Agile proceses have become popular,
                             |   cross-functional development teams have started
                             |   using extreme programming and Scrum methodologies
                             |   to improve productivity
                             |
                             | * By breaking up large releases that could take
                             |   months into small batches of feature changes that
                             |   only take days or weeks, teams can drastically
                             |   Shorten time to market
                             |
                             | * Teams also practice "Kaizen" (Continuous improvement)
                             |   to improve systems over time based on feedback
                             |   from customers
                             |
                             | * As Agile teams become more productive, Poentially
                             |   Shippable Increments build up in Staging and
                             |   Quality Assurance (QA)
                             |
                             | * Even though Agile teams can develop applications
                             |   faster, these products often aren't pushed to
                             |   production any faster than normal
                             |
  Operations                 | * Operations teams can streamline their processes
                             |   to increase the frequency of realeases to production
                             |
                             | * Operations teams can iterate through release
                             |   deployments to mimic the iteration cadence of the
                             |   development team.
                             |
  Release Management         | * Release management is the process of coordinating
                             |   the deployment of finished application increments
                             |   to production
                             |
                             | * Stagin is the interim area where application
                             |   sub-releases are tested prior to use by customers
                             |
                             | * In highly regulated industries, many approvals
                             |   are required before code can be released into
                             |   production
                             |
  Release Gating             | * Governance, risk management, auditing, and
                             |   compliance groups have had to change the way
                             |   they approve software release in order to
                             |   accommodate Agile's fast and frequent releases
                             |
                             | * Automation is necessary for this rapid approval
                             |   proces
                             |
                             | * Many vendors and open-source project have sprung
                             |   up to help automate the Continuous Deployment
                             |   process
                             |
  Security                   | * To comply with regulations and corporate policy
                             |   departments must verify that software adheres
                             |   to governance requirements.
                             |
                             | * By invoving security personnel in the automation
                             |   process, DevOps practitioners can improve the
                             |   throughput of security checkpoints and approvals
                             |
                             | * DevSecOps is the evolution of DevOps that
                             |   emphasizes the importance of security in the
                             |   software release pipeline
                             |
  Security Monitoring        | * After applications andsystems have been
                             |   promoted to production, they are continuously
                             |   monitored for vulnerabilities
                             |
                             | * Depending on the severity of an identified
                             |   vulnerability, applications might be removed from
                             |   production or simply cleansed of the vulnerability.
                             |
                             | * Typically, remediation involves the development
                             |   organization, as refactoring may e required in
                             |   order to update component libraries to versions
                             |   that have eliminated the threat.
                             |
  Release-and-adapt          | * Lessons learned from production performance often
                             |   subsequent iterations of software enhancement
                             |   to remediate performance and security defects.
                             |
                             | * A release-and-adapt cadence is the process through
                             |   which key performance indicators are communicated
                             |   back to developers so that remedial actions may be taken.
                             |
--------------------------------------------------------------------------------
== Cyber Security Concepts and standards part 1 ==
  Attack Surface             | * The atack surface of a system is the collection
                             |   of points (attack vectors) where an unauthorized
                             |   user (attacker) may enter to inject data or extract
                             |   data from an environment
                             | * Keeping the attack surface as small as possible
                             |   is a basic security measure.
                             |
  Malware and Vulnerabilities| * Malware is malicious software that attackers deploy
                             |   to infect individual computes or an entire digital
                             |   network
                             |
                             | * Malware exploits target system vulnerabilities that
                             |   can be hijacked, such as bugs in legitimate
                             |   software (e.g., browser or web application plugins)
                             |
                             | * A vulnerability is a weaknes or deficiency in a
                             |   computer system that an attacker can exploit to
                             |   perform unquthorized actions within the system
                             |
  The OpenSCAP Project       | * The Security Content Automation Protocol (SCAP)
                             |   is a U.S. security standard maintained by the
                             |   Naional Institute of Standards and TEchnology (NIST)
                             |
  The Center for Internet    | * The Center for Internet Security (CIS) provides     <--- series of books and articles for security
  Security (CIS)             |   security benchmarks and the National Checklist
                             |   Program (NCP), defined by the NIST
                             |
  Malware and Vulnerability  | * Scanners can be debployed to network hosts and
  Scanners                   |   run in memory- resident mode to monitor activity
                             |   in real time.
                             |
                             | * By monitoring multiple sensor points, scanners
                             |   can log vulnerabilities so that DevSecOps
                             |   stakeholders become aware of the need for
                             |   remedial action
                             |
                             | * Scanners should be used to interrogate new and
                             |   existing software to determine whether any
                             |   system or application may be infected by threat
                             |   actors or attackers.
                             |
                             | * There ae two type of scanning: dynamic scanning
                             |   and static scanning
                             |
  Dynamic vs Static Scanning | * Dynamic scanning is a method of code analysis
                             |   that identifies vulnerabilities in a runtime
                             |   environment
                             |
                             | * Dynamic tests monitor system memory, functional
                             |   behavior, response time, and the overall performance
                             |   of the system.
                             |
--------------------------------------------------------------------------------
== Cyber Security Concepts and standards part 2 ==
  Identifying and Scoring    | * Common Vulnerabilities and Exposures (CVE) is a
  Vulnerabilities            |   dictionary style list of standardized names for
                             |   vulnerabilities and other information related to
                             |   security exposures
                             |
                             | * CVE aims to standardize the names of all publicly
                             |   known vulnerabilities and security exposures
                             |
                             | * The common Vulnerability Scoring System (CVSS)
                             |   is a free and open industry standard for assessing
                             |   the severity of security vulnerabilities
                             |
                             | * CVSS assigns severity scores to vulnerabilities,
                             |   allowing responders to prioritize responses and
                             |   resource according the threat level
                             |
  National Vulnerability     | * The NST NVD provides Datafeeds and realtime API's
  Database (NVD)             |   that allow tooling to access the data and use it
                             |   as intelligenc for scanning and monitoring tools
                             |
  DevSecOps Resources        | * The National Checklist Program (NCP) repositroy
                             |   provides secure configuration for specific software
                             |   components
                             |
                             | * DevSecOps stakeholders can use the NCP repository
                             |   to search the CIS for information on particular
                             |   software products
                             |
                             | * The NCP repository provides metadata and links to
                             |   security checklists, including checklists that conform
                             |   to the SCAP
                             |
                             | * The NIST provides an online search tool as well as
                             |   data feeds that are used by man SCAP-validated tools
                             |   to provide intelligence for advanced DevSecOps
                             |   monitoring
                             |
                             | * The National Vulnerability Database (NVD) is a
                             |   terms security professionals use to refer to this
                             |   NIST repository and other data stores provided by
                             |   the NIST
--------------------------------------------------------------------------------
== Identity and Access Management ==
  Secure Automation          | * In DevSecOps, many of the processes required for
                             |   software development, testing, and deployment are
                             |   automated
                             |
                             | * Security checks should be implemented for each
                             |   server and tool to reduce the number of possible
                             |   attack vectors and prevent malfeasance
                             |
                             | * Security practices are different for every team
                             |   and system, but there are three main categories:
                             |   server hardening, application harening, and identity
                             |   and access management
                             |
  DevSecOps Pipeline Flow    | Development -> QA Testing -> Staging -> Production
                             |
                             | * The platforms and systems used to automate
                             |   DevSecOps processe must be secured individually
                             |   according to the specific technonogy they employ
                             |
  Identity and Access        | * Identity and Access Management (IAM) is the
  Management                 |   process of granting or restricting access to
                             |   computing resources for individual users, groups,
                             |   or systems
                             |
                             | * All modern software applications govern users
                             |   and group authentication, but their specific
                             |   methods vary
                             |
                             | * Systems that access applications through APIs
                             |   also have frameworks for managing access to
                             |   those application
                             |
                             | * To harden servers and applications in a DevSecOps
                             |   pipeline, teams have to implement security
                             |   practices based on the particular tooling being
                             |   used
                             |
                             |                   IAM
                             |
                             |  `+----------------+ +----------------+`
                             |  `| Authentication | | Authorization  |`
                             |  `|                | |                |`
                             |  `+----------------+ +----------------+`
                             |  `+----------------+ +----------------+`
                             |  `|      User      | |   Credentials  |`
                             |  `|   Management   | |   Repository   |`
                             |  `+----------------+ +----------------+`
                             |
                             |  Identity and Access Management involves authenticating,
                             |  auhorizing, and managing users and their credentials
                             |  via automation and security frameworks
                             |
  Server Hardening           | * Server hardening is the practice of enhancing
                             |   each server's security
                             |
                             | * Teams can consult benchmarks from CIS and
                             |   applications such as OpenSCAP to review possible
                             |   server vulnerabilities and determine what steps
                             |   to take to mitigate risks
                             |
                             | *** Reduce Potential Attack Vectors
                             | *** OpenSCAP -> Implement Benchmark Security
                             |
                             | The security community has developed best practice
                             | guidelines and automated tooling for server hardening
                             |
  Application Hardening      | * Application hardening is the practice of enhancing
                             |   an application or framework's security according
                             |   to the provider's recommendations.
                             |
                             | * Most DevSecOps tooling involves automated
                             |   integration with other third-party systems through
                             |   APIs
                             |
                             | * The process of hardening and application includes
                             |   both the initial implementation of security assets
                             |   and ongoing governance over time.
                             |
                             | Application hardening consists of conventional
                             | access authentication for humans and token management
                             | for application-to-application interfaces
                             |
  IAM Fundamentls            | * Identity repositories are systems that store
                             |   information about all users and groups within an
                             |   enterprise in a single plance
                             |
                             | * Access keys are encrypted keys that enable applications
                             |   to securely access servers
                             |
                             | * Signatures and certificates allow programs to
                             |   verify the source and authenticity of digital assets
                             |
                             | * Vaults store secrets and encrypt login credentials
                             |   to prevent attackers from accessing them
                             |
                             |
                             | Cyber security is an important part of software
                             | development, and all DevSecOps stakeholders should
                             |  be vamiliar with fundamental security practices
                             |
--------------------------------------------------------------------------------
== Clean Repositories ==
  Software Repositories      | * Software onboarding is the process developers use
                             |   to acquire the third-party components needed to
                             |   develop and compile an application.
                             |
                             | * With the rise of open source, many third-party
                             |   component libraries and frameworks are acquired
                             |   from public repositories
                             |
                             | * In some cases, off-premise repositories are not
                             |   administered or maintained by the developer's
                             |   organization
                             |
  Security in Public         | * Attack vectors are often exploited in public
  Repositories               |   systems
                             |
                             | * Since the systems are not on-premise, they must
                             |   be hardened and maintained by the organizations
                             |   that provide them
                             |
                             | * Highly regulated industries require levels of
                             |   security and protection that may exceed those
                             |   practiced by the organizations maintaining public
                             |   repositories
                             |
  Malware                    | * Malware exists in most public repositories, and
                             |   some of the most popular software components in
                             |   user today are known to be vulnerable
                             |
                             | * Once inside the private infrastructure, malware
                             |   can be unknowingly propagated to production
                             |   where vulnerabilities are further exploited by
                             |   attackers
                             |
--------------------------------------------------------------------------------
== Securing Public Repositories ==
  Use case: GitHub           | * GitHub is a useful and popular off-premise
                             |   used by many organizations
                             |
                             | * We will use GitHub as an example of a public
                             |   repository because it is one of the most well-
                             |   developed repositories in use today
                             |
  Why Attackers Target GitHub| * The files stored in GitHub are often application
                             |   source code and, thus, valuable intellectual
                             |   property
                             |
                             | * Copying the code may enable other companies or
                             |   even nation-states to quickly develop derivative
                             |   applications, saving years or even decades of
                             |   development time and leveraging trade secrets
                             |   without paying licensing fees.
                             |
                             | * Hackers might also steal code to resell it on
                             |   the dark web
                             |
  Threats Facing GitHub      | * Hackers can study application source code to
                             |   learn how to attack the software when it's run
                             |   in production
                             |
                             | * Stealing source code gives hackers time to look
                             |   for vulnerabilities that would be more difficult
                             |   to detect through the penetration of production
                             |   systems
                             |
                             | * Attackers can even run code in production on their
                             |  own systems and test attacks against it, refining
                             |  their attacks to increase their speed, stealth,
                             |  and effectiveness
                             |
                             | * State-sponsored cyber terrorism and global
                             |   corporate espionage are well-funded efforts
                             |   that retain professionals to develop methods
                             |   of intrusion and attack
                             |
  Login and Authentication   | * Usernames and passwords may be hard-coded in
                             |   source code because one program module requires
                             |   acess to another system or API. This is a known
                             |   vulnerability, and best practices dictate that
                             |   authentication credentials should be stored
                             |   externally in encrypted digital vaults
                             |
                             | * Sometimes files checked into GitHub inadvertently
                             |   containt login credentials for other internal or
                             |   external services
                             |
                             | * The rise of (SaaS) and microservice architectures
                             |   means that many application components have to
                             |   authenticate and establish a secure session with
                             |   an API on another system.
                             |
                             | * Some developers cut corners by embedding login
                             |   and authentication data in the source code or
                             |   supporting files checked in to GitHub
                             |
                             | * When hackers gain access to the code, they can
                             |   gain access to related services, giving them the
                             |   opportunity to steal more data and disrupt operations
                             |
  Unauthorized Access        | * In many cases, developers are granted access to
                             |  company repositories from their personal or coporate
                             |  email accounts
                             |
                             | * These emal accounts may be left vulnerable, as some
                             |   organizations do not purge old email accounts in a
                             |   timely manner when employees leave the company
                             |
                             | * Another poor security practice is when dvelopers
                             |   are granted access to all of the company's
                             |   repositories instead of just what they need for
                             |   their projects
                             |
                             | * Over time, deficient security policies and
                             |   procedures create a wide-open attack surface
                             |   that attackers can exploit
                             |
  Insider Threats            | * a lack of proactive monitoring can allow
                             |   malicious insiders to hide abnormal activities
                             |
                             | * A single developer accessing many repositories
                             |   could be an early indicator of an insider threat,
                             |   and such behavior should be detected and flagged
                             |
                             | * Unfortunately, due to limited resources, many
                             |   organizations do not monitor the use of GitHub
                             |   and other external repositories
                             |
  Practical Steps for        |
  DevSecOps                  |
                             |
  Threat Monitoring for      | * DevSecOps practitioners can take practical steps
  GitHub                     |   to tighten security when using public repositories
                             |
  Clean Up Login Credentials | * It is best to limit access to only those developers
                             |   who are involved in a given project.
                             |
                             | * When developers leave a project, their credentials
                             |   should be revoked
                             |
  Maintain and Administer    | * The software behind GitHub - the software version
  Repository Settings        |   control program Git - was originally developed for
                             |   managing development of the Linux Kernel
                             |
                             | * Both Git and GitHub are widely used in open-source
                             |   projects
                             |
                             | * Some developers, particularly those that contribute
                             |   to open-souce projecs, treat all GitHub repositories
                             |   as public, whether they're for open-source projects
                             |   or not
                             |
                             | * DevSecOps best practice requires that you organizations
                             |   GitHub configuration be maintained and
                             |   administered on an ongoing basis to ensure that
                             |   access isn't any broader than necessary
                             |
  Monitor GitHub for         | * Many attacks originate from remote locations.
  Suspicious Activity        |   Organizations can map IP addresses to locations
                             |   where known employees and business partners reside.
                             |   Access from outside these locales often indicates
                             |   suspicious activity
                             |
                             | * Automated and manual monitoring of GitHub can
                             |   detect a sudden spike in souce code check-ins
                             |
                             | * Monitoring should also detect the check-out of
                             |   an unusually large amount of source code
                             |
                             | * It is also possible to monitor and detect logins
                             |   from unusual locations, or logins or requests from
                             |   users outside the organization.
                             |
  Aggregate and Analyze      | * GitHub logs can be aggregated and downloaded
  GitHub Logs                |   on a regular basis for further analysis.
                             |
                             | * Toos are available for parsing logs and analyzing
                             |   activity against a baseline of what would be
                             |   considered normal use.
                             |
                             | * When unusual activity is detected it can be reported
                             |   through dashboards or even messaged to stakeholders
                             |   as a means of providing early warning of potential
                             |   threats
                             |
--------------------------------------------------------------------------------
== Secure Containerization ==
  Containers                 | * Containers are specially formatted files that
                             |   contain executable application programs,
                             |   modules, and the code libraries that they
                             |   depend upon.
                             |
                             | * They isolate an application from other applications
                             |   and from the operating system and hardware.
                             |
                             | * Containers help ensure that the versions of
                             |   libraries within the container do not mandate
                             |   patching nd upgrades that might affect other
                             |   applications in other containters
                             |
                             | * In virtual environments, the libraries and
                             |   dependencies of an application were oftentimes
                             |   shared with all of the other applications on a
                             |   particular virtual server
                             |
  Use Case: Docker           | * While there are many container engines to choose
                             |   from, our use case is Docker
                             |
                             | * Process Restrictions use root/non-root dichotomy.
                             |   This makes it difficult to provoke system level
                             |   damages during an intrusion, even if the intruder
                             |   manages to excalate to root within a container
                             |   because the container capabilities are fundamentally
                             |   restricted
                             |
                             | * Device and File Restrictions further reduce the
                             |   attack suface by restricting access by continerized
                             |   applications to the physical device on a host,
                             |   through the use of the device resouce control
                             |   groups (cgroups) mechanism.
                             |
                             | * Container images are ephemeral. Each container
                             |   has its own file sysem and can not write to the
                             |   host file system unless writes are committed.
                             |   Committing changes tracks and audits revisions
                             |   made to the base images as a new layer which
                             |   can then be pushed as a new image for storage
                             |   in Docker Hub and run in a container.
                             |
                             | * The audit trail is important in providing
                             |   information to maintain compliance. It also
                             |   allows for a fast and easy rollback to previous
                             |   versions if a container has been compromised or
                             |   a vulnerability introduced
                             |
  Docker Hub:                | * Docker Hub is the world's largest public
                             |   repository of container images with an array of
                             |   content sources including container community
                             |   developers, open source projects, and independent
                             |   software vendors (ISV) building and distributing
                             |   their code in containers
                             |
                             | * Docker Hub allows you to:
                             |   * Search and browse for millions of container images
                             |   * View image popularity, vendor souce and
                             |     certification to inform you selection
                             |   * Access free public repositories to store your
                             |     images and share with the community
                             |   * Choose a subscription plan for private
                             |     repositories to limit access to your images
                             |   * Use Autobuilds and Webhooks for easy inegration
                             |     into your DevOps pipeline
                             |
                             | * While Docker Hub is a public repository, it
                             |   contains public, private, and official images
                             |
                             | * Public images are shared amongst a broad
                             |   community
                             |
                             | * Private images might be limited to a single
                             |   organization or even project within an
                             |   organization
                             |
                             | * Official repositories are certified repositories
                             |   from independent software vendors (ISV's) and
                             |   Docker contributors such as Canonical, Oracle,
                             |   RedHat, and others
                             |
  VM / Container comparison  |
                             |
  Virtual Machines           | * Virtual machines utilize a host OS with thei
                             |   own libraries. A hypervisor is used to facilitate
                             |   the installation and running of guest virtual
                             |   servers. The guest server have their own images
                             |   of an operating system and libraries. Applications
                             |   within each virtual server rely on the version of
                             |   the libraries and the guest operating system
                             |   instance
                             |
  Containers                 | * Containers rely on isolation techniques like
                             |   control groups and namespaces to separate
                             |   applications. They do not have a hypervisor
                             |   and can share libraries if needed. Containers
                             |   share the physical host's kernel, so they do not
                             |   require an operating system. Container systems
                             |   have processes in place to prevent a container
                             |   from making potentially dangerous changes to
                             |   the kernel
                             |
  Docker and Malware         | * Just as a repository can contain malicious source
                             |   code or infected libraries, Docker containers
                             |   may likewise be tainted. When they are replicaed
                             |   broadly throughout on-premise and off-premise
                             |   infrastructures, they can cary the malware with
                             |   them and compromise the integrity of producion
                             |   systems
                             |
  Docker Architecture        |

`                              +-----------------------+`
                          `    |  ===================  |`
                          `    |  || Docker Daemon ||  |`
                          `    |  ===================  |`
                          `    |                       |          +-----------------------+`
`  ===================         |  -------------------  |          |  -------------------  |`
`  || Docker client || <-----  |  | Container 1     |  | <------- |  | image 1         |  |`
`  ===================         |  -------------------  |          |  -------------------  |`
`                              |                       |          |                       |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`  | docker pull     |         |  | Container 2     |  |          |  | image 2         |  |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`                              |                       |          |                       |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`  | docker run      |         |  | Container 3     |  |          |  | image 3         |  |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`                              |                       |          |                       |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`  | docker ...      |         |  | Container N     |  |          |  | image N         |  |`
`  -------------------         |  -------------------  |          |  -------------------  |`
`                              +-----------------------+          |                       |`
`                                                                 +-----------------------+`

  Client/Server                 Docker Host                        Docker Registry

--------------------------------------------------------------------------------
== Docker trusted Registries ==
  Trusted Content and        | * Trusted registries are secure managed repositiories
  Digital Signatures         |
                             | * A registry is a data store that contains metadata
                             |   (i.e., data about data)
                             |
                             | * A repository contains the actual content of
                             |   interest
                             |
                             | * Trusted registries use a digital signature to
                             |   indicate which content in the repository is safe
                             |
                             | * Sotware publishers digitally sign their content
                             |   when it is published
                             |
                             | * Developers can use systems that verify digital
                             |   signatures prior to donwloading content
                             |
  Content Trust in Docker    | * Image signing and vulnerability scnanning allow
                             |   operations teams to protect the contents of
                             |   containers
                             |
                             | * Metadata may contain information about the author,
                             |   the bill of materials, and whether or not there
                             |   is a critical vulnerability, which can help
                             |   ensure that a container is safe at the time
                             |   of onboarding
                             |
                             | * Automated insights enable oreganizations to meet
                             |   compliance requirements and prevent security
                             |   breaches
                             |
  Policy-Based Image         | * Policy-based image promotion accelerates the
  Promotion                  |   DevSecOps pipeline by providing the data needed
                             |   for automated or manual promotion
                             |
                             | * The gating process can be configured to require
                             |   images to pass security scans.
                             |
                             | * Policy-driven automation improves scale and speed
                             |   by accommodating hundreds or thousands of
                             |   container images
                             |
  Docker Notary              |
  Architecture and Componens | * Notary clients pull metadata from one or more
                             |   remote Notary services
                             |
                             | * Some Notary clients also push metadata to one
                             |   or more Notary services
                             |
                             | * A Notary service consists of a Notary server,
                             |   which stores and updates the signed TUF metadata
                             |   files for multiple trusted collections in an
                             |   associated database
                             |
                             | * A Notary signer stores private keys and signs
                             |   metadata for the Notary server
                             |
  Using Private Keys to Sign | * Docker Notary controls server access through
  Containers                 |   strict authentication and open SSL security.
                             |
                             | * Clients upload metadata for their container
                             |   images
                             |
                             | * Once the data is verified, the server sends
                             |   approval for the container image to be signed
                             |
                             | * Encrypted keys are used for the signature
                             |
                             | * Notary Server is the source of truth for the
                             |   state of a trusted collection
                             |
                             | * Timestamps and checksums are used as part of
                             |   the signature to prevent forgery
                             |
--------------------------------------------------------------------------------
== Docker Bench ==
  CIS Docker Benchmark       | * Docker Bench is a software tool that analyzes
                             |   server infrastructures and Docker components
                             |
                             | * Docker Bench uses the CIS Docker Benchmark to
                             |   make recommendations on server hardening and
                             |   proper Docker configuration
                             |
                             | * Since new vulnerabilities are createdc and
                             |   discovered over time, it is important to
                             |   consult the benchmarks as they are revised
                             |   and updated.
                             |
                             | * Most importantly, tools that scan and detect
                             |   based on configuration files that use benchmarks
                             |   must be updated to the most recent release in
                             |   order to be effective
                             |
  Docker Bench               | * In large enterprises, the engineering and
                             |   operations departments create continer images
                             |   that include the necessary tooling for ongoing
                             |   detection and remediation
                             |
                             | * Since new vulnerabilites often come from
                             |   unprotected sources, teams must maintain certified
                             |   repositories
                             |
                             | * Trusted registries are the optimal source, and
                             |   teams must carry out careful onboarding when
                             |   using unproven sources
                             |
                             | * Docker Bench can be run regularly to detect
                             |   configuration flaws
                             |
  Host Configuration         | * Docker Bench recommends host hardening
                             |
                             | * Avoid the common mistake of creating uers within
                             |   the Docker group. This known vulnerability
                             |   allows privilege escalation on a spawned
                             |   container process, which can enable a user to
                             |   gain root access
                             |
                             | * Audit the file system agains the Docker directories
                             |   to receive early warning about unusual access
                             |   orupdates to system logs
                             |
  Docker Daemon              | * Containers allow network bridging to be limited
  Configuration              |   to only those ports necessary for the particular
                             |   application within the continer instance
                             |
                             | * Since SSL authentication has been deprecated,
                             |   Docker Bench recommends that the Docker daemon
                             |   be configured to use TLS (Transport Layer Security)
                             |   authentication
                             |
                             | * When running a container, you can set a ulimit
                             |   to ensuret hat the container is limited to a
                             |   specified maximum number of open file descriptors
                             |
                             | * Containers should be prohibited from acquiring
                             |   new privileges
                             |
                             | * When configuring the Docker daemon, Linux file
                             |   security must be strictly enforced
                             |
                             | * The Docker daemon runs as root, and while Linux
                             |   allows processes to be configured such that
                             |   their spawned child processes also run as root,
                             |   this is a vulnerability
                             |
                             | * The 644 octet grants read/write privileges to
                             |   the owner (in this case, root) but only read
                             |   privileges to group- and user-level processes
                             |
                             | * Nework sockets carry a similar security setting
                             |   when permissions are set
                             |
  Docker Security Operations | * Docker Swarm is a native clustering solution from
  and Swarm Configuration    |   Docker that can be used for continer orchestration
                             |
                             | * The Docker Bench includes a review of Docker
                             |   Swarm hardening recommendations
                             |
                             | * Note the Docker Bench recommendations for
                             |   maintaining secrets in a Swam Cluster
                             |
  Container Images and Build | * The Docker content trust system uses The
  File                       |   Update Framework (TUF) to enforce content trust
                             |
                             | * Container images signing and verification
                             |   policies can be set to allow the use of only
                             |   trusted repositories
                             |
                             | * The following commands can be configured
                             |   to require content trust:
                             |     docker pull
                             |     docker push
                             |     docker build
                             |     docker create
                             |     docker run
                             |
--------------------------------------------------------------------------------
== Provisioning with PaaS Tooling ==
  Provisioning               | * Provisioning means providing something for use
                             |
                             | * In DevSecOps, the process of providing the
                             |   developer with the software needed to develop
                             |   an application is automated
                             |
                             | * It's important to ensure that the same software
                             |   the developers use is provisioned in the test,
                             |   staging, and production environments
                             |
                             | * Complex systems require automation to ensure
                             |   that provisioned processes and components
                             |   remain uniform and managed
                             |
  Platform as a Service      | * The goal of Agile development is to give
  (PaaS)                     |   developers greater autonomy
                             |
                             | * Shift left is a process change in which
                             |   and engineering teams shift processes upstream
                             |   to developers
                             |
                             | * Anything "as a service" allows consumers to
                             |   request and receive deliverables on demand via
                             |   self-service portal
                             |
                             | * Platform as a Service (PaaS) offerings provide
                             |   developer platforms and infrastructures via
                             |   self-service tools and automation
                             |
  Templates                  | * Enterprise architects evaluate and test software
                             |   components for production use
                             |
                             | * PaaS systems facilitate the development of templates
                             |   (predefined configurations that comply with policy)
                             |
                             | * When developers require specific frameworks and
                             |   infrastructures, they can select from available
                             |   templates
                             |
                             | * Infrastructure as Code  simplifies the configuration
                             |   and deployment process and reduces maintenance
                             |
    * Source to Image (S21)  | * Source to Image (S21) is a framework for building
                             |   reproducible container images from application
                             |   source code and ependent component libraries
                             |
  OpenShift                  | * OpenShift is an open-source PaaS offering from
                             |   Red Hat
                             |
                             | * As containers and clustering have grown in
                             |   popularity, OpenShift has adopted Docker and
                             |   Kubernetes as standards
                             |
                             | * Now that OpenShift can be used to deploy and
                             |   manage production evnironments, it is considered
                             |   a container orchestration tool instead of a PaaS
                             |
                             | * OpenShift is a fully automated container
                             |   orchestration system that meets developer
                             |   provisioning needs and automates S21 as workloads
                             |   are promoted from development to test, staging,
                             |   and production
                             |
--------------------------------------------------------------------------------
== Securing the Automated Build ==
  Jenkins                    | * Jenkins is a popular open-source build
                             |   automation system
                             |
                             | * Jenkins originated from the open-source Hudson
                             |   project
                             |
                             | * Jenkis is highly extensible and supports hundreds
                             |   of plugins that handle build tasks
                             |
                             | * Jenkins supports Continuous Integration by
                             |   integrating with source code management tools
                             |
                             | * Jenkis supports webhooks that automatically
                             |   trigger a build process when developers check
                             |   in modified appliaction souce code
                             |
  Typical CI/CD Pipeline     | * A commit starts the process when the developer
  Architecture (Using        |   checks in code
  Jenkins)                   |
                             | * The CI server launches a build process
                             |
                             | * Automated unit tests are typically part of the
                             |   build process
                             |
                             | * Developers may review the build status via their
                             |   IDE or the Jenkins console
                             |
                             | * The build server delivers build artifacts to
                             |   the appropriate target, typically a staging
                             |   server
                             | * Commit -> Build -> Test -> Stage -> Deploy
                             |
  CI/CD Pipeline             | * Java builds typically involve a repor that
  Architecture (Using Jenkins|   contains needed component libraries
  with Maven                 |
                             | * Apache Maven is an open-souce tool often used
                             |   by Java teams
                             |
                             | * When Maven performs a build, it automatically
                             |   downloads libraries from Maven Central
                             |
                             | * Maven Central is a public repository maintained
                             |   by Sonatype
                             |
                             | * Most enterprises configure a repository inside
                             |   their firewall using products like Nexus
                             |
  Attack Surface of a        | * Attack vectors exist at the point of code
  of a typical CI/CD Build   |   check-in and anywhere an API session is
  Environment                |   established to pull code
                             |
                             | * Malware and vulnerabilities exist in most
                             |   component libraries pulled from third-party
                             |   repos
                             |
                             | * Since it is necessary to use vulnerable code,
                             |  vulnerability detection and monitoring must
                             |  be done after the build process
                             |
                             | * The OWASP Dependency Checker is one open-source
                             |   tool that detects and reveals vunerabilities
                             |   and their severity levels
                             |
--------------------------------------------------------------------------------
== Vulnerability Detection and Remediation ==
                             |
  OWASP Dependency Checker   | * OWASP Dependency Check is an open-source
                             |   scanning system
                             |
                             | * Dependency Check can be run from the command
                             |   line or throughn automated build program such
                             |   as Jenkins
                             |
                             | * OWASP Dependency Check maintains a downloaded
                             |   CVE database from the NIST NVD
                             |
                             | * OWASP Dependency Check provides human-readable
                             |  and machine-readable reports
                             |
                             | * To enforce security policy, automated builds
                             |   can be configurd to fail when policy
                             |  thresholds are exceeded
                             |
  OWASP Top 10 - 2017        | * Prioritization is vital to an effective security
                             |   strategy
                             |
                             | * It is impossible to eliminae vulnerabilities
                             |
                             | * The severity of a vulnerability indicates its
                             |   potential threat
                             |
                             | * The actual threat factors in its context
                             |
                             | * The key factor for defining and automating a
                             |   security policy is business impact
                             |
  OWASP Risk Management      | * Attackers can potentially use many different
                             |   paths through your application to do harm to
                             |   your business or organization. Each of these
                             |   paths represents a risk that may, or may not,
                             |   be serious enough to warrant attention
                             |
                             | * Sometimes these paths are trivial to find and
                             |   exploit, and sometimes they are extremely
                             |   difficult. Similarly, the harm that is caused
                             |   may be of no consequence, or it may put ou out
                             |   of business. To determine the risk to your
                             |   organization, you can evaluate the likelihood
                             |   associated with each threat agent, attack vector,
                             |   and security weakness and combine it with an
                             |   estimate of the technical and business impact
                             |   to your organization. Together, these factors
                             |   determine your overall risk
                             |
  OWASP Top 10 Risks         | 1)  Injection
                             | 2)  Broken Authentications
                             | 3)  Sensitive Data Exposure
                             | 4)  XML External Entities (XXE)
                             | 5)  Broken Access Control
                             | 6)  Security Misconfiguration
                             | 7)  Cross-Site Scripting (XSS)
                             | 8)  Insecure Deserialization
                             | 9)  Using Components with Known Vulnerabilities
                             | 10) Insufficient Logging and Monitoring
                             |
  DevSecOps Detection and    | 1)  Automate scanning throughout the pipeline
  Remediation                | 2)  Create well-defined security policy
                             | 3)  Implement rigorous gating
                             | 4)  Reduce the attack surface of DevOps infrastructures
                             | 5)  Continuously monitor deployed applications
                             | 6)  Establish traceability back to the developent
                             | 7)  Practice ongoing hygiene
                             | 8)  Utilize automated Configuratiom Management
                             | 9)  Establish automated roll-back and recover
                             | 10) Practice Continuous Improvement with ongoing
                             |     inspection and adaptation to accommodate security
                             |     enhancements
                             |
--------------------------------------------------------------------------------
== Secure Staging ==
  Nexus Repository (Use Case)| * Sonatype Nexus is an open-source repository
                             |   management system
                             |
                             | * Build artifacts produced by programs like Maven
                             |   are scanned as part of the automated build
                             |   pipeline
                             |
                             | * Once a build output is produced, it is important
                             |   to push the compiled file to a secure repo
                             |
                             | * A private on-premise or hardened cloud-based repo
                             |   server is needed to prevent unauthorized access
                             |   to or tampering with executable binaries
                             |
                             | * The use of a repo for build artifacts ensurs
                             |   that test, QA, and staging environments all
                             |   pull the same file, maintaining uniformity and
                             |   control of the deployment pipeling
                             |
  Typical CI/CD Pipeline     | * The Nexus repo manager has a secure API that
  Architecture (Using        |   allows the Jenkins pipeline to push artifacts
  Nexus)                     |   to the repo
                             |
                             | * Once in the repo, atifacts are proteced, and the
                             |   attach surface is limited to authorizd and
                             |   authenticated endpoints
                             |
                             | * QA (Quality Assurace) and UAT (User Acceptace
                             |   Test) platforms can then pull the executables
                             |   when neede
                             |
                             | * Container images can be stored in Nexus to
                             |   ensure that components and binaries are packaged
                             |   with build executables
                             |
                             | * Once a build artifact is stored, all upstream
                             |  environments use the original binary, even when
                             |  it is promoted to production.
                             |
  Automated Provisioning and | * PaaS and ARA tooling depends on a stable repo
  Application Release        |   for fast-and-frequent releases
  Automation (ARA)           |
                             | * Automated release and promotion to test
                             |  environments prevents human error and other
                             |  factors from disrupting uniform and consistent
                             |  platforms
                             |
--------------------------------------------------------------------------------
== 4.1 Release Gating - The 16 Gates ==
  Release Gating             | * Release gating is a means of conrol that involves
                             |   checks and blances in large enterprises
                             |
                             | * Authorized stakeholders responsible for governance,
                             |   risk manaement, audit, and compliance review build
                             |   artifacts prior to approving a software release
                             |   for deployment
                             |
                             | * While release gating may be done at various
                             |   stages of the pipeline, it is most often peformed
                             |   in Pre-Producion
                             |
  The 16 Gates               | * The 16 gates are a set of software quality attributes
                             |   that should be evaluated as part of a governed
                             |   deployment process
                             |
                             | 1. Source code version control *  9. Immutable servers *
                             | 2. Optimum branching strategy     10. Integration testing
                             | 3. Static analysis             *  11. Performance testing
                             | 4. At least 80% code coverage     12. Bulid deploy testing automated for every commit *
                             | 5. Vulnerability scan          *  13. Automated rollback *
                             | 6. Open source scan            *  14. Automated change order
                             | 7. Artifact version control       15. Zero-downtime release
                             | 8. Auto provisioning           *  16. Feature toggle *
                             |
                             | (* - Aspects of the 16 Gates that are of particular
                             |      Concern to security)
                             |
                             |
                             |
----  5 - Continuous Delivery Release Automation  ------------------------------
== 5.1 - Automated Deployment ==
  Continuous Delivery        | * Continuous Delivery Release Auomation (CDRA)
  Release Automation (CDRA)  |   is the practice and tooling required to promote
                             |   application workloads to upper environments with
                             |   minimal or no manual inervention
                             |
                             | * Automted Deployment systems are typically employed
                             |   for all post-build platform includint test, QA
     (User Acceptance Test)  |   UAT, Pre-Production and ultimately production
                             |
                             | * CDRA systems categorized into two domans,
                             |   Application Release Automation (ARA) and Application
                             |   Release Orchestration (ARO)
                             |
                             | * The context of this lesson is primarily focused
                             |   on ARA. Orchestration would include many concepts
                             |   such as self-healing, cloud bursting, and hybrid
                             |   cloud orchestration
                             |
                             | * NOTE: Automated DEployment is critical to ensure
                             |         control and consistency when promoting
                             |         workloads into production environment
                             |
  Automated Deployment       | * Automaed Deployment refers to the practice and
                             |   tooling used to cause build artifacts to be
                             |   installed on upper level environments including
                             |   production systems
                             |
                             | * Automation is key to improving throughput, but
                             |   also as a means of controlling outcomes and
                             |   ensuring consistency
                             |
                             | * Once systems have cleared gating, triggers in
                             |   the tooling call programs that ready the
                             |   infrastructure and deploy, or install the
                             |   application so that it may be immediately executed
                             |
  DeployHub (Use Case)       | * Automated Deployment Tooling varies widely in
                             |   capability and level of implementation
                             |
                             | * DeployHub is an open source solution that is
                             |   hosted as a SaaS solution as well as being
                             |   offered for on-premie implementation
                             |
                             | * DeployHub provides a means of integrating
                             |   deployment with Jenkins build automation,
                             |   the nexus repo, and may use Ansible playbooks
                             |   for actual deployment
                             |
--------------------------------------------------------------------------------
== 5.2 - Configuration Management ==
  Configuration Management   | * Configuration Management is the practice and
                             |   and toolingrequired to fully automate the process
                             |   of configuring target environments and deploying
                             |   application workloads to them.
                             |
                             | * While Configuration Management is useful at all
                             |   stages of provisioning, it is especially imporant
                             |   when dealing wit production platforms
                             |
                             | * Configuration Management is an automated approach
                             |   that replaces traditional scripting and improves
                             |   control and consistency when deploying applications
                             |
                             | * Configuration management with this lesson is focused
                             |   on the domain of Automated Deployment
                             |
                             | * NOTE: Automated Deployment is critical to ensure
                             |         control and consistency when promoting workloads
                             |         into production environment
                             |
  (Ansible Use Case)         | * Ansible is an open source configuration management
                             |   tool from Red Hat
                             |
                             | * Ansible utilizes playbooks to deploy both systems-
                             |   level and application-level components to target
                             |   environments
                             |
                             | * Ansible uses YAML files known as playbooks to
                             |   automate doployments
                             |
                             | * Playbooks have the ability to test state on target
                             |   platforms and only perfom those configuration and
                             |   installation steps necessary to enable the worldload
                             |
                             | * Ansible performs its work in a predefined chronology
                             |   to ensure dependencies are met.
                             |
                             | * Infrastructures as Code (IaC is the key aim of
                             |   tooling such as Ansible
                             |
----  6 - Production Monitoring and Ongoing Detection and Remediation  ---------
== 6.1 - Production Monitoring ==
  Production Monitoring      | * Continuous monitoring is the ongoing, automated
                             |   evaluation of workloads to assess their health and
                             |   function
                             |
                             | * Production monitoring may include threat detection,
                             |   vulnerability detection, and malware prevention
                             |
                             | * Since new threats and vulnerabilities are
                             |  developed and discovered over time, it is important
                             |  to monitor applications throughout their entire
                             |  lifespan, not just while they're under development
                             |
                             | * When applications need to be refactored or upgraded
                             |   with patched third-party libraries, feeedback loops
                             |   and automated reporting notify the development team
                             |   that vulnerabilities or other defects require attention
                             |
  Static Application         | * Static scanning is used to test for new vulnerabilities
  Security Testin (SAST)     |   that have become known since an application's release
                             |   ino production
                             |
                             | * Scanning tools use container image manifests and
                             |   build time dependency lists to determine which
                             |   known vulnerabilities are present in compiled
                             |   appliations and container images
                             |
                             | * Due to ongoing chanes to operating systems, binary
                             |   libraries, and third-party software components,
                             |   applications need to be continually upgraded.
                             |   Scanning is fundamental to hygiene, and as
                             |   applications are redeployed, automated pipelines
                             |   ensure persistent security
                             |
                             | * NOTE: Ongoing Static Application Security Testing
                             |   (SAST) is necessary to keep applications free of
                             |   vulnerabilities
                             |
  Dynamic Application        | * Dynamic scanning uses black box security testing
  Security Testing (DAST)    |   methodology
                             |
                             | * A black box test involves testing an application
                             |   from the ouside in while it is running in production
                             |
                             | * In DAST, a security analyst attempts to hack an
                             |   application in the same way a cyber attacker would
                             |
                             | * Unlike SAST, DAST does not involve examining
                             |   source code to identify vulnerabilites from the
                             |   inside out
                             |
  Penetration Tests          | * Penetration tests (pentests) are a form of DAST
                             |   that use external programs to interrogate
                             |   applications ithrough their exposed API and HTTP
                             |   endpoints
                             |
                             | * Penetration tests simulate automated cyber attacks
                             |   on production infrastructure
                             |
                             | * Penetration tests detect common vulnerabilities such
                             |   as injection, cross-site scripting, and flaws in
     (Idenity and access     |   authentication and identity and access manaement
      management)            |   (IAM)
                             |
--------------------------------------------------------------------------------
== 6.2 - DashBoards and Automated Vulnerability Detection ==
  Dashboards and Auomated    | * Dashboards provide continual updates on the health
  Vulnerability Detection    |   of applications running in production
                             |
                             | * Dashboards aggregate and analyze logs, providing
                             |   a stream of real-time data that is presented visually
                             |   based on predefined ocnfigurations
                             |
                             | * Extensible dashboard software systems support
                             |   plugins that can be configured according to user
                             |   preferences
                             |
                             | * Dashboards also let you set up real-time alerts
                             |   for system events that require immediate attention
                             |
  Automated Vulnerability    | * DAST and SAST tools can provide logs for
  Detection                  |   aggregation and monitoring in dashboard systems
                             |
                             | * Many dashboard visualization systems generate
                             |   benchmark thresholds of normal performance and
                             |   report anomalies that exceed normal limits
                             |
                             | * Advanced machine lerning and artificial intelligence
                             |   algorithms can be used to score workloads over time
                             |   and provide alerts when threas increase
                             |
  Traceability and Rollback  | * Traceability refers to the process of communicating
                             |   information about threat detection back to stakeholders
                             |   including the development team
                             |
                             | * When release management and source code control is
                             |   established to track major releases and sub-releases
                             |   of applications, vulnerability reporting can be traced
                             |   back to the specific souce code being evaluaed
                             |
                             | * Alerts and threat detecion can be used to automatically
                             |   roll back vulnerable systems when new releases appear
                             |   flawed
                             |
                             | * NOTE: Branching and rebasing souce code throughout
                             |         an automated release cycle helps with
                             |         identifying vulnerable source code during
                             |         production monitoring
                             |
  Agile Lifecycle Integration| * Developmen teams use Agile Backlogs to record
                             |  user stories
                             |
                             | * Production monitoring systems often provide a way
                             |   to create tickts and integrae with Agile lifecycle
                             |   managemen tools
                             |
                             | * Production monitoring systems often provide a
                             |   way to creae tickes and integrae with Agile lifecycle
                             |   management tools
                             |
                             | * Up-to-date feedback from production systems helps
                             |   with continuous adapion and improvement
--------------------------------------------------------------------------------
== Next Steps ==
  Areas of Specialty

`- Development                 - Release Management           - Operations`
`  * Source Code Management      * Build Pipeline Automation    * Server Hardening`
`  * Agile Lifecycle Tools       * Continuous Integration       * Application Hardening`
`  * Test-Driven Development     * Automated Testing            * Continuous Deployment`
`  * PaaS Tooling                * Pre-Production Staging       * Continuous Monitoring`
`  * Security Standards          * Release Automation           * Security Analytics`
`  * Containerization            * Configuration Management     * Cloud Orchestration`

Mesuring DevSecOps Success   | * Deployment frequency (fast and frequent releases)
                             | * Lead time (code-to-cash cycle)
                             | * Detection of treats, vulnerabilities, and malware
                             | * Mean time to repair and remediaion
                             | * Efficiency of rollback and recovery
                             |
--------------------------------------------------------------------------------
