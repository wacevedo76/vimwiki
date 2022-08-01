

Well-Known/Reserved Ports: Ports 0 - 1023
          Ephemeral Ports: Ports 1024 - 65,535


--------------------------------------------------------------------------------
Ports and protocols
--------------------------------------------------------------------------------
`  Echo                       | Port 7        | Echo Service`
`                             | (TCP, UDP) |`
`--------------------------------------------------------------------------------`
`  File Transfer Protocol     | Ports 20, 21  | Provides insecure file Transfers`
`  (FTP)                      | (TCP,UDP)     | (no encryption)`
`--------------------------------------------------------------------------------`
`  Secure Shell (SSH)         |               | Provides secure remote control`
`  Secure Copy  (SCP)         | Port 22       | of another machine using a`
`  Secure File Transfer       | (TCP, SCTP    | text-based environment`
`  Protocol (SFTP)            |  SCTP)        | Provides secure file transfers`
`--------------------------------------------------------------------------------`
`  Telnet                     |               | Provides insecure remote control`
`                             | Port 23       | of another machine using a text-`
`                             |               | based environment (no encryption)`
`--------------------------------------------------------------------------------`
` Simple Main Transfer        | Port 25       | SMTP is used for email routing`
` Protocol (SMTP)             |               | between mail servers`
`--------------------------------------------------------------------------------`
` Domain Name System (DNS)    | Port 53       | Domain Name system name resolver`
`                             | (TCP, UDP)    |`
`--------------------------------------------------------------------------------`
` Dynamic Host Control        | Ports 67, 68  | Automatically provides network`
` control Protocol (DHCP)     |               | parameters to your clients, `
`                             |               | such as their assigned IP`
`                             |               |`
`                             |               |`
`                             |               |`
`--------------------------------------------------------------------------------`
` Trivial File Transfer       | Port 69       |`
` Protocol (TFTP)             |(UDP)          |`
`--------------------------------------------------------------------------------`
` Hypertext Transfer Protocol | Port 80       | HTTP uses TCP in versions 1.x `
` (HTTP)                      |               | and 2.`
`                             |               | HTTP/3 uses QUIC, a transport`
`                             |               | protocol on top of UDP`
`--------------------------------------------------------------------------------`
` Kerberos                    | Port 88       | Network authentication system`
`                             | (TCP, UDP)    |`
`--------------------------------------------------------------------------------`
` Iso-tsap                    | Port 102      | ISO Transport Service Access`
`                             |               | Point (TSAP) Class 0 protocol`
`--------------------------------------------------------------------------------`
` Post Office Protocol,       | Port 110      |`
` version 3 (POP3)            |               |`
`--------------------------------------------------------------------------------`
` Microsoft End Point Mapper  |               | MS EPMAP also known as DCE/RPC`
` (EPMAP)                     |               | Locator service, used to remotely`
`                             | Port 135      |  manage services including DHCP `
`                             | (TCP, UDP)    | server, DNS server, and WINS.`
`                             |               | Also used by DCOM`
`--------------------------------------------------------------------------------`
` NetBIOS-ns                  |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`
`                             |               |`

