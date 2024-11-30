# Raid

## Raid levels

| RAID Level                   | Description                                                                                                                    | Purpose                                                                                                                                                      | Minimum Disks                         | Maximum Disks                                                                      |
| :--------:                   | -----------                                                                                                                    | -------                                                                                                                                                      | :-----------:                         | -------------                                                                      |
| RAID 0                       | Striping: Data is split evenly across two or more disks without parity or redundancy.                                          | Performance: Increases read/write speeds by accessing multiple disks simultaneously. No fault tolerance; if one disk fails, all data is lost.                | 2                                     | No limit (practical limits apply)                                                  |
| RAID 1                       | Mirroring: Identical data is written to two or more disks.                                                                     | Redundancy: Provides fault tolerance by maintaining a complete copy of data on each disk. Can survive the failure of one or more disks.                      | 2                                     | Typically 2 (some implementations allow more)                                      |
| RAID 5                       | Striping with Distributed Parity: Data and parity information are striped across disks.                                        | Balance: Offers good performance, efficient storage, and fault tolerance. Can withstand a single disk failure.                                               | 3                                     | Limited by controller (practical limits apply)                                     |
| RAID 6                       | Striping with Double Parity: Similar to RAID 5 but with two parity blocks.                                                     | Enhanced Fault Tolerance: Can tolerate the failure of two disks simultaneously. Suitable for larger arrays.                                                  | 4                                     | Limited by controller (practical limits apply)                                     |
| RAID 10 (1+0)                | Striped Mirrors: Combines mirroring and striping by mirroring data across pairs of disks and then striping across those pairs. | Performance & Redundancy: High read/write speeds with fault tolerance. Can survive multiple disk failures as long as they are not in the same mirrored pair. | 4                                     | Must be even; no strict limit (practical limits apply)                             |
| RAID 0+1                     | Mirrored Stripes: Data is striped across disks, and the stripe set is then mirrored.                                           | Performance & Limited Redundancy: Similar to RAID 10 but less fault-tolerant. If a disk fails, one entire stripe set becomes unavailable.                    | 4                                     | Must be even; no strict limit (practical limits apply)                             |
| RAID 50 (5+0)                | Striped RAID 5 Arrays: Multiple RAID 5 arrays are striped together.                                                            | High Performance & Fault Tolerance: Better write performance and can tolerate multiple disk failures (one per RAID 5 array).                                 | 6                                     | (two RAID 5 arrays of 3 disks each)	Limited by controller (practical limits apply) |
| RAID 60 (6+0)                | Striped RAID 6 Arrays: Multiple RAID 6 arrays are striped together.                                                            | Maximum Fault Tolerance: Can tolerate multiple disk failures (up to two per RAID 6 array). Ideal for critical applications requiring high availability.      | 8 (two RAID 6 arrays of 4 disks each) | Limited by controller (practical limits apply)                                     |
| RAID 1E                      | Striped Mirroring with Odd Number of Disks: Combines mirroring and striping, works with an odd number of disks.                | Flexibility & Redundancy: Offers fault tolerance and improved performance with flexible disk configurations.                                                 | 3                                     | Limited by controller (practical limits apply)                                     |
| JBOD (Just a Bunch of Disks) | Disks are concatenated together without any RAID configuration.                                                                | Capacity Expansion: Utilizes the full capacity of all disks. No performance gain or fault tolerance.                                                         | 1                                     | Limited by controller                                                              |

### Key Considerations for NAS Setup:
* RAID 0: Best for non-critical systems where performance is prioritized over data safety.
* RAID 1: Suitable for small NAS setups needing simple redundancy and easy recovery.
* RAID 5: Common choice for NAS due to its balance of performance, storage efficiency, and fault tolerance.
* RAID 6: Recommended for larger NAS systems where the risk of multiple simultaneous disk failures is higher.
* RAID 10: Ideal for applications requiring high performance and redundancy but comes with higher cost due to reduced usable capacity.

### Additional Notes:
* RAID is Not a Backup Solution: RAID protects against hardware failures but doesn't replace regular backups, which are necessary to safeguard against data corruption, accidental deletion, or catastrophic events.
* Disk Compatibility: Ensure all disks used are of the same type and capacity for optimal performance and efficiency.
* Controller Considerations: Hardware RAID controllers offer better performance but are more expensive than software RAID solutions.
* Hot Spares: Configuring hot spare disks can reduce downtime by automatically rebuilding data onto a spare disk in case of a failure.

## Open Source Raid solutions

Open Source Software RAID Solutions

When setting up a Network Attached Storage (NAS) system, utilizing open-source software RAID solutions can provide flexibility, cost savings, and community support. Below are some of the most popular open-source software RAID options:

1. **<u>mdadm (Linux Software RAID)</u>**
* **Description**: mdadm is a Linux utility used to manage and monitor software RAID devices. It allows you to create and manage various RAID levels, including RAID 0, 1, 4, 5, 6, and 10.
* **Features**: 
  * Integrated into most Linux distributions.
  * Command-line tool offering granular control.
  * Supports hot-swapping and hot-spares.
* **Use Cases**: Ideal for users comfortable with the command line who want direct control over their RAID configurations without additional abstraction layers.

2. **<u>ZFS (Zettabyte File System)</u>**

