--------------------------------------------------------------------------------
# Ansible
--------------------------------------------------------------------------------
## Installation 
Extra Packages for           | yum list epel-release
Enterpise Linux (EPLE)       |
                             |
Primary configuration file   | /etc/ansible/ansible.cfg
                             |   (this configuration file describes where the
                             |    the other config files are located)
                             |
--------------------------------------------------------------------------------
## Misc commands 
                             |
Running ansible plays        | ansible-playbook myplaybook.yml
                             | ansible-playbook myplaybook.yml --syntax-check
                             | ansible-playbook myplaybook.yml --list-hosts
                             | ansible-playbook myplaybook.yml --list-tasks
                             |
--------------------------------------------------------------------------------
## Ansible Architecture 
  Ansible Inventory          | The Ansible inventory is a file or script that
                             | will provide the details about the managed nodes,
                             | including the hostname, connection methods,
                             | credentials to use and many other details
                             |
                             | It is possible to pass the inventory to Ansible
                             | using static inventory files, dynamic inventory
                             | scripts, or using the Configuration managment
                             | database (CMDB)
                             |
  Ansile Plugins             | Ansible plugins are small pieces of code that
                             | help to enable a flexible and expandable
                             | architechture.
                             |
                             | There are different types of of plugins in
                             | Ansible such as:
                             |   * Connection plugins,
                             |   * Action plugins,
                             |   * Become plugins,
                             |   * Inventory plugins
                             |
  Ansible modules            | An Ansible module is a piece of reusable and
                             | standalone script that can be used to achieve
                             | some specific tasks.
                             |
                             | An Ansible module is a piece of reusable and
                             | standalone cripts that can be used to achieve
                             | some specific taksks. Modules provide a defined
                             | interface with options to accept arguments and
                             | return information to Ansible in JSON format.
                             |
  Ansible content collections| Ansible modules are separated from the Ansible
                             | base and distributed as *Ansible content collections*
                             | or simply *Ansible Collections*
                             |
  Ansible playbook           | The Ansible playbook is a simple file written in
                             | YAML format with the instruction list of
                             | automation tasks.
                             |
                             | Example:
                             |
                             |           Playbook
                             |` ---`
                             |` - name: Enable Intranet Services            | # First play`
                             |`   hosts: node1                              |`
                             |`   become: yes                               |`
                             |`     tasks:                                  |`
                             |`     - name: Install httpd package           | #   First task`
                             |`       yum:                                  |`
                             |`         name: httpd                         |`
                             |`         state: latest                       |`
                             |`     - name: Start httpd service             | #   Second task`
                             |`         name: httpd                         |`
                             |`         enabled: true                       |`
                             |`         state: started                      |`
                             |`                                             |`
                             |` - name: Test intranet web server            | # Second play`
                             |`   hosts: localhost                          |`
                             |`   become: no                                |`
                             |`   tasks:                                    |`
                             |`     - name: connect to intranet webserver   | #   First task in second play`
                             |`       uri:                                  |`
                             |`         url: http://node1                   |`
                             |`         status_code: 200`
                             |
--------------------------------------------------------------------------------
## Documentation 
  Built-in Ansible document- | ansible-doc -s <module name>
  ation                      |
                             |
  List all available modules | ansible-doc -l
                             |
