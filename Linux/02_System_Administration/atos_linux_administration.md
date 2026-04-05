# Atos Linux Administration Course

## Introduction to Linux & the Command Line
Linux is an open-source Unix-like operating system based on the Linux kernel. The command line interface (CLI) provides powerful tools for system administration.

### Basic Commands
```bash
# Navigation
pwd          # Print working directory
ls           # List directory contents
cd           # Change directory

# File Operations
cp           # Copy files
mv           # Move/rename files
rm           # Remove files
mkdir        # Create directory
rmdir        # Remove directory

# File Viewing
cat          # Concatenate and display files
less         # View file contents page by page
head         # Show first lines of file
tail         # Show last lines of file

# System Information
uname -a     # Show system information
whoami       # Display current user
date         # Show current date and time
```

### Command Line Basics
- **Shell**: Interface between user and kernel (bash, zsh, fish)
- **Prompt**: Indicates shell is ready for commands (`$` for user, `#` for root)
- **Arguments**: Options passed to commands (`-l`, `--help`)
- **Pipes**: Connect command output to input (`|`)
- **Redirection**: Control input/output (`>`, `>>`, `<`)

## Manage Users & Groups

### User Management
```bash
# Add user
useradd username
adduser username  # Interactive version

# Set password
passwd username

# Modify user
usermod -aG groupname username  # Add to group
usermod -s /bin/bash username   # Change shell
usermod -L username            # Lock account
usermod -U username            # Unlock account

# Delete user
userdel username
userdel -r username  # Remove home directory too

# User information
id username
who
w
```

### Group Management
```bash
# Create group
groupadd groupname

# Add user to group
gpasswd -a username groupname

# Remove user from group
gpasswd -d username groupname

# Delete group
groupdel groupname

# List groups
groups username
getent group
```

### Configuration Files
- `/etc/passwd` - User account information
- `/etc/shadow` - Encrypted passwords
- `/etc/group` - Group definitions
- `/etc/gshadow` - Group passwords
- `/etc/skel/` - Skeleton directory for new users

## Files Access & Permissions

### Permission Types
- **Read (r)**: 4 - View file contents or list directory
- **Write (w)**: 2 - Modify file or create/delete in directory
- **Execute (x)**: 1 - Run file or access directory

### Permission Classes
- **User (u)**: File owner
- **Group (g)**: Members of file's group
- **Others (o)**: Everyone else

### Permission Commands
```bash
# View permissions
ls -l
stat filename

# Change permissions (symbolic)
chmod u+x filename      # Add execute for user
chmod g-w filename      # Remove write for group
chmod o=r filename      # Set others to read-only
chmod a+rx filename     # Add read/execute for all

# Change permissions (numeric)
chmod 755 filename      # rwxr-xr-x
chmod 644 filename      # rw-r--r--
chmod 600 filename      # rw-------

# Change ownership
chown user:group filename
chown user filename
chgrp group filename

# Special permissions
chmod +s filename       # Set SUID/SGID
chmod +t directory      # Sticky bit
```

### Default Permissions (umask)
```bash
# View current umask
umask

# Set umask
umask 022    # Default: files 644, directories 755
umask 027    # More restrictive: files 640, directories 750
```

## Disk Partitions & File Systems

### Partition Types
- **Primary**: Up to 4 per disk (or 3 primary + 1 extended)
- **Extended**: Container for logical partitions
- **Logical**: Created within extended partition

### Partition Tools
```bash
# View partitions
fdisk -l
lsblk
parted -l

# Create partitions (using fdisk)
fdisk /dev/sda
# Commands: n (new), d (delete), p (print), w (write), q (quit)

# GPT partitions (using gdisk)
gdisk /dev/sda
```

### File System Types
- **ext4**: Default for most Linux distributions
- **XFS**: High-performance journaling filesystem
- **Btrfs**: Copy-on-write with advanced features
- **ZFS**: Combined filesystem and volume manager
- **FAT32/VFAT**: Compatibility with Windows
- **NTFS**: Windows filesystem (read/write via ntfs-3g)

### Creating File Systems
```bash
# Create filesystem
mkfs.ext4 /dev/sda1
mkfs.xfs /dev/sda2
mkfs.btrfs /dev/sda3

# Label filesystem
e2label /dev/sda1 "boot"
xfs_admin -L "data" /dev/sda2
```

### Mounting File Systems
```bash
# Manual mount
mount /dev/sda1 /mnt/data

# Mount with options
mount -t ext4 -o defaults,noatime /dev/sda1 /mnt/data

# Unmount
umount /mnt/data

# View mounted filesystems
mount
findmnt
df -h
```

### /etc/fstab Configuration
```
# device    mountpoint    fstype    options    dump    pass
/dev/sda1   /boot         ext4      defaults   0       2
/dev/sda2   /             ext4      defaults   0       1
/dev/sda3   /home         ext4      defaults   0       2
/dev/sdb1   /mnt/data     xfs       defaults   0       2
```

## Logical Volumes & Filesystem Hierarchy

