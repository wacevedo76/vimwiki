--------------------------------------------------------------------------------
Debian specific settings
--------------------------------------------------------------------------------
* Debian 11
* setting up static ip
                             | auto enp0s3
                             | iface enp0s3 inet static
                             | address 192.168.2.2
                             | netmask 255.255.255.0
                             | gateway 192.168.2.2
                             | dns-nameservers 8.8.4.4 8.8.8.8
                             |
  install debian package     | dpkg -i {package name}
    need Dependencies        | apt -f install
                             |
