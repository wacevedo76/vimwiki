# Systemd - System and Service Manager

## Overview
Systemd is a system and service manager for Linux operating systems. It replaces the traditional SysV init system and provides:
- Parallel startup of system services
- On-demand starting of daemons
- System state snapshotting
- Dependency-based service control
- Extensive logging via journald

## Systemd Components
Systemd is made of several components:
- **systemctl** - Control the systemd system and service manager
- **journalctl** - Query and display messages from the journal
- **Init** - System initialization
- **Process management** - Process tracking and supervision
- **Network management** (networkd) - Network configuration
- **Login management** (logind) - User session management
- **Logs** (journald) - System logging
- **Timers** - Job scheduling (cron replacement)
- **Mount management** - Filesystem mounting

## Systemd Units

### What are Units?
A unit is an entity managed by systemd. Systemd units can manage:
- **Service** - System services
- **Socket** - Inter-process communication sockets
- **Device** - Device files
- **Mountpoint or Automount point** - Filesystem mounts
- **Swap file** - Swap space
- **Partition** - Disk partitions
- **Startup target** - Named runlevels
- **Watched filesystem path** - Path monitoring
- **Timer** - Scheduled tasks
- **Slice** - Resource management groups
- **Scope** - Externally created processes

### Unit File Locations
```
/lib/systemd/system      # Standard systemd unit files (distro maintainers)
/usr/lib/systemd/system  # From locally installed packages (e.g., via apt-get)
/run/systemd/system      # Transient unit files (runtime only)
/etc/systemd/system      # Custom unit files (administrator created)
```

## Working with Services

### Listing Services

```bash
# Display all currently running systemd services
systemctl list-units --type=service --state=running

# See all services (including stopped or failed)
systemctl list-units --type=service

# Simplified list of all installed services and their enabled/disabled status
systemctl list-unit-files --type=service

# System hierarchy of services in tree format
systemctl status
```

### Service Management Commands

```bash
# Check service status
systemctl status <service-name>

# Start a service
systemctl start <service-name>

# Stop a service
systemctl stop <service-name>

# Restart a service
systemctl restart <service-name>

# Reload service configuration (without restart)
systemctl reload <service-name>

# Enable service to start at boot
systemctl enable <service-name>

# Disable service from starting at boot
systemctl disable <service-name>

# Mask a service (prevent all starts, even manual)
systemctl mask <service-name>

# Unmask a service
systemctl unmask <service-name>

# Kill a service
systemctl kill <service-name>
```

### Unit States
- **Inactive** - Not running (deactivating, exited)
- **Active** - Running (activating, running)
- **Failed** - Failed to start or crashed
- **Static** - Not started, frozen by systemd
- **Bad** - Broken unit file
- **Masked** - Completely disabled (linked to /dev/null)
- **Indirect** - Disabled but referenced by other units
- **Linked** - Symlinked unit

## Unit File Syntax

### Basic Structure
```ini
[Unit]
Description=Description of your service
After=network.target  # Service runs after network is up
Requires=network.target  # Hard dependency
Wants=network.target  # Soft dependency

[Service]
Type=simple  # simple, forking, oneshot, dbus, notify, idle
ExecStart=/path/to/executable
ExecReload=/path/to/reload-script
ExecStop=/path/to/stop-script
Restart=on-failure  # on-failure, always, on-abnormal, on-watchdog, on-abort
User=service-user
Group=service-group

[Install]
WantedBy=multi-user.target  # Enable creates symlink to this target
```

### Example: Nginx Service Unit
```ini
[Unit]
Description=A high performance webserver and a reverse proxy server
Documentation=man:nginx(8)
After=network.target

[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t -q -g 'daemon on; master_process on;'
ExecStart=/usr/bin/nginx -g 'daemon on; master_process on;'
ExecReload=/usr/bin/nginx -g 'daemon on; master_process on;' -s reload
ExecStop=/sbin/start-stop-daemon --quiet --stop --retry QUIT/5 --pidfile /run/nginx.pid
TimeoutStopSec=5
KillMode=mixed

[Install]
WantedBy=multi-user.target
```

## Targets (Runlevels)

### Understanding Targets
Targets are a way of managing relationships between all units. They represent system states or phases during boot and allow ordering of units.

