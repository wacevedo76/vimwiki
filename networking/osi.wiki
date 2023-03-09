-- The Open Systems Interconnect (OSI) Model -----------------------------------
== OSI / TCP models ==

  `+--------------+-------------+--------------------------+----------------+-----------------------------------------------------------------------+`
  `|  OSI         | Protocols   | Protocol Data Unit (PDU) | TCP/IP Model   |  Function                                                             |`
  `+--------------+-------------+--------------------------+----------------+-----------------------------------------------------------------------+`
  `| Application  | DHCP, DNS   |                          |                | High-level APIs, including resource sharing, remote file access       |`
  `|--------------| FTP, HTTP   |                          |                |-----------------------------------------------------------------------|`
  `| Presentation | POP, SMTP   |                          |                | Translation of data between a networking service and an application   |`
  `|              | SSH, etc    |                          |                | including character encoding, data compression, and encryption        |`
  `|              |             |      Data                |                | decryption                                                            |`
  `|              |             |                          | Application    |                                                                       |`
  `+--------------+             |                          |                +-----------------------------------------------------------------------+`
  `| Session      |             |                          |                | Managing communication sessions, i.e. continuous exchage of           |`
  `|              |             |                          |                | information in the form of mutiple back-and-forth transmissions       |`
  `|              |             |                          |                | between nodes                                                         |`
  `|              |             |                          |                |                                                                       |`
  `+--------------+------Ports--+--------------------------+----------------+-----------------------------------------------------------------------+`
  `| Transport    | TCP   RTP   |      Segments (TCP)      | Transport      | Reliable transmission of data segments between points on a            |`
  `|              | UDP         |      Datagrams (UDP)     |                | network, including segmentation, acknowledgement and multiplexing     |`
  `+--------------+-------------+--------------------------+----------------+-----------------------------------------------------------------------+`
  `| Network      | ICMP, IGMP  |                          | Internet       | Structuring and managing a multi-node network, including addressing   |`
  `|              | IP4, IP6    |      Packets             |                | routing and traffic control                                           |`
  `+--------------+--------Arp--+--------------------------+----------------+-----------------------------------------------------------------------+`
  `| Data Link    | MAC Address |                          |                | Reliable transmission of data frames between two nodes connected by a |`
  `|              |             |      Frames              |                | physical layer                                                        |`
  `+--------------+-------------+--------------------------+ Network Access +-----------------------------------------------------------------------+`
  `| Physical     | Ethernet    |      Bits                | Net. Interface | Transmission and reception of raw bit streams over a physical medium  |`
  `|              | Fiber       |                          |                |                                                                       |`
  `|              | Wifi        |                          |                |                                                                       |`
  `|______________|_____________|__________________________|________________|_______________________________________________________________________|`


== TCP/IP Model ==
`                         +-------------------------+   +-------------------------+`
`                         | TCP +-----------------+ |   | UDP +-----------------+ |`
` Application Layer       |     |  Stream         | |   |     |  Message        | |`
`                         |     +-----------------+ |   |     +-----------------+ |`
`                         |                         |   |                         |`
`                         |     +-----------------+ |   |     +-----------------+ |`
` Transport Layer         |     |  Segment        | |   |     |  packet         | |`
`                         |     +-----------------+ |   |     +-----------------+ |`
`                         |                         |   |                         |`
`                         |     +-----------------+ |   |     +-----------------+ |`
` Internet Layer          |     |  Datagram       | |   |     |  Datagram       | |`
`                         |     +-----------------+ |   |     +-----------------+ |`
`                         |                         |   |                         |`
`                         |     +-----------------+ |   |     +-----------------+ |`
` Network Acces Layer     |     |  Frame          | |   |     |  frame          | |`
`                         |     +-----------------+ |   |     +-----------------+ |`
`                         |                         |   |                         |`
`                         +-------------------------+   +-------------------------+`

Notes:
OSI Model Layers and descriptions
  7 - Application            | Specifies methods for accomplishing some user-
                             | initiated task. Application-layer protocols
                             | tend to be devised and implemented by
                             | application developers. Exmaples include FTP,
                             | Skype, etc
                             |
  6 - Presentation           | Specifies methods for expressing dat aformats
                             | and translation rules for applications. A
                             | standard example would b conversion of EBCDIC
                             | to ASCII coding for characters (but of little
                             | concern today). Encryption is somtimes
                             | associated with this layer but can also be
                             | found in other layers
                             |
  5 - Session                | Specifies methods for multiple connections
                             | constituting a communication session. These may
                             | include closing connectins, restarting
                             | connectins, and checkpointing progress. ISO
                             | X.225 is a session-layer protocol.
                             |
  4 - Transport              | Specifies methods for conections or
                             |  associations between multiple programs running
                             |  on the same computer system . This layer may
                             |  alos implement reliable delivery if not
                             |  implemented elsewhere(e.g., Internet TCP, ISO
                             |  TP4)
                             |
  3 - Network or Internetwork| Specifies methods for communicating in a
                             | multihop fashion across potentially different
                             | type of link networks. For packet networks,
                             | describes an abstract packet format and its
                             | standard addressing structure (e.g., IP datagram
                             | , x.25 PLP, ISO CLNP)
                             |
  2 - Link                   | Specifies methods for communication across a
                             | single link, incuding "media access" control
                             | protocols when multiple systems share the same
                             | media. Error detection is commonly included at
                             | this layer, along with link-layer address
                             | formats (e.g., Ethernet, Wi-Fi, IS 13239/HDLC).
                             |
  1 - Physical               | Specifies connectors, data rates, and how bits
                             | are encoded on some media. Also describes low-
                             | level error detection and correction, plus
                             | frequency assignments. Examples include V.92,
                             | Ethernet 1000BASE-T, SONET/SDH
                             |

