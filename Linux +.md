--------------------------------------------------------------------------------
= CompTia Linux + =
--------------------------------------------------------------------------------
== General Notes ==
  visudo                    | * Specific versions of vi intended to edit
                            |   /ect/sudoers file
--------------------------------------------------------------------------------
== Linux Filesystem Hierarchy Standard ==
  Linux directories defined  |
  by the FHS                 |
                             |
  /bin                       | Contains binary commands for use by all users (on
                             | most Linux systems, this directory is a shortcut
                             | to /usr/bin)
                             |
  /boot                      | Contains the Linux kernel and files used by the
                             | boot laoader
                             |
  /dev                       | Contains device files
                             |
  /etc                       | Contains system-specific configuration files
                             |
  /home                      | Is the default location for user home directories
                             |
  /lib                       | Contains shared program libraries (used by the
                             | commands in /bin and /sbin) as well as kernel
                             | modules
                             |
  /media                     | A director that containes subdirectories used for
                             | accessing (mounting) filesystems on removable
                             | media devices such as floppy disks, DVDs, and USB
                             | flash drives
                             |
  /opt                       | Stores additional software programs
                             |
  /proc                      | Contains process and kernel information
                             |
  /root                      | Is the root user's home directory
                             |
  /sbin                      | Contains system binary commands (used for
                             | administration)
                             |
  /sys                       | Contains configuration information for hardward
                             | devices on the system
                             |
  /tmp                       | Holds temporary files create by programs
                             |
  /usr                       | Contains most system commands and utilities -
                             | contains the following directories
                             |
                             | /usr/bin - User binary commands
                             | /usr/games - Educational programs and games
                             | /usr/include - C program header files
                             | /usr/lib - Libraries
                             | /usr/local - Local programs
                             | /usr/sbin - System binary commands
                             | /usr/share - Files that are architecture independent
                             | /usr/src - Source code
                             | /usr/X11R6 - The X Window System (somtimes
                             |              replaced by /etc/X11)
                             |
  /usr/local                 | Is the location for most additional programs
                             |
  /var                       | Contains log files and spools
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== File Redirection ==
  Redirecting only errors    | 2>   Overwrite all content with error stream
                             | 2>>  Appending error stream
                             |
--------------------------------------------------------------------------------
== Managing Users and Groups ==
=== Types of users ===
  root                       | User ID: 0
                             | Group ID: 0
                             | Home Dir: /root
                             | Shell: /bin/bash
                             |
  Regular                    | User ID: 1000 to 60000
                             | Group ID: 1000 to 60000
                             | Home Dir: /home/username
                             | Shell: /bin/bash
                             |
  Service                    | User ID: 1 to 999
                             | Group ID: 1000 to 60000
                             | Home Dir: /var/ftp, etc
                             | Shell: /sbin/nologin
                             |
=== Users ===
  adding users               | useradd
                             |    -c (comment)
                             |    -e (expriration date) 2021/01/30
                             |    -s set default shell
                             |    -d set home directory
                             |
  removing users             | userdel
                             |    -r removes all user files
                             |
  Moddifying users           | usermod
                             |    -c add comment
                             |    -l change login name
                             |    -a append user to group (only use with -G flag)
                             |
  set or change exp date     | chage [options] LOGIN
  on user password           |    -l displays current password settings
                             |
  location of default user   | /etc/skel/
  settings (new user)        |
                             |
                             | /etc/login.defs
                             |
                             | /etc/defaul/
                             |
                             | /etc/passwd
                             |
  how to read the values     | username:!!(date):(pass min age):(pass max age):(days before warning)
  on the shadow passwd       |
                             |
  Change users defaul shell  | chsh
                             |
=== Groups ===
  creating a group           | groupadd
                             |
  delete  a group            | groupdel
                             |
  modify a group             | groupmod
                             |    - n modify the name
                             |    - groupmod -n <newname> <old name>
                             |
  Add user to group          | gpasswd -a <user name> <group>
                             |
  remove user from group     | gpasswd -d <user name> <group>
                             |
  Check group membership     | id <user name>
                             |
  Assign group administrator | gpasswd -A <user name> <group>
                             |
