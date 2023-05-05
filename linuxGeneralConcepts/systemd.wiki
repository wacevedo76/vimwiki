--------------------------------------------------------------------------------
= Systemd =
--------------------------------------------------------------------------------
  What is systemd made of?   | * systemctl
                             | * journalctl
                             | * Init
                             | * Process management
                             | * Network management (networkd)
                             | * Login management (logind)
                             | * Logs (journald)
                             | * etc
                             |
  Systemd Units              | A unit is an entity managed by systemd (service)
                             | A systemd unit can manage a:
                             |   * Service
                             |   * Socket
                             |   * Device
                             |   * Mountpoint or Automount point
                             |   * Swap file
                             |   * Pertition
                             |   * Partition
                             |   * Startup target (akin to named runlevels)
                             |   * Watched filesystem path
                             |   * Group or externally created processes
                             |
  Unit file locations        |
    /lib/systemd/system      | - Standard systemd unit files (your distro maintainers)
                             |
    /usr/lib/systemd/system  | - from locally installed packages (e.g. via apt-get)
                             |
    /run/systemd/system      | - transient unit files
                             |
    /etc/systemd/system      | - This is where you will put your custom unit files
                             |
  Systemd unit file syntax   | [unit]
                             | Description=The description of your service
                             | After=netwok-up.target                           <- the service will be run after this is met
                             |
                             | [service]
                             | ExecStart=<path to the executable>
                             |
                             | [Install]
                             | WantedBy=multi-user.target
                             |
  Initialize new and custom  | *systemctl daemon-reload*                          <- Forces systemd to re-read all unit files
  Units                      |
                             |
  example of unit file       | -------------------------------------------------
  (nginx)                    | # comments are created with the hash symbol
                             | [unit]
                             | Description=A high performance webserver and a reverse proxy server
                             | Documentation=man:nginx(8)
                             | After=network.target
                             |
                             | [service]
                             | Type=forking
                             | PIDFile=/run/nginx.pid
                             | ExecStartPre=/user/sbin/nginx -t -q -g 'daemon on; master_process on;'
                             | ExecStart=/usr/bin/nginx -g 'daemon on; master_process on;'
                             | ExecReload=/usr/bin/nginx -g 'daemon on; master_process on;' -s reload
                             | ExecStop=/sbin/start-stop-daemon --quiet --stop --retry QUIT/5 --pidfile /run/nginx.pid
                             | TimeoutStopSec=5
                             | KillMode=mixed
                             |
                             | [Install]
                             | WantedBy=multi-user.target
                             | -------------------------------------------------
                             |
  *systemctl*                  | Running the systemctl command without
                             | is the same as running systemctl list-units      <- will only show running units
                             |
                             | systemctl list-units --type=<type of unit>
                             | systemctl list-units --type=service              <- filter for specific types of units
                             |
                             | systemctl list-unit-files                        <- lists all units (inactive as well as active)
                             |
                             | systemctl status <unit name>
                             | systemctl start <unit name>
                             | systemctl stop <unit name>
                             | systemctl restart <unit name>
                             | systemctl kill <unit name>
                             | systemctl enable <unit name>
                             | systemctl disable <unit name>
                             |
    *Unit States*              | * Inactive (deactivating, exited)
                             | * Active (Activating, running)
                             | * Failed
                             | * Static (not started, frozen by systemd)
                             | * Bad (broken)
                             | * Masked
                             | * Indirect (disabled but referenced)
                             | * Linked (symlinked)
                             |
                             | Units can have additional sub-states depending on unit type
                             |
  Targets                    | Targest are a way of managing relationships
                             | between all units. Targets are a way of handling
                             | system state or phases duing boot which allows
                             | you to order the units under.
                             |
    Switch Targets           | systemctl isolate $TARGET
                             |
    Get Default Target       | systemctl get-default
                             |
    add a unit to specific   | # Probably *don't* want to do this. It might be more advantagious to do this in the unit file
    Target                   | systemctl add-wants multi-user.target nginx.service
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