--------------------------------------------------------------------------------
## Inventory Files 
                             | * and ini like format to define target hosts
                             |   it is simplay a list of services
                             |
  Default inventory file     | /etc/ansible/hosts
                             |
  Grouping servers together  | * servers can be grouped together my surrounding
                             |   the group name with "[]" example:
                             |
                             | [mail]                 <-- group name
                             | server3.company.com    <-- Server under [mail]
                             | server4.company.com    <-- Server under [mail]
                             |
                             | or
                             |
                             | server[2:3].company.com  <-patters which covers
                             |                            server2 and server3
                             |
                             |
                             | [db]                   <-- group name
                             | server5.company.com    <-- Server under [db]
                             | server6.company.com    <-- Server under [db]
                             |
                             | [web]                  <-- group name
                             | server5.company.com    <-- Server under [web]
                             | server6.company.com    <-- Server under [web]
                             |
  A group of groups          | [all_servers:children] <-- group name:specify children
                             | mail                   <-- child of "all_servers"
                             | db                     <-- child of "all_servers"
                             | web                    <-- child of "all_servers"
                             |
  Inventory host aliases     | <alias>  ansible_host=<server ip or hostname>
                             |
                             | web      ansible_host=server1.conpany.com
                             | db       ansible_host=server2.company.com
                             | mail     ansible_host=server3.company.com
                             | web2     ansible_host=server4.company.com
                             |
  Define connetion type      | <alias>  ansible_host=<server ip or hostname> ansible_connection=<connection type>
                             |
                             | web      ansible_host=server1.conpany.com ansible_connection=ssh
                             | db       ansible_host=server2.company.com ansible_connection=winrm
                             | mail     ansible_host=server3.company.com ansible_connection=ssh
                             | web2     ansible_host=server4.company.com ansible_connection=winrm
                             |
  Other parameters           | * ansible_port - 22/5986
                             | * ansible_user - root/administrator
                             | * ansible_ssh_pass - Password
                             |
 Check connectivity to host  | > ansible <target host name> -m ping -i <inventory file>   <-- -m for module
                             | > ansible target01 -m ping -i inventory.txt
                             |
--------------------------------------------------------------------------------
## Yaml 
                             | <-- whitespace is used to help define structure
  Key Value Pair             | key: value  # example ->
                             | Fruit: Apple
                             | Vegetable: Carrot
                             | liquid: water
                             |
  Array / List               | <array name>:
                             | -   list_item_1
                             | -   list_item_2
                             | -   list_item_3
                             |
  Dictionary / Map           | <map name>:
                             |     key01: value01
                             |     key02: value02
                             |     key03: value03
                             |
--------------------------------------------------------------------------------
## Playbooks 
  * Playbook - A single YAML file
    * Play - Defines a set of activities (task) to be run on hosts
      * Task - An action to be performed on the host
        > Execute a command
        > Run a script
        > Install a package
        > Shutdown / Restart
  Example playbook:

  # Simple Ansible Playbook1.yml
  -
    name: Play 1
    hosts: localhost
    tasks:
      - name: Execute command 'date'
        command: date

      - name: Execute script on server
        script: test_script.sh

      - name: Install httpd service
        yum:
          name: httpd
          state: present

      - name: Start web server
        service:
          name: httpd
          state: started
                             |
--------------------------------------------------------------------------------
## Playbook Format 
    Example:

      # Simple Ansible Playbook1.ymp
      -                                    <-- Defines beginning of play
        name: Play 1                       <-- Name of play
        hosts: localhost                   <-- host (local host or from Inventory file)
        tasks:                             <-- start task list
          - name: Execute command 'date'   <-- name of task
            command: date                  <-- Ansible module

          - name: Execute script on server <-- name of task
            script: test_script.sh         <-- Ansible module

      -                                    <-- Defines beginning of play
        name: Play 2                       <-- Name of play
        hosts: localhost                   <-- host (local host or from Inventory file)
        tasks:                             <-- start task list
          - name: Install httpd service    <-- name of task
            yum:                           <-- Ansible module
              name: httpd
              state: present

          - name: Start web server         <-- name of task
            service:                       <-- Ansible module
              name: httpd
              state: started
   Execute Ansible Playbook  | > ansible-playbook playbook.yml
                             |
--------------------------------------------------------------------------------
## Running Ansible commands 
  One-offs (syntax)          | ansible <hosts> -a <command>
                             | ansible all -a "/sbin/reboot"
                             |
                             | ansible <hosts> -m <module>
                             | ansible target01 -m ping
                             |
  Playbooks                  | ansible-playbook <playbook name> -i <inventory file>
                             |
  Dry run                    | ansible-playbook <playbook name> -i <inventory file> --check
                             |
  Retry                      | If a playbook fails, a retry file is generated and
                             | contains the list of hosts where the playbook failed
                             | playbook-name.retry
                             |
                             | The file may be specificed using --limit with
                             | the same playbook to reattempt that playbook at
                             | a later time
                             |
  filter                     | Allows you to filter through setup to extract
                             | specific information (accepts regular expressions)
                             |
                             | example
                             | ansible server-02.com -m setup -a filter=*ipv4* <= returns all
                             |                                                  lines containing ipv4
