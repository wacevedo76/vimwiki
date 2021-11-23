--------------------------------------------------------------------------------
  Prerequisets               | httpd php
                             | gcc glib glibc-common > tools to compile Nagios
                             | gd gd-devel > GNU debugger and libraries
                             |
  Add nagios user            | useradd -m nagios
      and group              | groupadd nagcmd
                             | usermod -a -G nagcmd nagios
                             | usermod -a -G nagcmd apache
                             |
  Download nagios core       |
                             |
  Compile                    | ./config --with-command-group=nagcmd
                             | make install-commandmode
                             |
  modify the config file     | vi /usr/local/nagios/etc/objects/contacts.cfg
                             |
                             |
                             |
                             |
                             |
                             |
                             |