`NetBIOS-ns                   | Port 137       |  `
`                             | TCP, UDP	 NetBIOS Name Service, used for name registration and resolution              |`
`NetBIOS-ssn                  | Port 139`
`                             | TCP, UDP	NetBIOS Session Service              |`
`IMAP4                        | Port 143`
`                             | TCP, UDP	 Internet Message Access Protocol (IMAP), management of electronic mail messages on a server              |`
`HP                           | Port 381`
`                             | Openview	TCP, UDP	HP data alarm manager              |`
`HP                           | Port 383`
`                             | Openview	TCP, UDP	HP data alarm manager              |`
`HTTP                         | Port 443`
`                             | over SSL	TCP, UDP, SCTP	Hypertext Transfer Protocol Secure (HTTPS) uses TCP in versions 1.x and 2. HTTP/3 uses QUIC, a transport protocol on top of UDP.              |`
`Kerberos                     | Port 464`
`                             | TCP, UDP	Kerberos Change/Set password              |`
`SMTP                         | Port 465`
`                             | over TLS/SSL, SSM	TCP	Authenticated SMTP over TLS/SSL (SMTPS), URL Rendezvous Directory for SSM (Cisco protocol)              |`
`SMTP                         | Port 587`
`                             | TCP	Email message submission              |`
`Microsoft                    | Port 593`
`                             | DCOM	TCP, UDP	HTTP RPC Ep Map, Remote procedure call over Hypertext Transfer Protocol, often used by Distributed Component Object Model services and Microsoft Exchange Server              |`
`LDAP                         | Port 636`
`                             | over TLS/SSL	TCP, UDP	Lightweight Directory Access Protocol over TLS/SSL              |`
`MS                           | Port 691`
`                             | Exchange	TCP	MS Exchange Routing              |`
`VMware                       | Port 902`
`                             | Server	unofficial	VMware ESXi              |`
`FTP                          | Port 989`
`                             | over SSL	TCP, UDP	FTPS Protocol (data), FTP over TLS/SSL              |`
`FTP                          | Port 990`
`                             | over SSL	TCP, UDP	 FTPS Protocol (control), FTP over TLS/SSL              |`
`IMAP4                        | Port 993`
`                             | over SSL	TCP	Internet Message Access Protocol over TLS/SSL (IMAPS)              |`
`POP3                         | Port 995`
`                             | over SSL	TCP, UDP	Post Office Protocol 3 over TLS/SSL              |`
`Microsoft                    | Port 1025`
`                             | RPC	TCP	Microsoft operating systems tend to allocate one or more unsuspected, publicly exposed services (probably DCOM, but who knows) among the first handful of ports immediately above the end of the service port range (1024+).              |`
`OpenVPN                      | Port 1194`
`                             | TCP, UDP	OpenVPN              |`
`WASTE                        | Port 1337`
`                             | unofficial	WASTE Encrypted File Sharing Program              |`
`Cisco                        | Port 1589`
`                             | VQP	TCP, UDP	Cisco VLAN Query Protocol (VQP)              |`
`Steam                        | Port 1725`
`                             | UDP	Valve Steam Client uses port 1725               |`
`cPanel                       | Port 2082`
`                             | unofficial	cPanel default              |`
`radsec,                      | Port 2083`
`                             | TCP, UDP	 Secure RADIUS Service (radsec), cPanel default SSL              |`
`Oracle                       | Port 2483`
`                             | DB	TCP, UDP	Oracle database listening for insecure client connections to the listener, replaces port 1521              |`
`Oracle                       | Port 2484`
`                             | DB	TCP, UDP	Oracle database listening for SSL client connections to the listener              |`
`Symantec                     | Port 2967`
`                             | AV	TCP, UDP	Symantec System Center agent (SSC-AGENT)              |`
`XBOX                         | Port 3074`
`                             | Live	TCP, UDP	Xbox LIVE and Games for Windows – Live              |`
`MySQL                        | Port 3306`
`                             | TCP	 MySQL database system              |`
`World                        | Port 3724`
`                             | of Warcraft	TCP, UDP	Some Blizzard games, Unofficial Club Penguin Disney online game for kids              |`
`Google                       | Port 4664`
`                             | Desktop	unofficial	Google Desktop Search              |`
`PostgreSQL                   | Port 5432`
`                             | TCP	PostgreSQL database system              |`
`RFB/VNC                      | Port 5900`
`                             | Server	TCP, UDP	virtual Network Computing (VNC) Remote Frame Buffer RFB protocol              |`
`IRC                          | Port 6665`
`                             | TCP	Internet Relay Chat               |`
`IRC                          | Port 6669`
`                             | TCP	Internet Relay Chat               |`
`BitTorrent                   | Port 6881`
`                             | unofficial	BitTorrent is part of the full range of ports used most often              |`
`BitTorrent                   | Port 6999`
`                             | unofficial	BitTorrent is part of the full range of ports used most often              |`
`Quicktime                    | Port 6970`
`                             | unofficial	QuickTime Streaming Server              |`
`Kaspersky                    | Port 8086`
`                             | AV	TCP	Kaspersky AV Control Center              |`
`Kaspersky                    | Port 8087`
`                             | AV	UDP	Kaspersky AV Control Center              |`
`VMware                       | Port 8222`
`                             | Server	TCP, UDP	VMware Server Management User Interface (insecure Web interface).              |`
`PDL                          | Port 9100`
`                             | TCP	PDL Data Stream, used for printing to certain network printers[1              |`
`BackupExec                   | Port 10000`
`                             | unofficial	Webmin, Web-based Unix/Linux system administration tool (default port)              |`
`NetBus                       | Port 12345`
`                             | unofficial	NetBus remote administration tool (often Trojan horse).              |`
`Sub7                         | Port 27374`
`                             | unofficial	Sub7 default              |`
`Back                         | Port 18006`
`                             |  Orifice	unofficial	Back Orifice 2000 remote administration tools              |`