### Common Targets
- **poweroff.target** - System power off (runlevel 0)
- **rescue.target** - Single-user mode (runlevel 1)
- **multi-user.target** - Multi-user, non-graphical (runlevel 3)
- **graphical.target** - Multi-user, graphical (runlevel 5)
- **reboot.target** - System reboot (runlevel 6)

### Target Commands
```bash
# Get current default target
systemctl get-default

# Set default target
systemctl set-default multi-user.target

# Switch to a target immediately
systemctl isolate multi-user.target

# List all available targets
systemctl list-unit-files --type=target

# See dependencies of a target
systemctl list-dependencies multi-user.target
```

### Adding Units to Targets
```bash
# Add a unit to a specific target (creates wants dependency)
systemctl add-wants multi-user.target nginx.service

# Note: Usually better to specify this in the unit file [Install] section
```

## Journalctl - System Logging

### Viewing Logs
```bash
# Show all logs from current boot
journalctl -b

# Follow logs in real-time
journalctl -f

# Show logs for a specific service
journalctl -u nginx.service

# Show logs with priority error or higher
journalctl -p err

# Show logs from specific time
journalctl --since "2024-01-01 00:00:00" --until "2024-01-02 00:00:00"

# Show kernel messages
journalctl -k
```

### Filtering and Formatting
```bash
# Show last 100 lines
journalctl -n 100

# Show in JSON format
journalctl -o json

# Show with full details
journalctl -o verbose

# Filter by executable
journalctl /usr/bin/nginx
```

## Systemd Timers (Cron Replacement)

### Timer vs Service
Timers are systemd units that trigger activation of other units based on timers.

### Example Timer Unit
```ini
[Unit]
Description=Run backup daily

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

### Timer Commands
```bash
# List all timers
systemctl list-timers

# List timers with details
systemctl list-timers --all

# Check when timer will run next
systemctl status backup.timer
```

## Best Practices

### 1. Unit File Management
- Place custom unit files in `/etc/systemd/system/`
- Use `systemctl daemon-reload` after creating/modifying unit files
- Test with `systemctl start --dry-run` if available

### 2. Service Design
- Use `Type=simple` for services that don't fork
- Use `Type=forking` for traditional daemons
- Set appropriate `Restart` policies
- Specify `User` and `Group` for security

### 3. Debugging
- Check unit status: `systemctl status <unit>`
- View logs: `journalctl -u <unit>`
- Test manually: `systemctl start <unit>`
- Check dependencies: `systemctl list-dependencies <unit>`

### 4. Performance
- Use `After=` dependencies instead of `Requires=` when possible
- Consider using `Wants=` for optional dependencies
- Group services with `PartOf=` for coordinated control

## Common Issues and Solutions

### Service Won't Start
```bash
# Check status
systemctl status service-name

# View logs
journalctl -u service-name

# Check dependencies
systemctl list-dependencies service-name

# Test manually
/usr/bin/service-executable --test
```

### Unit File Errors
```bash
# Check syntax
systemd-analyze verify /etc/systemd/system/service-name.service

# Reload systemd
systemctl daemon-reload

# Reset failed state
systemctl reset-failed service-name
```

### Boot Issues
```bash
# Analyze boot process
systemd-analyze time
systemd-analyze critical-chain
systemd-analyze blame

# Emergency shell if system won't boot
# Add "systemd.unit=rescue.target" to kernel command line
```

## Advanced Features

### 1. Slices and Scopes
- **Slices** - Organize units into hierarchical groups for resource management
- **Scopes** - Manage externally created processes

### 2. Transient Units
Create temporary units without writing files:
```bash
systemd-run --unit=temporary-service --service-type=simple /path/to/command
```

### 3. Systemd-nspawn
Lightweight container management:
```bash
systemd-nspawn -D /path/to/container
```

### 4. Networkd
Network configuration via systemd:
```bash
# Configure network interfaces with .network files
/etc/systemd/network/eth0.network
```

## Migration from SysV Init

### Comparing Commands
| SysV Init | Systemd Equivalent |
|-----------|-------------------|
| `service nginx start` | `systemctl start nginx` |
| `chkconfig nginx on` | `systemctl enable nginx` |
| `runlevel` | `systemctl get-default` |
| `init 3` | `systemctl isolate multi-user.target` |

### Converting Init Scripts
1. Analyze existing init script
2. Create corresponding `.service` file
3. Test with `systemctl start`
4. Enable with `systemctl enable`

---
*Last updated: 2026-04-05*  
*Enhanced from: systemd.md + General_administration.md systemd section*