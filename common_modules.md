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
