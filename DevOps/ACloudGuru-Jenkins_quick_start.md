---------------------------------------------------- to load folds:  :loadview -
= A Cloud Guru - Jenkins Quick Start =
--------------------------------------------------------------------------------
== Installation and Configuration ==
  Retrieve latest repos      | sudo wget -O /etc/yum.repos.d/jenkins.repo \
  (Redhat, Centos, etc)      |   https://pkg.jenkis-ci.org/redhat/jenkins.repo
                             |
  Retrieve associated key    | sudo rpm --import https://jenkins-ci.org/redhad/jenkins-ci.org.key
                             |
  Update package manager     | sudo yum update
                             |
  Install                    | sudo yum install jenkins
                             |
  (Jenkins relies on Java)   |
                             |
  (open 8080 on firewall)    |
                             |
  *NOTE:* if you are working   | (install nginx)
  in an environment which    | Modify the nginx config file (/etc/nginx/nginx.conf)
  restricts access to 8080,  |
  you can use nginx as a     | location / {
  proxy                      |     *proxy_pass  http://127.0.0.1:8080;*  <- line to add
                             | }
                             |
  (on Redhat variants,       | *if* getenforce -> # Enforcing
   configure SELinux)        | # setenforce 0  (then restart nginx)
                             |
  to permanently change      | (make sure SELinux tools are installed)
  SELinux policy             | yum install -y setroubleshoot-server selinux-policy-devel
                             |
  Check SELinux policy       | # sepolicy network -t http_port_t
                             |   (if 8080 isn't on the list of allowed ports)
                             | # semanage port -a -t http_port_t -p tcp 8080
                             |
--------------------------------------------------------------------------------
== Preparing Our Environment -Build Accounts ==
  the Jenkins user acc does  | set shell in /etc/passwd
  not have a default shell   |
                             |
  Give the Jenkins user a    |
  password (if it doesn't    |
  have one)                  |
                             |
  It is advisable to give    | # visudo  ->
  the jenkins user NOPASSWD  |   ## Allow root to run any commands anywhere
  root privilages            |   root    ALL=(ALL)     ALL
  (allows jenkins to run     |   *jenkins ALL=(ALL)     NOPASSWD:  ALL*
   builds without entering   |
   a password)               |
                             |
  Generate ssh-keys for the  | (since the jenkins user does not have a default
  Jenkins user and copy the  |  home directory, you will copy the ssh pub key
  keys to local host         |  to local host)
                             |
                             | ssh-copy-id localhost
                             |
                             |
--------------------------------------------------------------------------------
== Plugin Management and Builds ==
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
== Creating Scheduled Builds ==
                             |
--------------------------------------------------------------------------------
== Setting UP a Build Slave ==
                             |
--------------------------------------------------------------------------------
== Launching Jobs on the Slave Node ==
                             |
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
