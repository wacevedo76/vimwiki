[[Python|index]]
## interesting modules to look up
  * argparse      - For building the CLI and parsing flags
  * pwd           - For accessing the Password/User database
  * json          - For JSON encoding and decoding
  * csf          - For csf encoding and decoding

  - Working with databases
    * SQLAlchemy
    * flask-Migrate

## SQlite3
  * [Sqlite3](Python/sqlite3)

## ipython
  * [ipython](Python/ipython)

## Python Networking
  * Pexpect
  * Paramiko
  * Netmiko
  * NAPALM
  * Nornir

## Working with time
``` 
  get current epoc time      | import time
  (time module)              | current_epoch_time = int(time.time())
                             |
  convert epoc time to a     | current_time_struct = time.gmttime(current_epoch_time)
  human readable form        | formatted_time = time.strftime("%Y-%m-%d $H:%M:%S", current_time_struct)
                             |
  Get current epoch time     | # Get the current datetime object
  (datetime module)          | current_datetime = datetime.datetime.now()
                             |
                             | # Convert datetime object to epoch time
                             | current_epoch_time = int(current_datetime.timestamp())
                             | print("Current Epoch Time:", current_epoch_time)
                             |
                             | # Create a datetime object from an epoch time
                             | epoch_time = 1609459200  # Example epoch time (January 1, 2021, at 00:00:00 UTC)
                             | datetime_from_epoch = datetime.datetime.utcfromtimestamp(epoch_time)
                             | print("Datetime from Epoch:", datetime_from_epoch)
```

## Common Module methods
### os Module 
```
  Working with Enviromental  | os.environ  -> returns a dictionary of environmental
  variables                  |                variables -> Throws an error if
                             |                variable does not exists
                             |
                             | os.getenv("key", default=None)  -> returns string
```

### sys Module
```
  Return exit code to shell  | sys.exit(exit_number)
```