Layer 2 (Data Link) notes:
  data type: Frames          |
                             |
  Logical Link control       | Provides connection services and allows
                             | acknowledgement of receipt of messages.
                             | Also provides basic error control functions.
                             |
  Isochronous                | Network device use a common reference clock
                             | source and create time slots for transmission
                             |
                             |
  Synchronous                | Network devices agree on clocking method to
                             | indicate beginning and end of frams and can use
                             | control characters
--------------------------------------------------------------------------------
Layer 3 (Network) notes:
  data type: Packets         |
                             |
  How data is forwarded      | Packet Switching (routing) (most often used)
  (routed)                   |   Data is divided into packets and then forwarded
                             |
                             | Circuit Switching
                             |   Dedicated communication link is established
                             |   between two devices
                             |
                             | Message Switching
                             |   Data is divided into messages which may be
                             |   stored and then forwarded
                             |
  Route Discovery and        | Manually configured as a static rout or
  Selection                  | dynamically through a routing protocol
                             |
                             | Some routing protocols include:
                             | * RIP
                             | * OSPF
                             | * EIGRP
                             |
  Connection Services        | Augment Layer 2 connection services to improve
                             | Reliability
                             |
                             | * Flow control
                             | * Packet reordering
                             |
  Internet Control Message   | Sends error messages and operational information
  Protocol (ICMP)            | to an IP destination
                             |
                             | Some tools used are:
                             | * ping
                             | * traceroute
--------------------------------------------------------------------------------
Layer 4 (Transport) notes
  data type: segment(TCP)    | the two primary transport protocol
             data gram (UDP) | * TCP
                             | * UDP
                             |
  Transport Control Protocol | Connection-oriented protocol that is a reliable
  (TCP) (segments)           | way to transport segments across the network
                             |
                             | Client >--Syn (seq=x)--------------> Server
                             | client <--Syn Ack (ack=x+1 seq=y)--< Server
                             | client >--Ack (ack=y+1 seq=x+1)----> Server
                             | client <----------data-------------< Server
                             |
  User Diagram Protocol      | Connectionless protocol that is an unreliable
  (UDP) (datagram)           | way to transport segments across the network
                             |
  Comparison Chart           |           TCP            |             UDP           |
`                             |       * Reliable         |      * Unreliable         |`
`                             |  * Connection-oriented   |     * Connectionless      |`
`                             |  *Segment retransmission |     * No windowing or     |`
`                             |  and flow control through|      retransmission       |`
`                             |  windowing               |                           |`
`                             |   * Segment sequencing   |    * No sequencing        |`
`                             |                          |                           |`
                             | Layer 4 Reliability features include:
                             | * Windowing
                             | * Buffering
                             |
                             |
                             |
                             |
                             |
Acronyms:
OSI (1-7) (P)lease (D)o (N)o (Throw) (S)ausage (P)izza (A)way
OSI (7-1) (A)ll (P)eople (S)eem (T)o (N)eed (D)ata (P)rocessing
Payload names: (D)o (S)ome (P)eople (F)ear (B)irthdays

Layer 4 - Segments -> Protocol Data Units

--------------------------------------------------------------------------------
Data Ecapsulation and decapsulation within the OSI model context
--------------------------------------------------------------------------------
  - Ethernet header
  - Internet

== The encapsulated structure of a TCP/IP packet ==

  `+----------------------------------+`
  `|      layer 2 information         |`
  `|      (MAC address)               |`
  `|  +----------------------------+  |`
  `|  |     Layer 3 information    |  |`
  `|  |     (IP address            |  |`
  `|  |   +---------------------+  |  |`
  `|  |   |    TCP header       |  |  |`
  `| F| P +---------------------+  |  |`
  `| r| a | S                   |  |  |`
  `| a| c | e      Data         |  |  |`
  `| m| k | g                   |  |  |`
  `| e| e | m                   |  |  |`
  `|  | t | e                   |  |  |`
  `|  |   | n                   |  |  |`
  `|  |   | t                   |  |  |`
  `|  |   f_____________________+  |  |`
  `|  |____________________________|  |`
  `|__________________________________|`


== Overhead of TCP and UDP ==
=== TCP Header (20 bytes) ===
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `| Offsets | Octet |               0                       |                   1                   |                   2                   |                   3                   |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `| Octet   | Bit   |  0 |  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|    0    |   0   |                  Source Port                                                  |            Destination port                                                   |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|    4    |  32   |                                                                 Sequence Number                                                                               |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|    8    |  64   |                                                           Acknowledgment Number (if ACK set)                                                                  |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|   12    |  96   | Data offset  | Reserved          | TCP Flags                                  |                                                                               |`
  `|         |       |              |                   |N   |C   |E   |U   |A   |P   |R   |S   |F   |                                                                               |`
  `|         |       |              |                   |S   |W   |C   |R   |C   |S   |S   |Y   |I   |            Window Size                                                        |`
  `|         |       |              | 000               |    |R   |E   |G   |K   |H   |T   |N   |N   |                                                                               |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|   16    | 128   |                  Checksum                                                     |            Urgent pointer (if URG set)                                        |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`
  `|   20    | 160   |                                         Options (if dad offset > 5. Padded at the ent with "-" bytes if necessary.)                                           |`
  `+---------+-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+`

=== UDP Header (8 bytes) ===

`+-------------+------------------+`
`| Source Port | Destination Port |`
`+-------------+------------------+`
`|  UDP Length |  UDP Checksum    |`
`+-------------+------------------+`
