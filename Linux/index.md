# Linux Documentation Index

## Overview
This repository contains organized Linux documentation covering general concepts, system administration, distributions, tools, and certifications.

## Directory Structure

### [01_General/](01_General/) - General Linux Concepts
- **Linux Fundamentals**
  - [Linux General Notes](01_General/Linux_General_Notes.md) - Basic Linux concepts
  - [Filesystem Hierarchy Standard (FHS)](01_General/fhs.md) - Linux directory structure
  - [Linux Plus Notes](01_General/linux_plus.md) - Comprehensive Linux notes

### [02_System_Administration/](02_System_Administration/) - System Management
- **Core Administration**
  - [Atos Linux Administration](02_System_Administration/atos_linux_administration.md) - Complete administration course
  - [General Administration](02_System_Administration/General_administration.md) - Daily administration tasks
  - [Linux System Administration](02_System_Administration/linux_sysad.md) - Sysadmin basics
  
- **Service Management**
  - [Systemd](02_System_Administration/systemd.md) - System and service manager
  - [Firewalls](02_System_Administration/firewalls.md) - Firewalld and iptables

### [03_Distributions/](03_Distributions/) - Linux Distributions
- **Enterprise Distributions**
  - [CentOS 8](03_Distributions/centos8.md) - CentOS 8 documentation
  - [SUSE Linux Enterprise Server 15](03_Distributions/suse_linux_enterprise_server_15.md) - SLES 15 guide
  
- **Community Distributions**
  - [Arch Linux](03_Distributions/arch_linux.md) - Arch Linux documentation
  - [Debian Linux](03_Distributions/debian_linux.md) - Debian basics

### [04_Tools_Applications/](04_Tools_Applications/) - Tools & Software
- **Command Line Tools**
  - [Basic Commands](04_Tools_Applications/basic_commands.md) - Essential Linux commands
  - [sed](04_Tools_Applications/sed.md) - Stream editor tutorial
  - [Executing Linux Commands in Python](04_Tools_Applications/Executing_Linux_commands_in_Python.md) - Python integration
  
- **System Components**
  - [Package Management](04_Tools_Applications/package_management.md) - Package managers
  - [Hyprland](04_Tools_Applications/hyprland.md) - Wayland compositor
  - [LightDM](04_Tools_Applications/lightdm.md) - Display manager

### [05_Certifications_Courses/](05_Certifications_Courses/) - Learning Resources
- **Course Materials**
  - [Linux Bootcamp](05_Certifications_Courses/linuxbootcamp.md) - Bootcamp curriculum
  - [LXC Syllabus](05_Certifications_Courses/lxc-syllabus.md) - Linux Containers course

## Quick Reference

### Essential Commands
- File operations: `ls`, `cp`, `mv`, `rm`, `find`
- Text processing: `grep`, `sed`, `awk`, `cut`, `sort`
- System info: `uname`, `df`, `free`, `top`, `ps`
- Networking: `ip`, `ss`, `ping`, `curl`, `wget`

### Common Tasks
1. **User Management**: `useradd`, `usermod`, `passwd`, `groupadd`
2. **Permissions**: `chmod`, `chown`, `chgrp`, `umask`
3. **Process Management**: `ps`, `top`, `kill`, `systemctl`
4. **Package Management**: `apt`, `yum`, `dnf`, `pacman`
5. **Network Configuration**: `ip`, `nmcli`, `firewall-cmd`

## How to Use This Documentation

### For Beginners
1. Start with [01_General/](01_General/) for basic concepts
2. Learn essential commands from [basic_commands.md](04_Tools_Applications/basic_commands.md)
3. Practice with the [Atos Linux Administration](02_System_Administration/atos_linux_administration.md) course

### For System Administrators
1. Review [System Administration](02_System_Administration/) section
2. Master [systemd](02_System_Administration/systemd.md) for service management
3. Study distribution-specific guides in [03_Distributions/](03_Distributions/)

### For Developers
1. Learn command-line tools in [04_Tools_Applications/](04_Tools_Applications/)
2. Understand Python integration with Linux commands
3. Explore containerization with LXC syllabus

## Contributing
This documentation is organized for clarity and ease of use. To contribute:

1. Place new files in the appropriate category directory
2. Update this index.md file with new entries
3. Follow existing formatting conventions
4. Test all commands and examples

## Recent Updates
- **2026-04-05**: Reorganized 22 Linux markdown files into logical structure
- **2026-04-05**: Merged duplicate files (commands, firewalls)
- **2026-04-05**: Enhanced systemd documentation
- **2026-04-05**: Completed TODOs in Atos Linux Administration course

## Related Resources
- [Linux Man Pages](https://man7.org/linux/man-pages/)
- [The Linux Documentation Project](https://tldp.org/)
- [Linux Foundation Training](https://training.linuxfoundation.org/)
- [Red Hat Documentation](https://access.redhat.com/documentation/)

---
*Last updated: 2026-04-05*  
*Total files: 20 organized markdown files*