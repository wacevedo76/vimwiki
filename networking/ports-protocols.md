# Ports and protocols

## Note:
* Well-Known/Reserved Ports: Ports 0 - 1023
* Ephemeral Ports: Ports 1024 - 65,535
          
          
| **Protocol**                          | **Port**                       | **Description**                                                                                                                                   |
| --------------------------            | :----------------------------: | --------------------------------                                                                                                                  |
| Echo                                  | port 7 (TCP, UDP)              | Echo Service                                                                                                                                      |
| File Transfer Protocol (FTP)          | ports 20, 21 (TCP, UDP)        | Provides insecure file Transfers                                                                                                                  |
| SSH, SCP SFTP                         | port 22 (TCP, SCTP)            | Provides secure remote control of another machine using a text-based enviroment and secure file transer                                           |
| Telnet                                | port 23                        | Provides insecure remote control of another machine using a text-based enviroment                                                                 |
| Simple Mail Transfer protocol         | port 25                        | SMPT is used for email routing between mail servers                                                                                               |
| Domain Name System (DNS)              | port 53                        | Domain Name system name resolver                                                                                                                  |
| Dynamic Host Control Protocol (DHCP)  | ports 67, 68                   | Automatically provides network parameters to your clients, such as their assigned IP                                                              |
| Trivial File Transfer Protocol (TFTP) | port 69 (UDP)                  |                                                                                                                                                   |
| Hypertext Transfer Protocol (HTTP)    | port 80                        | HTTP uses TCP in versions 1.x and 2 HTTP/3 uses QUIC, a transport protocol on top of UDP                                                          |
| Kerberos                              | port 88 (TCP, UDP)             | Network authentication system                                                                                                                     |
| Iso-tsap                              | port 102                       | ISO Transport Service Access Point (TSAP) Class 0 protocol                                                                                        |
| Post Office Protocol version 3 (POP3) | port 110                       |                                                                                                                                                   |
| Microsoft End Point Mapper (EPMAP)    | Port 135 (TCP, UDP)            | MS EPMAP, also known as DCE/RPC Locator service, used to remotely manage services including DHCCP server, DNS server, and WINS. Also used by Dcom |
| NetBIOS-ns                            | Port 137 (TCP, UDP)            | NetBIOS Name Service, used for name registration and resolution                                                                                   |
| NetBIOS-ssn                           | Port 139 (TCP, UDP)            | NetBIOS Session Service                                                                                                                           |
| IMAP4                                 | Port 143 (TCP, UDP)            | Internet Message Access Protocol, management of electronic mail messages on a server                                                              |
| HP                                    | Port 381 (TCP, UDP)            | HP data alarm manager                                                                                                                             |
| HP                                    | port 383 (TCP, UDP)            | Openview HP dtat alarm manager                                                                                                                    |
| SHTTP                                 | Port 443 (TCP, UDP, SSL, SCTP) |                                                                                                                                                   |
| Kerberos                              | port 464 (TCP, UDP)            | Kerberos Change/Set password                                                                                                                      |
| SMTP                                  | port 465 (TCP, TLS, SSL, SSM)  | Authenticated SMTP over TLS/SSL (SMTPS), URL Rendezvous Directory for SSM (Cisco protocol)                                                        |
| SMTP                                  | port 487 (TCP)                 | TCP Email message submission                                                                                                                      |
| Microsoft                             | port 593 (TCP, UDP)            | Remote procedure call over Hypertext Transfer Protocol, often used by Distributed Component Objec Model services and Microsoft Exchange Server    |
| LDAP                                  | port 636 (TCP, UDP             | Lightweight Directory Access Protocol over TLS/SSL                                                                                                |
| MS                                    | port 691 (TCP, UDP)            | Exchange TCP MS Exchange Routing                                                                                                                  |
| VMware                                | port 902                       | Server unofficial VMware ESXi                                                                                                                     |
| FTP                                   | port 989 (TCP, UDP)            | FTPS protocol (data), FTP over TLS/SSL                                                                                                            |
| FTP                                   | port 990 (TCP, UDP)            | FTPS protocol (data), FTP over TLS/SSL                                                                                                            |
| IMAP4                                 | port 993                       |                                                                                                                                                   |

IMAP4                        | Port 993
                             | over SSL	TCP	Internet Message Access Protocol over TLS/SSL (IMAPS)
                             |  
POP3                         | Port 995
                             | over SSL	(TCP, UDP) Post Office Protocol 3 over TLS/SSL
                             |  
Microsoft                    | Port 1025
                             | RPC	TCP	Microsoft operating systems tend to allocate one or more unsuspected, publicly exposed services (probably DCOM, but who knows) among the first handful of ports immediately above the end of the service port range (1024+).              |
                             |  
OpenVPN                      | Port 1194
                             | (TCP, UDP) OpenVPN
                             |  
WASTE                        | Port 1337
                             | unofficial	WASTE Encrypted File Sharing Program
                             |  
Cisco                        | Port 1589
                             | VQP	(TCP, UDP) Cisco VLAN Query Protocol (VQP)
                             |  
Steam                        | Port 1725
                             | UDP	Valve Steam Client uses port 1725
                             |  
cPanel                       | Port 2082
                             | unofficial	cPanel default
                             |  
radsec,                      | Port 2083
                             | (TCP, UDP)  Secure RADIUS Service (radsec), cPanel default SSL
                             |  
Oracle                       | Port 2483
                             | DB	(TCP, UDP) Oracle database listening for insecure client connections to the listener, replaces port 1521
                             |  
Oracle                       | Port 2484
                             | DB	(TCP, UDP) Oracle database listening for SSL client connections to the listener
                             |  
Symantec                     | Port 2967
                             | AV	(TCP, UDP) Symantec System Center agent (SSC-AGENT)
                             |  
XBOX                         | Port 3074
                             | Live	(TCP, UDP) Xbox LIVE and Games for Windows – Live
                             |  
MySQL                        | Port 3306
                             | TCP	 MySQL database system
                             |  
World                        | Port 3724
                             | of Warcraft	(TCP, UDP) Some Blizzard games, Unofficial Club Penguin Disney online game for kids
                             |  
Google                       | Port 4664
                             | Desktop	unofficial	Google Desktop Search
                             |  
PostgreSQL                   | Port 5432
                             | TCP	PostgreSQL database system
                             |  
RFB/VNC                      | Port 5900
                             | Server	(TCP, UDP) virtual Network Computing (VNC) Remote Frame Buffer RFB protocol
                             |  
IRC                          | Port 6665
                             | TCP	Internet Relay Chat
                             |  
IRC                          | Port 6669
                             | TCP	Internet Relay Chat
                             |  
BitTorrent                   | Port 6881
                             | unofficial	BitTorrent is part of the full range of ports used most often
                             |  
BitTorrent                   | Port 6999
                             | unofficial	BitTorrent is part of the full range of ports used most often
                             |  
Quicktime                    | Port 6970
                             | unofficial	QuickTime Streaming Server
                             |  
Kaspersky                    | Port 8086
                             | AV	TCP	Kaspersky AV Control Center
                             |  
Kaspersky                    | Port 8087
                             | AV	UDP	Kaspersky AV Control Center
                             |  
VMware                       | Port 8222
                             | Server	(TCP, UDP) VMware Server Management User Interface (insecure Web interface).
                             |  
PDL                          | Port 9100
                             | TCP	PDL Data Stream, used for printing to certain network printers[1
                             |  
BackupExec                   | Port 10000
                             | unofficial	Webmin, Web-based Unix/Linux system administration tool (default port)
                             |  
NetBus                       | Port 12345
                             | unofficial	NetBus remote administration tool (often Trojan horse).
                             |  
Sub7                         | Port 27374
                             | unofficial	Sub7 default
                             |  
Back                         | Port 18006
                             |  Orifice	unofficial	Back Orifice 2000 remote administration tools
```
