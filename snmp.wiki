--------------------------------------------------------------------------------
= Simple Network Managment Protocol =
--------------------------------------------------------------------------------
== Other related terms ==
TLS                          | Transport layer Security - Cryptographic protocols
                             | designed to provide communications security over 
                             | a computer network
                             |
--------------------------------------------------------------------------------
== Terms ==
OID - Object Identifier      | a numerical Identifier for some aspect of a 
                             | system which has been set to be monitored
                             |--------------------------------------------------
                             | * Something that can gather information about on 
                             |   an SNMP enabled device
                             | * Identified by a Name - Object Name
                             | * Data-Type Definition - counter, sring, gauge, integer
                             | * Level of access - read/write
                             | * Range information
                             |
  How to locate 'sysUpTime'  | sysUpTime - .1.3.6.1.2.1.3
  from RFC-1213 MIB?         | . iso                        1
                             |   . dod                      3
                             |     . internet               6
                             |       . mgmt-2               1
                             |         . mib-2              2
                             |           . system           1  <--- most MIBs beging here
                             |             . sysDescr
                             |             . sysObjectID
                             |             . < sysUpTime >  3  <---- Thie is the 3rd obj
                             |             . sysContact
                             |             . SysName
                             |             . sysLocation
                             |             . sysServices
                             |
                             |  .iso.org.dodl.internet.mgmt.mib-2.system.sysUpTime
                             |
  example                    | HOST-RESOURCES-MIB::hrMemorySize.0
                             | The module HOST-RESOURCES-MIB contains a whole bunch of 
                             | objects defined in a specific standard
                             |
                             | .iso.org.dod.internet.mgmt.mib-2.host.hrSystem.hrMemorySize.0
                             | .1.3.6.1.2.1.25.2.2.0
                             |
MIB - Managment Informaton   | a text file which is used to translate an OID 
      Base                   | into 'word' based OIDs
                             |
                             | SNMP organizes infomation hierachically, arranging 
                             | everythin by category and sub-category and so on.
                             | The definition of this tree is called a Management
                             | Information base or MIB. An idividual entry in the 
                             | MIB is called an object. Most objects have a value
                             | 
                             | MIB  = Dashboard
                             |
                             |
                             |
                             |
SMI - Structure of           | The format in which MIBs are written
      Management Information | current version is SMI-2 (version 2) 
                             | It's format requires defining exatly what data you're
                             | presenting, and how it is presented.  SMI is a  
                             | slightly tweaked subset of Abstract Syntax Notation
                             | version 1 (ASN.1)
                             |
ASN - Abstract Syntax        | Phone, manufacturing, power, and other complex 
   notation                  | interconnected systems use ASN.1, many use SMI-2
                             | ASN is the syntax from which SMI is derived
                             |
                             |
Polliing                     | the Network monitor connects to a device 
                             | on port 161
                             |
Notifying                    | Device sends OID related mesage to monitor 
                             | the monitoring system on port 162
                             |
traps, notifications or      | the OID messages send from the device
informs                      | 
                             |
SNMP walk                    | a simple way to set up the collectio of information 
                             | an SNMP enabled device. It will allow you to see 
                             | all of the OID parameters available on your SNMP
                             | device and ten set rules against the values
                             |
Object groups                | A mib might batch a bunch of related object together
                             | as a group. Each group has its own object, but it's
                             | purely organizational. you will never see that 
                             | object in a walk. The groupd has no value. you can
                             | query by the group name or OID, though
                             |
Tables                       | Some groups are very specifically formatted, for 
                             | example
                             |  IF-MIB::ifName.1 = STRING: ether1-home
                             |  IF-MIB::ifName.2 = STRING: ether2-lab
                             |  ...
                             |  IF-MIB::ifName.10 = STRING: ether10
                             |  IF-MIB::ifName.11 = STRING: bridge
                             |  IF-MIB::ifInMulticastPkts.1 = Counter32: 0
                             |  IF-MIB::ifInMulticastPkts.2 = Counter32: 0
--------------------------------------------------------------------------------
== System Components ==
SNMP manager                 | Client software that issues SNMP requests. It's 
                             | called a manager because it's expected to extract
                             | management information from devices and issue 
                             | commands to them,
                             |
SNMP agent                   | The server running on a device such as a router, 
                             | server, or worksation. An agent is a little more 
                             | dynamic than most server software; it's expected 
                             | to be able to interrogate the local system and 
                             | provide information to the manager, and it might 
                             | even reconfigure the host if it's configured 
                             | properly.
                             |
Network magement system      | a manager that's designed to collect data and 
  (NMS)                      | issue commands to agents. It probably also runs
                             | tools for managing systems via several other 
                             | protocols. It includes programs that transform 
                             | SNMP and other data into pretty human-readable 
                             | graphs so you can make decisions.
                             |
Monitoring systems           | A server or software that runs SNMP queries and 
                             | transforms the data into human-friendly graphs
                             | and charts and tables, and/or sends alerts when 
                             | something breaksj
--------------------------------------------------------------------------------
examples:
  Monitoring systesm: Cacti, MRTG, Graphite...
  Having some NMS feature: Zabbix, Nagios, Icinga
  Full featured NMSes: OpenNMS HP BTO?OpenView
--------------------------------------------------------------------------------
An MIB provides definitions for what the objects refer to. SNMP supports many 
differt but interrelated MIBs. MIB names are generally in all caps, except when 
the authors are trying to communicate something through the name. 
  SNMPvs-MIB                 | General host information under SNMPv2c
  MIB HOST-RESOURCES-MIB     | contains a bunch of stuff for servers and 
                             | worksations, such as memory and processes and 
                             | printer errors
  IF-MIB                     | An MIB for network interfaces
  IP-MIB                     | IP and ICMP traffic
--------------------------------------------------------------------------------
== Common OID Value Type Units == 
Timeticks                    | on hundredth of a second. This is a 32-bit number
                             | so its maximum value is a litter over 497 days
                             | it is almost always used for timekeeping
                             |
Interger / integer32         | a signed 32-bit number ranging from -2,147,483,648
                             | to 2,147,483,647. Agenst use integer for all sorts 
                             | of things
                             |
String                       | contains either binary or text data, most 
                             | implementations and most MIs restring it to 255 
                             | characters, while octet string includes binary
                             |
Object Identifier (OID)      | litterally another OID, an ojbect that points to 
                             | another OID helps glue different parts of the MIB
                             | tree together
                             |
IP Address                   | literal IPv4 adresses, used for networking, mostly 
                             | used for routing and sockets
                             |
counter32 and counter64      | are 32-bit and 64-bit counters. Used to count 
                             | something, such as the umber of packets sent or the
                             | number of memory allocation failures. Loops back when
                             | reaching its limit, SNMPv1 is based on SMI-1 and 
                             | doesn't include counter64 
                             |
guage32                      | can increase and decrease. Agents use gauges for 
                             | current levels of something, such as current network
                             | utilization or the instantaneous swap space used
--------------------------------------------------------------------------------
Notes:
  SNMP version 3 (SNMPv3) is the current protocol. It's extensible, encrypted, and
  flexibe.
