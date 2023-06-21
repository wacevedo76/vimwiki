--------------------------------------------------------------------------------
= Firewalld =
--------------------------------------------------------------------------------
== General Commands ==
  List zones                 | firewall-cmd --get-zones
                             |
  List services associated   | firewall-cmd --list-all (default zone is public)
  with zones                 |
                             | firewall-cmd --zone=external --list-all (specify exteranl zone)
                             |
  Change default zone        | firewall-cmd --set-default={zonename}
                             |
  *Allow and deny by service*  |
                             |
    Add a service            | firewall-cmd --zone=external --add-service=ftp (not permanent)
                             | firewall-cmd --permanent --zone=external --add-service=ftp (permanent)
                             |
                             |
    Remove a service         | firewall-cmd --zone=external --remove-service=ftp
                             |
    Check enabled services   | firewall-cmd --zone=external --list-services
    by zone                  |
                             |
    Reload firewall          | firewall-cmd --reload
    configuration            |
                             |
  *Allow and deny by port*     | firewall-cmd --permanent --zone=external --add-port=60001/udp (portnumber/protocol)
                             | firewall-cmd --permanent --zone=external --remove-port=60001/udp
                             |
--------------------------------------------------------------------------------