--------------------------------------------------------------------------------
== Files types ==
  Regular file: -            | Normal files such as text, data, or executable
  Directory:    d            | Files which are lists of other files
  Link:         l            | A shortcut which points to the location of the actual file
  Special file: c            | A mechanism which is used for input and output, such as files in /dev
  Socket:       s            | A special file which provides inter-process networking protected by the system's access control
  Pip:          p            | A special file which allows processes to communicate with each other without using network socket semantics
                             |
--------------------------------------------------------------------------------
== File Access & Permission ==
  change file permissions    | chmod
                             |
  umask                      | /etc/profile 0 default location for umask
                             |
  chown                      | change the user and group of a file
--------------------------------------------------------------------------------
== Linking Files ==
  Understanind how files     | To better understand how files are linked, you
  are linked                 | must understand how files are stored on a
                             | filesystem. On a structural level, a filesystem
                             | has three main sections:
                             |   * Superblock
                             |   * Inode table
                             |   * Data blocks
                             |
  Superblock                 | The superblock is the section that contains
                             | information about the filesystem in general,
                             | such as the number of inodes and data blocks, as
                             | well as homw much data a data block stores
                             |
  Inode table                | The inode table consists of several inodes
                             | (information nodes); each inode describes one file
                             | or directory on the filesystem, and contains a
                             | unique inode number for identification. What is
                             | more important, the inode stores information such
                             | as the file size, data block locations, last date
                             | modified, permissions, and ownership. When a file
                             | is deleted, only its inode (which serves as a
                             | pointer to the actual data) is deleted.
                             |
  Data blocks                | The data that makes up the contents of the file
                             | as well as the filename are stored in data blocks,
                             | which are feferenced by the inode. In filesystem-
                             | neutral terminology, blocks are known as allocation
                             | units because they are the unit by which disk space
                             | is allocated for storage
                             |
  Hard-Linked files          | Hard-linked files share the same inode and inode
                             | number. As a result, they share the same inode
                             | number and data blocks, but the data blocks allow
                             | for multiple filenames. Thus, when one hard-linked
                             | file is modified, the other hard-linked files are
                             | updated as well.
                             |
  Symboli links              | Symbolic links are different from hard links because
                             | they do not share the same inode and data blocks with
                             | their target file; one is merely a pointer to the
                             | other, thus both files have different sizes. The data
                             | blocks in a symbolically lined file contain only
                             | the pathname ot the target file. When a user edits
                             | a symbolically linked file, she is actually editing
                             | target file. Thus, if the target file is deleted,
                             | the symbolic link serves no function.
                             |
--------------------------------------------------------------------------------
== Special Permissions ==
  Setting special permissions| You set special permissions with the *chmod* command.
                             | The first octet is used to seth the one or more
                             | options:
                             | Read, write, and execute are the regular file
                             | permissions that you would use to assign security
                             | to files; however, you can optionally use three
                             | more special permissionson files and directories:
                             |
                             | * SUID (set User ID)
                             | * SGID (set Group ID)
                             | * Sticky bit
                             |
  SUID                       | The SUID has not special function when set on a
                             | directory; however, if the SUID is set on a file
                             | and that file is executed, the person who executed
                             | the file temporarily becomes the owner of the file
                             | while it is executing. Many commands on a typical
                             | Linux system have this special permission set; the
                             | passwd command that is used to change your password
                             | is one such file.
                             |
  SGID                       | The SGID has a function when applied to both files
                             | and directories. Just as the SUID allows regular
                             | users to execute a binary copiled program and
                             | become the owner of the file for the duration of
                             | execution, the SGID allows regular users to
                             | execute a binary compiled program and become a
                             | member of the group that is attached to the file.
                             | When a user creates a file, recall that the user's
                             | name and primary group become the owner and group
                             | owner of the file, respectively. However, if a user
                             | creates a file in a directory that has the SGID
                             | permission set, that user's name become the owner
                             | of the file and the directory's group become the
                             | group owner of the file.
                             |
  Sticky Bit                 | The sticky bit was used on files in the past to
                             | lock them in memory; however, today the sticky bit
                             | performs a useful function only on directories. As
                             | explained earlier in this chapter, the write
                             | permission applied to a directory allows you to
                             | add and remove any file to and from that directory.
                             | Thus, if you have a write permission to a certain
                             | directory but no permission to files with it, you
                             | could delete all of those files. Consider a company
                             | that requires a common directory that gives all
                             | employees the ability to add files; this directory
                             | mustgive everyone the write permission. Unfortunately,
                             | the write permission also gives all employees the
                             | ability to delet all files and directories within,
                             | including the ones that others have added to the
                             | directory. If the sticky bit is applied to this
                             | common directory in addition to the write permission,
                             | employees can add files to the directory but only
                             | delete those fils that they have added and not others
                             |
                             | the math is the same as when setting read, write,
                             | and execute permissions with the *chmod* command
                             |
                             | examples:
                             |
                             |   chmod 4755 foo.txt  ->  sets the SUID, U+rwx, G+rx, O+rx
                             |   chmod 5740 foo.txt  ->  sets the SUID+Sticky Bit, U+rwx, G+r, O nothing
                             |
                             | YOu can also use symbols to set special permissions
                             | on a file or directory.
                             |
                             |   chmod u+s,g+s foo.txt  -> add the SUID and the SGID to the file
                             |   chmod o+t              -> add the sticky bit to file
                             |
