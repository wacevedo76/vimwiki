--------------------------------------------------------------------------------
# Red Hat Certified System Administrator Certification Training notes
--------------------------------------------------------------------------------
## LBD RHCSA notes
--------------------------------------------------------------------------------
[[certs/rhcsa/Exam-objectives|The RHCSA Exam Objectives]]
--------------------------------------------------------------------------------
[[certs/rhcsa/exam-taking-notes|Notes on taking the Exam]]

## Chapter 1 - Local Installation
### Installation Logs
[[certs/rhcsa/installation-logs|Installation Logs]]
## Virtual console Screens (during installation)
[[certs/rhcsa/installation-virtual-console-screens|Virtual Console Screens]]

[[certs/rhcsa/review-questions|Review Questions]]
--------------------------------------------------------------------------------
## man sections
  1   Executable program or shell commands
  2   System calls (functions provided by the kernel)
  3   Library calls (functions within program libraries)
  4   Special files (usually found in /dev)
  5   File formats and conventions eg /etc/passwd
  6   Games
  7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
  8   System administration commands (usually only for root)
  9   Kernel routines [Non standard]

-------------------------------------------------------------------------------
## Chapter 5 - Connecting to RedHat Enterpirse Linux 8
  **Terms**                      |
  Console                    | A Console is the environment the user is looking
                             | at
                             |
  Terminal                   | A Terminal is an environment that is opened on
                             | the console and provides access to a text shell,
                             | which is the command-line environment that can be
                             | used to type commands
                             |
                             | You can have multiple terminals open on a
                             | console, but you cannot have multiple consoles
                             | open in one terminal
                             |
  Virtual Terminals          | To open these terminal windows, you can use the
                             | key sequences Alt-F1 through Alt-F6
                             |
                             | **F1**: Gives access to the GNOME Display Manager
                             | (GDM) graphical login. --> **/dev/tt1**
                             |
                             | **F2**: Provides access to the current graphical
                             | console  --> **/dev/tt2**
                             |
                             | **F3**: Gives access back to the current graphical
                             | session  --> **/dev/tt3**
                             |
                             | **F4-F6**: Gives access to nongraphical consoles
                             | **/dev/tt4 - /dev/tt6**
                             |
                             | A convenient alternative to using the Alt-
                             | Function key sequence is offered by the **chvt**
                             | command.
                             |
  Shutting down              | systemctl reboot or reboot
                             | systemctl halt or halt
                             | systemctl poweroff or poweroff
                             |
                             | If the above don't work
                             | echo b > /proc/sysrq-trigger
                             |
  SSH                        |
  Starting graphical apps    | There are two requirements:
  through sssh               | * An X server must be running on the client
                             |   computer. The X server is the software
                             |   component that creates the graphical
                             |   screens.
                             |
                             | * The remote host must be allowd to display
                             |   screens on the local computer
                             |
    Options                  | -v : Verbose; Shows the detail what is happening
                             |      while establishing the connection
                             |
                             | -Y : Enables support for graphical applications
                             |
  rsync                      | Options:
                             | -r : Synchronizes the entire directory tree
                             | -l : Also synchronizes symbolic links
                             | -p : Preserves symbolic links
                             | -n : Performs only a dry run, not actual
                             |      synchronizing anything
                             | -a : Users archive mode, thus ensuring that
                             |      entire subdirectory trees and all file
                             |      properties will be synchronized
                             | -A : Uses archive mode, and in addition
                             |      synchronizes ACLs
                             | -X : Synchronizes SELinux context as well
                             |
--------------------------------------------------------------------------------
## Chapter 6 - User and Group Management
  Get information on a user  | id <USERNAME>
                             |
  Methods to Run tasks with  | su - opens a subsheel as a different user, with
  elevated permissions       |      the advantage that commands are executed as
                             |      root only in the subshell
                             |
                             | sudo - Enables you to set up an environment where
                             |        specific tasks are executed with
                             |        administrative privileges
                             |
                             | PolicyKit - Enables you to set up graphical
                             |             utilities to run with administrative
                             |             privileges
                             |
  Elevating privileges for   | using *visudo*
  specific commands for a    | (username) ALL=/usr/bin/useradd,/usr/bin/passwd
  user                       |
                             |
  PolicyKit                  | Associated man pages:
                             | *pkexec*, *polkit*
                             |
  /etc/passwd                | Field summary
                             | * Username
                             | * Password
                             | * UID
                             | * GID
                             | * Comment Field
                             | * Directory (home directory)
                             | * Shell
                             |
  /etc/shadow                | Field Summary
                             | * Login name
                             | * Encrypted password
                             | * Days since Jan. 1, 1970, that the password was last changed
                             | * Days before password may be changed
                             | * Days after which password must be changed
                             | * Days after password expires that account is disabled
                             | * Days since Jan. 1, 1970, that account is disabled
                             | * A reserved field, which was once added "for future use"
                             |
  Create users               | Here are some ways to create users
                             | * vipw - used to edit /etc/password and /etc/shadow
                             | * useradd
                             |
    Example                  | useradd -m -u 1201 -G sales,ops linda
                             |
  Remove users               | * userdel (-r to remove a user and the complete user
                             |   environment)
                             |
  Managing User Properties   | For changing user properties, you can either
                             | work directly in the configuration files uise
                             | *vipw* or use can user *usermod*
                             |
  Configuration files for    | When you're working with tools such as useradd,
  user management defaults   | some default values are assumed. These default
                             | values are set in two configuration files:
                             | * /etc/login.defs
                             | * /etc/default/useradd
                             |
  defaults in                | In the file /etc/login.defs, different login related
  /etc/login.defs            | variables are set. This file ise used by different
                             | commands, and it relates to setting up the
                             | appropriate environment for new users. Here is a
                             | list of some of the most significant properties
                             |
                             | * MOTD_FILE: Defines the file that is used as
                             |   the "message of the day" file. In this file,
                             |   you can include messages to be displayed after
                             |   the user has successflly logged in to the sever.
                             |
                             | * ENV_PATH: Defines the $PATH variable,
                             | * PASS_MAX_DAYS, PASS_MIN_DAYS, PASS_WARN_AGE:
                             |   Define the default password expiration
                             |   properties when creating new users
                             | * UID_MIN: Indicates the first UID to use when
                             |   creating new users
                             |
  Managing Password          | passwd
  Properties                 |   Example: passwd -n 30 -w 3 -x 90 lind
                             |     sets the password to a minimal usage period
                             |     of 30 days and an expiry after 90 days, where
                             |     a warning is generated 3 days before expiry
                             |
                             | chage:
                             |   Example: chage -E 2025-12-31 bob
                             |     -E = expiration date
                             |     -I = interactive
                             |
  Creating a User Environment| Files used in creating a user environment
                             | * /etc/profile: Used for default settings for
                             |      all users when starting a login shell
                             | * /etc/bashrc: Used to define defaults for all
                             |      users when starting a subshell
                             | * ~/.profile: Specific settings for one user
                             |     applied when starting a login shell
                             | * ~/.bashrc: Specific settings for one user applied when starting a subshell
                             |
  Createing groups           | vigr
                             |
    /etc/group fields        | * Group name:
                             | * Group password
                             | * Group ID
                             | * Members
                             |
  Using groupadd to Create   | groupadd <name of new group>
  Groups                     |   - g : specify a group I
                             |
  Managing Group Properties  |
    Change the name or group | groupmod
    id                       |
                             |
    Add members to a group   | usermod -aG
                             |
    find out what groups a   | groupmems
    user is member of        |   example: groupmems -g sales -l
                             |