--------------------------------------------------------------------------------
## Ad-hoc commands 
  Ad-hoc command syntax      | ansible <HOSt> -b -m <MODULE> -a "<ARG1 ARG2 ARG3>"
                             |
  Important flags            | -b   => become (without argument, default is root)
                             | -m   => module
                             | -a   => Module arguments
  examples                   |
    Install softare          | ansible centos7-02 -b -m yum -a "name=httpd state=latest"
                             |   (the '-b' flag is for 'become', default state is root
                             |
    Modify service state     | ansible centos7-02 -b -m service -a "name=httpd state=started"
                             |
                             |
--------------------------------------------------------------------------------
## Modules 
  System                     | - User
                             | - Group
                             | - Hostname
                             | - Iptables
                             | - Lvg
                             | - Lvol
                             | - Make
                             | - Mount
                             | - Ping
                             | - Timezone
                             | - Systemd
                             | - Service
                             | - setup     <- Pulls system information from tartget host (ansible facts)
                             |
  Commands                   | - Command
                             | - Expect
                             | - Raw
                             | - Script
                             | - Shell
                             |
  Files                      | - Acl
                             | - Archive
                             | - Copy
                             | - File
                             | - Find
                             | - Lineinfile
                             | - Replace
                             | - Stat
                             | - Template
                             | - Unarchive
                             |
  Database                   | - Mongodb
                             | - Mssql
                             | - Mysql
                             | - Postgresql
                             | - Proxysql
                             | - vertica
                             |
  Cloud                      | - Amazon
                             | - Atomic
                             | - Azure
                             | - Centrylink
                             | - Cloudscale
                             | - Cloudstack
                             | - Digital Ocean
                             | - Docker
                             | - Google
                             | - Linode
                             | - Openstack
                             | - Sartos
                             | - Softlayer
                             | - VMware
                             |
  Windows                    | - Win_copy
                             | - Win_command
                             | - Win_domain
                             | - Win_file
                             | - Win_iis_website
                             | - Win_msg
                             | - Win_package
                             | - Win_ping
                             | - Win_path
                             | - Win_robocopy
                             | - Win_regedit
                             | - Win_shell
                             | - Win_service
                             | - Win_user
--------------------------------------------------------------------------------
## Variables 
  Variables are defined      | * Variable names should be letters, numbers and
  as key-value pairs         |   underscores. Tey should always start with a letter
                             |
                             | * Variables can be scoped by group, host, or
                             |   within a playbook
                             |
                             | * Variables may be passed in via command line
                             |   using the --extra-vars, the -e flag, or defined
                             |   within a playbook
                             |
                             | Examples:
                             |   ansible-playbook service.yml -e \
                             |   "target_hosts=localhost \
                             |   target_service=httpd";
                             |
                             | * Variables are referenced using double curly braces
`                             |   hosts: "{{ my_host_var }}"`
                             |
                             | # Sample Ansible Playbook1.yml
                             | -
                             |   name: Add DNS server to resolv.conf
                             |   hosts: localhost
                             |   vars:
                             |     dns_server: 10.1.250.10
                             |  tasks:
                             |     - lineinfile:
                             |         path: /etc/resolv.com
 `                            |          line: 'nameserver {{ dns_server }}'`
                             |           <-- variables are called within double brackets
                             |
  register                   | In Ansible, any play can 'register' a variable and
                             | once registered, that variable will be available
                             | to all subsequent tasks
                             |
                             | - shell: my_command_here
                             |   register: my_command_result
                             |
                             | Later, you can access stdout and stderr with
                             |   my_command_result.stdout
                             |   my_command_result.stderr
                             |
                             |
  Environment variables      | If you need to set some environment variables for
                             | your remote user accoutn, you can do that by adding
                             | lines to the remote user's .bash_provile
                             |
                             | - name: Add an environment variable to the remote user's shell
                             |   lineinfile:
                             |     dest: ~/.bash_profile
                             |     regexp: '^ENV_VAR='
                             |     line: "ENV_VAR=value'
                             |
                             | - name: Get the value of the environment variable we just added
                             |   shell: 'source ~/.bash_profile && echo $ENV_VAR'              <-- environment variables can only be used by the shell module
                             |   register: foo                                                 <-- using the register option to store the variables value
                             |
                             | - name: Print the value of the environment variable
                             |   debug:
                             |     msg: "The variable is `{{ foo.stdout }}`"                   <-- using the stored register value from the previous task
                             |
                             | Linux will also read global environment variables added to /etc/environment
                             |
                             | - name: Add a global environment variable
                             |   lineinfile:
                             |     dest: /etc/environment
                             |     regexp: '^ENV_VAR='
                             |     line: "ENV_VAR=value"
                             |   become: yes
                             |
  Per-task environment vars  | You can also set the environment for just one
                             | task, using the *environment* option for that task
                             |
                             | Example:
                             | - name: Download a file, using example-prox as a proxy
                             |   get_url:
                             |     url: http://www.example.com/file.tar.gz
                             |     dest: ~/Downloads
                             |   environment:
                             |     http_proxy: http://example-proxy:80/
                             |
                             | or you can pass an environment in va a variable in
                             | via a variable in your playbooks' *vars* secont
                             |
                             | Example:
                             |
                             | vars:
                             |   proxy_vars:                  <---
                             |     http_proxy: http://example-proxy:80/
                             |     https_proxy: https://example-proxy:443/
                             |
                             | tasks:
                             | - name: Download a file, using example-proxy as a proxy
                             |   get_url:
                             |     url: http://www.example.com/file.tar.gz
                             |     dest: ~/Downloads/
                             |   environment: proxy_vars      <----
                             |
                             | If a proxy needs to be set system-wide (as is the
                             | case behind many corporate firewalls), it can be
                             | done using the global /etc/environment file
                             |
                             | Example:
                             |
                             | # In the *vars* section of the playbook (set to 'absent' to remove):
                             | proxy_state: present
                             |
                             | # In the 'tasks' secon of the playbook:
                             | - name: Configure the proxy
                             |   inlinfile:
                             |     dest: /ect/environment
                             |     `regexp: "{{ item.regexp }}"`
                             |     `line: "{{ item.line }}"`
                             |     `state: "{{ proxy_state }}"`
                             |   with_items:
                             |     - regexp: "^http_proxy="
                             |       line: "http_proxy=http://example-proxy:80/"
                             |     - regexp: "^https_proxy="
                             |       line: "https_proxy=https://example-proxy:443/"
                             |     - regexp: "^ftp_proxy="
                             |       line: "ftp_proxy=http://example-proxy:80/"
                             |
--------------------------------------------------------------------------------
## Imports and Includes 
  Including var files        | - hosts: all
                             |
                             |   vars_files:
                             |     - vars.yml
                             |
    Import tasks             | tasks:
                             |   -import_tasks: imported-tasks.yml
                             |
    Import task with vars    | tasks:
                             |   - import_tasks: user.yml
                             |     vars:
                             |       username: johndoe
                             |       ssh_private_keys:
                             |         - { src: /path/to/johndoe/key1, dest: id_rsa }
                             |         - { src: /path/to/johndoe/key2, dest: id_rsa_2 }
                             |
                             |   - import_tasks: user.yml
                             |     vars:
                             |       username: janedoe
                             |       ssh_private_keys:
                             |         - { src: /path/to/johndoe/key1, dest: id_rsa }
                             |         - { src: /path/to/johndoe/key2, dest: id_rsa_2 }
                             |
    Dynamically Include      | - include_tasks: log_paths.yml
    tasks                    |
                             |
  Dynamic includes           | # Include extra tasks file, only if it's present at runtime
                             | - name: Check if extra_tasks.yml is present
                             |   stat:  `                                   +-- `with *stat*
                             |     path: tasks/extra-tasks.yml             |   Check this file and
                             |   register: extra_tasks_file          <-----+   save the results in this variable
                             |   connection: local
                             |
                             |  ...
                             |
                             | - include_tasks: tasks/extra-tasks.yml
                             |   when: extra_tasks_file.stat.exists        <-- Check to see if the file exists
                             |
  Handler Imports            | Handlers:
                             |   - import_tasks: handlers.yml
                             |
  Playbook imports           | - hosts: all
                             |   remote_user: root
                             |
                             |   tasks:
                             |     [...]
                             |
                             | - *import_playbook*: web.yml
                             | - *import_playbook*: db.yml
                             |
--------------------------------------------------------------------------------
  ## Playbook - beyond basics 
  When                       | One of the most helpful extr keys you can add to
                             | a play is a *when* statement. Lets take a look at
                             | a simple use of when:
                             |
                             | - yum: name=mysql-server state=present
                             |   when: (is_db_server is defined) and is_db_server
                             |
                             | *when* is even more powerful if used in
                             | conjunction with variables registered by previous
                             | tasks. As en example we want to check the status
                             | of a running application:
                             |
                             | - command: my-app --status
                             |   register: myapp_result
                             |
                             | - command: do-something-to-my-app
                             |   when: "'ready' in myapp_result.stdout"
                             |
  changed_when and           | It is difficult for Ansible to determin if a
  failed_when                | given command results in changes, so if you use
                             | the command or shell module without also using *
                             | changed_when*, Ansible will always report a
                             | change.
                             |
                             | - name: Install dependencies via Composer.
                             |   command: "/usr/local/bin/composer global require phhunit/phpunit --prefer-dist"
                             |   register: composer
                             |   changed_when: "'Nothing to install' not in composer.stdout"
                             |
                             | Many command-line utilities print results to
                             | stderr instead of stdout, so *failed_when* can be
                             | used to tell Ansible when a taks has actuall
                             | failed and is not jut reporting its results in
                             | the wrong way.
                             |
                             | - name: Import a Jenkins job via CLI
                             |   shell: >
                             |     java -jar /opt/jenkins-cli.jar -s http:/localhost:8080/
                             |     create-job "My Job" < /usr/local/my-job.xml
                             |   register: import
                             |   failed_when: "import.stderr and 'exists' not in import.stderr"
                             |
  ignore_errors              | add this to the task:
                             | ignore_erros: true
                             |
  Delegation                 | Some tasks, like sending a notification,
                             | communicatng with load balancers, or making
                             | changes to DNS, netwokring, or monitoring
                             | servers, require Ansible to run the task on the
                             | host machine (running the playbook) or another
                             | host besides the one(s) being managed by the
                             | playbook
                             |
                             | - name: Add server to Munin monitoring configuration
                             |   command: monitor-server webservers `{{ inventory_hostname }}`
                             |   delegate_to: "`{{ monitoring_master }}`"
                             |
                             | or
                             |
                             | - name: Remove server from load balancer
                             |   command: remove -from-lb `{{ inventory_hostname }}`
                             |   delegate_to: 127.0.0.1
                             |
  Local Actions              | - name: Remove server from load balancer
                             |   local_action: command remove-from-lb `{{ inventory_hostname }}`
                             |
  Pausing playbook execution | You might also user *local_action* in the middle
  with *wait_for*              | of a playbook to wait for a freshly-
                             | bootedserver or application to start listening
                             | on a particular port:
                             |
                             | - name: Wait for web server t ostart
                             |   local_action:
                             |     module: wait_for
                             |     host: "`{{ inventory_hostname }}`"
                             |     port: "`{{ webserver_port}}`"
                             |     delay: 10
                             |     timeout: 300
                             |     state: started
                             |
                             | *wait_for* can be used to pause your playbook
                             | execution to wait for many different things:
                             |
                             | * Using hosts and port, wait a maximum of *
                             | timeout* seconds for the port to be available (or not)
                             |
                             | * Using *path* (and *search_regex* if desired),
                             | wait a maximum of *timeout* seconds for the file
                             | to be present (or absent)
                             |
                             | * Using *host* and *port* and *drained* for the *
                             | state* parameter. Check if a given port has
                             | drained all its active connections
                             |
                             | * Using *delay*, you can simply pause playbook
                             | execution for a given amount of time (in seconds)
                             |
  Running an entire playbook | ansible-playbook test.yml --conection=local:
  locally                    |
                             | ---
                             | - hosts: 127.0.0.1
                             |   gather_facts: no
                             |
                             |   tasks:
                             |     - name: Check the current system date.
                             |       command: date
                             |       register: date
                             |
                             |     - name: Print the current system date.
                             |       debug:
                             |         var: date.stdout
                             |
  Prompts                    | You may require the user to enter the value of a
                             | variable that will be used in the playbook,
                             | use *vars_prompt*
                             |
                             | ---
                             | - hosts: all
                             |
                             | vars_prompt:
                             |   - name: share_user
                             |     prompt: "What is your network username?"
                             |
                             |   - name: share_pass
                             |     prompt: "What is your network password?"
                             |     private: yes
                             |
                             | Here area few special options you can add to prompts
                             | * *private*: If set to *yes*, the user's input
                             |   will be hidden on the command line
                             | * *default*: You can set a default value for the
                             |   prompt, to save time for the end user
                             | * *encrypt / confirm / salt_size*: These values
                             | can be set for passwords so you can verify the
                             | entry (the user will have to enter the password
                             | twice if confirm is set to yes), and encrypt it
                             | using a salt (with the specified size and crypt
                             | scheme).
                             |
  Tags                       | Tags allow you to run (or exclude) subsets of a playbook's tasks
                             |
                             | ---
                             | # You can apply tags to an entire play
                             | - hosts: webservers
                             |   tags: deploy
                             |
                             |   roles:
                             |     # Tags applied to a role will be appliedto tasks in the role
                             |     - role: tomcat
                             |       tags: ['tomcat', 'app']
                             |
                             |   tasks:
                             |     - name: Notify on completion.
                             |       local_action:
                             |         module: osx_say
                             |         msg: "`{{ inventory_hostname }}` is finished!"
                             |         voice: Zarvox
                             |       tags:
                             |         - notifications
                             |         - say
                             |
                             |     - import_tasks: foo.yml
                             |       tags: foo
                             |
      Exlude tags            | ansible-playbook tags.yml --skip-tags "notifications"
                             |
      Adding multiple tags   | # Shorthand list syntax
                             | tags: ['one', 'two', 'three']
                             |
                             | # Explicit list syntax
                             | tags:
                             |   - one
                             |   - two
                             |   - three
                             |
      Apply tags to a play   | ansible-playbook tags.yml --tags "tomcat,say"
                             |
  Blocks                     | Blocks allow you to group related tasks together
                             | and aply particular task parameters on the block
                             | level.
                             |
                             | ---
                             | - hosts: web
                             |   tasks:
                             |     # Install and configure Apache on REHL/CentOS hosts
                             |     - block:
                             |         - yum: name=httpd state=present
                             |         - template: src=httpd.conf.js dest=/etc/httpd/conf/httpd.conf
                             |         - service: name=httpd state=started enabled=yes
                             |       when: ansible_os_family == 'RedHat'
                             |       become: yes
                             |
                             |     # Install and configure Apache on Debian/Ubuntu hosts
                             |     - block:
                             |         - apt: name=apache2 state=present
                             |         - template: src=httpd.conf.j2 state=started enabled=yes
                             |       when: ansible_os_family == 'Debian'
                             |       become: yes
                             |
                             | If you want to perform a seires of tasks with one
                             | set of task parameters (e.g. *with_items, when,*
                             | *or become*) applied, blocks are quite handy
                             |
    Handling errors with     | tasks:
    blocks                   |   - block:
                             |       - name: Script to connect the app to a monitoring service.
                             |         script: monitoring-connect.sh
                             |     rescure:
                             |       - name: This will only run in case of an error in the block.
                             |         debug: msg="There was an erro in the block"
                             |     always:
                             |       - name: This will always run, no matter what.
                             |         debug: msg="This always executes"
                             |
--------------------------------------------------------------------------------
## Ansible Valut 
  Encrypt file               | ansible-vault encrypt <path to file>
                             |
  Providing an ansible-      | # Use --ask-vault-pass to supply the vault password at runtime
  vault password             | ansible-playbook main.yml --ask-vault-pass
                             |
                             | # Use --valut-password-file to supply the password via file/script
                             | ansible-playbook main.yml --valut-password-file ~/.ansible/\vault_pass.txt
                             |
                             | # edit an ecrypted file
                             | ansible-vault edit
                             |
                             | # Re-key already encrypted vault file witn a new password file
                             | ansible-vault rekey --vault-password-file=<old_password_file> --new-vault-password-file=<new_password_file>
                             |
--------------------------------------------------------------------------------
## Loops 
                             | # Sample Ansible Playbook1.yml
                             | -
                             |   name: Install Packages
                             |   host: localhost
                             |   tasks:
                             |     - yum: name=http       state=present
   --> looping key word      |       with_items:
                             |           - httpd
                             |           - binutils
                             |           - glibc
                             |           - ksh
                             |           - libaio
                             |           - libXext
                             |           - gcc
                             |           - make
                             |           - sysstat
                             |           - unixODBC
                             |           - mongodb
                             |           - nodejs
                             |           - grunt
                             |
--------------------------------------------------------------------------------
## Roles 
  An Ansible role is a collection of tasks, handlers, templates, and variables
  for configuring the target system so that it meets the desired state.
  Sample File Structure:
                             | There are only two directories required to make a
                             | working Ansible role
                             |
                             | role_name/
                             |   meta/
                             |     main.yml
                             |   tasks/
                             |     main.yaml
                             |
  How to run an Ansible role | If you create a directory structure like the one
                             | shown above, with a *main.yml* file in each directory
                             | , Ansible will run all the tasks defined in *tasks
                             | /main.yml* if you call the role from your playbook
                             | using the following syntax:
                             |
                             | ---
                             | - hosts: all
                             |   roles:
                             |     - role_name
                             |
  Build role scaffolding     | ansible-galaxy role init role_name
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
    Defaults/main.yml        | This contains variables for the rol that can be
                             | overwritten when the role is used
                             |
    tasks/main.yml           | This containes the main list of tasks to be
                             | executed when using the role.
                             |
    vars/main.yml            | This containes internal variables for the role.
                             |
    files                    | This contains static files that can be referenced
                             | from this role.
                             |
    templates                | This is the jinja2 templates that can be used via
                             | this role.
                             |
    Handlers/main.yml        | This contains the handler definitions
                             |
    meta/main.yml            | This defines some metadata for this role, such as
                             | the author, license, platform, and dependencies
                             |
    tests                    | This is an inventory. test.yml file that can be
                             | used to ttest this role
                             |
  used to modularize         | # Sample Ansible Playbook1.ym
  playbooks                  | -
                             |   name: Set Firewall Configuration
                             |   hosts: web
  include variables file     |   vars_files:
                             |     - varibles.yml
                             |   tasks:
  all other includes ->      |     - include: tasks.yml
                             |
Roles best practices         |
  lets look a a possible file structure:
                             |
  - Ansible Project          | # Sample Ansible setup_application.yml
    * inventory.txt          | -
    * setup_application.yml  |   name: Set Firewall Configurations
    - roles                  |   hosts: web
      - webservers           |   roles:
        - files              |       - webservers
        - templates          |
        - tasks              |------------------------------------------------
        - handlers           | by seting the role "webservers"
        - vars               | all relevant files including tasks and vars
        - defaults           | in the "webservers" directory will be automatically
        - mets               | loaded
                             |
--------------------------------------------------------------------------------
## Debugging 
  *debug*                    | The debug module may be used to help troubleshoot
                             | plays:
                             |   * use to print detail information about in-progress
                             |     plays
                             |   * Handy for troubleshooting
                             |
                             | *debug* takes two primary parameters that are
                             | mutually exclusive:
                             |   * msg: A message that is printed to STDOUT
                             |   * var: A variable whose content is printed
                             |     to STDOUT
                             |
                             | Example:
                             | - debug:
                             |     msg: "System `{{ inventory_hostname }}`
                             | has uuid `{{ ansible_product_uuid }}"`
                             |
  *register*                   | The *register* module is used to store task output
                             |
                             | Several attributes are avaiable: return code,
                             | stderr, and stdout.
                             |
                             | The following play will store the results of the
                             | shell module in a variable named *motd_contents*:
                             | - hosts: all
                             |   tasks:
                             |   - shell: cat /etc/motd
                             |     register: motd_contents
                             |
--------------------------------------------------------------------------------
## Handlers 
  Handlers                   | Ansible provides a mechanism that allows an action
                             | to be flagged for execution when a task performs a
                             | change
                             |
                             | By only executing certain tasks during a change,
                             | plays are more efficient.
                             |
                             | This mechanism is known as a *handler* in Ansible
                             |
                             | A handler may be defined similarly to tasks:
                             | handlers:
                             | - name: restart memcached
                             |   service:
                             |     name: memcached
                             |     state: restarted
                             |   listen: "restart chae services""
                             |
                             | A handler may be called using the *notify* keyword:
                             | - name: template configuration file
                             |   template:
                             |     src: foo.conf
                             |     dest: /etc/foo.conf
                             |   notify:                        <-- Handler caller
                             |   - restart memcached            <-- must be the same name
                             |   - restart someotherservice     <-- can be used to call multiple handers
                             |
                             | No matter how many times a handler is flagged in a
                             | play, it only runs during a play's final phase.
                             |
                             | *notify* will only flag a handler if a task block
                             | makes changes.
                             |
--------------------------------------------------------------------------------
## Jinja 
  With Conditionals          | when
                             | changed_when
                             | faile_when
                             |
      Literals               | * Strings: 'string'
                             | * integers: 42
                             | * floats: 42.33
                             | * lists: [1, 2, 3]
                             | * dictionaries: {key: value, key2, value2}
                             | * booleans: true, false
                             |
      Math operations        | addition, subtraction, multiplication and division
      Comparisons            | ==, != >=, <=
      Logicat operators      | and, or, not
                             |
      Examples: true         | 1 in [1, 2, 3]
                             | 'see' in 'Can you see me'
                             | foo != bar
                             | (1 < 2) and ('a' not in 'best')
                             |
      Examples: false        | 4 in [1, 2, 3]
                             | foo == bar
                             | (foo != foo) or (a in [1, 2, 3])
                             |
      Other checks           | *undefined* (the opposite of *defined*)
                             | *equalto* (works like ==)
                             | *even*
                             | *iterable* (if you can iterate over the object)
                             |
  register                   | Any play can 'register' a variable, and once
                             | registered, that variable will be available to
                             | all subsequent tasks
                             |
                             | Many times, you may need to output (stdout or stderr)
                             | of a shell command, and you can get that in a
                             | variable using the following syntax:
                             |
                             | - shell: my_command_here
                             |   register: my_command_result
                             |
                             | You can now access stdout (as a string) with
                             | *my_command_result.stout* and *my_command_result.stderr*
                             |
  when                       | *when* is even more powerful if used in conjunction
                             | with variables registered by previous tasks. As an
                             | example, we want to check the status of a running
                             | application and run a play only when that app
                             | reporst it is 'ready' in its output:
                             |
                             | - command: my-app --status
                             |   regester: myapp_result
                             |
                             | - command: do-something-to-my-app
                             |   when: "'ready' in myapp_result.stdout"
                             |
--------------------------------------------------------------------------------
