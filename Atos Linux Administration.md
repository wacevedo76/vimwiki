--------------------------------------------------------------------------------
Linux Administration
--------------------------------------------------------------------------------
= Introduction to linux & the command line =
  TODO                       |
--------------------------------------------------------------------------------
= Mange Users & Groups =
  TODO                       |
--------------------------------------------------------------------------------
= Files access & Permissions =
  TODO                       |
--------------------------------------------------------------------------------
= Disk Partitions & File Systems =
  TODO                       |
--------------------------------------------------------------------------------
= Logical Volumes and & Filesystem Hierarchy =
  TODO                       |
--------------------------------------------------------------------------------
= Using vi/vim to edit =
  TODO                       |
--------------------------------------------------------------------------------
= Locating & manipulating File =
  TODO                       |
--------------------------------------------------------------------------------
= Searching & Manipulating File Contents =
  TODO                       |
--------------------------------------------------------------------------------
= Boot Process & Kernel =
== Configureing the Linux Kernel ==
  location of modules        | /usr/lib/modules /lib/modules
                             |
  Command to list modules    | lsmod
                             |
  Install module             | insmod
                             |
  remove mod                 | rmmod
                             |
  have system detect         | modprobe
    hardware                 |
                             |
  location of module files   |
  on myny Linux files sys    | /etc/modprobe.d/
                             |
  list parameters being      | sysctl -a 
  passed to the kernel       |
                             |
Describing the boot process 
            `-----------------------------------`
            `|            Bios UEFI             |`
            `-----------------------------------`
                             |
            `-----------------------------------`
            `|            MBR / GPT             |`
            `-----------------------------------`
                             |
            `-----------------------------------`
            `|              GRUB2               |`
            `-----------------------------------`
                             |
            `-----------------------------------`
            `|        initrd / Kernel           |`
            `-----------------------------------`
                             |
            `-----------------------------------`
            `|       systemd process            |`
            `-----------------------------------`
                             |
--------------------------------------------------------------------------------
= Graphical user Interfaces =
  TODO                       |
--------------------------------------------------------------------------------
= Managing Services =
  TODO                       |
--------------------------------------------------------------------------------
= Troubleshooting Services =
  TODO                       |
--------------------------------------------------------------------------------
= Managing & Configuring Hardware =
  TODO                       |
--------------------------------------------------------------------------------
= TCP / IP & Networking =
  find ip address command    | ip addr
                             |
  address classes            | Class A - 255.0.0.0     - /8  - 16,777,214 Hosts
                             | Class B - 255.255.0.0   - /16 - 65,534 Hosts
                             | Class C - 255.255.255.0 - /24 - 254 Hosts
                             |
  Private class addresses    | Class A - 10.x.x.x    - /8
                             | Class B - 172.16.x.x  - 172.31.x.xx /16
                             | Class C - 192.168.x.x - /24
                             |
  TCP IP stack               |
                             |
      Application            | HTTP  |  FTP  |  SMTP  |  TFTP  |  SNMP
      Transport              |               TCP  |  UDP
      Internet               |                   IP
      Media Acess            |    802.3 Ethernet  | 802.11 Wireless
                             |
  Interesting tools          | nslookup
                             | ss | netstat
                             |
  Configuration tools        | ifconfig
                             | route
                             |
                             | ip addr
                             | ip route
                             |
                             | dhclient  - gets new addres
                             | dhclient -r 
                             |
                             | systemctl restart network (systemd)
                             | service network restart   (old init system)
                             |
  Common places to find      | /etc/sysconfig  (centOS, Redhad, Fedora)
  network configuration      |               /network-scripts/
  files                      |
                             | /etc/network (ubuntu)
                             | /etc/netplan
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
= Troubleshooting Network Connections =
  TODO                       |
--------------------------------------------------------------------------------
= Installing and Managing Software =
  TODO                       |
--------------------------------------------------------------------------------
= Installing Sofeware from Source Code =
  TODO                       |
--------------------------------------------------------------------------------
= Security Best Practices =
  TODO                       |
--------------------------------------------------------------------------------
= SELinux && AppArmor =
  TODO                       |
--------------------------------------------------------------------------------
= Network Firewall & Traffic Filtering =
  TODO                       |
--------------------------------------------------------------------------------
= Backup and Restore =
  TODO                       |
--------------------------------------------------------------------------------
= Bourne-again Shell & Scripting =
  TODO                       |
--------------------------------------------------------------------------------
= Scheduling Tasks =
  TODO                       |
--------------------------------------------------------------------------------
= Git Version Control =
  TODO                       |
--------------------------------------------------------------------------------
= Installing CentOS =
  TODO                       |
--------------------------------------------------------------------------------
= Installing Ubuntu =
  TODO                       |
--------------------------------------------------------------------------------