--------------------------------------------------------------------------------
## Chapter 7 - Permissions Management
  *Displaying ownership*       | ls -l
                             |
  list of all files on system| find / -user {username}
  of a given user or group   | find / -group {groupname}
                             |
  *Changing User Ownership*    | chown {who} {what}
                             | -R    <-- recursively
                             |
  *Changing Group Ownership*   | chown .{group} {where}    <--- dot in front of group name
                             | chown :{group} {where}    <--- colon in front of group name - Produces same as above
                             |
    can also change group    | chgrp -r {group} {location}    <--- recursively
    ownership                |
                             |
  *Show current effective*     | groups {username}
  *group*                      |
                             |
  *Change the effective*       | newgrp {name of group}
  *group for the current*      |
  *session*                    |
                             |
  Understanding read/write   | *Permission*     *Applied to Files*            *Applied to Directories*
  permissions                | Read           Open a file                 List contents of directory
                             | Write          Change contents of a file   Create and delete files
                             | Execute        Run a program file          Change to the directory
                             |
  *Understanding Advanced*     |
  *Permissions*                |
                             |
    Set User ID (sUID)       | On executable files - runs a file with the same
                             | permissions as the file owner
                             |
                             | sets an "s" were "x" would normally be --> -rw*s*r -xr-x root root 33424  Feb 18 2022 /usr/bin/passwd
                             |
    Set Group ID (SGID)      | On executable file - it gives the runner of the
                             | file the group permissions of the file
                             |
                             | On directorys - it sets the default group ownership
                             | of all files created within the directory
                             |
                             | sets an "s" were "x" would normally be --> drwxr-*s*r-x. 2  root  account 4096 Apr 30 21:28 account
                             |
    Sticky bit               | Prevents users from deleting files that they didn't create
                             | When using ls -l, you can see sticky bit as a *t*
                             | at the position where you normally see the execute
                             | permission for others
                             |
                             |   drwxr-sr-t. 2 root account 4096 Apr 30 21:28 account/
                             |
  *Applying Advanced*          | * For SUID, use *chmod u+s*
  *Permissions*                | * For SGID, use *chmod g+s*
                             | * For sticky bit, use *chmod +t* followe by the
                             |   name of the file or the directory that you
                             |   want to set a the permissions on.
                             |
                             | Special Permissions summary
                             |
                             | *Permissions*    *Numeric Value*   *Relative Value*    *On Files*                    *On Directories*
                             | SUID           4               u+s               User executes file with     no meaning
                             |                                                  permissions of file owner
                             | SGID           2               g+s               User executes file with     Files created in directory get
                             |                                                  permissions of group owner  the same group owner
                             | Sticky bit     1               +t                No Meaning                  Prevents users from deleting
                             |                                                                              files from other users
  *Managine ACLs*              |
    Backing up ACLs          | getfacl -R /directory > file.acls
    Restoring ACLS           | setfacl --restor=file.acl
                             |
    Set ACLs                 | setfacl -m(odify) g:<groupname>:<permissions_to_apply> /path/to/file
                             | setfacl -m u:<username>:<permissions_to_apply> /path/to/file
                             | setfacl -R(ecursively) -m u:<username>:- /path/to/file (removes all permisions for username to all files in path)
                             |
    Set Default ACL          |
                             |
    Set ACL so that all      | setfacl -m *d*:g:sales:rx /data (-d = default)
    permissions are set on   |     (all new files created in this directory will
    all new files            |     inherit permissions, but do not change pre-
                             |     existing files)
                             |
                             |     setfacl -R -m    --> modify ACLs for current files
                             |     setfacl -m d:    --> take care of all new items
                             |
    disable permissions for  | setfacl -m d:o::- /data
    'others'                 |     -m (modify) d: (default) o: (others) ::
                             |
                             |
  *Setting Default*            | The maximu settings for:
  **Permissions with umask**     | files = 666
                             | directories = 777
                             |
  umask values and their     | Value    Applied to Files    Applied to Directories
  results                    | 0        Read and write      Everything
                             | 1        Read and write      Read and Write
                             | 2        Read                Read and execute
                             | 3        Read                Read
                             | 4        Write               Write and execute
                             | 5        Write               Write
                             | 6        Nothing             Execute
                             | 7        Nothhing            Nothing
                             |
  change umask for all users | All users: /etc/profile
  and individual users       |            /etc/profile.d/umask.sh  <-- correct approach
                             |
                             | Individual users: ~/.profile        <-- can be set in /etc/skel/.bashrc
                             |
  **Working with User**-         | chatter (+|- attribute) (file)  <change attribute>
  **Extended Attributes**        | lsattr (file)                  <list attributes>
                             |
                             | Brief description of attributes
                             | **A** - This attribute ensures that the file
                             |     access time of the file is *not* modified
                             | **a** - allows a file to be added, but not to be
                             |     removed
                             | **c** - if volume level compression is supported,
                             |     ensurse that file is compressed the first
                             |     time the compression engine become active
                             | **D** - changes to files ar ewritten to disk
                             |     immediately
                             | **d** - makes sure files will not be backed up
                             | **I** - enables indexing for the directory where it is enabled
                             | **i** - makes file immutable
                             | **j** - On Ext3 file systems, the file is first
                             |     written to the journal and then to harddrive
                             | **s** - This attribute overwrites the blocks where the
                             |     file was store with 0s after the file has been
                             |     deleted
                             | **u** - Saves undeleted information
                             |
--------------------------------------------------------------------------------
## Chapter 8 - Configuring Networking
  Terms                      |
    CIDR                     | Classless interdomain Routing Notation: Indicates
                             |   the number of bits in in the subnet mask
                             |
  Network Fundamentals       | *IPv4 Addresses* - These are based on 32-bit
                             |   addresses and have four octets, separated by
                             |   dots.
                             |
                             | *IPv6 Addresses* - These are based on 128-bit
                             |   addresses and are written in eight groups of
                             |   hexadeimal numbers that are 16-bits each and
                             |   separated by colons.
                             |
  Private network Addresses  | * 10.0.0.0/8 (a single Class A Network)
                             | * 172.16.0.0/12 (16 Class B networks)
                             | * 192.168.0.0/16 (256 Class C networks)
                             |
  Variable length subnet     | IP Address (example)
  masks                      | 212.209l.113.33 = 11010100.11010001.00001010.00100001
                             |
                             | Subnet mask
                             | /27 = 11111111.11111111.11111111.11100000
                             |
  Binary-Decimal Conversion  | *Binary Value      Decimal Value*
  Overview                   | 00000000         0
                             | 00100000         32
                             | 01000000         64
                             | 01100000         96
                             | 10000000         128
                             | 10100000         160
                             | 11000000         192
                             | 11100000         224
                             |
  MAC Addresses              | MAC addresses consists of two parts. The first 6
                             | bytes is the vendor ID, and the second 6 bytes is
                             | the unique node ID
                             |
  *Managing Network*           | In RHEL 8, the default names for network cards are
  **addresses and Interfaces**   | based on firmware, device topology, and device types.
                             | This leads  to network card names that always consist
                             | of the following parts:
                             | * Ethernet interfaces begin with *en*, WLAN interf-
                             |   aces begin with *wl*, and WWAN interfaces begin with
                             |   *ww*
                             | * The next part of the name represents the type
                             |   of adapter. An *o* is used for onboard, *s* is for a
                             |   hotplug slot, and *p* is for a PCI location.
                             |   Administrators can also use x to create a device
                             |   name that is based on the MAC address of the
                             |   network card
                             | * The follows a number, which is used to
                             |   represent an index, ID, or port
                             | * IF the fixed name cannot be determined,
                             |   traditional names such as eth0 are used.
                             |
                             | Also, network cards can be named based on the
                             | BIOS device name as well. In this naming scheme,
                             | names such as em1 (embedded network card 1) or
                             | p4p1 (which is PCI slot 4, port 1) can be used.
                             | To use this kind of naming, the biosdevname
                             | package must be used
                             |
  *Validating Network*         |
  *Configuration*              |
                             |
    configure/monitory       | ip addr
    network Addresses        |
                             |
    configure/monitory       | ip route
    routing information      |
                             |
    configure/monitory       | ip link
    network link staten      |
                             |
    Viewing Netowkr State    | ip a(ddress) s(how)
                             | -s  (statistics)
                             |
    View only link state     | ip -s link show
                             |
    Add ip address           | ip a(ddr) a(add) <new_ip_address> dev <interface_name>
                             |   example: ip a add 10.0.0.10/24 dev ens18
                             |
                             |
    Temporarily bring up     | ip link set dev <device_name> up
    interface                |   example: ip link set dev ens33 up
                             |
    view listening ports     | ss -lt  (t = tcp)
                             | ss -tul (t = tcp, u = udp)
                             |
  *Configuring Network*        |
  *configuration with nmtui*   |
  *and nmcli*                  |
    View NetworkManager      | systemctl status NetworkManager
    status                   |
                             |
    Location of Network card | /etc/sysconfig/network-scripts/
    configuration scripts    |     (the scripts start with *ifcfg* followed by
                             |     network card name)
                             |
    Difference between       | * A device is a network interface card
    device and connection    | * A connection is the configuration that is used on a device.
                             |
    Tools used to manage     | * nmcli  ---> command line tool
    network devices and      | * nmtui  ---> same as above, but with text user interface
    connections              |
                             |
    Check permissions to     | nmcli gen permissions
    change network configu-  |
                             |
    Show all connections     | nmcli con show
                             | nmcli con show <dev_name>  <--- shows more information
                             |
    Man page for connection  | man 5 nm-settings
    settings                 |
                             |
    List all devices         | nmcli dev show
                             |
    show settings for        | nmcli dev show <device_name>
    specific device          |
                             |
    Create a new network     | nmcli con add <con-name> dhcp type ethernet ifname <iface name> ipv4.method auto
    connection               | nmcli con add con-name static ifname ens33 autoconnect no type ethernet ip4 10.0.0.10/s4 gw4 10.0.0.1 ipv4.method manual
                             |
    nmcli-examples man page  | man nmcli-examples
                             |
  *Working with hostnames*     |
                             |
   Different ways to change  | * Use *nmtui* and select the option *Change Hostname*
   the hostname:             | * Use *hostnamectl set-hostname*
                             | * Edit the contents of the configuration file /etc/hostname
                             |     example: hostnamectl set-hostnamem myhost.example.com
                             |
  *DNS Name Resolution*        |
    Add dns server           | nmcli con mod <connection-id> [+]ipv4.dns <ip-of-dns>
                             |
    enable/disable auto dns  | nmcli con mod <con-name> ipv4.ignore-auto-dns (yes|no)
                             |
    verify hostname          | getent hosts <servername>
    resolution               |
                             |