--------------------------------------------------------------------------------
  == ACL ==
  Setting Custom Permissions | An access control list (ACL) is a list of users
  in the Access Control      | or groups that you can assign permissions to.
  list (ACL)                 | The default ACL used in Linux consists of three
                             | entities: user, group, and other. However, there
                             | may be situations where you need to assign a
                             | specific set of permissions on a file or directory
                             | to an individual user or group.
                             |
  Set File Access Control    |
  List *setfacl*               | setfacl -m u:bob:r-- foo.txt  -> sets read permissions for bob
                             | setfacl -m g:smbusers:rwx ./foodir/  -> sets read,write,execute permissions for the subusers' group
                             |
  View ACL Specific          | when using *ls -l*, additional *acl* permissions
  permissions                | will appear as an additional *+* symbol at the
                             | end of the permissions list
                             |
                             |   > *ls -l* foo.txt
                             |       -rw-rw----+   1 user1    acctg    0 May 2 22:01 foo.txt
                             |
    getfacl                  | *getfacl* command will display the additional
                             | permissions.
                             |
--------------------------------------------------------------------------------
== Managing Filesystem Attributes ==
                             | As with the Windows Operating system, Linux has
                             | file attributes that can be set, if necessary.
                             | These attributes work outside Linux permissions
                             | and are filesystem-specific. This section for the
                             | ext4 filesystem that you can configure
                             |
  lsattr (list attributes)   | > lsattr foo.txt
                             |     --------------e----  foo.txt
                             |
                             | By default, all files have the *e* attribute,
                             | which writes to the file in "extent" blocks
                             | (rather than immediately in a byte-by-byte fasion).
                             | If you would like to add or remove attributes,
                             | you can use the chattr (change attributes) command
                             | The following example assigns the immutable (i) to
                             | the foo.txt file and displays the results:
                             |
                             | > *chattr* +i foo.txt
                             |     ----i---------e----  foo.txt
                             |
                             | The immutable attribure is the most commonly used
                             | filesystem attribure and prevents the file from
                             | being modified in any way. Because attributes are
                             | applied at the filesystem level, not even the root
                             | user can modify a file that has the immutable
                             | attribute set.
                             |
                             | (a full listing of filesystem attributes can be
                             |  viewed in the *chattr* man page)
                             |
--------------------------------------------------------------------------------
== Disk Partitinns and File System ==
  Logical Volumes            |
--------------------------------------------------------------------------------
== Locating & Manipulating Files ==

  find                       | find / -name kemit.txt 2>/dev/null
  (redirect errors)          |
                             |
    based on permisions      | find /usr/bin -perm +rwx
                             |
  locate (searches the       | locate
  mlocate database)          |
                             |
--------------------------------------------------------------------------------
== Boot Process & Kernel ==
                             |
--------------------------------------------------------------------------------
== Introduction to Linux & the Command Line ==
Managing Users and Groups
File Access and Permissions
Disk Partitions & File Systems
Logical Volumes and Fielsystem Hierachy
Using vi/vim to Edit files

=== Configureing the Linux Kernel ===
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
== Managing Services ==
  == Configuring Services with systemd ==
  Unit file location         | /lib/systemd/system
                             |
--------------------------------------------------------------------------------