### LVM Components
- **Physical Volume (PV)**: Disk or partition
- **Volume Group (VG)**: Pool of physical volumes
- **Logical Volume (LV)**: Allocated space from volume group

### LVM Commands
```bash
# Physical Volume
pvcreate /dev/sdb
pvdisplay
pvs

# Volume Group
vgcreate vg_data /dev/sdb
vgdisplay
vgs
vgextend vg_data /dev/sdc

# Logical Volume
lvcreate -L 10G -n lv_home vg_data
lvcreate -l 100%FREE -n lv_data vg_data
lvdisplay
lvs
lvextend -L +5G /dev/vg_data/lv_home

# Resize filesystem (ext4 example)
resize2fs /dev/vg_data/lv_home
```

### Filesystem Hierarchy Standard (FHS)
- **/** - Root directory
- **/bin** - Essential user binaries
- **/boot** - Boot loader files
- **/dev** - Device files
- **/etc** - Configuration files
- **/home** - User home directories
- **/lib** - Essential shared libraries
- **/media** - Removable media mount points
- **/mnt** - Temporary mount points
- **/opt** - Optional application software
- **/proc** - Process and kernel information
- **/root** - Root user home
- **/run** - Runtime variable data
- **/sbin** - System administration binaries
- **/srv** - Service data
- **/sys** - Kernel and system information
- **/tmp** - Temporary files
- **/usr** - User programs and data
- **/var** - Variable data (logs, spool, etc.)

## Using vi/vim to Edit Files

### Vim Modes
- **Normal mode**: Navigation and commands (press `Esc`)
- **Insert mode**: Text entry (press `i`, `a`, `o`)
- **Visual mode**: Text selection (press `v`, `V`, `Ctrl+v`)
- **Command-line mode**: Enter commands (press `:`)

### Basic Navigation
```vim
h    # Left
j    # Down
k    # Up
l    # Right
w    # Next word
b    # Previous word
0    # Beginning of line
$    # End of line
gg   # First line
G    # Last line
:10  # Go to line 10
```

### Editing Commands
```vim
i    # Insert before cursor
a    # Insert after cursor
o    # Insert new line below
O    # Insert new line above
x    # Delete character
dd   # Delete line
yy   # Yank (copy) line
p    # Paste after cursor
P    # Paste before cursor
u    # Undo
Ctrl+r # Redo
```

### Search and Replace
```vim
/pattern   # Search forward
?pattern   # Search backward
n          # Next match
N          # Previous match
:%s/old/new/g   # Replace all
:10,20s/old/new/g # Replace in lines 10-20
```

### Saving and Exiting
```vim
:w        # Save
:wq       # Save and quit
:q        # Quit (if no changes)
:q!       # Quit without saving
:w newfile # Save as newfile
```

## Locating & Manipulating Files

### Finding Files
```bash
# Find by name
find / -name "filename"
find /home -iname "*.txt"  # Case-insensitive

# Find by type
find / -type f             # Files
find / -type d             # Directories
find / -type l             # Symbolic links

# Find by size
find / -size +100M         # Larger than 100MB
find / -size -1k           # Smaller than 1KB

# Find by time
find / -mtime -7           # Modified in last 7 days
find / -atime +30          # Accessed more than 30 days ago

# Find by permissions
find / -perm 644
find / -perm /u=s          # SUID files

# Execute commands on found files
find /tmp -name "*.tmp" -delete
find /var/log -name "*.log" -exec cp {} /backup/ \;
```

### Locate Command
```bash
# Update database
updatedb

# Find files
locate filename
locate -i "*.conf"        # Case-insensitive
locate -c "*.py"          # Count matches
```

### Which/Whereis/Whatis
```bash
which ls          # Shows path to executable
whereis ls        # Shows binary, source, and manual
whatis ls         # Shows one-line description
```

## Searching & Manipulating File Contents

### grep - Pattern Searching
```bash
# Basic search
grep "pattern" filename
grep -i "pattern" filename  # Case-insensitive
grep -v "pattern" filename  # Invert match
grep -r "pattern" /path     # Recursive
grep -l "pattern" *.txt     # List files containing pattern

# Extended regular expressions
grep -E "pattern1|pattern2" filename
egrep "pattern1|pattern2" filename

# Context
grep -B 3 "pattern" filename  # 3 lines before
grep -A 3 "pattern" filename  # 3 lines after
grep -C 3 "pattern" filename  # 3 lines before and after
```

### sed - Stream Editor
```bash
# Substitute text
sed 's/old/new/' filename
sed 's/old/new/g' filename  # Global replacement
sed 's/old/new/2' filename  # Replace 2nd occurrence

# Delete lines
sed '5d' filename           # Delete line 5
sed '1,10d' filename        # Delete lines 1-10
sed '/pattern/d' filename   # Delete lines matching pattern

# Print specific lines
sed -n '10,20p' filename    # Print lines 10-20
sed -n '/pattern/p' filename # Print matching lines

# In-place editing
sed -i 's/old/new/g' filename
sed -i.bak 's/old/new/g' filename  # Create backup
```

