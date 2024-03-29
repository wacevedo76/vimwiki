SUSE Enterprise Server 
--------------------------------------------------------------------------------
= Understand YaST =
--------------------------------------------------------------------------------
  * Local system configuration tool
    * Acronym: Yet Another System Tool
    * User Interfaces:
    ** Command line non-interactive
    ** Comand line interactive
    ** Graphical
    ** Non-graphical (ncurses)
    * Two versions, started with different commands
      Command           Terminal in X           Command Line
      yast              ncurses                 ncurses
      yast2             Graphical               ncurses
                              |
== Command line commands ==
    list of modules           | yast -l | yast --list
    start module              | yast <module> | yast2 <module>
                              |
== YaST control Center - Modules ==
  * YaST modules are written in Ruby and provide specific tools
    for administering the various components of a SUSE Linux Enterprise computer.
    Some Examples:
      - Online Update
      - Software Management
      - Network Settings
      - NTP Configuration
      - Samba Server
      - User and Group Management
--------------------------------------------------------------------------------
= Understanding the Filesystem Hierarchy Standard =
--------------------------------------------------------------------------------
== Filesystem Hierarchy Standard (FHS) ==
  * Part of the LSB (Linux Standard base) specifications
  * Which directories must be located on the first level and what they contain
  * Defines a two-layer hierachy 
  * Directories in the top layer (off the root "/")
  * At the second layer under /usr and /var
  * Design Factors
  * Compartmentalization
  * Writablility
  * Shareability
  * Details: https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard
  ** This of the FHS as "what goes where and why"
--------------------------------------------------------------------------------
== The Linux File System Structure ==
  The Root directory "/"
  * Refers to the highest layer of the file system tree. This root partion is 
    mounted first at system boot. All programs that are run at system startup 
    must be in hte partition

  * The following directories must be in the root partition:
    - /bin        - User binaries
    - /dev        - Device files
    - /etc        - Configuration files
    - /lib        - Libraries
    - /sbin       - System binaries

  * Essential binaries for all users (/bin)
  * Containes executables required when no other file systems are mounted. For
    example, programs required for system booting, working with files and
    configuration
    
    /bin/bash     - The bash shell
    /bin/cat      - Display file contents
    /bin/cp       - Copy files
    /bin/dd       - Copy files byte-wise
    /bin/gzip     - Compresses files
    /bin/mount    - Mount file systems
    /bin/rm       - Delete files
    /bin/vi       - Edit files
  
  * System Binraires (/sbin)
  * Contains programs important for system administration. Typically are intended
    to be run by the root user and therefore it is not in the regular users path.
    
  * Some important files:
    /sbin/yast    - Administration tool
    /sbin/fdisk   - Modifies partitions
    /sbin/fsck    - File system check
    /sbin/mkfs    - Creates file systems
    /sbin/shutdown - Shutd down the system
  
--------------------------------------------------------------------------------
= Linux Filetypes =
                             |  Normal files
                             |    * ASCII text files
                             |    * Executalbe files
                             |    * Graphics fles
                             |  Directories
                             |    * Organize files on the disk
                             |    * Cotain files and subdirectories
                             |    * Implement the hierarchical file system
                             |  Hard Links
                             |    * Secondary file names for files on the disk
                             |    * Multiple file names referencing a sing inode
                             |    * Referenced files must reside in the same file system
                             |  Symbolic Links
                             |    * References to other files on the disk
                             |    * The inode contains a reference to another file name
                             |    * Referenced files can exist in the same file 
                             |      sytem or in other file systems
                             |    * A symbolic link can reference a non-existing
                             |      file (broken link)
                             |  Device Files
                             |    * Represent hardware (except network cards)
                             |    * Link between hardware devices and the kernel drivers
                             |    * Kernel drivers read from and write to the device file
                             |    * The kernel get the data to the actual hardware in the correct format
                             |    * Types:
                             |        * Block Devices
                             |        * Character Devices
                             |    * Created automatically by the OS (udev)
                             |
Linux Device Names for Hard  |  * 1st initialized hard drive = /dev/sda
  Hard Drives                |  * 2nd initialized hard drive = /dev/sdb ... ect
                             |  * Partition numbers are appended to the device name:
                             |
        Devce                                                 Name
        First primary partition on first hard driver          /dev/sda1
        Second primary partition or an extended partition on  /dev/sda2
        first hard driver
        First primary partition on the third hard drive       /dev/sdc1
        First logical partition on  first hard drive          /dev/sda5
        Second logical partition on first hard drive          /dev/sda6
                             |
