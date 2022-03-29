To configure network connectivity, you must be familiar with IPv4 addresses and how they work. Communication between computers can happen only if they can identify each other on the network. When you assign a unique IPv4 address to each networked computer, the IPv4 address identifies the computer to the other computers on the network. That IPv4 address, combined with the subnet mask, identifies the computer’s location on the network, just as the combination of a number and a street name identify the location of a house.

:::image type="content" source="../media/overview-ip4v-811d752b.jpg" alt-text="Diagram showing the relationship of IPv4.":::


## Overview of connecting with another network host

In a typical situation, communication starts with a request to connect to another host by its computer name. However, to communicate, the requesting host needs to know the media access control (MAC) address of the receiving host’s network interface. Conversely, the receiving host needs to know the requesting host’s MAC address. Once the requesting host discovers the MAC information, it caches it locally. A MAC address is a hard-coded, unique identifier assigned to network interfaces by the manufacturers of network adapters. Before the requesting host can find the receiving host’s MAC address, a number of steps occur.

The following is a high-level overview of these steps:

1.  A host sends a request to connect to Server. The name Server1 must be resolved to an IPv4 address.
2.  Once the sender knows the recipient’s IPv4 address, it uses the subnet mask to determine whether the IPv4 address is remote or on the local subnet.
3.  If it is local, an Address Resolution Protocol (ARP) request is broadcast on the local subnet. If it is remote, an ARP request is sent to the default gateway and then routed to the correct subnet.
4.  The host that owns that IPv4 address will respond with its MAC address and a request for the sender’s MAC address.
5.  Once the exchange of MAC addresses completes, IPv4 communication negotiation and the exchange of IP data packets can occur.

## Components of an IPv4 address

IPv4 uses 32-bit addresses. If you view an IPv4 address in its binary format, it has 32 characters, as the following example shows:

```
11000000101010000000000111001000

```

IPv4 divides the address into four octets, as the following example shows:

```
11000000.10101000.00000001.11001000

```

To make the IP addresses more readable, binary representation of the address typically shows it in decimal form, as the following example shows:

```
192.168.1.200

```

In conjunction with a subnet mask, the address identifies:

 -  The computer’s unique identity, which is the host ID.
 -  The subnet on which the computer resides, which is the network ID.

This enables a networked computer to communicate with other networked computers in a routed environment.

## IPv4 address classes

The Internet Assigned Numbers Authority (IANA) organizes IPv4 addresses into classes, and the number of hosts in a network determines the required class of addresses. Class A through Class E are the names that IANA has specified for IPv4 address classes.

Classes A, B, and C are IP addresses that you can assign to host computers as unique IP addresses, whereas you can use Class D for multicasting. Additionally, IANA reserves Class E for experimental use.
