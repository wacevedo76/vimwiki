#s:q
Arch Linux Specific Commands
## Misc
  
| Purpose                             | command                            |
| ----------------------------------- | ---------------------------------- |
| Remove package and all dependencies | `sudo pacman -Rcns <package name>` |

## Bluetooth
To find out the specifications for the built-in Bluetooth module on an Arch Linux system, you can use a combination of command-line tools that provide detailed information about your hardware. Here are some steps and commands to achieve this:

### Install Required Tools:
Ensure you have lsusb, bluetoothctl, and lshw installed. You can install them using pacman:
```bash
sudo pacman -S usbutils bluez-utils lshw
```
### List USB Devices:
Use lsusb to list all USB devices connected to your system. This will help you identify the Bluetooth module:
```bash
lsusb
```
Look for an entry related to Bluetooth. The output will look something like this:

```yaml
Bus 001 Device 003: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
```
### Detailed Information Using lsusb:
Get more detailed information about the Bluetooth device using `lsusb -v` and specifying the device ID found in the previous step:
```bash
lsusb -v -d 8087:0a2a
```
This will provide detailed specifications about the Bluetooth device.

### Bluetoothctl:
Use bluetoothctl to interact with the Bluetooth device. This tool will list available controllers and their information:
```bash
bluetoothctl
```
Once inside bluetoothctl, you can use the following commands:
```bash
list
show <controller>
Replace <controller> with the appropriate controller name obtained from the list command.
```

### Use lshw:
Use lshw to list detailed information about your hardware, including the Bluetooth module:
```bash
sudo lshw -C communication
```
This command will filter the output to show only communication devices, including the Bluetooth module.

Here is a sample of what each command might output:

`> lsusb:`

```yaml
Bus 001 Device 003: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
```
`> lsusb -v -d 8087:0a2a:`

```python
idVendor           0x8087 Intel Corp.
idProduct          0x0a2a Bluetooth wireless interface
```

`> bluetoothctl:`
```ruby
[bluetooth]# list
Controller XX:XX:XX:XX:XX:XX My-Device-Name [default]
[bluetooth]# show XX:XX:XX:XX:XX:XX
Controller XX:XX:XX:XX:XX:XX (public)
      Name: My-Device-Name
      Alias: My-Device-Name
      Class: 0x000c0104
      Powered: yes
      Discoverable: no
      Pairable: yes
      UUID: Generic Access Profile (00001800-0000-1000-8000-00805f9b34fb)
      UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
      ...
```
`> sudo lshw -C communication:`
```yaml
*-communication
     description: Bluetooth wireless interface
     product: Bluetooth Device
     vendor: Intel Corp.
     physical id: 0
     bus info: usb@1:3
     version: 0.01
     capabilities: bluetooth usb-2.00
     configuration: driver=btusb
```
These commands provide comprehensive information about your Bluetooth module's specifications, including its vendor, product ID, and capabilities.

## How to install and enable Bluetooth?
To install and enable Bluetooth on Arch Linux, follow these steps:

### Install Bluetooth Packages:
First, you need to install the necessary Bluetooth packages, including bluez, bluez-utils, and an optional graphical front-end like blueman for easier management.

```bash
sudo pacman -S bluez bluez-utils
sudo pacman -S blueman # Optional, for graphical management
```
#### Enable and Start the Bluetooth Service:
After installing the packages, you need to enable and start the Bluetooth service.
```bash
sudo systemctl enable bluetooth.service
sudo systemctl start bluetooth.service
```
#### Verify the Bluetooth Service Status:
Check the status of the Bluetooth service to ensure it is running correctly.
```bash
systemctl status bluetooth.service
```
You should see output indicating that the service is active and running.

### Using Bluetoothctl:
You can use bluetoothctl to manage Bluetooth devices from the command line.
```bash
bluetoothctl
```
Within the bluetoothctl interface, you can use the following commands:

| Command               | Performs                                      |
| --------------------: | --------------------------------------------- |
| `list`                | Lists available Bluetooth controllers         |
| `power on`            | Powers on the Bluetooth controller            |
| `scan on`             | Starts scanning for nearby Bluetooth devices  |
| `pair <device_id>`    | Pars with a device                            |
| `connect <device_id>` | Connects to a paired device                   |
| `trust <device_id`    | Marks a device as trusted                     |
| `exit`                | Exits the bluetoothctl interface              |

## Using Blueman (Optional):
If you installed blueman, you can start it from your desktop environment's application menu or by running the following command:
```bash
blueman-manager
```
Blueman provides a graphical interface for managing Bluetooth devices, making it easier to connect, pair, and configure Bluetooth devices.

#### Example Workflow:
##### Open Bluetoothctl:
```bash
bluetoothctl
```
##### Power On Bluetooth:
```bash
[bluetooth] # power on
```
##### Start Scanning for Devices:
```bash
[bluetooth]# scan on
```
##### Pair with a Device:
```bash
[bluetooth]# pair XX:XX:XX:XX:XX:XX
```
##### Trust the Device:
```bash
[bluetooth]# trust XX:XX:XX:XX:XX:XX
```
##### Connect to the Device:
```bash
[bluetooth]# connect XX:XX:XX:XX:XX:XX
```
##### Exit Bluetoothctl:
```bash
[bluetooth]# exit
```
