--------------------------------------------------------------------------------
# Networking notes 

## Wired and Wireless Network Topologies 
  A **Bridge** is a virtual network interface that connects multiple physical
  network interfaces together, allowing them to communicate as if they were on
  the same physical network.  
  
  A **Bond** is a type of bridge that combines multiple
  physical network interfaces into a single virtual interface, allowing for
  increased throughput and redundancy.
  
  A **Vlan** is a virtual local area network
  that allows multiple networks to be logically separated on the same physical
  network. VLANs are used to segment networks into smaller, more secure segments.

### Topology 
```
  Topology                   | Physical: The actual layout of the computer
                             |   cables and other network devices
                             | Logical: The way in which the network appears
                             |   to the devices that use it
                             |
                             | Common topologies
                             |   * Bus
                             |   * Ring
                             |   * Star
                             |   * Mesh
                             |   * Wireless
                             |
  ==== Bus ====
                             | * Uses a trunk or backbone to connect all the
                             |   computers on the network
                             | * Systems connect to this backbone using T
                             |   connectors or taps (vampire tap)
                             | * To avoid signal reflection, a physical bus
                             |   topology requires that each end of the physical
                             |   bus be terminated, with on end also being
                             |   grounded.
                             | * A hub or switch is not needed in this installation
--------------------------------------------------------------------------------
  Advantages / Disadvantages
  compared to other topologies, a bus  |  Network disruption might occure when
  is cheap and easy to implement.      |  added or removed
                                       |
  Requires less cable than other       | Because all systems on the network
  topologies                           | connect to a single backbone, a break
                                       | in the cable prevents all systems from
                                       | accessing the network.
                                       |
  Does not requre any specialized      | Difficult to troubleshoot
  network equipment.                   |
--------------------------------------------------------------------------------
#### Ring 
                             | * Logical ring; The data travels in a circular
                             |   form from one computer to another on the network.
                             |   (It is not a physical ring topology)
                             | * A Hub or Switch is not needed
                             | * Most commonly wired in a start configuration, In
     (Multistation access    |   In a token ring network, a multistation access unit
        Unit - MSAU)         |   (MSAU) is equivalent to a hub / switch.
                             | * To create a complet ring, the Ring-in port (RI)
                             |   on each MSAU is connecte to the the rign-out
                             |   (RO) port on another MSAU. The last MSAU in the
                             |   ring is then connected to the first to complete
                             |   the ring.
--------------------------------------------------------------------------------
      Advantages                            Disadvantages
  Cable faults are easily located,     |  Expansion to the network can cause
  making troubleshooting easier.       |  network disruption
                                       |
  Ring network are moderately easy to  |  a single break in the cable can disrupt
  install                              |  the entire network.
--------------------------------------------------------------------------------
      Advantages                            Disadvantages
#### Star 
                             | * All computers and other network devices connect
                             |   to a central device called a hub or a switch
``` 
## Related topics
* [OSI Model](networking/osi)
* [Subnetting](networking/Subnetting)
* [Routing](Routing)
* [ports](networking/ports-protocols)

