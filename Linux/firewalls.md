# Linux Firewall Management

## Overview
Linux provides multiple firewall solutions. The two main approaches are:
1. **firewalld** - Dynamic firewall manager with zones (default on RHEL/CentOS/Fedora)
2. **iptables** - Traditional packet filtering framework

## Firewalld

### Basic Concepts
- **Zones**: Predefined sets of rules (public, external, internal, etc.)
- **Services**: Named sets of ports/protocols (http, ssh, ftp, etc.)
- **Runtime vs Permanent**: Changes can be temporary or saved permanently

### General Commands

#### Zone Management
```bash
# List all available zones
firewall-cmd --get-zones

# List all configuration for default zone (usually public)
firewall-cmd --list-all

# List configuration for specific zone
firewall-cmd --zone=external --list-all

# Change default zone
firewall-cmd --set-default-zone=external
```

#### Service Management
```bash
# Add a service to a zone (temporary)
firewall-cmd --zone=external --add-service=ftp

# Add a service permanently
firewall-cmd --permanent --zone=external --add-service=ftp

# Remove a service
firewall-cmd --zone=external --remove-service=ftp

# List enabled services in a zone
firewall-cmd --zone=external --list-services
```

#### Port Management
```bash
# Add a port (portnumber/protocol)
firewall-cmd --permanent --zone=external --add-port=60001/udp

# Remove a port
firewall-cmd --permanent --zone=external --remove-port=60001/udp
```

#### Applying Changes
```bash
# Reload firewall configuration (preserves runtime changes)
firewall-cmd --reload

# Complete reload (drops runtime changes, loads only permanent)
firewall-cmd --complete-reload
```

## iptables

### Architecture
iptables uses tables and chains:

```
+-------------------------------------------------------------------------+
|                           IPTABLES                                      |
|                                                                         |
|   Filter Table             Nat Table              Mangle Table          |
|  +-------------------+   +-------------------+   +-------------------+  |
|  | INPUT CHAIN       |   | OUTPUT CHAIN      |   | INPUT CHAIN       |  |
|  +-------------------+   +-------------------+   +-------------------+  |
|  | OUTPUT CHAIN      |   | PREROUTING CHAIN  |   | OUTPUT CHAIN      |  |
|  +-------------------+   +-------------------+   +-------------------+  |
|  | FORWARD CHAIN     |   | POSTROUTING CHAIN |   | POSTROUTING CHAIN |  |
|  +-------------------+   +-------------------+   +-------------------+  |
|                                                  | PREROUTING CHAIN  |  |
|                                                  +-------------------+  |
|                                                  | FORWARD CHAIN     |  |
|                                                  +-------------------+  |
+-------------------------------------------------------------------------+
```

### Tables
1. **Filter Table** - Default table for packet filtering
   - INPUT: Incoming traffic to local sockets
   - OUTPUT: Outgoing locally-generated traffic
   - FORWARD: Traffic routed through the system

2. **Nat Table** - Network Address Translation
   - PREROUTING: Alter packets as they arrive
   - OUTPUT: Alter locally-generated packets before routing
   - POSTROUTING: Alter packets as they are about to leave

3. **Mangle Table** - Specialized packet alteration
   - All standard chains plus PREROUTING and POSTROUTING

### Common iptables Commands
```bash
# List all rules
iptables -L -n -v

# List rules for specific table
iptables -t nat -L -n -v

# Allow SSH (port 22)
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Set default policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Save rules (distribution specific)
# RHEL/CentOS: service iptables save
# Debian/Ubuntu: iptables-save > /etc/iptables/rules.v4
```

## Choosing Between firewalld and iptables

### Use firewalld when:
- You need dynamic firewall management
- Working with zones and services abstraction
- On RHEL/CentOS 7+ or Fedora
- Need D-Bus interface for applications

### Use iptables when:
- You need fine-grained control
- Working on older systems or minimal installations
- Need compatibility with existing scripts
- Require complex NAT or packet mangling

## Migration and Compatibility

### Check current backend
```bash
# See if firewalld is using iptables or nftables backend
firewall-cmd --version
```

### Using both together
- firewalld can use iptables or nftables as backend
- Direct iptables commands may conflict with firewalld
- For mixed environments, use one or the other consistently

## Best Practices

1. **Test rules before applying**: Use `--permanent` flag last
2. **Use services over ports**: More readable and maintainable
3. **Document changes**: Keep a record of firewall modifications
4. **Backup configurations**: Save iptables rules and firewalld zones
5. **Minimal permissions**: Start with deny-all, allow specifically

## Troubleshooting

### Common Issues
- **Rules not applying**: Check if `--permanent` was used and `--reload` executed
- **Service not starting**: Verify SELinux/AppArmor isn't blocking
- **Lost connectivity**: Have console access or use `--timeout` option

### Diagnostic Commands
```bash
# Check firewalld status
systemctl status firewalld

# Check loaded zones
firewall-cmd --get-active-zones

# Check iptables rules
iptables -L -n -v --line-numbers

# Monitor firewall logs
journalctl -u firewalld -f
tail -f /var/log/messages
```

---
*Last updated: 2026-04-05*  
*Merged from: firewalld.md + iptables.md*