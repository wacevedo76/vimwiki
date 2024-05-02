# Subnetting
## Overview
With an ip address, you should be able to derive:
* Subnet Address
* 1st Host

## IP Address classes
```
*Quick Overview*

| Address class | First octet | Classful Mask | Prefix Notation |
| Class A       | 1 - 126     | 255.0.0.0     | /8              |
| Class B       | 128 - 191   | 255.255.0.0   | /16             |
| Class C       | 192 - 223   | 255.255.255.0 | /24             |
| Class D       | 224 - 239   | n/a           | n/a             |
 
* 127 block is skipped as it is a reserved block for
  the loopback address

``` 
### Class A Address
* Uses only the first octet to identify the netwok
  number, the remaining three for the host:  
  `Network.Host.Host.Host`

  example:  
```
10.2.5.4

|         | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|         | Network  | Host     | Host     | Host     |
| Decimal | 10.      | 2.       | 5.       | 4        |
| Binary  | 00001010 | 00000010 | 00000101 | 00000100 |
| Hex     | 0   A    | 0   2    | 00005    | 0   4    |
```

* Class A addresses are number 1 to 126 in the first
octet, the first bit in the octet must be 0
```
| Octet 1   | Octet 2   | Octet 3   | Octet 4  |
| Network   | Host      | Host      | Host     |
| 00000001. | xxxxxxxx. | xxxxxxxx. | xxxxxxxx |
```


* The last network number is 127, which cannot be
used because it is reserved for troubleshooting

* 127.0.0.1 is used to ping the host computer (loopback)
```
| 127.      | 0.        | 0.        | 1        |
| 01111111. | 00000000. | 00000000. | 00000001 |
```

* Class A network, Netwok 10 for example
```
|           | Network   | Host      | Host       | Host     |
| 1st host  | 10.       | 0.        | 0.         | 1        |
|           | 00001010. | 00000000. | 00000000.  | 00000000 |
| last host | 10.       | 255.      | 255.       | 254      |
|           | 00001010. | 11111111. | 11111111.  | 11111110 |
| Broadcast | 10.       | 255.      | 255.       | 255      |
|           | 00001010  | 11111111. | 11111111.  | 11111111 |
```

### Class B Address
* Begin at 128
* Must have the first to binary values in the first octet 1 and 0
* Uses the first two octets for the network address
```
|   | Octet 1   | Octet 2   | Octet 3   | Octet4   |
|   | Netwrok   | Network   | Host      | Host     |
|   | 10000000. | 00000000. | xxxxxxxx. | xxxxxxxx |
```
## Class C Address
* The first network number is 192
  - 192
  - 11000000.00000000.00000000.00000000
<br><br>
* The last is 233
  - 233
  - 11011111.00000000.00000000.00000000
<br><br>
* The private (reserved address are:
  - 10.x.x.x - Any IP addresse beginning with 10
  - 172.16.x.x - Any IP starting with 172.16 to 172.31 inclusive
  - 192.168.x.x - any IP address starting with 192.168

## Non-routable IP ranges
```
| Address | Address                       | Default         |
| Class   | Range                         | Subnet Mask     |
| Class A | 10.0.0.0 - 10.255.255.255     | 255.0.0.0       |
| Class B | 172.16.0.0 - 172.31.255.255   | 255.255.0.0     |
| Class C | 192.168.0.0 - 192.168.255.255 | 255.255.255.0 j |
```

## specialized IPs
* Loopback addresses: 
  - Refers to the device itself and used for testing (127.x.x.x range)
  - Most commonly used as 127.0.0.1

* Automatic Private IP Addresses (APIPA):
  - Dynamically assigned by OS when DHCP server is unavailable and address not assigned manualy
  - Range of 169.254.x.x

```
| Loopback | Class A | 127.0.0.1 - 127.255.255.255   | 255.0.0.0   |
| APIPA    | Class B | 169.254.0.0 - 169.254.255.255 | 255.255.0.0 |
```

Chart of subnets per CIDR:  
```
| CIDR | # Subnets | # IPs |
| /30  | 64        | 4     |
| /29  | 32        | 8     |
| /28  | 16        | 16    |
| /27  | 8         | 32    |
| /26  | 4         | 64    |
| /25  | 2         | 128   |
| /24  | 1         | 256   |
| /23  | 128       | 2     |
| /22  | 64        | 4     |
| /21  | 32        | 8     |
| /20  | 16        | 16    |
| /19  | 8         | 32    |
| /18  | 4         | 64    |
| /17  | 2         | 128   |
```

### Subnetting Basic Method
### Binary method
Rules:
* To get the Network/Subnet Address
  - fill the host portion of an address with binary 0's
<br><br>
* To get the broadcast Address
  - Fill the host portion of an address with binary 1's
<br><br>
* To get the First Host
  - Fill the host portion of an address with binray 0's except for the last bit
<br><br>
* To get the Last Host
  - Fill th host portion of an address with binary 1's except for the last bit which is set to binray 0

## Cheat Sheet making instructions
    * Line 1: from right to left start by one and double eeach number till you reach 128
        128       64       32       16        8        4        2        1
    * Line 2: Subtract 256 from each number in the first row
        128       64       32       16        8        4        2        1
        128      192      224      240       248      252      254      255
    # Line 3: From /32, list CIDR notation
        128       64       32       16        8        4        2        1
        128      192      224      240       248      252      254      255
        /25      /26      /27      /28       /29      /30      /31      /32

### Subnetting Cheat Sheets
```
 Group size:   128       64       32       16       8        4        2        1
   Sub mask:   128      192      224      240      248      252      254      255
   4th CIDR:   /25      /26      /27      /28      /29      /30      /31      /32
   3rd CIDR:   /17      /18      /19      /20      /21      /22      /23      /24

+-------------------------------------------------------------------+
|   Subnets   |  1  |  2  |  4  |  8  | 16  | 32  | 64  | 128 | 256 |
+-------------+-----+-----+-----+-----+-----+-----+-----+-----+-----+
|     Host    | 256 | 128 | 64  | 32  | 16  |  8  |  4  |  2  |  1  |
+-------------+-----+-----+-----+-----+-----+-----+-----+-----+-----+
| Subnet Mask | /24 | /25 | /26 | /27 | /28 | 29  | /30 | /31 | /32 |
+-------------------------------------------------------------------+
```
