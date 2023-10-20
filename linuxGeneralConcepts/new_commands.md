--------------------------------------------------------------------------------
# New Commands
--------------------------------------------------------------------------------
Start a keyring daemon       |
eval $(ssh-agent -s)         |
                             |
--------------------------------------------------------------------------------
Keep a command running       | while ( ! rsync --recursive --timeout=60 --partial <source> <destination> --info=progress2 ); do sleep 1; done
  (rsync example)            |
                             |
--------------------------------------------------------------------------------
[Tunneling](Tunneling) traffic via SSH    | Syntax
                             | ssh -L <local-port>:localhost:<remote-port> <username>@10.10.10.101
                             |
                             |
                             |
                             |
