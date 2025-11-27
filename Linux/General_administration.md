# General Linux Administration
## xdg-utils
  The `xdg-utils` package commonly used to to control the applications, files, or directories that are set as default applications set by the user or the desktop enviornment.  
### Configure Default Applications
To configure the default applications used to open files based on their extensions, you need to set the MIME type associations. This can bedone using the `xdg-mime` command or by editing the configuration files directly.  
#### Method 1: Using the `xdg-mime`
1. Determine the MIME type of a file:
  ```bash
  xdg-mime query filetype <file>
  ```
  For example, to find the MIME type of a PDF file:
  ```bash
  xdg-mime query filetype example.pdf
  ```
2. Set the Default Application for a MIME type:
  ```bash
  xdg-mime default <application.desktop> <MIME_type>
  ```
  For example, to set the default application for PDF files to `evince`:
  ```bash
  xdg-mime default evince.desktop application/pdf
  ```
#### Method 2: Edition Configuration Files
The default applications are usually configured in .desktop files and MIME type association files. Here are the typical locations:

1. User-Specific Settings:
  * ~/.config/mimeapps.list
  * ~/.local/share/applications/mimeapps.list
2. System-Wide Settings:
  * `/etc/xdg/mimeapps.list`
  * `/usr/share/applications/`  

To set a default application, edit the mimeapps.list file and add an entry for the MIME type and the corresponding .desktop file.

##### Example: Editing mimeapps.list

## Configuring Encrypted Drives to automount at boot

  Crucial Security Warning: This method requires storing a decryption key on the main
  drive. If your Debian system's root partition (/) is not encrypted, this key
  will be readable by anyone with physical access to that drive.

  Method: crypttab and fstab with a Keyfile

  This is the standard Debian method for automated decryption.

  1. Create a Secure Keyfile

  This key will unlock your drives. These commands create the key and make it readable
  only by the root user.

   1 `sudo dd if=/dev/urandom of=/root/luks_drives.keyfile bs=4096 count=1`
   2 `sudo chmod 600 /root/luks_drives.keyfile`

  2. Add the Keyfile to Your LUKS Drives

  You must add this new keyfile as a valid way to unlock each encrypted partition.
  First, find your device names with sudo lsblk -f. They will be like /dev/sdb1,
  /dev/sdc1, etc.

  For each of your two drives, run the following, replacing /dev/sdXn with the correct
  device name. You will be prompted for your existing passphrase for each command.

   1 # Run this for your first drive
   2 `sudo cryptsetup luksAddKey /dev/sdXn /root/luks_drives.keyfile`
   3
   4 # Run this for your second drive
   5 `sudo cryptsetup luksAddKey /dev/sdYn /root/luks_drives.keyfile`

  3. Get the UUID for Each Encrypted Partition

  Using UUIDs is safer because device names like /dev/sdb1 can change.

   1 `sudo blkid /dev/sdXn /dev/sdYn`
  Copy the UUID="..." value for each of your two LUKS partitions.

  4. Configure Automatic Unlocking in `/etc/crypttab`

  This file tells the system to unlock the devices at boot using your keyfile.
  Edit it with sudo nano /etc/crypttab and add two lines like these.

   * Give each drive a unique <target_name> (e.g., hdd1_crypt, hdd2_crypt).
   * Use the UUIDs you copied.
   * The path to the keyfile is absolute.

   ```
   1 # <target_name>  <source_device>                            <key_file>              <options>
   2 hdd1_crypt       UUID=YOUR_FIRST_DRIVE_UUID_HERE          /root/luks_drives.keyfile luks
   3 hdd2_crypt       UUID=YOUR_SECOND_DRIVE_UUID_HERE         /root/luks_drives.keyfile luks
   ```

  5. Create Mount Points

  These are the directories where your decrypted drives will appear.

   1 `sudo mkdir /mnt/data1`
   2 `sudo mkdir /mnt/data2`

  6. Configure Automatic Mounting in `/etc/fstab`

  This file mounts the unlocked devices to the directories you just created.
  Edit it with sudo nano /etc/fstab and add two lines.

   * The device path is /dev/mapper/<target_name>.
   * Replace <filesystem_type> with your actual filesystem (e.g., ext4, xfs).
   * nofail is critical; it prevents the system from failing to boot if a drive
      is not connected.

   ```
   1 # <file system>              <mount point>  <type>  <options>         <dump> <pass>
   2 /dev/mapper/hdd1_crypt       /mnt/data1     ext4    defaults,nofail   0      2
   3 /dev/mapper/hdd2_crypt       /mnt/data2     ext4    defaults,nofail   0      2
   ```

  7. Test Without Rebooting

  It is critical to test your configuration before you reboot the remote machine.

    1 # Reload system configurations
    2 `sudo systemctl daemon-reload`
    3
    4 # Manually start the decryption for your targets
    5 `sudo cryptdisks_start hdd1_crypt`
    6 `sudo cryptdisks_start hdd2_crypt`
    7
    8 # Mount all devices listed in fstab
    9 `sudo mount -a`
   10
   11 # Verify that the drives are mounted correctly
   12 `df -h`

  If df -h shows your drives mounted at /mnt/data1 and /mnt/data2, the setup is
  correct. You can now safely reboot your remote machine.
