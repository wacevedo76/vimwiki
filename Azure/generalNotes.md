[[AzureIndex.wiki|Back]]
--------------------------------------------------------------------------------
= Azure Cloud General Notes =
--------------------------------------------------------------------------------
5 Characteristics of could   | * On-Demand Self service
Computing                    | * Broad Network Access
                             | * Resource Pooling
                             | * Rapid Elasticity
                             | * Measured Service
                             |
  On-Demand Self Service     | * No human interation is needed for resource provisioning
                             | * Resource cab be provisioned with a click of a button
                             | * Provisioning is avaiable 24/7
                             |
  Broad Network Access       | * Reources can be accessed from anywhere using the network
                             | * Ideally high broadband
                             | * No physicall access is required at any time
                             |
  Resouce Pooling            | * Physical resources are shared between customes
                             | * The cloud's backbone decides which physical resouce to
                             |   allocate for a customer's virtua services
                             |
                             | * Some advanced cloud services allow for physical resource
                             |   separation
                             |
  Rapid Elasticity           | * Resources can be scaled up and down as needed, automatically
                             | * No need to purhase resources for a one -time peak scenario
                             |
  Measured Service           | * Payment is done only for resources actually used
                             | * Server time/ DB storage / Function calls etc.
                             | * Measurment usually done in high-resolution
                             |   * Server time by the seond
                             | * No need ot invest money in non-used resources
                             |
Types of Cloud Services      | * Iaas
                             | * PaaS
                             | * SaaS
                             |
  Infrastructure as a Service| * The cloud provides the underlying platform
  (Iaas)                     |   * Compute
                             |   * Networking
                             |   * Storage
                             | * The client handles, and is responsible for all the rest. Examples:
                             |   - Virtual Machines - The cloud provides the host machine, networking
                             |       and disks. The client creates the virutal (guest) machine,
                             |       installs software on it, patches it, maintains it, etc
                             |
  Platform as a Service      |
  (PaaS)                     | * The cloud provides the platform for running aps
                             |   * Compute
                             |   * Networking
                             |   * Storage
                             |   * runtime environment
                             |   * scaling,
                             |   * redundancy
                             |   * security
                             |   * updates
                             |   * patching
                             |   * maintenance, etc
                             | * The client just needs to bring the code, and it just runs
                             | * The client has no access to the underlying virtual machines
                             | * Most common example:
                             |   * Web Apps
                             |
                             |
  Software as a Service      | * A software running completely in the cloud
  (SaaS)                     | * The user doesn't need to install anything on-premises or on
                             |   their machine
                             | * The provider of the software takes care of updates, patches
                             |   redundancy, scalability, etc
                             | * Most common example:
                             |   * Office 365, Salesforce

=== Matrix of controll ===
`   on-premises        IaaS               Paas               SaaS      `
`| Application      | Application      | Application        Application     `
`| Data             | Data             | Data               Data            `
`| Runtime          | Runtime            Runtime            Runtime         `
`| middleware       | middleware         middleware         middleware      `
`| OS               | OS                 OS                 OS              `
`| Virtualization     Virtualization     Virtualization     Virtualization  `
`| Servers            Servers            Servers            Servers         `
`| Storage            Storage            Storage            Storage         `
`| Networking         Networking         Networking         Networking      `
                             |
                             |
                             |
                             |
                             |
                             |
[[AzureIndex.wiki|Back]]