* **Description**: ZFS is both a filesystem and a volume manager that includes built-in RAID-like functionality known as RAID-Z (equivalent to RAID 5) and RAID-Z2/RAID-Z3 (equivalent to RAID 6 with double and triple parity).
* **Features**:
  * Advanced data integrity checks with copy-on-write.
  * Supports snapshots, cloning, and data compression.
  * Scalable to large storage capacities.
* **Use Cases**: Suited for systems where data integrity and reliability are critical. Commonly used in FreeBSD and Solaris environments and is the default filesystem for TrueNAS CORE.

3. **<u>Btrfs (B-Tree File System)</u>**
* **Description**: Btrfs is a modern Linux filesystem that incorporates advanced features, including built-in RAID support for RAID 0, 1, 5, 6, and 10.
* **Features**:
  * Supports snapshots and subvolumes.
  * Online resizing and defragmentation.
  * Data and metadata checksumming for integrity.
* **Use Cases**: Good for users wanting advanced filesystem features integrated with RAID capabilities on Linux systems.

4. **<u>LVM (Logical Volume Manager)</u>**
* **Description**: LVM allows for flexible disk management on Linux, providing a layer between physical disks and file systems. While not a RAID solution by itself, it can be combined with mdadm or used to create mirrored volumes.
* **Features**:
  * Dynamic resizing of logical volumes.
  * Snapshots for backups.
  * Stripe and mirror capabilities.
* **Use Cases**: Ideal for complex storage setups requiring dynamic resizing and management.

5. **<u>OpenMediaVault</u>**
* **Description**: A Debian-based NAS operating system that provides a web-based administration interface for easier management, including support for software RAID via mdadm.
* **Features**:
  * Plugin system for extended functionality.
  * Supports various network protocols (SMB/CIFS, FTP, NFS).
  * Monitoring and email notifications.
* **Use Cases**: Suitable for home or small office environments where ease of use and web-based management are desired.

6. **<u>TrueNAS CORE (formerly FreeNAS)</u>**
* **Description**: An open-source NAS operating system based on FreeBSD that uses ZFS for storage management.
* **Features**:
  * Advanced ZFS features for data protection and integrity.
  * Web-based management interface.
  * Supports plugins, jails, and virtual machines.
* **Use Cases**: Ideal for users needing robust data integrity features with a user-friendly interface.

7. **<u>Rockstor</u>**
* **Description**: A Linux and Btrfs-based NAS solution offering a web interface for easy management.
* **Features**:
  * Docker support for running applications.
  * Easy management of storage pools, shares, and snapshots.
  * Replication and scheduled tasks.
* **Use Cases**: Good for users who want the advanced features of Btrfs with simplified management.

8. **<u>SnapRAID</u>**
* **Description**: A backup program for disk arrays that provides redundancy and protection against disk failures.
* **Features**:
  * Allows disks of different sizes.
  * Adds parity information to recover from disk failures.
  * Data is stored unaltered; files are not split across disks.
* **Use Cases**: Suitable for large media collections that are mostly static and require protection against disk failures without the overhead of traditional RAID.

9. **<u>Greyhole</u>**
* **Description**: An application that uses Samba shares to create a storage pool of all available hard drives with file-level redundancy.
* **Features**:
  * Uses existing filesystems; no need to format drives.
  * Configurable file duplication across multiple drives.
  * Integrates with Amahi Home Server for easy management.
* **Use Cases**: Ideal for users wanting to pool disparate disks and have redundancy at the file level without traditional RAID.

10. **<u>mergerfs</u>**
* **Description**: A union filesystem that allows multiple drives to be combined into a single pool without RAID.
* **Features**:
  * Files are stored on individual drives.
  * Supports various policies for file placement.
  * Can be used in conjunction with SnapRAID for redundancy.
* **Use Cases**: Great for pooling drives of different sizes while maintaining simplicity and flexibility.

Key Considerations:

Data Integrity and Protection:

Filesystems like ZFS and Btrfs offer advanced features for data integrity, such as checksumming and self-healing.
Traditional RAID (via mdadm) provides redundancy but doesn't protect against data corruption.
Ease of Use vs. Control:

Solutions with web-based interfaces (TrueNAS CORE, OpenMediaVault, Rockstor) are easier to manage but may offer less granular control than command-line tools.
Command-line tools (mdadm, LVM) provide more control and are scriptable but have a steeper learning curve.
Community and Support:

Open-source projects often have active communities for support.
Consider the maturity and update frequency of the project.
Compatibility:

Ensure that the chosen solution is compatible with your hardware and meets your performance requirements.
Some filesystems (like ZFS) have specific memory requirements.
Conclusion:

Selecting the right open-source software RAID solution depends on your specific needs, technical expertise, and the importance of features like data integrity, scalability, and ease of management. Whether you prefer the command-line control of mdadm and LVM or the user-friendly interfaces of NAS distributions like TrueNAS CORE and OpenMediaVault, open-source options provide robust solutions for building a reliable and efficient NAS system.

Next Steps:

Evaluate Your Requirements: Determine the importance of factors like data integrity, ease of management, performance, and scalability.
Test in a Safe Environment: If possible, set up a test environment to familiarize yourself with the tools and ensure compatibility.
Consult Documentation and Communities: Leverage the extensive documentation and active user communities associated with these open-source projects for guidance and best practices.
