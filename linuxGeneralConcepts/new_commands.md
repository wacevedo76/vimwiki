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
                             |