## Common Module's Method's
```
-----------------------------+-----------------------------+
os                           | re                          |
                             |                             |
'abc',                       | 'compile',                  |
'abort',                     | 'copyreg',                  |
'access',                    | 'enum',                     |
'altsep',                    | 'error',                    |
'chdir',                     | 'escape',                   |
'chmod',                     | 'findall',                  |
'chown',                     | 'finditer',                 |
'chroot',                    | 'fullmatch',                |
'close',                     | 'functools',                |
'closerange',                | 'match',                    |
'confstr',                   | 'purge',                    |
'confstr_names',             | 'search',                   |
'copy_file_range',           | 'split',                    |
'cpu_count',                 | 'sre_compile',              |
'ctermid',                   | 'sre_parse',                |
'curdir',                    | 'sub',                      |
'defpath',                   | 'subn',                     |
'device_encoding',           | 'template'                  |
'devnull',                   +-----------------------------+
'dup',                       | shutil                      |
'dup2',                      |                             |
'environ',                   | 'chown',                    |
'environb',                  | 'collections',              |
'error',                     | 'copy',                     |
'eventfd',                   | 'copy2',                    |
'eventfd_read',              | 'copyfile',                 |
'eventfd_write',             | 'copyfileobj',              |
'execl',                     | 'copymode',                 |
'execle',                    | 'copystat',                 |
'execlp',                    | 'copytree',                 |
'execlpe',                   | 'disk_usage',               |
'execv',                     | 'errno',                    |
'execve',                    | 'fnmatch',                  |
'execvp',                    | 'get_archive_formats',      |
'execvpe',                   | 'get_terminal_size',        |
'extsep',                    | 'get_unpack_formats',       |
'fchdir',                    | 'ignore_patterns',          |
'fchmod',                    | 'make_archive',             |
'fchown',                    | 'move',                     |
'fdatasync',                 | 'nt',                       |
'fdopen',                    | 'os',                       |
'fork',                      | 'posix',                    |
'forkpty',                   | 'register_archive_format',  |
'fpathconf',                 | 'register_unpack_format',   |
'fsdecode',                  | 'rmtree',                   |
'fsencode',                  | 'stat',                     |
'fspath',                    | 'sys',                      |
'fstat',                     | 'unpack_archive',           |
'fstatvfs',                  | 'unregister_archive_format',|
'fsync',                     | 'unregister_unpack_format', |
'ftruncate',                 | 'which'                     |
'fwalk',                     +-----------------------------+
'get_blocking',              | os.path                     |
'get_exec_path',             |                             |
'get_inheritable',           | 'abspath'                   |
'get_terminal_size',         | 'altsep',                   |
'getcwd',                    | 'basename',                 |
'getcwdb',                   | 'commonpath',               |
'getegid',                   | 'commonprefix',             |
'getenv',                    | 'curdir',                   |
'getenvb',                   | 'defpath',                  |
'geteuid',                   | 'devnull',                  |
'getgid',                    | 'dirname',                  |
'getgrouplist',              | 'exists',                   |
'getgroups',                 | 'expanduser',               |
'getloadavg',                | 'expandvars',               |
'getlogin',                  | 'extsep',                   |
'getpgid',                   | 'genericpath',              |
'getpgrp',                   | 'getatime',                 |
'getpid',                    | 'getctime',                 |
'getppid',                   | 'getmtime',                 |
'getpriority',               | 'getsize',                  |
'getrandom',                 | 'isabs',                    |
'getresgid',                 | 'isdir',                    |
'getresuid',                 | 'isfile',                   |
'getsid',                    | 'islink',                   |
'getuid',                    | 'ismount',                  |
'getxattr',                  | 'join',                     |
'initgroups',                | 'lexists',                  |
'isatty',                    | 'normcase',                 |
'kill',                      | 'normpath',                 |
'killpg',                    | 'os',                       |
'lchown',                    | 'pardir',                   |
'linesep',                   | 'pathsep',                  |
'link',                      | 'realpath',                 |
'listdir',                   | 'relpath',                  |
'listxattr',                 | 'samefile',                 |
'lockf',                     | 'sameopenfile',             |
'lseek',                     | 'samestat',                 |
'lstat',                     | 'sep',                      |
'major',                     | 'split',                    |
'makedev',                   | 'splitdrive',               |
'makedirs',                  | 'splitext',                 |
'memfd_create',              | 'stat',                     |
'minor',                     | 'supports_unicode_filenames'|
'mkdir',                     | 'sys'                       |
'mkfifo',                    |                             |
'mknod',                     |                             |
'name',                      |                             |
'nice',                      |                             |
'open',                      |                             |
'openpty',                   |                             |
'pardir',                    |                             |
'path',                      |                             |
'pathconf',                  |                             |
'pathconf_names',            |                             |
'pathsep',                   |                             |
'pidfd_open',                |                             |
'pipe',                      |                             |
'pipe2',                     |                             |
'popen',                     |                             |
'posix_fadvise',             |                             |
'posix_fallocate',           |                             |
'posix_spawn',               |                             |
'posix_spawnp',              |                             |
'pread',                     |                             |
'preadv',                    |                             |
'putenv',                    |                             |
'pwrite',                    |                             |
'pwritev',                   |                             |
'read',                      |                             |
'readlink',                  |                             |
'readv',                     |                             |
'register_at_fork',          |                             |
'remove',                    |                             |
'removedirs',                |                             |
'removexattr',               |                             |
'rename',                    |                             |
'renames',                   |                             |
'replace',                   |                             |
'rmdir',                     |                             |
'scandir',                   |                             |
'sched_get_priority_max',    |                             |
'sched_get_priority_min',    |                             |
'sched_getaffinity',         |                             |
'sched_getparam',            |                             |
'sched_getscheduler',        |                             |
'sched_param',               |                             |
'sched_rr_get_interval',     |                             |
'sched_setaffinity',         |                             |
'sched_setparam',            |                             |
'sched_setscheduler',        |                             |
'sched_yield',               |                             |
'sendfile',                  |                             |
'sep',                       |                             |
'set_blocking',              |                             |
'set_inheritable',           |                             |
'setegid',                   |                             |
'seteuid',                   |                             |
'setgid',                    |                             |
'setgroups',                 |                             |
'setpgid',                   |                             |
'setpgrp',                   |                             |
'setpriority',               |                             |
'setregid',                  |                             |
'setresgid',                 |                             |
'setresuid',                 |                             |
'setreuid',                  |                             |
'setsid',                    |                             |
'setuid',                    |                             |
'setxattr',                  |                             |
'spawnl',                    |                             |
'spawnle',                   |                             |
'spawnlp',                   |                             |
'spawnlpe',                  |                             |
'spawnv',                    |                             |
'spawnve',                   |                             |
'spawnvp',                   |                             |
'spawnvpe',                  |                             |
'splice',                    |                             |
'st',                        |                             |
'stat',                      |                             |
'stat_result',               |                             |
'statvfs',                   |                             |
'statvfs_result',            |                             |
'strerror',                  |                             |
'supports_bytes_environ',    |                             |
'supports_dir_fd',           |                             |
'supports_effective_ids',    |                             |
'supports_fd',               |                             |
'supports_follow_symlinks',  |                             |
'symlink',                   |                             |
'sync',                      |                             |
'sys',                       |                             |
'sysconf',                   |                             |
'sysconf_names',             |                             |
'system',                    |                             |
'tcgetpgrp',                 |                             |
'tcsetpgrp',                 |                             |
'terminal_size',             |                             |
'times',                     |                             |
'times_result',              |                             |
'truncate',                  |                             |
'ttyname',                   |                             |
'umask',                     |                             |
'uname',                     |                             |
'uname_result',              |                             |
'unlink',                    |                             |
'unsetenv',                  |                             |
'urandom',                   |                             |
'utime',                     |                             |
'path',                      |                             |
-----------------------------+-----------------------------+
```