### awk - Text Processing
```bash
# Print columns
awk '{print $1}' filename          # First column
awk '{print $1, $3}' filename      # First and third columns
awk -F: '{print $1}' /etc/passwd   # Custom delimiter

# Conditional processing
awk '$3 > 1000 {print $1}' /etc/passwd
awk '/pattern/ {print $0}' filename
awk 'NR == 5' filename             # Line number 5

# Calculations
awk '{sum += $1} END {print sum}' filename
awk '{print NR ": " $0}' filename  # Add line numbers
```

### cut - Column Extraction
```bash
cut -d: -f1 /etc/passwd      # First field with colon delimiter
cut -c1-10 filename          # Characters 1-10
cut -f1,3 -d, filename.csv   # First and third fields
```

### sort - Sorting
```bash
sort filename                # Alphabetical sort
sort -n filename             # Numerical sort
sort -r filename             # Reverse sort
sort -u filename             # Unique lines
sort -k2 filename            # Sort by second column
sort -t: -k3 -n /etc/passwd  # Sort by third column numerically
```

### uniq - Unique Lines
```bash
sort filename | uniq         # Remove duplicates
uniq -c filename             # Count occurrences
uniq -d filename             # Show duplicates only
uniq -u filename             # Show unique only
```

## Boot Process & Kernel

### Linux Boot Process
1. **BIOS/UEFI** - Hardware initialization
2. **MBR/GPT** - Boot loader location
3. **GRUB2** - Boot loader menu
4. **initrd/initramfs + Kernel** - Initial RAM disk and kernel load
5. **systemd** - First process (PID 1) and service manager

### Boot Loader (GRUB2)
```bash
# Configuration files
/boot/grub2/grub.cfg        # Main configuration (generated)
/etc/default/grub           # User configuration
/etc/grub.d/                # Script directory

# Update GRUB
grub2-mkconfig -o /boot/grub2/grub.cfg
update-grub                  # On Debian/Ubuntu

# Boot into single-user mode
# Add "single" or "systemd.unit=rescue.target" to kernel line
```

### Kernel Modules

#### Module Locations
```
/usr/lib/modules/$(uname -r)/  # Primary location
/lib/modules/$(uname -r)/      # Alternative location
/etc/modprobe.d/               # Module configuration
```

#### Module Commands
```bash
# List loaded modules
lsmod

# Load module
insmod module.ko
modprobe module_name

# Remove module
rmmod module_name
modprobe -r module_name

# Module information
modinfo module_name

# List module parameters
modprobe -c | grep module_name
```

#### Module Configuration
```bash
# Blacklist module (prevent loading)
echo "blacklist module_name" > /etc/modprobe.d/blacklist.conf

# Module options
echo "options module_name param=value" > /etc/modprobe.d/module_name.conf
```

### Kernel Parameters
```bash
# View all parameters
sysctl -a

# View specific parameter
sysctl kernel.hostname

# Set temporarily
sysctl -w kernel.hostname="newhost"

# Set permanently
echo "kernel.hostname = newhost" >> /etc/sysctl.conf
sysctl -p  # Apply changes
```

### Common Kernel Parameters
```bash
# Security
kernel.exec-shield=1
kernel.randomize_va_space=2

# Network
net.ipv4.ip_forward=1
net.ipv4.tcp_syncookies=1

# Memory
vm.swappiness=10
vm.vfs_cache_pressure=50

# Filesystem
fs.file-max=65536
fs.inotify.max_user_watches=524288
```

## Graphical User Interfaces

### Display Servers
- **X11/X.Org** - Traditional display server
- **Wayland** - Modern display server protocol

### Desktop Environments
- **GNOME** - Default for many distributions
- **KDE Plasma** - Feature-rich, customizable
- **XFCE** - Lightweight, traditional
- **LXQt/LXDE** - Very lightweight
- **MATE** - GNOME 2 fork
- **Cinnamon** - Linux Mint default

### Display Manager (Login Manager)
- **GDM** - GNOME Display Manager
- **SDDM** - Simple Desktop Display Manager (KDE)
- **LightDM** - Lightweight, cross-desktop
- **XDM** - X Display Manager

### X11 Configuration
```bash
# Configuration file
/etc/X11/xorg.conf
/etc/X11/xorg.conf.d/

# Generate configuration
Xorg -configure  # Creates xorg.conf.new

# Test configuration
X -config xorg.conf.new

# Display information
xrandr
xrandr --output HDMI-1 --auto --right-of eDP-1
```

### Wayland
```bash
# Check if using Wayland
echo $XDG_SESSION_TYPE

# Wayland compositors
weston        # Reference compositor
mutter        # GNOME's compositor
kwin_wayland  # KDE's compositor
sway          # i3-compatible Wayland compositor
```

## Managing Services

### Systemd Service Management
See detailed systemd documentation in `systemd.md`

### Traditional Init Scripts