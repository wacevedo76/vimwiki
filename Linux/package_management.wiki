--------------------------------------------------------------------------------
= Linux Package Management =
--------------------------------------------------------------------------------
== Centos ==
  Correct mirror issue       | sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*
                             | sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*
                             |
                             |
                             |
                             |
