# Basic Linux Commands

## Filesystem Commands

### `findmnt`
Lists all mounted filesystems or searches for a filesystem. The `findmnt` command is able to search in `/etc/fstab`, `/etc/mtab` or `/proc/self/mountinfo`. If device or mountpoint is not given, all filesystems are shown.

### `file`
Returns the type of file.

## Finding Files

### `which`
Looks for binaries in `$PATH`.

### `locate`
Uses a database, built by `updatedb` to find files in a database.

## Text Processing

### `cut`
- `-f <field number>` - specify field number
- `-d <delimiter>` - specify delimiter

### `grep`
- `-A5` - show 5 lines after match
- `-B5` - show 5 lines before match
- `-R` - recursive search

## User and Group Management

### `lid` (Red Hat)
- `-g <group name>` - list all users in a group

## SSH and Authentication

### Start SSH Agent
```bash
eval $(ssh-agent -s)
```

### SSH Tunneling
Tunnel traffic via SSH:
```bash
ssh -L <local-port>:localhost:<remote-port> <username>@10.10.10.101
```

## Continuous Operations

### Keep a command running (rsync example)
```bash
while ( ! rsync --recursive --timeout=60 --partial <source> <destination> --info=progress2 ); do
    sleep 1
done
```

## Command Structure
Each command entry follows this format:
- **Command name** - Brief description
- **Common options** - Frequently used flags and parameters
- **Examples** - Practical usage examples
- **Notes** - Special considerations or platform differences

## Best Practices
1. **Use man pages**: `man <command>` for detailed documentation
2. **Check version**: `<command> --version` or `-v`
3. **Test with dry-run**: Many commands support `--dry-run` or `-n` flag
4. **Use help**: `--help` or `-h` for quick reference

---
*Last updated: 2026-04-05*  
*Merged from: commonCommands.md + new_commands.md*