Interprocess Communication   |  * Files used by processes to communicate with
  File                       |    each other
                             |  * Types:
                             |    * Sockets (bi-directional communication)
                             |    * Pipes/FIFOs (unidirectional communication)
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
= Week two - Work with the command Line > Getting help at the cli =
--------------------------------------------------------------------------------
  Help Resources             |  <command> -h or <command> --help
                             |  Man [section] command
                             |    * Find references: man -f keyword
                             |    * List for keywords: man -k keyword
                             |    * Display descriptions: whatis <command>
                             |  Info pages: info command
                             |  * Software package documentation in
                             |    - /usr/share/doc/packages
                             |  * Release notes
                             |    - /usr/share/doc/release-notes
                             | 
  Shell Environment          |  A shell can be invoked in two different ways
                             |    * Login Shell     - The user's environment is set
                             |    * Non-login Shell - The shell inherits an existing
                             |                        environment
                             |
  Profiles                   |  Global profiles
                             |  /etc/profile
                             |    /etc/profile.d/*.sh               <-- not touched when install and upgrad
                             |    /etc/profile.local
                             |
                             |  /etc/bash.bashrc
                             |    /etc/bash_completion.d/*.sh       <-- not touched when install and upgrad
                             |    /etc/bash.bashrc.local
                             |
                             |  /etc/inputrc
                             |    (bash -> libreadline.so)
                             |
                             |  User specific profiles:
                             |    ~/.profile
                             |    ~/.bashrc
                             |    ~/.alias
                             |
                             |
  Order of execution for     |  1) /etc/profile
  login shells               |  2) /etc/profile.d/*.sh
                             |  3) /etc/profile.local
                             |  4) ~/.profile
                             |  5) /etc/bash.bashrc
                             |  6) /etc/bash_completion.d/*.sh
                             |  7) /etc/bash.bashrc.local
                             |  8) /etc/inputrc
                             |  9) ~/.bashrc
                             |  10) ~/.alias
                             |
  Order of execution for     |  1) /etc/bash.bashrc
  non-login shells           |  2) /etc/bash_completion.d/*.sh
                             |  3) /etc/bash.bashrc.local
                             |  4) /etc/inputrc
                             |  5) ~/.bashrc
                             |  6) ~/.alias
                             |
  show current aliases       |  > alias
                             |
  Temp remove alias          |  > unalias
                             |
  execute a command from     | Ctrl+R
  history                    |
                             |
Shell Expansions {wild cards)| * Any number or zero values
                             |
                             | ? Any one value
                             |
                             | {..} list of values
                             |
                             | [...] Range of values [1-9], [a-z]
                             |
                             | [!abc] None of these characters
                             |
                             | "..." Interpret all characters between the quotes
                             |       as ASCII characters except: $  \ 
                             |
                             | '...' Interpret all characters between the quotes
                             |       as ASCII characters
                             |
Variables                    |
  set                        | Displays all shell variables and function
                             |
  env                        | Displays only environment variables
                             | (i.e. variables with -x attribute set)
                             |
  $$ or ${...}                 | Reference a value stored in a variable
                             |
  `...`  or $(...)             | Execute command(s) and return the output as input
                             | for another command
  `$((...))` or `$[...]`         | Perform an Arithmetic operation on the contents of
                             | variables and retun its results
                             |
  `$?`                         | "Return" or "exit" value of the previously executed
                             | command
                             |
  `$0`                         | Name of the command being executed
  `$#`                         | Number of command arguments
  `$*`                         | All command arguments
  `$1, $2, ... $N`             | Value of the corresponding argument
  `$$`                         | Process ID of the current shell
                             |
-------------------------------------------------------------------------------
== Common Shell Commands ==
-------------------------------------------------------------------------------
  View File Content          |
    tac                      | Same as cat, but displays the files in reverse
                             |
    head                     | Displays the first lines of a file
                             | to set the number of lines use the -n option
                             |
    Tails                    | Display the last lines of a file
                             | To set the number lines use the -n option
                             | To output append data use the -f option
                             |
  Backup-Oriented Shell      |
  Commands                   |
    tar                      | Create, expand or list archive files
                             | * Use option c to create a archive
                             | * use option f to specify the archive file name
                             | * use option v for verbose mode
                             | * use option x to extract an archive
                             | * use option t to list the content of an archive
                             | * use option z to (un-)compress the archive with gzip
                             | * use the j to (un-)compress the archive with bzip
                             |
    cpio                     | Another archiving command
                             |
    gzip                     | Compress files using he gzip algorithm
                             | Option -d same as gunzip
                             |
    gunzip                   | Expand files compressed with gzip
                             |
    bzip2                    | Compress files sing the bzip2 algorithm
                             |
    bunzip2                  | Expand files compressed with bzip
                             |
  Special File Copying       |
  Commands                   |
    rsync                    | Copy only deltas between two directories
                             | * Locacl or via network
                             | * Uses ssh as default transport
                             | * Can talk to rsync daemon on the remote machine
                             |
    dd                       | Copies files block by block
                             | * Used to create disk or partition images
                             | * most important options:
                             |   if=input_file
                             |   of=output_file
                             |   bs=block_size
                             |
  Search for files           |
    find                     | Search for files or directories
                             |  * Syntax: find path criterion [action]
                             |
    type                     | Shows the kind of command, eg:
                             | * shell built-in
                             | * external command
                             | * alias
                             | * function
                             |
                             |
                             |
                             |
                             |
                             |
-------------------------------------------------------------------------------
== Remote administration ==
=== SSH ===
  Read SSH host keys from    | ssh-keyscan
  another system             |   -t  - Type of key
                             |
  SSH Server Configuration   | configuration file: /etc/ssh/sshd_config
                             |
    AllowUsers               | Allows SSH login only for users
                             |
    DenyUsers                | Denies SSH login to users listed
                             |
    ListenAddress            | Local addresses that sshd listens on.
                             | Syntax: IP_address:port
                             |
    Port                     | Port number that sshd listens on. (default 22)
                             | Multiple options of this type are permitted
                             |
    PasswordAuthentication   | Specifies whether password authentication is
                             | allowed. To disable it, set this and UsePam to no
                             |
    UsePam                   | Enables the Pluggable Authentication module interface
                             |
  Client Configuration       |
                             |
    Create an SSH key Pair   | ssh-keygen
                             |    -t type of key
                             |
    upload public key        | ssh-copy-id -i <location of key> username@host
                             |    -i (location of key
                             |
  Use the SSH Agent          | eval $(ssh-agent -s)
    Eliminate the need to    | ssh-add .ssh/id_dsa
    type the passphrase upon |
    each connection          |
-------------------------------------------------------------------------------
=== vnc ===
  Remote management          | * SLE Provides management useing Virtual Network
                             |   Computing (VNC)
                             |
                             | * VN enables manaement via a graphical desktop
                             |
                             | * VNC is
                             |     - Platform independent
                             |     - Opwn source
                             |
                             | * VNC consists ot two components
                             |   * Server
                             |   * client
                             |
  Configured using YaST      | -> Remote Management (VNC) option
                             |
  Three options:             | * Allow Remote Management with Session Management
                             | * Allow Remote Management without Session Management
                             | * Do not allow Remot Administration
                             |
                             | Firewall configuration option is available
                             |
  Remote Management Options  | * Allow remote manage with Session Management
                             |   * Enables multiple concurrent sessions
                             |   * Access available to multople clients simultaneously
                             |   * All applications started in this session run
                             |     regardless of client connections until the 
                             |     session is terminated
                             |
                             | * Allow Remote Management without Session Management
                             |   * Once concurrent session only
                             |
  Configure a One Time VNC   | * One-time VNC sessions are started via the xinetd daemon
    Session                  | * A configuration fie is located at /etc/xinetd.d/vnc
                             | * By default it offers:
                             |   * Three fore VNC view (vnc1 to vnc3)
                             |   * Three serving a Java applet (vnchttpd1 to vnchttp3)
                             |   * By default only vnc1 and vnchttpd1 are active
                             |
                             | * To activate a configuration:
                             |   ( Comment the line disable = yes with a # character
                             |   in the first column
                             |
                             | * To configure the Xvnc server:
                             |   * see Xvnc --help
                             |
                             | * use any VNC Client
                             |   * Default port TCP 5901
                             | * Java enabled web browser
                             |   * http://<ip or fqdn or host>:5801
-------------------------------------------------------------------------------
= Week Three =
-------------------------------------------------------------------------------
== Define and List SLE12 boot Process ==

BIOS/UEFI
`|------------------|`
`|    BIOS/UEFI     |`
`-------------------`
`         |`
  `|------------------|`
  `|   Stage 1 - MBR  |`
`  |------------------`
    Bootloader
  `|------------------|`
  `|   Stage 2 -      |`
`  ``|------------------``
         |
  `|------------------|`
  `|   Kernel         |`
  `|`  initramfs       |
`  |------------------|`
`  |Hardware (udev)   |`
`  |__________________|`
`         |`
`  |--------------------------------|`
`  |   |---------------------------||`
`  |   |  systemclt default        ||`
`  |   |---------------------------||`
`  |   |     /etc/systemd/system/  ||`
`  |   |     default.target        ||`
`  |   |---------------------------||`
`  |                  |             |`
`  |   |---------------------------||`
`  |   |   /usr/lib/systemd/system/||`
`  |   |      *.target             ||`
`  |   |---------------------------||`
`  |         Default target         |`
`  |   |---------------------------||`
`  |   |systemctl start *.service  ||`
`  |   ---------------------------- |`
`  |   |              |GUI (xdm)   ||`
`  |   ---------------------------- |`
`  |   |---------------------------||`
`  |   |/usr/lib/systemd/system/   ||`
`  |   |  getty@.service           ||`
`  |   |---------------------------||`
`  |                 |              |`
`  |   |---------------------------||`
`  |   |   Virtual terminalsa      ||`
`  |   ---------------------------- |`
`  ----------------------------------`
initramfs
                             | * cpio Archinve
                             | * Loaded by the kernel intor Ram disk
                             | * Minimal Linux Evironment 
                             | * udev provides the iniramfs with the needed devices
                             |   * mkinitrd creates an initramfs
                             |   * mkinitrd -R creates an init executable
-------------------------------------------------------------------------------
== Define and Explain UEFI, Secure Boot, and Trusted Execution ==
-------------------------------------------------------------------------------
  Advantages of UEFI         | * Advantages of UEFI CPU-independent architecture
                             |   and drivers
                             | * Flexible pre-OS environment with network capabilities
                             | * Compatibility Support Module (CSM)
                             | * PC-BIOS-like emulation
                             | * Can user secure boot     `|BIOS > Any os Loader Code <- ? Malware ? _> OS start>`
                             |                           ` |UEFI > Verified OS Loader > OS start > os verified`
                             |
-------------------------------------------------------------------------------
  Secure Boot                |
  * PK                       | Platform Key
  * KEK                      | Key Exchange Key
  * MOK                      | Machine Owner Key
                             |
  Secure Boot (Process)      |    where? | Stage                                       | Next step
                             |  FIRMWARE | PK -> KEK db -> (to OS)
                             |
                             |        OS | KEK -> (Shim)  <--> Boot Var -> (MOK List)  |-> (to SUSE Pub)
                             |           | SUSE Pub (Verify and load)                  |-> (to MOK -> GRUB2)
                             |           | MOK -> GRUB2 (Verify and boot)              |-> (to MOK -> Kernel)
                             |           | MOK -> Kernel
-------------------------------------------------------------------------------
  Difference between GRUB    | * Different configuration files
  Legacy and GRUB2           | * More file systems are supported (e.g., Btrfs)
                             | * Read files on LVM or RAID devices
                             | * User interface can be:
                             |   * translated
                             |   * altered with themes
                             | * Load modules to support additional features(e.g., file systems)
                             | * Search for tand generate boot entries for other kernels and
                             |   operating systems automatically
                             |
  Configuration File         | File                         Description
  Structure                  | /boot/grub2/grub.cfg         Configuration of the GRUB2 menu items
                             | /boot/grub2/custom.cfg       Add custom items to the boot menu
                             | /etc/default/grub            User setting of GRUB2, additional environmenta
                             |                              settings
                             | /etc/grub./*                 Integrated into the main configuration file
                             | /etc/sysconfig/bootloader    Boot loader independent settings needed by YaST
                             |                              and new kernels
                             | /boot/grub2/x86_64-efi,      Architecture-specific options
                             | /boot/grub2/power-ieee12
                             | /boot/grub2/s390x
-------------------------------------------------------------------------------
== Understand the GRUB2 Boot loader ==
  Grube 2 General Options    | 
    Component                | Description
    GRUB_DEFAULT             | Sets the boot menu entry that is booted by
                             | default. Its value can be a numeric value,
                             | the complete name of a menu entry, or saved
                             |
    GRUB_DEFAULT=2           | boot the third (counted from zero) boot 
                             | menu entry
                             |
    GRUB_DEFAULT="2>0"       | boots the first submenu of the third top-
                             | level menu enty
                             |
    GRUB_DEFAULT="menu1"     | Boots the menu entry with the title "menu1"
                             |
    GRUB_DEFAULT=saved       | Boots the entry specified by the grub2-reboot or
                             | grub2-set-default commands. While grub2-reboot sets
                             | the default boot entry for the next reboot only,
                             | grub2-set-default sets the default boot entry
                             | until changed
                             |
    GRUB_HIDDEN_TIMEOUT      | Waits the specified number of seconds for the user
                             | to press a key. During the period no menu is shown
                             | unless the user presses a key.
-------------------------------------------------------------------------------
  /etc/default/grub - OS OPTIONS
    OPTION                   |        * DESCRIPTION
    GRUB_CMDLINE_LINUX       |        * Entries are added at the end of the boot entries 
                             |        * for normal and recovery mode
                             |
    GRUB_CMDLINE_LINUX_DEFAULT        * Entries are added in the normal mode only
                             |
    GRUB_CMDLINE_LINUX_RECOVERY       * Entries are added in the recovery mode only
                             |
    GRUB_CMDLINE_LINUX_XEN_REPLACE    * Replace GRUB_*_LINUX entries for all Xen boot entries
                             |
    GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT  * Replaces entries of GRUB_*_LINUX_DEFAULT
                             |
    GRUB_CMDLINE_XEN         |        * Entries for the Xen guest kernel only
                             |
    GRUB_CMDLINE_XEN_DEFAULT |        * Xen entries are added in the normal mode only
                             |
    GRUB_HIDDEN_TIMEOUT_QUIET|        * If false is specified, a countdown timer is displayed
                             |          on a black screen when the GRUB_HIDDEN_TIMEOUT is active
                             |
    GRUB_TIMEOUT             |        * Time period in seconds the boot menu is displayed 
                             |          before automatically booting the default boot entry
                             |          If you press a key, the timout is canceld and GRUB2 
                             |          waits for you to make a selection manually
                             |
    GRUB_TIMOUT=-1           |        * will cause the menu to be displayed until you select 
                             |          the boot entry manually
                             |
    GRUB_DISABLE_OS_PROBER   |        * If this option is set to true, automatic searching for 
                             |          other operating systems is disabled. Only the kernal 
                             |          images in /boot/ and the options fro m you onw scripts 
                             |          in /ec/grub.d/ are detected
                             |
    SUSE_BTRFS_SNAPSHOT_BOOTING       * If this option is set to true, GRUB 2 can boot directly 
                             |          into Snapper snapshots
                             |
                             |
  One-time VNC sessions are  |
  are started with the       |
  xinetd daemon              |
-------------------------------------------------------------------------------
== GRUB2 Commands ==
  grub2-mkconfig             | Generates a new /boot/grub2/grub.cfg (option -o)
  grub2-mkrescue             | Creates a bootable rescure image
  grub2-script-check         | Checks the given file for syntax errors
  grub2-once                 | Set the default boot entry for the next boot
-------------------------------------------------------------------------------
== Set a Boot Password ==
  * If set, the boot password is required on every boot!
  * Procedure
    - Encrypt the password using  -> grup2-mkpasswd-pbkdf2
      > in /etc/grub.d/40_custom
  * Paste the resulting string in:
    - password_pbkdf2 <superuser> <pw_string>
      set superusers="root"
      password_pbkdf2 root <pw_string>
    set superusers command
      > Run -> grub2-mkconfig
      
                              |
                              |
                              |
                              |
                              |
                              |
                              |
-------------------------------------------------------------------------------
== Define and Describe systemd ==
  What is systemd            | * systemd is a system and session manager for Linux,
                             |   compatible with System V and LSB init scripts
                             |
                             | * systemd
                             |   * Aggressive parallelization capabilities
                             |   * on-demand daemon activation
                             |   * keeps track of processes using Linux Kernal 
                             |     Controls Groups (cgroups)
                             |   * can auto-restart failing daemons
                             |   * Logging not only of syslog messages from services,
                             |     but also messages services displayed on stdout
                             |   * Well documented in manual pages
                             |
  systemd Basics             | * Always process ID 1
                             |   * All other programs are either startded directly by
                             |     systemd or by one of its child processes
                             |   * Started directly by the Kernel
                             |   * Resists signal 9
                             |   * Replacement for System V init daemon
                             |     * Fully compatible with System V init
                             |
  Unit File                  | * A unit configuration file encodes information about
                             |   a service, a socket, a device, etc.
                             | * A manual page for each type, such as
                             |   * man systemd.service, explains the specifics of the 
                             |     respective type
                             |   * Service unit file can replace the /etc/init.d/ scripts
                             |
                             | * File name extension defines Unit type
                             | * Location: /usr/lib/systemd/system/   <-- applying service packs can overwrite
                             |             /etc/systemd/system        <-- apply changes here 
                             |                                            files do not run if they do not exist here.
                             |
                             |    Unit             Filename
                             |    Service          <service>.service
                             |    Targe           <target>.target
                             |    Sockets          <socket>.socket
                             |    Path             <path>.path
                             |    Timer            <timer>.timer
                             |    Mountpoint       <mount>.mount
                             |    Automount Point  <automount>.automount
                             |    Swap             <swap>.swap
                             |    Device           <device>.device
                             |    Scope/Slice      <scope>.scope
                             |
  Unit File Structure        | * Sections:
                             |   * [Unit]
                             |   * [Service]|[Target]|...
                             |   * [Install]
                             |
  Unit File: [Unit]          | Option           Description
                             | Description      Description
                             | After            Start of the unit is delayed 
                             |                  until all listed units have started up
                             | Before           Invers of After
                             | Requires         The units listed here are activated as well
                             | Conflicts        Unit is in conflict with the listed units
                             |
  Unit File Sections:        | Option           Description
    [Service]                | Type             Process start-up type
                             |                  Available types: simple, forking, onshot, dbus, notify, idle
                             | EnvironmentFile  File to read environment variables from
                             | ExecStart        Command line(absolute path, with arguments) that is
                             |                  execute when theis sevice is tarted
                             | ExecStartPre,    Additional commands that are executed before or after the     
                             | ExecStartPost    command in Execstart
                             | ExecReload       Commands to trigger a configuration reload in the service
                             | ExecStop         Commands to execute to stop the service
                             | KillMode         How processes of this service shall be killed.
                             |                  Available modes: control-group, process, none
                             | Restart          Configures whether the main service process shall be 
                             |                  restarted when it exits.
                             |                  Available options: no, one-success, on-failure, on-abort, or
                             |                  always
                             |
  Unit File Sections:        | * Applies to [Service], [Socket], [Mount],[Swap] 
    Secure Services          |   sections /unit types
                             |   * Limit networ access (namespace)
                             |     - PrivateNetwork=yes
                             |
                             |   * Private /tmp
                             |     - PrivateTmp=yes
                             |   * Restrict access to directories
                             |     - InaccessibleDirectories=/home
                             |     - ReadOnlyDirectories=/var
                             |   * Restrict capabilities
                             |     - CapabilitiesBoundingSet=CAP_CHOWN CAP_KILL
                             |     - CapabilitiesBoundingSet=-Cap_PTRACE (all but this one)
                             |
                             |   * Set user, group, and root directory
                             |     - User=
                             |     - Group=
                             |     - RootDirectory=
                             |   * Device access restriction (whitelist)
                             |     - DeviceAllow=/dev/nul rw
                             |   * Resource restriction
                             |     - LimitNPROC=1
                             |     - LimitFSIZE=0
                             |
  Unit File Sections:        | Option         Description
    [Install]                | WantedBy       A symbolic link is created in the .wants/ or
                             | RequiredBy     .requires/ directory of each of the listed units
                             |                wehn this unit is installed by systemctl enable
                             |
                             | Alias          A space-seperated list of additional names this
                             |                unit shall be installed under.
                             | Also           Additional units to install/deinstall when this unit
                             |                is installed/deinstalled
                             |
  systemctl                  | * Systemctl is the command to interact with systemd
                             | * without options,it displays the various units active on the
                             |   system, with -a also the inactive units
                             | * by default less is used a pager
                             | * Some units are not defined in files in
                             |   /usr/lib/systemd/system/, they are created automatically,
                             |   such as:
                             |     * various .mount units based on entries in /etc/fstab
                             |     * other units based on rules in /usr/lib/udev/rules.d/ that contain
                             |       rules that contain TAG+=systemd entries
                             |
  Manage Services            |              command
                             | systemd      systemctl <command> <service>.service
                             | System V     rc<service> <command>
                             |
                             | Systemd Command        Description                     System V
                             | start                  Start service                   start
                             | stop                   Stop service                    stop
                             | restart                Restart service                 restart
                             | reload                 Reload configuration without    reload
                             |                        Interupting operation
                             | reload-or-restart      Reload service if it is         n/a
                             |                        Supported, otherwise restart
                             |                        It
                             | reload-or-try-restart  Reload service if it is         n/a
                             |                        supported, otherwise restart
                             |                        it if it is running
                             | status                 List status information         status
                             | is-active              List short status information   status
                             |
  Enabling/Disabling         | * systemctl <command> <service>.service
    Services                 |
                             | systemd      Description                                 System V
                             | enable       Enable service                              inserv
                             | disable      Disable service                             inserv -r
                             | is-enabled   Check if service is enabled                 chkconfig
                             | reenable     Disable service and enable it afterwards    n/a
                             | mask         After "disabling" a service, it can still   n/a
                             |              be started manually, after masking it 
                             |              cannot
                             | umask        A service that hs a been masked can only    n/a
                             |              be used again after it has been unmasked
                             |
    Target Units             | * Targets are synchronization points, similare to runlevels, but
                             |   more fine-grained
                             | * Targets group service and other units
                             | * some target untis are the equivalent to runlevels
                             |   * multi-user.target - runlevel 3
                             |   * graphical.target - runlevel 5
                             | * Switching:
                             |   * systemctl isolate multi-user.target
                             |
                             | Target Unit                  Description                               System V
                             | default.target               Booted by default                         n/a
                             |
                             | graphical.target             System with network, multi-user suppport  Runlevel 5
                             | (runlevel5.target)           and a displaymanager
                             |
                             | multi-user.target            Multi-user system with network            Runlevel 3
                             | (runlevel2.target,
                             | runlevel3.target)
                             |
                             | n/a                          Local multi-user system without network   Runlevel 2
                             |
                             | mail-transfer-agent.target   All services necessary for sending and    n/a
                             |                              receiving mails
                             |
                             | resuce.target                Single user system without network        Runlevel 1
                             | (runlevel6.target)                                                     Runlevel s
                             |
                             | emergency.target             Emergency shell on the console
                             |
                             | reboot.target                Reboot the system                         Runlevel 6
                             | (runlevel6.target)
                             |
                             | halt.target                  Shut down the system                      Runlevel 0
                             | (runlevel0.target,
                             | poweroff.target)
                             |
  Change Targets             | Change the current target/runlevel:
                             |   systemctl isolate <target>.target
                             | Change to the default target/runlevel:
                             |   systemctl default
                             | Get the current target/runlevel:
                             |   systemctl list-units --type=target
                             | Persistently change the default runlevel:
                             |   systemctl set-default --force <target>.target
                             | Change the default runlevel for the current oot process:
                             |   systemd.unit=<target>.target
                             | Show a target's/runlevels' dependencies:
                             |   systemctl show -p "Requires" <target>.target
                             |   systemctl show -p "Wants" <target>.target
                             |
                             |
                             |
                             |
-------------------------------------------------------------------------------
== Process management ==
  Manage Processes           | kill <PID> [signal]              Sends a signal to a specific PID
                             | killall <process_name>[signal]   Sends a signal to all processes with a 
                             |                                  specified name
                             |
                             | No.    Signal  Description
                             |  1     HUP     Hangup
                             |  2     INT     Interrupt
                             |  3     QUIT    Quit
                             |  4     ILL     Illegal instruction
                             |  5     TRAP    Trae/breakpoint trap
                             |  6     ABRT    Aborted
                             |  7     BUS     Bus error
                             |  8     FPE     Floating point exception
                             |  9     KILL    Killed
                             | 10     USR1    user defined singal 1
                             | 11     SEGV    Segmentation fault
                             | 12     USR2    User defined signal 2
                             | 13     PIPE    Broken pip
                             | 14     ALRM    Alarm clock
                             | 15     TERM    Terminated
                             | 16     STKFLT  Stack fault
                             | 17     CHLD    Child exited
                             | 18     CONT    Continued
                             | 19     STOP    Stopped (signal)
-------------------------------------------------------------------------------
== Understanding User Management == 
  User and Group ID          |
    UID                      | * 0: root
                             | * 1 - 99: System
                             | * 100 - 499: System accounts
                             | * 1000 and above: Normal (unprivileged) accounts
    GID                      | * 0: root
                             | * 1 - 99: System Groups
                             | * 100 - 499: Dynamically allocated System Groups
                             | * 100 and above: Normal groups
                             |
  Display User Information   |
    whoami                   | returns username
                             |
    id <username>            | returns uid, gid, groups
                             |
    groups <username>        | returns list of 
                             |
    finger                   | returns username, full name, home directory
                             | default shell, last longin date time and location
                             | mail and plan status
                             |
  User and Group Database    | * Users and Passwords
  Files                      |   /etc/passwd
                             |   /etc/shadow
                             |
                             | * Groups
                             |   /etc/group
                             |
  /etc/passwd                | geeko:x:1000:1000:Geeko chameleon:/home/geeko:/bin/bash
                             | ` |    |   |     |       |              |          | `
                             |` Login |   |     |       |              |          |`
                             |` password  |     |       |              |          |                                              `
                             |`           |     |       |              |          |`
                             |` user Id --      |       |              |          |`
                             | `primary gid------       |              |          |`
                             | `Comments----------------               |          |` 
                             | `Home Directory-------------------------           |`
                             |` Default shell--------------------------------------`
                             |
  /etc/group                 |  `           video:x:33:geeko,tux`
                             |  `             |   |  |      |`
                             |  ` group Name--    |  |      |`
                             |  ` Group password--   |      |`
                             |  ` Group ID-----------       |`
                             |  ` Secondary members---------`
                             |
  C User Management          |
    useradd                  | create users
    adduser                  | interactively create users
    usermod                  | modify existing users
    userdel                  | delete users
                             |
    groupadd                 | create groups
    groupmod                 | modify existing groups
    groupdel                 | delete groups
                             |
    passwd                   | Set/Modify users passwords
    gpasswd                  | Set/Modify groups password
                             |
  File Permissions and       |
  Ownership                  |
                             |
                             |
                             |
-------------------------------------------------------------------------------
== Understanding ACLs ==
  Use ACLs                   | * To use ACLs you need to be familar with:
                             |   * How ACLs work
                             |   * ACL Terminology
                             |   * ACL Types
                             |   * How ACLs and Permission Bits map to each other
                             |   * Using ACL Command Line Tools
                             |   * Configuring a Directory with an Access ACL
                             |   * Configureing ad Directory with a Default ACL
                             |   * Using Additional setfacl Options
                             |   * ACL Check Algorithm
                             |   * How Applications Handle ACLs
                             |
  How ACLs work              | * ACLs provide an extension of the three traditional
                             |   Sets of permissions:
                             |   * Read (r)
                             |   * Write (w)
                             |   * Execute (x)
                             |
                             | * Applied to:
                             |   * Owner
                             |   * Group
                             |   * Others
                             |
                             | * ACLs allow you to assign permissions to individual users
                             |   or groups even if they are not the owner or a member of 
                             |   the owning group.
                             |
  ACL Types                  | * Two basic classes of ACLs:
                             |   * Minimal ACLs (for practical purposes: same as
                             |     POSIX permissions)
                             |
                             |   * Extended ACL
                             |
                             | * ACLs extend the classic Linux file permissions:
                             |   * Named user
                             |   * Named groups
                             |   * Mask
                             |
  ACL Terminology            | * Important ACL terms include:
                             |   * user classes
                             |     - Owner class
                             |     - Group class
                             |     - Other class
                             |   * Access ACL
                             |   * Default ACL
                             |   * ACL entry
                             |
  ACLs and Permisison Bits   | The following hsows the mapping of minial ACLs
                             |
                             |         owner     user::rw-        <----->     rw-     owner class
                             | owning groups    group:;r--        <----->     r--     group class
                             |         other    other::--         <----->     ---     other class
                             |
  all possible ACL Types     | TYPE           Text Form
                             | owner          user::rwx
                             | named user     user:<name>:rwx
                             | owning group   grous::rwx
                             | named group    group:<name>:rwx
                             | mask           mask::rwx
                             | other          other::rwx
                             |
  Effective Permissions      | In the following example, effective permissions for the user
                             | jane are shown:
                             |
                             | Entry Type       Text Form         Permissions
                             | Named user       user:jane:r-x     r-x
                             | mask             mask::rw-         rw
                             |          Effective permissions: r--
                             |
                             |         owner        user::rw-  <----->     rw-  owner class
                             |    named user    user:jane:rw-  <----->
                             | 
                             | owning groups       group:;r--  <----->     r--  group class
                             |         other       other::--   <----->     ---  other class
                             |
                             |
  Set ACL                    | setfacl [options][ACL-Entries] <file>
                             |   Option     Description
                             |   -m         Add or modify an ACL entry
                             |   -x         Remove an ACL entry
                             |   -d         Set a default ACL
                             |   -b         Remove all extended ACL entries
                             |   -M         restore ACLs that have been removed from a file
                             |
  GET ACL                    | getfacl [options][ACL-Entries] <file>
                             |   Option     Description
                             |   -a         Display the file access control list
                             |   -d         Display the default access control list
                             |   -R         List the ACLs of all files and directories recursively
                             |
  Define Extended ACLs:      | * Named user:
  Examples                   |   * setfacl -m u:tux:rx my_file
                             |
                             | * Named groups:
                             |   * setfacl -m g:accounting:rw my_file
                             |
                             | * Mask:
                             |   * setfacl -m m::rx
                             |
  Configure a Directory with | * Default ACLs for a directory define the access permissions
  Default ACLs               |   objects in the directory inherit when they are created:
                             |   * A subdirectory inherits the default ACL of the parent directory
                             |     as default ACLs and as its own access ACLs
                             |   * A file inherits the default ACL as its own access ACL
                             |
  Directory Default ACL      | * Add default ACLs to the existing mydir directory:
  Example                    |   * setfacl -d -m group:jungle:r-x mydir
                             |
  How Applications Handle    | * udev uses ACLs to allow users logged in to the graphical
  ACLs                       |   user interface to access devices, such as DVD drives
                             |
                             | * Some applications lack ACL Support
                             |   * Star Archiver is a backup application with full preservation
                             |     of ACLs, others may or may not preserve them
-------------------------------------------------------------------------------
== Understanding Privilege Delegation ==
  Identity switching commands| su - Switch user
                             |   * The "-" give use login shell and users default environment
                             |   * Execute a single command as root user, use the -c option
                             |     * e.g., su -c "grep geeko /et/shadow"
                             |
  Switching primary group    | newgrp, sg
                             |
  Configure sudo             | * Configuration file: /etc/sudoers
                             |
  General sytax (sudo)       |   <user/%group> <host> = <command1>[, <command2> ...]
                             |
                             | * User Example:
                             |   geeko ALL = /sbin/shutdown
                             |   geeko All = NOPASSWD: /sbin/shutdown
                             |
                             | * Group Example:
                             |   %admins = /sbin/shutdown
                             |
  sudo Aliases               | * User Alias:
                             |   User_Alias <ALIAS> = <user1>, [, <user2>, ...]
                             |   User_Alias POWERUSRS = tux, geeko
                             |
                             | * Command Alias:
                             |   Cmnd_Alias <ALIAS> = <command1>[, <command2>,...]
                             |   Cmnd_Alias KPROCS = /bin/kill, /usr/bin/killall
                             |
                             | * Host Alias:
                             |   Host_Alias <ALIAS> = <host1>[, <host2>, ...]
                             |   Host_Alias HOSTS = da1
                             |
                             | * Run as Alias
                             |   Runas_Alias <ALIAS> = <user1>[, <user2>,...]
                             |   Runas_Alias RUNASUSERS = tux, geeko
                             |
  Configure sudo Aliases     | * Syntax:
                             |   <User_alias> <Host_Alias> = (<user>) <Cmnd_Alias>
                             | * Example:
                             |   POWERUSERS HOSTS = (root) KPROCS 
                             |
                             |   User_Alias POWERUSRS = tux, geeko
                             |   Cmnd_Alias KPROCS = /bin/kill, /usr/bin/killall
                      ---->  |   Host_Alias HOSTS = da1
                             |   POWERUSRS HOSTS = (root) KPROCS
                             |
  Introduction to Polkit     | * Application framework
                             | * Negotiator between the unpriviledged user session and 
                             |   the privileged system context
                             | * Does not grant root permissions to an entire session,
                             |   but only to the action in question
                             | * Specifically targets applications in rich desktop
                             |   environments but also applies at the command line
                             | * Does not rely on special kernel features
                             |
    Privilege Delegation     | TRADITIONAL METHODS
                             |   * SUID/SGID
                             |     * No authentication required
                             |     * Entire application runs with privilege
                             |   * su
                             |     * Root password required to authenticat
                             |     * Entire shell and all its child processes run with privilege
                             |   * sudo
                             |     * User's password required to authenticate
                             |     * Entire applicaton runs with privilege
                             |
                             | PRIVILEGE DELEGATION
                             |   * PolKit
                             |     * User's password required to authenticat (at login time)
                             |     * Only certain, requested actions of application run 
                             |       with privilege
                             |
                             | Supported Appllications
                             |   * Pulseaudio
                             |   * Cups
                             |   * GNOME
                             |   * libvirt
                             |   * Polkit
                             |   * PackageKit
                             |   * System
                             |   * YaST
                             |
    PolKit Authorization     | ( The entities that the Mechanism wors with:
                             |   * Subject      - The "who" requesting the action
                             |   * Object       - The "what" that is being acted upon
                             |   * Action       - The "how" (what is requested to be done)
                             |
    List Registered Actions  | pkaction
                             |
    Authorization Types      | * Possible answers PolKit provides as to whether a 
                             |   process is entitled for a priviledged operation are:
                             |     * yes
                             |     * no
                             |     * authentication needed
                             | * Privileges
                             |     * Implicit (Default)
                             |       * Athentication
                             |       * One Shot Authentication
                             |       * Keep Session Authentication
                             |       * Keep Indefinitely Authentication
                             |     * Explicit
                             |
    Display Privileges       | pkaction -v -a org.freedesktop.login1.hibernate
                             |
    Default Privileges       | * For most desktop systems:
                             |   /etc/polkit-default-privs.standard
                             | * For machines administrated centrally (default)
                             |   /etc/polkit-default-privs.restrictive
                             | * For your own custom set of privileges:
                             |   /etc/polkit-default-privs.local
                             |
                             | Change default:
--------------------------------------------------------------------------------
== Understand Compiling Software from source ==
  Compile From Source Code   | * Lnux Source Code Build tools
                             | * Works well for a single
--------------------------------------------------------------------------------
== Understand Management of RPM Packages ==
  RPM Basics                 | * RPM Database
                             |   * works in the background of the Package Mananger
                             |   * Contains a list of all information on all installed RPM Packages.
                             |   * keeps track of all files that are changed and created when a user
                             |     installs a program
                             | * RPM Package Manager
                             |   * Utility that handles insalling and unistalling RPM packages
                             | * RPM Package
                             |   * Software packaged for easy installation into the system
                             |
  RPm Package Components     | * Information Header 
                             |   * CPIO Archive 
                             |   * GPG Signature
                             |   * Installation Scripts
                             |
                             |  `Rpm package naming: zypper-1.11.8-1.1.x86_64.rpm`
                             |  `                       |      |    |     |`
                             |  `Software Name-----------      |    |     |`
                             |  `Software Version---------------    |     |`
                             |  `Release Number----------------------     |`
                             |  `Architecture------------------------------`
                             |
                             |
  Install RPM Packages       | * Command: rpm -i <package>.rpm
                             | * Additional Options:
                             |   * -v (verbose) for more information
                             |   * - (hash) for a progress bar
                             | * In case of dependency conflicts or file problems:
                             |   * --nodeps to ignore dependencies
                             |   * --force to overwrite existing files
                             |
  Update RPM Packages        | * Update: rpm -U <package>.rpm
                             |   * works even if no previous version is installed
                             | * Freshen: rpm -f <package>.rpm
                             |   * works only if a previous version is installed
                             |
  Uninstall RPM Packages     | * Command: rpm -e <package>
                             | * Additional options:
                             |   * --nodeps to ignore dependencies
                             |
  Query RPM Database and     | Option         Description
  Packages                   | -q             Query RPM databask
                             | -p             Inspect not installed RPM archives
    Common query options     | -a             List all installed packages
                             | -i             List package information
                             | -l             Display file list
                             | -f <file>      find out which package the file belongs to
                             |                Must specify the full path
                             | -d             List only documentation files(implies -l)
                             | -c             List only configuration files (implies-l)
                             | --dump         Display a file list with complete details
                             |                used with -l, -c or -d
                             | --provides     List features of the package that another
                             |                package can request with --requires
                             | --requires, -R List capabilities the package requires
                             | --scripts      list installation scripts
                             |                Pre-install, post-install and un-install
                             | --changelog    Display detailed list of information about a
                             |                Specific package
                             |                Updates, ocnfiguration, modifications, etc.
                             |
  RPM Package Verification   | * Verify that the package has not changed since it was 
                             |   created
                             |   * rpm --checksig <package>.rpm
                             |
                             | * Verify integrity of files installed by an RPM package
                             |   * rpm -V <package>
                             |
                             | Characer   Description
                             | S          list package information
                             | M          Mode has changed
                             | 5          Size is different
                             | D          Device major/minor numbers are different
                             | L          Readlink (symbolic link) path mismatch
                             | U          User ownership differs
                             | G          Group ownership differes
                             | T          mtime differes
                             | P          Capabilities differ
-------------------------------------------------------------------------------
== Understanding Software Management with Libzypp ==
  What is Libzypp            | * Libzip is a wrapper around the rpm system
                             |
  what are softeware repo?   | * Directories that contain RPM software packages and meta-data
                             |   files
                             | * Can be accessed by RPM meta-managers
                             | * Can be accessed from different media and local file systems
                             |
  The 4 "P"s of Libzypp      | * Packages
                             |   * RPM packages (including patch/delta RPMs)
                             |   * Contain files to be installed in file system
                             | * Patterns
                             |   * Reference 1 or more packages
                             |   * Typically install all packages needed for a certain server 'role'
                             | * Products
                             |   * Contain 1 or more patterns
                             |   * Associated with a product with its own support and maintenance
                             |     such as an Extension / Add-on
                             | * Patches
                             |   * Reference 1 or more update packages
                             |     (packages provided as both full and patch/delta RPMs
-------------------------------------------------------------------------------
== Understanding Networt Manaement with SLE ==
  ping                       | -c count
                             | -I interface
                             | -i seconds
                             | -f     
                             |
  Network Related            | * Network interface configuration files:
  Configuration files        |   * /etc/sysconfig/network
                             | * Name Resolution
                             |   * Systems's hostname: /etc/hostname
                             |   * Name resolution locally: /etc/hosts
                             |   * DNS Servers: /etc/resolve.conf
                             |   * Order of name resolution services: /etc/nsswitch.conf
                             |
  SUSE sysconfig Network     | * Sytax: <command> <interface>
  Commands                   | * Bring a configured network interface up:
                             |   * ifup eth0
                             | * Bring a configured network interface down:
                             |   * ifdown eth0
                             | * Renew DHCP IP Address
                             |   * ifrenew eth0
                             | * Display information about a configured network inteface
                             |   * ifstatus eth0
                             |
  Address Configuration      | * Syntax
                             |   * ip [address|add|a] <task> <arguments>
                             | * Display IP Address configuration:
                             |   * ip addr show
                             | * Add an IP address to an interface:
                             |   * ip addr add 10.0.0.10/24 brd + dev eth0
                             | * Remove an IP address from an interface:
                             |   * ip addre del 10.0.0,10/24 dev eth0
                             |
  Route Configuration        | * Syntax: ip [route|r] <task> <arguments>
                             | * Display routing table
                             |   * ip route show
                             | * Add a route to the local network
                             |   * ip route add 172.17.0.0/16 dev eth0
                             | * Add a route to a different network:
                             |   * ip route add 192.168.1.0/24 via 172.17.1.1
                             | * add a default route:
                             |   * ip route add default via 172.17.2.2
                             | * Delete a route
                             |   * ip route delete 192.168.1.0/24 dev eth0
                             |
  Link Configuration         | * Syntax: ip [link|l] <task> <arguments>
                             | * Display link level configuration
                             |   * ip link show
                             | * Bring an interface up:
                             |   * ip link set eth0 up
                             | * Bring an interface down:
                             |   * ip link set eth0 down
                             | * Change the MAC address of an interface:
                             |   * ip link set eth0 addr 00:11:22:AA:BB:CC
                             | * Rename a network interface:
                             |   * ip link set eth0 name penth0
                             |
  Ethernet Configuration     | * Syntax: ethtool <options> <interface>
                             | * Display configuration of an interface
                             |   * ethtool eth0
                             | * Change link speed of an interface:
                             |   * ethtool -s speed 1000 eth0
                             | * Disable link auto-negotioantion on an interface
                             |   * ethtool autoneg=off eth0
                             | * Force full duplex on an interface:
                             |   * ethtool duplex full eth0
  
  Bridge Configuration       | * Syntax: brctl <action> <arguments>
                             | * Display currently configured bridges:
                             |   * brctl show
                             | * Create a new bridge:
                             |   * brctl addbr br1
                             | * Add an interface t oa bridge:
                             |   * brctl addif br1 eth1
                             | * Remove and interface from a bridge:
                             |   * brctl delif br1 eth1
                             | * Remove an existing bridge:
                             |   * brctl delbr br1
                             |

  Configure Network Interface

                                `---------------`
                                `|   Server1    |                 -------------`
                                `|              |                 |           |`
    Basic Network Interface     `|           eth0-----------------|   LAN     |`
                                `|              |                 |           |`
                                `|           eth1                 |           |`
                                `|              |                 -------------`
                                `----------------`
                             | * Associated with physical network devices such as Ethernet and wireless
                             | * network interfaces are persistently named using udev.
                             | * Can have more than one IP address bout to it without needing to create
                             |   alias interfaces (i.e. eth0:1, etho0:2, ...)


                                `---------------`
                                `|   Server1    |                 -------------`
                                `|              |                 |           |`
    Bonded Network Interface    `|           eth0-----------------|   LAN     |`
                                `|      bond0   |                 |           |`
                                `|           eth1-----------------|           |`
                                `|              |                 -------------`
                                `----------------`
                             | * Virtual network interface comprised of 1 or more physical network devices
                             | * Used for fault tolerance and / or link aggregation
                             | * The bonding driver can bon the interfaces using different methods called modes


                                `---------------`
                                `|   Server1    |                 -------------`
                                `|    vlan100   |                 |           |`
    VLAN Network Interface      `|           eth0-----------------|   LAN     |`
                                `|    vlan101   |                 |           |`
                                `|           eth1                 |           |`
                                `|              |                 -------------`
                                `----------------`
                             | * Virtual network interface that tags all packets that pass through it with 802.11q tagging
                             | * VLAN interfaces are configured on and communicate throug ha physical network interfaces

                                `---------------`
                                `|   Server1    |                 -------------`
                                `|              |                 |           |`
    Network Bridge              `|         0|eth0-----------------|   LAN     |`
                                `|         r|   |                 |           |`
                                `|         b|eth1                 |           |`
                                `|              |                 -------------`
                                `----------------`
                             | * Virtual network interface that allows multiple ntwork 
                             |   interfaces to communicate in a single broadcaset domain
                             | * All interfaces attached to the bridge function as switch ports
                             | * The SUSE sysconfig tools allow you to define bridges in the same manner

  Basic Network Inteface:    | * in /etc/sysconfig/network
    Config File              | * Typically named ifcfg-ethX (X for the interface name)
                             |

                  `BOOTPROTO='static'`                  `BOOTPROTO='static'`
                  `IPADDR1='10.0.0.1'`                  `IPADDR1='10.0.0.1/24'`
                  `NETMASK='255.255.255.0'`             `IPADDR2='10.1.0.1/16'`
                  `IPADDR2='10.1.0.1'`                  `STARTMODE='AUTO'`
                  `NETMASK2='255.255.0.0'`              `USERCONTROL='no'`
                  `STARTMODE='AUTO'`                    `MTU=''`
                  `USERCONTROL='no'`
                  `ETHTOOL_OPTIONS=''`
                  `MTU=''`

  Persistent Network         | * /etc/udev/rules.d/70-persistent-net.rules
  Interface Names            |
                             | `SUBSYSTEM=="net", ACTION=="add", DRIVES=="?*",`
                             | `ATTR{ADDRESS}=="00:15:c5:55:0c:a8", ATTR{type}=="1"`
                             | `Kernel=="eth*", NAME="eth0"`
-------------------------------------------------------------------------------
== Understand firewalld ==
  firewalld                  | * SLE 15 introduced firewalld as the new software firewall.
                             |   This also caused necessary changes to installatin and
                             |   system management wit YaST and AutoYaST.
                             |
                             | yest firewalld provides a command-line interface
                             | (firewalld-cmd) and a graphical interface(firewall-config)
                             | for configuration
                             |   * YaST CLI and GUI for SuSEFirewall2 had been largely removed in
                             |     SLE 15.0
                             |     > A new GUI for YaST (yast2-firewall) has since been created and 
                             |       now used instead of firewall-config
                             |
                             | AutoYaST: AutoYaST profiles based on SuSEFirewall2 do not fit with
                             | the firewalld configuration
                             |   * A new AutoyaST schema for configuring firewalld was needed 
                             |
  firewalld                  | An importand concept of firewalld is the distinction between two
                             | separete configurations, the runtime and the permanent
                             | configurations.
                             |   * Runtime - represents the currently active rules.
                             |     * Allows for temporary rules that can be discarded after firewalld is
                             |       restarted
                             |     * Allows for experimentation with nre rulls while being about to revert.
                             |   * permanent - represents the the saved rules that will be applied when
                             |     restarting firewalld
                             |
  firewalld-cmd              | Firewall-cmd is the command-line tool for manipulating firewalld
                             |   * Defaults to the runtime configuration
                             |   * Can add --permanent to apply to permanent configuration
                             |     * Won't take affect until firewalld is reloaded / restarted
                             |
                             |   * Can push all runtime rules to permanent with -runtime-to-permanent
                             |
                             |   * firewalld-cmd --reload and systemctl reload firewalld will revert to
                             |     the permanent configurationk
                             |
                             | You can list all network interfaces currently assigned to zone:
                             | * root # firewall-cmd --zone=public --list-interfaces
                             |
                             | you can add an interface to a zond*, or change its zone:
                             | * root # firewall-cmd --zone=internal --add-interface=eth0
                             | * root # firewall-cmd --zone=internal --change-interface=eth0
-------------------------------------------------------------------------------
== Recogize Traditional Linux File Systems ==
  Supported Filesystems      | * Ext2
                             | * Ext3 (default in SLE11)
                             | * Ext4
                             | * XFS (default in SLE 12 for data partitions)
                             | * Reiser FS (default in SLE10)
                             | * Btrfs (default in SLE10 for / )
                             | * JFS (existing volumes only)
                             | * NTFS-3G (only in SLED)
                             | * VFAT
                             |
  File System Health Tools   | df           Reports file system disk space usage
                             | du           Estimate file space usage
                             | lsof         List Open files
                             | fuser        Displays the PIDs of processes using the specified files
                             | fsck         Check and optionally repair Linux file systems
                             | e2fsck
                             | xfs_check
                             | resize2fs    ext2/ext3/ext4 file systems
-------------------------------------------------------------------------------
== Section 11 - Storage Administration ==
  Linux IO Stack
    File System Mount Layer       FHS (Files & Directories)
    File System Layer             Cluster Files System  |  Traditional Files Systems  |  Btrfs
    Block Device layer            Block Device Files
    Logical storage Layer             Device-maper     MD
                                  MPIO | DM-RAID| LVM

  Local Disks                |
    Tools to configure MBR   | - YaST
    and GPT                  | - fdisk
                             | - parted
                             |
  Mount Options for mount    | Option             Description                                          Mount  fstab
  and /etc/fstab             | remount            File system can be mounted more than once              X      X
                             | rw, ro             Files ystem is writeable or read-only                  X      X
                             | sync, async        Synchronous or asynchronous input and output           X      X
                             | atime, noatime     Access time of a files is updated or not               X      X
                             | nodev, dev         Device files from being interpreted as such or not     X      X
                             | noexec, exec       Prohibit the execution of programs or not              X      X
                             | nosuid, suid       Ignore SUID and SGID bits or not                       X      X
                             | auto, noauto       Mount files system automatically or not                       X
                             | user, nouser       Allow user to mout files system or not                        X
                             | defaults           rw, suid, dev, exec, auto ,nousr, async                       X
                             |
  Currently Mounted File     | * Command:         - mount
  Systems                    | * Files:           - /etc/mtab
                             |                    - /proc/mounts
                             |

== Configure Logical Volume Management ==
                             |
  Create LVM Physical Volumes| * Syntax: pvcreate /dev/<device>
                             | * Partitions can be used directly
                             |
                             | To use a complete disk, delet partition table in MBR:
                             |   * dd if=/dev/zero of=/dev/<device> bs=512 count=1
                             |
  View LVM Physical Volume   | pvscan             Detect physical volumes and volume group
  Info                       |                    membership
                             | pvs                View attributes of physical volumes
                             | pvdisplay          View attributes of physical volumes
                             | pvhange [-ay|-an]  Activate/Deactivate physical volumes
                             |
  Create and Activate LVM    | vgcreate     Create a volume group
  Volume Groups              | vgscan       Discover and list volume groups
                             | vgchange     Activate/Deactivate a volume group
                             |
                             |
                             |
-------------------------------------------------------------------------------
Notes - 
  Package Manager: zypper
  Install command: zypper in <package name> 
