[Main Index](../../../index.md)

# One-Week Deep Dive into LXC
## Index
* [Day 1: Foundations of LXC](Day1)
* [Day 2: Creating and Managing Containers](Day2)
* [Day 3: Networking with LXC](Day3)
* [Day 4: Deep Configuration and Resource Limits](Day4)
* [Day 5: Advanced Usage](Day5)
* [Day 6: Building a Practical Project](Day6)
* [Day 7: Troubleshooting, Optimization, and Next Steps](Day7)

## Prerequisites:
* Basic Linux system administration knowledge (CLI, processes, file system, networking).
* Familiarity with virtualization and container concepts (basic understanding).

### Day 1: Foundations of LXC
* What is LXC? How it compares to Docker, systemd-nspawn, VMs.
* How LXC works under the hood (namespaces, cgroups, chroot, AppArmor/SELinux).
* Installing LXC on your system (Ubuntu/Debian/Arch).
* Key components: `lxc`, `lxd` (brief difference).
* Setting up the environment:
    * Install LXC
    * Configure unprivileged user containers
* Your first container:
    * Create
    * Start
    * Stop
    * Destroy

**Mini Project**: Create your first container and install a package inside it.

### Day 2: Creating and Managing Containers
* `lxc-create` options explained (templates, configs).
* Using templates (Ubuntu, Alpine, BusyBox, custom templates).
* Managing lifecycle:
    * `lxc-start`, `lxc-stop`, `lxc-restart`, `lxc-destroy`
* Understanding and modifying container configuration files.
* Inspecting containers (`lxc-info`).

**Mini Project**: Create 2 containers (one privileged, one unprivileged) and modify their configs manually.

### Day 3: Networking with LXC
* Understanding default LXC networking (lxcbr0, macvlan, phys).
* Creating containers with custom networking.
* Bridged networking vs NAT.
* Assigning static IPs to containers.
* Port forwarding (host to container).

**Mini Project**: Create a container with a static IP and SSH into it from the host.

### Day 4: Deep Configuration and Resource Limits
* Detailed walkthrough of `config` files.
* Setting resource limits (CPU, Memory, Disk I/O, Network).
* Mounting host directories into containers.
* Securing containers: AppArmor and Seccomp basics for LXC.
* Using `lxc-attach` and `lxc-console` to connect to containers.

**Mini Project**: Set resource limits on a container and mount a directory from host to container.

### Day 5: Advanced Usage
* Cloning containers (`lxc-copy`).
* Snapshotting containers.
* Migrating containers between hosts (basic overview).
* Creating your own LXC template (basic script).
* Using autostart containers with the host system boot.

**Mini Project**: Clone a container, create a snapshot, and restore it.

### Day 6: Building a Practical Project
* Building a lightweight multi-container environment:
    * Web Server Container (e.g., nginx)
    * Database Server Container (e.g., MariaDB)
    * Client Container (e.g., curl)
* Inter-container communication setup (network bridge).

**Mini Project**: Deploy a simple web page that talks to the database using separate containers.

### Day 7: Troubleshooting, Optimization, and Next Steps
* Troubleshooting tips (logs, `dmesg`, LXC debug mode).
* Optimizing container performance.
* When to use LXD vs LXC.
* Comparing LXC with other container systems.
* Ideas for next steps:
    * LXC inside systemd services.
    * Build an entire home-lab using only LXC.
    * Exploring container orchestration with LXC.

**Final Project**: Create a multi-container mini-app with resource isolation, custom networking, and auto-start on boot.

## Materials You’ll Need
* Access to a Linux machine (VM or bare metal preferred).
* Root access or sufficient permissions for container management.
* About 1–2 hours per day for exercises.
