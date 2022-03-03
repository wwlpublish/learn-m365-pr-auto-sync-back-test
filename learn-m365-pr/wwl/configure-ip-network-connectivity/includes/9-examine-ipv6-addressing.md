The most obvious, distinguishing feature of IPv6 is its use of much larger addresses. IPv4 addresses are expressed in four groups of decimal numbers, such as 192.168.1.1. Each grouping of numbers represents a binary octet. In binary, the preceding number is as follows:

```
11000000.10101000.00000001.00000001

```

(four octets = 32 bits) The size of an address in IPv6 is four times larger than an IPv4 address. IPv6 addresses are expressed in hexadecimal, as the following example shows:

```
2001:DB8::2F3B:2AA:FF:FE28:9C5A

```

This might seem complex for end users, but the assumption is that users will rely on DNS names to resolve hosts, meaning they will rarely type IPv6 addresses manually. The IPv6 address in hexadecimal also is easier to convert to binary. This makes it simpler to work with subnets and calculate hosts and networks.

## Benefits of IPv6

The IPv6 protocol provides the following benefits:

 -  **Large address space**. A 32-bit address space can have 4,294,967,296 possible addresses. IPv6 uses 128-bit address spaces, which can have 340,282,366,920,938,463,463,374,607,431,768,211,456 (or 3.4x10^38 or 340 undecillion) possible addresses.
 -  **Hierarchical addressing and routing infrastructure**. The IPv6 address space is more efficient for routers, which means that even though there are many more addresses, routers can process data much more efficiently because of address optimization.
 -  **Stateless and stateful address configuration**. IPv6 has autoconfiguration capability without DHCP, and it can discover router information so that hosts can access the Internet. This is a stateless address configuration. A stateful address configuration is when you use the DHCP version 6 (DHCPv6) protocol. Stateful configuration has two more configuration levels: one in which DHCP provides all the information, including the IP address and configuration settings, and another in which DHCP provides just configuration settings.
 -  **Required support for Internet Protocol security (IPsec)**. The IPv6 standards require support for the Authentication Header (AH) and encapsulating security payload (ESP) headers that IPsec defines. Although IPsec does not define support for its specific authentication methods and cryptographic algorithms, IPsec is defined from the start as the way to protect IPv6 packets.

    > [!NOTE]
    > IPsec provides for authentication and, optionally, encryption for communications between hosts.

 -  **Restored end-to-end communication**. The global addressing model for IPv6 traffic means that translation between different types of addresses is not necessary, such as the translation done by NAT devices for IPv4 traffic. This simplifies communication because you do not need to use NAT devices for peer-to-peer applications, such as video conferencing.
 -  **Prioritized delivery**. IPv6 contains a field in the packet that lets network devices determine that the packet processing should occur at a rate that you specify. This enables traffic prioritization. For example, when you are streaming video traffic, it is critical that the packets arrive in a timely manner. You can set this field to ensure that network devices determine that the packet delivery is time-sensitive.
 -  **Support for single-subnet environments**. IPv6 has much better support of automatic configuration and operation on networks consisting of a single subnet. You can use this to create temporary, improvised networks through which you can connect and share information.
 -  **Extensibility**. The design of IPv6 enables you to extend it with less constraint than IPv4.

## IPv6 address types

IPv6 address types are similar to IPv4 address types. The IPv6 address types are:

 -  **Unicast**. An IPv6 unicast address is equivalent to an IPv4 unicast address. You can use this address type for one-to-one communication between hosts. Each IPv6 host has multiple unicast addresses. There are three types of unicast addresses:
 -  **Global unicast addresses**. These are equivalent to public IPv4 addresses. They are globally routable and reachable on the IPv6 portion of the Internet.
 -  **Link-local addresses**. Hosts use link-local addresses when communicating with neighboring hosts on the same link. For example, on a single-link IPv6 network with no router, hosts communicate by using link-local addresses. Link-local addresses are local-use unicast addresses with the following properties:
    
     -  IPv6 link-local addresses are equivalent to IPv4 APIPA addresses.
     -  Link-local addresses always begin with FE80.
 -  **Unique local unicast addresses**. Unique local addresses provide an equivalent to the private IPv4 address space for organizations, without the overlap in address space when organizations combine.
 -  **Multicast**. An IPv6 multicast is equivalent to an IPv4 multicast address. You use this address type for one-to-many communication between computers that you define as using the same multicast address.
 -  **Anycast**. An anycast address is an IPv6 unicast address that is assigned to multiple computers. When IPv6 addresses communicate to an anycast address, only the closest host responds. You typically use this address type for locating services or the nearest router.

In IPv4, you typically assign a single host with a single unicast address. However, in IPv6, you can assign multiple unicast addresses to each host. To verify communication processes on a network, you must know the purposes for which IPv6 uses each of these addresses.

## Interface identifiers

The last 64 bits of an IPv6 address are the interface identifier. This is equivalent to the host ID in an IPv4 address. Each interface on an IPv6 network must have a unique interface identifier. Because the interface identifier is unique to each interface, IPv6 uses interface identifiers rather than MAC addresses to identify hosts uniquely.