--------------------------------------------------------------------------------
## Chapter 9 - Managing Software
  *Managing Subscriptions*     |
    Register a system        | # subscription-manager register
    List available subscrip. | # subscription-manager list --available
    Automatically attach a   | # subscription-manager attach --auto
      subscription           |
    Get subscription overview| # subscription-manager --consumed
    Unregister subscription  | # subscription-manager unregister
                             |
  Files important to         | /etc/pki/product - Certificates indicating which
  subscriptions              |   Red Hat produces are installed
                             | /etc/pki/consumer - stores certificates identfying
                             |   the Red Hat account to which the system is registered
                             | /etc/pki/entitlement - contains information about
                             |   the subscriptions that are attached to the system
                             |
  *Specifying Which*           | To tell your server which repo to use, you need to
  *Repository to use*          | create a file with the name that ends in *.repo* in
                             | the directory */etc/yum.repos.d*. In that file you
                             | need:
                             |   * [lable] - The .repo file can contain different
                             |     repositories, each section starting with the
                             |     a label that identifies the specific repository.
                             |
                             |   * name= - Use this to specify the name of the
                             |     repository you and to use.
                             |
                             |   * mirrorlist= - Referes to a URL where information
                             |       about mirror servers for this server can
                             |       be obtained. Typically used for big online repos
                             |
                             |   * baseurl= This option contains the URL that
                             |     points to the specific repository location
                             |
                             |   * gpgcheck= - Set to 1 if a GNU Privacy Guard (GPG)
                             |       integrity check needs to be performed on
                             |       the packages. If set to 1, a GPG key is required
                             |
                             |   * gpgkey= - Specifies the location of the GPG
                             |       key that is used to check package integrity
                             |
                             | When you use a URL, two components are included.
                             | First, the URL identifies the protocol to be used
                             | and is in the format, protocol://, such as:
                             |   https://. ftp://, or file://.
                             | Following the URL is the exact location on that
                             | URL.
                             |
  *Creating your own Repo*     | For this, you will need to have access to th RHEL
                             | or CentOS installation disk or Iso file
                             |
                             | * Insert the installation disk in you vm and make
                             |   sure it is attached and available
                             |
                             | * Type mkdir /repo so that you have a mount point
                             |   where you can mount the ISO file
                             |
                             | * Add the following line to the end of the /etc/fstab
                             |   file: */dev/sr0 /repo iso9660 defaults 0 0*
                             |
                             | * Type *mount -a*, followed by *mount | grep sr0*. You
                             |   should now see that the optical device is
                             |   mounted on the directory /repo. At this point,
                             |   the directory /repo can be used as a repository
                             |
                             | * At this point, two repositories are aavailable
                             |   through the /repo directory. The BaseOS repository
                             |   provides access to application streams (these
                             |   repositories provides access to the base packages,
                             |   and the Application Stream (AppStream) repository
                             |   provides access to application streams. To make
                             |   them accessible, you need to add two files to
                             |   /etc/yum.repos.d direcotry
                             |
                             |   *BaseOs.repo*
                             |
                             |   [BaseOS]
                             |   name=BaseOS
                             |   baseurl=file:///repo/BaseOS
                             |   gpgcheck=0
                             |
                             |   AppStream.repo
                             |
                             |   [Appstream]
                             |   name=AppStream
                             |   baseurl=file:///repo/AppStream
                             |
  *Using yum*                  |
    Common yum tasks         |
                             |
      search                 | * Search for the exact name of a package.
      [what]provides #/name  | * Perform a deep search in the package to
                             |   look fopecific files within the package.  (runs in *BASH*)
      info                   | * Provide more information about the package
      install                | * Install the package
      remove                 | * Remove the package
      list [all | installed] | * List all or installed packages
      group list             | * List package groups
      group install          | * install all packages from a group
      update                 | * Update packages specified
      clean all              | * Remove all stored metadata
                             |
  *Working with yum Package*   |
  *Groups*                     |
    List default groups      | yum group list
    List all groups          | yum group list hidden
                             |
    View yum history         | yum history
    Undo yum action (history)| yum history undo <num_of_action>
                             |
  *Managing Package*           |
                             |
  *Understanding Modules*      | In the Application Stream repository, content
                             | with varying lifecycels is provided. This content
                             | This content is provided as the traditional RPM
                             | packages, but also as modules.
                             |
    Modules                  | A module describes as set of RPM packages that
                             | belong together. Typically, modules are organized
                             | aroound a specific version of an application, and
                             | in a module you'll find module packages, together
                             | with all of thedependencies for that specific
                             | version
                             |
    Profiles                 | Modules an also have one or more profiles. A
                             | profiles is a list of packages that are installed
                             | together for a particular use case
                             |
  *Module Streams*             |
                             |
    Yum Module Terminology   | *Item*         *Explanation*
                             | RPM          The default package format. Contains files,
                             |              as well as metadata that descripts how to
                             |              install the files. Optionally may contain
                             |              pre- and post-installation scripts as well
                             |
                             | Module       A delivery mechanism to install RPM packages
                             |              In a module different versions and profiles
                             |              can be provided.
                             |
                             | Application  A specific version of the Module
                             | stream
                             |
                             | Profile      A collectio of packages that are
                             |              installed together for a particular
                             |              use case
                             |
  *Managing Modules*           |
                             |
    List Modules             | yum module list
                             |
    List specific streams    | yum module list <modulename>
      for a module           |
                             |
    Get information specific | yum module info <modulename>
      module profile stream  |
                             |
    Install module           | yum module install <modulename[:version]>
                             |
                             |
    Enable module stream     | yum module enable <modulename[:version]>
                             |
    Sync module and          | yum distro-sync
    dependencies             |
                             |
                             |
  *Querying the RPM DB*        |
    Show a list of all       | rpm -qa <package_name>
    installed packages       |
                             |
    Show a description of    | rpm -qi <package_name>
    a package                |
                             |
    Show a list of all files | rpm -ql <package_name>
    in a package             |
                             |
    Show all documentation   | rpm -qd <package_name>
    for package              |
                             |
    Show all configuration   | rpm -qc <package_name>
    files for a package      |
                             |
    Show the package to which| rpm -qf <file_name>
    a specific file belongs  |
                             |
  *Managing Software Packages* |
  *with rpm*                   |
                             |
    Install rpm package      | rpm -Uvh <package_name>
    (mostly replaced by yum) |   (When installing packages with rpm, the yum
                             |    database will not be updated)
                             |
    Understanding RPM        | When you'reworking with RPM packagesdirectly, it
    filenames                | makessense to understand how the RPM filename is
                             | composed. A typical RPM filenme looks like:
                             |   autofs-5.0.7-40.el7.x86_64.rpm
                             | This name consists of several parts:
                             |   * autofs: The name of the actual package
                             |   * 5.0.7: The version of the package. This
                             |     normally corresponds to the name of the
                             |     pacakge as it was release by its creator
                             |   * -40: The subersion of the package
                             |   * el7: The Red Hat version this package was
                             |     created for
                             |   * x86_65: The platform this package was created
                             |     for
                             |
  *Querying RPM Package files* |
    Common RPM Query commands|
                             |
      rpm -qf                | Uses a filename as its argument to find the
                             | specific RPM Package a file belongs to
      rpm -ql                | Use the RPM database to provide a list of files
                             | in the RPM package
                             |
      rpm -qi                | Usese the RPM database to provide package
                             | information (eqivalent to yum info)
                             |
      rpm -qd                | Uses the RPM database to show all documentation
                             | that is available in the package
                             |
      rpm -qc                | Uses the RPM database to show all configuration
                             | files that are available in the package
                             |
      rpm -q --scripts       | Usese the RPM database to show scripts that are
                             | used in the package. This is particularly useful
                             | if combined with the *-p* option
                             |
      rpm -qp <pkg>          | The *-p* optin is used with all the previously
                             | listed opting in the query individual RPM package
                             | files instead of the RPM package database. Using
                             | this option before installation helps you to find
                             | out what is actually in the package before it is
                             | installed
                             |
      rpm -qR                | Shows dependencies for a specific package
                             |
      rpm -V                 | Shows which parts of a specific package have been
                             | changed since installation
                             |
      rpm -Va                | Verifies all installed packages and shows which
                             | parts of the package have been changed since
                             | installation. This is any easy and convenient way
                             | to do a package integrity check.
                             |
      rpm -qa                | Lists all packages that are installed on this server
                             |
  *Using repoquery*            | To query packages from the repositories before
                             | they have been installed (within the *yum-utils* package)
                             |
                             | The *repoquery* command is similar to the rpm -q
                             | command and uses many similar options, though the
                             | *--scripts* opting is not available
                             |
                             | To thoroughly analyze what an RPM package is
                             | doing when it is installed, you can download it
                             | to your machine, which allows you to use the
                             | *rpm -qp --scripts* command on the package
                             |
    Download a package from  | *yumdownloader* (yum-utils)
    the repo to local machine|
                             |
--------------------------------------------------------------------------------
## Chapter 10 - Managing Processes
  *The three major types of*   | * Shell jobs - commands started from the
  *processes*                  |   command line. They are associated with
                             |   the shell that was currentwhen the process
                             |   wasstarted. Shell jobs are also referred to
                             |   as *interactive processes*.
                             |
                             | * Daemons - Processes that provide services. They
                             |   normally are started when a computer isbooted
                             |   and often (but certainly not all cases) run
                             |   with root privileges.
                             |
                             | * Kernel threads - Part of the Linux kernel. You
                             |   cannot manage them using common tools, but for
                             |   monitoring of performance on a system. it's
                             |   important to keep an eye on them.
                             |
  *Threads*                    | When a process is started, it can use multiple
                             | threads. A *thread* is a task started by a
                             | process and that a dedicated CPU can service. The
                             | Linux shell does not offertools to manage
                             | individual threads. Thread management should be
                             | taken care of from within the command.
                             |
  *Managing Shell Jobs*        | Job management overview
                             | *Command*    *Use*
                             | &          Starts the command immediately in the
                             |            background
                             | Ctrl-Z     Stops the job temporarily os that it
                             |            can be managed. For instance, it can
                             |            be moved to the background
                             | Ctrl-D     Sends the End Of File (EOF) character
                             |            to the current job to indicate that it
                             |            should stop waiting for further input.
                             | Ctrl-C     Can be used to cancel the current
                             |            interactive job.
                             | bg         Continues the job that has been frozen
                             |            using Ctrl-Z in the background
                             | fg         Brings back to the foreground the last
                             |            job that was moved to background
                             |            execution.
                             |
  *Understanding Processes*    | There are two types of background processes
  *and Threads*                | * Kernel Threads - They are a part of the Linux
                             |   kernel, and each of them is started with its
                             |   own process identification number (PID). They
                             |   are easily recognizable because they have a
                             |   name that is between square brackets (ps)
                             |
                             |   Kernel threads canot be managed, their priority
                             |   can not be adjusted, neither is it possible to
                             |   kill them, except by taking down the entire machine
                             |
                             | * Daemon Processes
                             |
  *Using ps to get process*    |
  *Information*                |
                             |
    ps                       | Without any arguments, it shows only those
                             | processes that have been started by the current
                             | user.
                             |
    ps aux                   | Displays a short sumary of active processes
                             |
    ps -ef                   | Displayes the exact command that was used to
                             | start the process
                             |
    ps fax                   | Shows hierarchical relationships between parent
                             | and child processes
                             |
    pgrep <command>          | shortcut to filter process list
                             |
  *Adjusting Process Priority* | All Regular processes are equal and are started
  *with nice*                  | with the same priority, whic is the priority
                             | number 20
                             |
   nice                      | Start a process with an adjusted priority
                             |
   renice                    | Change the priority for a currently active process.
                             |
   r (from within *top*)       | Use the *r* command from the *top* utility to
                             | change the priority of a currently running
                             | process
                             |
   Using nice and renice     | When using *nice* or *renice* to adjust process
                             | priority, you can select from values ranging
                             | from -20 to 19. The default niceness of a process
                             | is set to 0 (which results in the priority value
                             | of 20). By applying a negative niceness, you
                             | increase the priority. Use a positive niceness to
                             | decrease the priority.
                             |
   Examples                  | nice -n 5 <command>
                             | renice -n 10 -p <PId>
                             |
                             | Regular users can only decrease the priority of a
                             | running process. You must be root to give
                             | processes increased priority
                             |
  *Sending Signals to*         | View man 7 signals for a complete overview of
  *processs with kill, killall*| all available signals. Three of these signals
  *and pkill*                  | work for all processes:
                             | * The signal SIGTERM (15) is used to ask a process to stop. (kill -15)
                             | * The signal SIGKILL (9) is used to force a process to stop. (kill -9)
                             | * The SIGHP (1) signal is used to hang up a (kill)
                             |   process. The effect is that the process will
                             |   reread its configuration files, which makse
                             |   this a suseful signal to use after making
                             |   modifications to a process oncifuration file
                             |
    Show a list of available | kill -l
    signals that kill can use|
                             |
    pkill                    | Similar to kill but takes a name rather than a PID
                             |
    killall                  | Use if multiple processes using the same name
                             | need to be killed simultaneously.
                             |
    Find processes nice level| ps ax -o pid,ni,cmd
                             |
  *Using top to manage*        | Linux Process States Overview
  *processes*                  | *State*            *Meaning*
                             | Running (R)      The process is currently active
                             |                  and using CPU time, or in the
                             |                  queue of runnable processes
                             |                  waiting to get services.
                             |
                             | Sleeping (S)     The process is waiting for an
                             |                  even to complete
                             |
                             | Uninteruptible   The process is in a sleep state
                             | sleep (D)        that cannot be stopped. This
                             |                  usually happens while a process is waiting for I/O
                             |
                             | Stopped (T)      The process has been stopped,
                             |                  which typically has happened to
                             |                  an interactive shell process,
                             |                  using the Ctrl-Z key sequence.
                             |
                             | Zombie (Z)       The process has been stopped but
                             |                  could not be removed by its
                             |                  parent, which has put it in an
                             |                  unmanageable state.
                             |
    Find uptime and load     | uptime
    average                  |
                             |
    Find out how many cpus   | lscpu
    in system (for load avg) |
                             |
  *Using tuned to optimize*    | Tuned offers a daemon that monitors system
  *performance*                | activity and rovides some profiles. In the
                             | profiles, an administrator can automatically
                             | tune a system for best possible latency,
                             | throughput, or power consumption
                             |
    Tuned Profile Overview   | *Profile*          *Use*
                             | balanced         The best compromise between
                             |                  power usage and performance
                             |
                             | desktop          Based on the blanced profile,
                             |                  but tuned for better response to
                             |                  interactive applications
                             |
                             | latency-         Tuned for maximum throughput
                             | performance
                             |
                             | nework-latency   Based on latency-performance,
                             |                  but with additional options to
                             |                  reduce network latency
                             |
                             | network-         Based on throughput-performance,
                             |                  optimizes older CPUs for
                             |                  streaming content
                             |
                             | powersave        Tunesfor maximum power saving
                             |
                             | throughput-      Tunes for maximum throughput
                             | performance
                             |
                             | virtual-guest    Optimizes Linux for running as a
                             |                  virtual machine
                             |
                             | virtual-host     Optimized Linux for use asa KVM
                             |                  host
                             |
    Start the tuned daemon   | systemctl enable --now tuned
                             |
    Find out which profile   | tuned-adm active
    is currenty selected     |
                             |
    List available profiles  | tuned-adm list
                             |
    Selet another profil     | tuned-adm profile <profile_name>
                             |
    Have tuned recommend a   | tuned-adm recommend
    profile                  |
                             |
--------------------------------------------------------------------------------
## Chapter 11 - Working with Systemd
[[linuxGeneralConcepts/systemd|Additional Systemd Notes]]

  **Types of systemd units**     | automount
                             | device
                             | mount
                             | path
                             | scope
                             | slice
                             | socket
                             | swap
                             | target
                             | timer
                             | service
                             |
  **Where unit files can be**    | * /usr/lib/systemd/system - Contains default unit
  **found**                      |     files tha thave been installed from RPM
                             |     packages. You should never edit these files
                             |     directly
                             |
                             | * /etc/systemd/system - Contains custom unt
                             |     files. It may also contain include files that
                             |     have been written by an administrator or
                             |     generated by the systemctl edit command.
                             |
                             | * /run/systemd/system - contains unit files that
                             |     have automatically been generated
                             |
  **Systemd unit files**         | 1. /run/systemd/system
  **priority**                   | 2. /etc/systemd/system
                             | 3. /usr/lib/systemd/system
                             |
  **Understanding Systemd**      | Arguably, the most important unit type is the
  **Service Units**              | service unit. It is used to start processes.
                             | You can start any type of process by using a
                             | service unit, including daemon process and
                             | commands.
                             |
                             | Example: vsftpd.service
                             |
                             |   [Unit]
                             |   Description=Vsftpd ftp daemon
                             |   After=network.target
                             |
                             |   [Service]
                             |   Type=forking
                             |   ExecStart=/usr/sbin/vsftpd /etc/vaftpd/vsftpd.conf
                             |
                             |   [Install]
                             |   WantedBy=multi-user.target
                             |
                             | Any Systemd *service* unit file consists of the
                             | following three sections (other types of unit
                             | files have different sections).
                             |
                             | * [**Unit**] - Describes the unit and defines
                             |   dependencies. This section also contains the
                             |   important *After* statement and optionally
                             |   the *Before* statement. These statemens define
                             |   dependencies between different units, and they
                             |   relate to the perspective of this unit. The
                             |   *Before* statement indicates that this unit
                             |   should be started before the unit that is
                             |   specified. The *After* Statement indicates that
                             |   this unit should be started after the unit that
                             |   is specified.
                             |
                             | * [**Service**] - Describes how to start and stop
                             |   the service and request status installation.
                             |   Normally, you can expect and **ExecStart** line,
                             |   which indicates how to start the unit, or an
                             |   **ExecStop** line, which indicates how to stop
                             |   the unit. Note the **Type** option, which is used
                             |   to specify how the process should start. The
                             |   **forking** type is commonly used by daemon
                             |   processes, but you can also use other types,
                             |   such as **oneshot**, which will start any command
                             |   from a Systemd unit. See **man 5 systemd.service**
                             |   for more details
                             |
                             | * [**Install**] - Indicates in which target this
                             |   unit has to be started.
                             |
  **Understanding Systemd**      | A mount unit specifies how a file system can be
  **Mount Units**                | mounted on a specific directory.
                             |
                             | Exampe: A Mount Unit Files
                             |
                             |     tmp.mount unit file
                             |
                             |     [Unit]
                             |     Description=Temporary Directory (/tmp)
                             |     Documentation=man:hier(7)
                             |     Documentation=https://www.freedesktop.org/wiki/software/systemd/APIFileSystems
                             |     ConditionPathIsSymbolicLink=!/tmp
                             |     DefaultDependencies=no
                             |     Conflicts=umount.target
                             |     Before=local-fs.target umount.target
                             |     After=swap.target
                             |
                             |     [Mount]
                             |     What=tmpfs
                             |     Where=/tmp
                             |     Type=tmpfs
                             |
                             | This shows some interesting Additional
                             | configureation options in its sections:
                             |
                             | [**Unit**] The **Conflicts** statement is used o
                             | list units that cannot be used together with this
                             | unit. Use this statement for mutually exclusinve
                             | units
                             |
                             | [**Mount**] This section defines exactly where the
                             | mount has to be performed. Here you see the
                             | arguments that are typically used in any
                             | **mount** command.
                             |
  **Understanding Systemd**      | A socket creates a method for applications to
  **Socket Units**               | communicate with one another. A socket may be
                             | defined as a file but also as a port on which
                             | Systemd will be listening for incoming
                             | connections. That way, a service doesn't have to
                             | run continuously but instead will start only if a
                             | connection is comming in on the socket that
                             | is specified. Every scoket needs a corresponding
                             | service file.
                             |
                             | Example: cockpit.socket
                             |
                             |   [Unit]
                             |   Description=Cockpit Web Service Socket
                             |   Documentation=man:cockpit-ws(8)
                             |   Wants=cockpit-motd.service
                             |
                             |   [Socket]
                             |   ListenStream=9090
                             |   ExecStartPost=-/usr/share/cockpit/motd/update-motd '' localhost
                             |   ExecStartPost=-/bin/ln -snf active.motd /run/cockpit/motd
                             |   ExecStopPost=-/bin/ln -snf /usr/share/cockpit/motd/inactive.motd /run/cockpit/motd
                             |
                             |   [Install]
                             |   WantedBy=sockets.target
                             |
                             | The important option from above is
                             | **ListenStream**. This option defines the TCP
                             | port that Systemd should be listening to for
                             | incoming connections. Sockets can also be created
                             | for UDP ports, in which case you would use
                             | **ListenDatagram** instead of **ListenStream**.
                             |
  **Understanding Systemd**      | Targets can have dependencies on other
  **Target Units**               | targets. These dependencies are defined in the
                             | target unit. An example of such a dependency
                             | relation is the basic.target. This target defines
                             | all the units that should alwasy be started. You
                             | can use the **systemctl list-dependencies**
                             | command for an over view of any existing
                             | dependencies.
                             |
                             | Example: **multi-user.target**
                             |
                             |     [Unit]
                             |     Description=Multi-User System
                             |     Documentation=man:systemd.special(7)
                             |     Requires=basic.target
                             |     Conflics=rescue.service rescue.target
                             |     After=basic.target rescue.service rescue.target
                             |     AllowIsolate=yes
                             |
                             |     [Install]
                             |     Alias=default.target
                             |
  **Managing Units Through**     | **Systemd Status Overview**
  **Systemd**                    | **Status**             **Description**
                             | Loaded             The unit file has been processed and the unit is active
                             | Active(running)    The unit is running with one or more active processes
                             | Active(exited)     The unit has successfully completed a one-time run
                             | Active(waiting)    The unit is running and waiting for an event
                             | Inactive(dead)     The unit is not running
                             | Enabled            The unit will be started at boot time
                             | Disabled           The unit will not be started at boot time
                             | Static             The unit connot be enabled but may be started by another unit automatically
                             |
    Display current unit     | systemct **cat** <full_unit_filename>
    configuration            |
                             |
  **systemctl Unit Overview**    | **Command**                            **Description*
  **commands**                   | systemctl --type=service           Shows only service units
                             |
                             | Systemctl list-units --            Shows all active services units (same results as the
                             | type=servie                        previous command)
                             |
                             | systemctl list-units --            Shows inactive service units as well as acive service units
                             | type=service --all
                             |
                             | systemctl --failed --              Shows all services that have failed
                             | type=service
                             |
                             | systemctl status -l your.service   Shows detailed status information about service
                             |
  **Managing Dependencies**      | In general, there are two ways to manage Systemd dependencies:
                             | * Unit types such as socket and path are directly
                             |   related to a service unit. Accessing either of
                             |   these unit types will automatically trigger the
                             |   service type
                             |
                             | * Dependencies can be defined within the unit,
                             |   using keywords like **Requires**, **Requisite**,
                             |   **After**, and **Before**
                             |
    Request a list of        | systemctl list-dependencieskj
    Dependencies             |     -- reverse   --> find out which units are dependents of this unit
                             |
                             | To ensure accurate dependency management, you can
                             | use differet keywords in the [Unit] section of a unit:
                             |
                             | **Requires**: If this unit loads, units listed
                             | here will load also. If one of the other units is
                             | deactivated, this unit will also be deactivated
                             |
                             | **Requisite**: If the unit listed here is not
                             | already loaded, this unit will fail
                             |
                             | **Wants**: This unit wants to load the units that
                             | are listed here, but it will not fail if any of
                             | the listed units fail
                             |
                             | **Before**: This unit wil start before the unit specified with **Before**
                             |
                             | **After**: This unit will start after the unit specified with **After**
                             |
    Show which options are   | systemctl show <unit_name>
    Available for a specific |
    unit                     |
                             |
    Recommended whay to apply| systemctl edit <unit_name>
    options to a unit file   |
                             |
--------------------------------------------------------------------------------
## Chapter 12 - Scheduling Tasks
  **Understanding cron Timing**  | cron Time and Date Fields
                             | **Field**          **Values**
                             | minute         0-59
                             | hour           0-23
                             | day of month   1-31
                             | month          1-12 (or nams tha tare better avoided)
                             |
                             | In any of these fields, you can use an * as a
                             | wildcard to refere to any value. Ranges of
                             | numbers are allowed, as are lists and patterns.
                             | Some examples are:
                             |
                             |   - * 11 * * *       --> Every minute between 11:00 11:59
                             |   - 0 11 * * 1-5     --> Every day at 11 a.m. on weekdays only
                             |   - 0 7-8 * * 1-5    --> Every hour at the top of the hour between 7 am and 6 pm. on weekdays
                             |   - 0 `*/2` 2 12 5     --> Every two hours on the hour on December 2 and every Friday in December
                             |
                             | Refer to **man 5 crontab** to show all possible constructions
                             |
                             |  Example of job definition:
                             |  .---------------- minute (0 - 59)
                             |  |  .------------- hour (0 - 23)
                             |  |  |  .---------- day of month (1 - 31)
                             |  |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
                             |  |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
                             |  |  |  |  |  |
                             |  *  *  *  *  * user-name  command to be executed
                             |
  Which files to modify      | Instead of modifying /etc/crontab, different
                             | configuration files are used:
                             |   * cron files in /etc/cron.d
                             |   * Scripts in /etc/cron.hourly,
                             |       cron.daily, cron.weekly, and cron.monthly
                             |   * User-specific files that are created with **crontab -e**
                             |
  Start a user specific cron | * crontab -e (as specific user)
  job                        | * crontab -e -u <username> (as root)
                             |
  List jobs for specific     | * crontab -l
  User                       |
                             |
                             | If you want to add cron jobs that are not bound
                             | to a specific user account (and which for that
                             | reasn by default will be executed as root if not
                             | specifie otherwise), you add these to the
                             | **/etc/cron.d** directory
                             |
                             | The last way to schedule cron jobs is through the following directories:
                             |   * /etc/cron.hourly
                             |   * /etc/cron.daily
                             |   * /etc/cron.weekly
                             |   * /etc/crony.monthly
                             |
                             | In these directories, you typically find
                             | scripts (not files the meet the crontab syntax
                             | requirements)
                             |
  Limit users ability to     | /etc/cron.allow and /etc/cron.deny (both files
  create cron jobs           | should not exist at the same time)
                             |
  **Configuring at to Schedule** | To run a job through the **atd** service, you
  **Future Tasks**               | would use the **at** command, followed by the
                             | time the job needs to be executed. This can at a
                             | specific time, as in **at 14:00**, but it can
                             | also be a time indication like **at teatime** or
                             | **at noon**. After you type this, the at shell
                             | opens. From this shell, you can type several
                             | commands that will be executed at the specific
                             | time that is mentioned. Press Ctrl-D to quit the
                             | **at** shell.
                             |
  Get overview of jobs       | atq  --> (at queue)
  scheduled with at          |
                             |
--------------------------------------------------------------------------------
## Chapter 13 - Configure Logging
  The 3 primary places to    | * **Direct write**: Some services write loggin
  search for logs            |   information directly to the log files
                             |
                             | * **rsyslogd**: rsyslogd is the enhancement of
                             |   syslogd, a service that takes care of managing
                             |   centralized log files.
                             |
                             | * **journald**: With the introduction of Systemd, the
                             |   journald log service systemd-journald has been
                             |   introduced also. This service is tightly
                             |   integrated with Systemd, which allows
                             |   administrators to read detailed information
                             |   from the journal while monitoring service
                             |   status using the systemctl status command
                             |
  Three approaches for       | * Monitor the files in /var/log that are written
  monitoring RHEL            |   by rsyslogd
                             |
                             | * Use the **journalctl** command to get more
                             |   detailed information from the journal.
                             |
                             | * Use the systemctl status <unit> command to
                             |   get a short overview of the last significant
                             |   events that havee been logged by Systemd units
                             |   through journald. This command shows the status
                             |   of services, as well as the last cople of lines
                             |   that have been logged
                             |
  **Common System Log Files**    |
                             |
    /var/log/messages        | Contains the most commonly used log file; it is
                             | the generic log file where most messages are
                             | written
                             |
    /var/log/dmesg           | Contains kernel log messages
                             |
    /var/log/secure          | Contains authentication-related messages. Look
                             | here to see which authentication errors have
                             | occurred on a server
                             |
    /var/log/boot.log        | Contains messages that are related to system startup
                             |
    /var/log/audit/audit.log | Contains audit messages. SELinux writes the this file.
                             |
    /var/log/maillog         | Contains mail-related messaes
                             |
    /var/log/samba           | Provides log files for the Samba service. Notice
                             | that Samba by default is not managed through
                             | rsyslog, but writes directly to the /var/log
                             |
    /var/log/sssd            | Contains messages that have been written by the
                             | sssd service, which plays an important role in
                             | the authentication pocess
                             |
    /var/log/cups            | Contains log messages that were generated by the
                             | print service CUPS
                             |
    /var/log/httpd           | Contains log files that are written by the Apache
                             | web server. Notice that Apache writes messages to
                             | these files directly and not through rsyslog.
                             |
  **Understanding Log Files**    |
    **General logfile format**   | * Date and time:
                             | * Host
                             | * Service or process name
                             | * Message content
                             |
  **Live Log Monitoring**        | tail -f <logfile>
                             |
  **Using logger**               | The **logger** command enables users to write
                             | messages to rsyslog from the command line or a
                             | script. To use logger, just type **logger**, followed
                             | by the message you want to write to the logs
                             |
    log message with specific| logger -p user.**notice** "some text"
    priority                 |
                             |
  **Configureing rsyslogd**      |
    rsyslogd Primary         | /etc/rsyslog.conf
    configuration file       |
                             |
    Other files that are     | /ect/rsyslog.d
    used to configure        |
    rsyslogd                 |
                             |
    setting additional       | /etc/sysconfig/rsyslog   --> SYSLOGD_PTIONS=""
    startup options          |                define rsyslogd startup options
                             |
                             |
  **Understanding rsyslog.conf** | The rsyslog.conf file is used to specify what
  **Sections**                   | should be logged and where it should be logged.
                             | To do this, you'll find different sections in the
                             | rsyslog.conf file:
                             |
                             | * #### **MODULES** ####: Rsyslogd is modular.
                             | Modules are included to enhance the support
                             | features in rsyslogd.
                             |
                             | * #### **GLOBAL DIRECTIVES** ####: This section is
                             | used to specify global parameters, such as the
                             | location where auxiliary files are written or the
                             | default timestamp format.
                             |
                             | * #### **RULES** ####: This is the most important
                             | part of the rsyslog.conf file. It contains the
                             | rules that specify what information should be
                             | logged to which destination.
                             |
  **Understanding Facilities**,  | To specify what information should be logged to
  **Priorities, and Log**        | which destination, rsyslogd uses facilities,
  **Destinations**               | priorities, and destinations:
                             |
                             | * A *facility* specifies a category of information
                             | that is logged. rsyslogd uses a fixed list of
                             | facilities, which cannot be extended. This is
                             | because of backward compatibility with the legacy
                             | syslog service.
                             |
                             | * A *priority* is used to define the the severity
                             | of the message that needs to be logged. When you
                             | specify a priority, by default all messages with
                             | that priority and all higher priorites are logged.
                             |
                             | * A *destination* defines whre the message should
                             | be written. Typical destinations are files, but
                             | rsyslog modules can be used as a destination as
                             | well, to allow further processing through a
                             | rsyslogd module
                             |
  **rsyslogd Facilities**        | **Facility**       **Used by**
                             | auth/authpriv  Messages related to authentication
                             | cron           Messages generated by the crond service
                             | daemon         Generic facility that can be used for nonspecified daemons
                             | kern           Kernel messages
                             | lpr            Messages generated through the legacy lpd print system
                             | mail           Email-related messages
                             | mark           Special facility that can be used to write a marker periodically
                             | news           Messages generated by the NNTP news system
                             | security       Same as auth/authpriv. Should not be used anymore
                             | syslog         Messages generated by the syslog system
                             | user           Messages generated in user space
                             | uucp           Messages generated by the legacy UUCP system
                             | local0-7       Messaged generated by services that are configured by any of the local0 through local7 facilities
                             |
  **rsyslogd Priorites**         | **Priority**       **Description**
                             | debug          Debug messages that will give as much information as possible about service operation
                             | info           Informational messages about normal service operation
                             | notice         Informational messages about items that might become an issue later.
                             | warning/warn   Something is suboptimal, but there is no real error yet.
                             | err/error      A noncritical error has occurred
                             | crit           A critical error has occurred
                             | alert          Message used when the availability of the service is about to be disconnected
                             | emerg/panic    Message generated
                             |
                             | When a specific priority is used, all messages
                             | with that priority and higher are logged
                             | according to the specificatosns used in that
                             | specific rule. If you need to configure logging
                             | in a detailed way, where messsages with different
                             | priorites are sent to different files, you can
                             | specify the priority with and equal sign (=) inf
                             | ron of it, as in the following line, which will
                             | write all cron messages with only the debug
                             | priority to a specific file with the name
                             | /var/log/cron.debug. The - in front of the line
                             | specifies to the buffer writes so that
                             | information is logged in a more efficient way.
                             |
                             |   cron.=debug -/var/log/cron.debug
                             |
  **Rotating Log Files**         | /etc/logrotate.conf  --> Default settings
                             |
  **Working with journald**      | The systemd-journald service stores log
                             | messages in the hournal, a binary file that is
                             | temorarily stored in the file /run/log/journal.
                             | This file can be examined using the **journalctl**
                             | command
                             |
    Some journalctl options  | journalctl --no-pager            Streams the contents
                             | journalctl -f                    opens a live view (most recent contents)
                             | journalctl <tab> <tab>           Shows specific options that can be used for filtering (??)
                             | journalctl -n {n}                Display the last {n} lines of the jouranl (like tail)
                             | journalctl -p {err}              Filter ouput by message priorities
                             | --since/--until YYYY-MM-DDD
                             |   yesterday | today | tomorrow
                             | journalctl --dmesg               Shows kernel-related messages only (dmsg)
                             | journalctl -o verbose
                             | `journalctl _SYSTEMD_UNIT=sshd.service   specifies service to filter (sshd)`
                             |
  **Preserving the Systemd**     | Ensure that /var/log/journal/ directory exists
  **Journal**                    | /etc/systemd/hournal.conf persistence values:
                             |   * Storage=auto       The journal will be written on diks if the directory /var/logk
                             |   * Storage=volatile   The journal will be stored only in the /run/log/journal directory
                             |   * Storage=persistent The journal will be stored on disk in the directory /var/log/journal.
                             |                        This directory will be created automatically if id doesn't exist
                             |   * Storage=none       No data will be stored, but forwarding to other targest such as
                             |                        the kernel log buffer or syslog will still work
                             |
    notes                    | * The journal has monthly built-in log rotation
                             | * The journal is limited to 10% of the files system size and will
                             |   stop growing if less than 15% of file system is still free
                             |   (to change these settings - /etc/systemd/hournald.conf)
                             |
--------------------------------------------------------------------------------
## Chapter 14 - Managing Storage
  **The MBR Partitioning**       | * An operating system boot loader is as well as
  **Scheme**                     |   the partition table is present on MBR
                             | * The MBR was defines as the first 512 bytes on a
                             |   Computer's bootable hard drive
                             | * The partition table was 64 bytes
                             | * Maximum size that could be used by a partition
                             |   was 2 TiB
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
## Chapter 15 - Managing Advanced Storage
  **LVM Architecture**           | * Physical volumes - Complete disks, partitions,
                             |     logical units (LUns), storage-area network (SAN), etc
                             |
                             | * Volume group - Physical volumes are grouped or added together.
                             |
                             | * Logical volumes - They layer at which a file system is created
                             |
                             | **Note**: It is a good idea to avoid logical volumes
                             |       from spanning multiple physical volumes;
                             |       if one of the physical volumes breaks, all
                             |       of the files on the LVM file system will
                             |       become inaccessible.
                             |
  **LVM Features**               | * Volumes are no longer bound to the resctrictions of
                             |   physical hard drive.
                             | * Volume groups can be easily extended by adding a new
                             |   physical volume if additional storage space is needed
                             | * Logical volums can also be reduced if the file system
                             |   on the volume supports the feature
                             | * LVM supports snapshots
                             | * Failing hardware can be replaced easily.
                             |
  **Creating LVM Logical**       | Creating LVM Logical volumes involves creating the three
  **Volumes**                    | layers in the LVM architecture.
                             | * Convert physical devices (disks, partitons) into
                             |   physical volumes (PVs)
                             | * Create the Volume group and assign PVs to it
                             | * Create logical volume (LV) itself.
                             |
  **Creating the Physical**      | Before you can use the LVM tools to create physical
  **Volumes**                    | volumes, you need to create a partitionmarked as
                             | the LVM partition type:
                             |   * In fdisk and gdisk: use **t** from the menu to change
                             |     the type
                             |   * If you are using an MBR disk, the partition type is 8e
                             |   * If you are using a GUID disk, use the partiton type 8e00
                             |   * If you are using **parted**, use **set n lvm on**
                             |
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
## Chapter 16 - Basic Kernel Management
  **Tainted Kernel**             | When a kernel is using one or more closed-source
                             | drivers
                             |
  **Analyzing what the Kernel**  | To help analyze what the kernel is doing, the Linux
  **is doing**                   | operating system provide some tools:
                             | * The **dmesg** utility
                             | * The /proc file system
                             | * The **uname** utility
                             |
  **dmesg**                      | * Shows the contents of the kernel ring buffer, an
                             |   area of memory where the Linux kernel keeps its
                             |   recent log messages.
                             | * An alternative is **journalctl --dmesg**
                             |
  **/proc**                      | * The **/proc** file system is an interface to the Linux
                             |   kernel
                             |
  **uname**                      | uname -a - overview of all relevant parameters
                             | uname -r - displayes the current kernel version
                             |
  **Understanding Hardware**     | The loading of drivers is an automated process
  **Initialization**             | that roughly goes like this:
                             | 1. During boot, the kernel probes available hardware
                             | 2. Upon detection of a hardware component, the
                             |    systemd-udevd process takes care of loading the
                             |    appropriate driver and making the hardware device available
                             | 3. To decide how the devices are initialized, **systemd-udevd**
                             |    goes to /etc/udev/rules.d. These are system-provided
                             |    rules files that should not be modified.
                             | 4. After processing the system-provided udev rules
                             |    files, **systemd-udevd**goes to the /etc/udev/rules.d
                             |    directory to read any custom rules if these are available
                             | 5. As a result, required kernel modules are loaded
                             |    automatically, and status about the kernel
                             |    modules and associated hardware is written to the sysfs
                             |    file system, which is mounted on the /sys directory.
                             |    The linux kernel used this pseudo file system to
                             |    track hardware-related settings
                             |
  **Monitoring Hardware changes**| * As root: **udevadm monitor**
                             |
  **Managing Kernel Modules**    |
                             |
    **lsmod**                    | * Lists currently loaded kernel modules
    **modinfo**                  | * Displays information about kernel modules
    **modprobe**                 | * Loads kernel modules, including all of their
                             |   dependencies
    **modprobe -r**              | * Unloads kernel modules, considering kernel
                             |   module dependencies
    **modinfo**                  | * Gives more information about a specific module
                             |
  **Checking Driver**            | Some devices on a system are not supported properly
  **Availability for Hardware**  | and, as a resulte, their modules are not currently
  **Devices**                    | loaded. To find out, use the **lspci** command
                             |
                             |
    **lspci**                    | Shows all hardware devices that have been detected
                             | on the PCI bus.
                             | * **lspci -k**: lists all kernel modules that are used
                             |   for the PCI devices that were detected
                             |
  **Managing Kernel Module**     | * Occasionally, you might want to load kernel modules
  **Parameters**                 |   with specific parameters
                             | * To make this an automated procedure, you can create
                             |   a file in the /etc/modprobe.d/ directory
                             |
  **Upgrading the Linux Kernel** | * **yum upgrade kernel**
                             | * **yum install kernal** - the same as above
                             |
--------------------------------------------------------------------------------
## Chapter 17 - Managing and Understanding the Boot Procedure
  **Understanding Systemd**      | A Systemd *target* is basically just a group of
  **Targets**                    | units that belong together. Some targets are used
                             | to define the state a system is booting in, and these
                             | can be isolated. Four targets can be used while booting:
                             |
                             | * **emergency.target**: In this target only a minimal
                             |   number of units are started, just enough to fix your
                             |   system if something is seriously wrong.
                             |
                             | * **rescue.target**: This target starts all units that are
                             |   required to get a fully operational Linux system. It
                             |   doesn't start nonessential services though.
                             |
                             | * **multi-user.target**: This target is often used as the
                             |   the default target a system starts in.  It starts
                             |   everyting that is needed for full system functionality
                             |   and is commonly used on servers.
                             |
                             | * **graphical.target**: This target also is commonly
                             |   used. It starts all units that are needed for full
                             |   functionality, as well as a graphical interface.
                             |
  **Working with Targets**       | Working with targets comes down to three common tasks:
                             | * Adding units to be automatically started
                             | * Setting a default target
                             | * Running a nondefault target to enter troubleshooting mode
                             |
  **Understanding Target Units** | Target configuration consists of two parts:
                             | * The target unit file
                             | * The "wants" directory, which contains references
                             |   to all unit files that need to be loaded when
                             |   entering a specific target
                             |
  multi-user.target file     | /usr/lib/systemd/system/multi-user.target
  command to display file    | **systemctl cat multi-user.target**
                             |
  **Understanding Wants**        | Wants are created when Systemd units are enabled
                             | using **systemctl enable**, and this happens by
                             | creating a symbolic link in the /etc/systemd/system
                             | directory. In this directory, you'll finda
                             | subdirectory for every target, containing wants
                             | as symbolic links to specific servies that are
                             | to be started
                             |
  Display list of all        | systemctl --type=target         -- only active targets
  currently loaded targets   | systemctl --type=target -- all  -- all targets existing on the system
                             |
  Starter targets and        | poweroff.target    runlevel 0
  associated runlevels       | rescue.target      runlevel 1
                             | multi-user.target  runlevel 3
                             | graphical.target   runlevel 5
                             | reboot.target      runlevel 6
                             |
  display current default    | systemctl get-default
  target                     |
                             |
  Set the default target     | systemctl set-default
                             |
  **Understanding GRUB 2**       | The GRUB 2 boot loader makes sure that you
                             | can boot Linux. GRUB 2 is installed in the boot
                             | sector of your server's hard drive and is
                             | configured to load a Linux kernel and he iniramfs
                             |
  Applying changes to GRUB 2 | Starting point: /etc/default/grub
                             | also: /etc/grub.d   **usually does not need to be modified**
                             |
  **Understanding GRUB 2 config**| Config Files:
  **file**                       |   BIOS: /boot/grub2/grub.cfg          automatically generated
                             |   UEFI: /boot/efi/EFI/{redhat,centos} automatically generated
                             |
  how to find GRUB 2 boot    | **man 7 bootparam**
  arguments                  |
                             |
  apply changes to grub2     | **grub2-mkconfig**
                             | BIOS: grub2-mkconfig -l /boot/grub2/grub.cfg
                             | UEFI: grub2-mkconfig - /boot/efi/EFI/redhat/grub.cfg
                             |
--------------------------------------------------------------------------------
## Man
Manpage types                | 1   Executable programs or shell commands
                             | 2   System calls (functions provided by the kernel)
                             | 3   Library calls (functions within program libraries)
                             | 4   Special files (usually found in /dev)
                             | 5   File formats and conventions, e.g. /etc/passwd
                             | 6   Games
                             | 7   Miscellaneous (including  macro  packages  and  conventions),  e.g. man(7), groff(7)
                             | 8   System administration commands (usually only for root)
                             | 9   Kernel routines [Non standard]
                             |
search mandb based on keyword| man -k | apropos
rebuild mandb                | mandb
                             |
--------------------------------------------------------------------------------
## Finding Files
Search for binaries in PATH  | which
Search from local db         | locate -> updatedb
General search               | find
                             | find / -name fstab  -> search by name (can use globbing)
                             | find / -type f -size +100M -> search all files larger than 100M
                             | find / -user student -> search all files owned by student
                             |
--------------------------------------------------------------------------------
## Globbing
Glob any number of chars     | *
Glob 1 of any char           | ?
Glob 1 of a list of chars    | [hm] -> either h or m
Exclued 1 of a list of chars | [!hm] -> any char except h or m
Glob 1 of a range of numbers | [0-9] -> any number between 0 and 9
                             |
--------------------------------------------------------------------------------
## RPM
Install package              | rpm -i telnet.rpm
remove package               | rpm -e telent.rpm
query package                | rpm -q telnet.rpm
                             |
*** NOTE - rpm does not resolve dependencies
YUM - package manager which uses rpms
Install package              | yum install ansible
View YUM Repos               | yum repolist
                             |
--------------------------------------------------------------------------------
## Working with Linux Files - Permissions / Links
  Hard / Soft Links          | Hard Link:
                             |   * Additional name for an existing file
                             |   * Can't be created for directories
                             |   * Can't cross filesystem boundaries or partitions
                             |   * Same inode number and permissions as original file
                             |
                             | Soft Link
                             |   * Special file that points to another file
                             |   * Can be created for directories
                             |   * Can cross filesystem boundaries or partitions
                             |   * Different indoe number and file permissions than original
                             |   * Doesn't contain file data
                             |
  umask                      | The file creation mask (umask) sets permissions for new files/directories
                             | The umask is subtractive: it removes the persissioms from default permisions
                             |
                             | Default permissions for files is 666; directories are 777
                             |
                             | umask value    File Permissions    Directory Permissions
                             | 002            -rw-rw-r--          drwxrwxr-x
                             | 007            -rw-rw----          drwxrwx---
                             | 022            -rw-r--r--          drwxr-xr-x
                             | 027            -rw-r-----          drwxr-x---
                             | 077            -rw-------          drwx------
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
