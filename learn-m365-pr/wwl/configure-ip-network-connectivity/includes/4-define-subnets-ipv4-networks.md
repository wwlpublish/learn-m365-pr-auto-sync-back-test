A subnet is a network segment. Single or multiple routers separate the subnet from the rest of the network. When your Internet service provider (ISP) assigns a network to a Class A, B, or C address range, you often must subdivide the range to match the network’s physical layout. Subdividing enables you to break a large network into smaller, logical subnets.

When you subdivide a network into subnets, you must create a unique ID for each subnet, which you derive from the main network ID. To create subnets, you must allocate some of the bits in the host ID to the network ID. By doing so, you can create more networks.

:::image type="content" source="../media/define-subnet-masks-93e35cfa.jpg" alt-text="Image showing subnet masks.":::


By using subnets, you can:

 -  Use a single Class A, B, or C network across multiple physical locations.
 -  Reduce network congestion by segmenting traffic and reducing broadcasts on each segment.
 -  Overcome the limitations of current technologies, such as exceeding the maximum number of hosts that each segment can have.

A **subnet mask** specifies which part of an IPv4 address is the network ID and which is the host ID. A subnet mask has four octets, similar to an IPv4 address.

## Simple IPv4 networks

In simple IPv4 networks, the subnet mask defines full octets as part of the network and host IDs. A 255 represents an octet that is part of the network ID, and a 0 represents an octet that is part of the host ID. Class A, B, and C networks use default subnet masks. The following table lists the characteristics of each IP address class.

:::row:::
  :::column:::
    **Class**
  :::column-end:::
  :::column:::
    **First octet**
  :::column-end:::
  :::column:::
    **Default subnet mask**
  :::column-end:::
  :::column:::
    **Number of networks**
  :::column-end:::
  :::column:::
    **Number of hosts per network**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A
  :::column-end:::
  :::column:::
    1 to 127
  :::column-end:::
  :::column:::
    255.0.0.0
  :::column-end:::
  :::column:::
    126
  :::column-end:::
  :::column:::
    16,777,214
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    B
  :::column-end:::
  :::column:::
    128 to 191
  :::column-end:::
  :::column:::
    255.255.0.0
  :::column-end:::
  :::column:::
    16,384
  :::column-end:::
  :::column:::
    65,534
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    C
  :::column-end:::
  :::column:::
    192 to 223
  :::column-end:::
  :::column:::
    255.255.255.0
  :::column-end:::
  :::column:::
    2,097,152
  :::column-end:::
  :::column:::
    254
  :::column-end:::
:::row-end:::


## Complex IPv4 networks

In complex networks, subnet masks might not be simple combinations of 255 and 0. Rather, you might subdivide one octet with some bits for the network ID and some for the host ID. If you do not use an octet for subnetting, this is classless addressing, or Classless Interdomain Routing (CIDR). You use more or less of the octet. This type of subnetting uses a different notation, which the following example shows:

```
172.16.16.1/255.255.240.0

```

The following example shows the more common representation of classless IPv4 addressing:

```
172.16.16.1/20

```

The /20 represents how many leftmost subnet bits are set to 1 in the mask. This notation style is called CIDR. This subnet mask in binary notation would look like this:

```
11111111.11111111.11110000.00000000

```

The first 20 bits are set to 1 and indicate the subnet ID, and the last 12 zero placeholders represent how many bits are used to identify the host.

## Configuring connectivity to other subnets

A **default gateway** is a device on a TCP/IP internetwork, usually a router, which forwards IP packets to other subnets. A router connects groups of subnets to create an intranet. In an intranet, any given subnet might have several routers that connect it to other local and remote subnets. You must configure one of the routers as the default gateway for local hosts so that the local hosts can communicate with hosts on remote networks.

When a host delivers an IPv4 packet, it performs an internal calculation by using the subnet mask to determine whether the destination host is on the same network or on a remote network. If the destination host is on the same network, the local host delivers the packet. If the destination host is on a different network, the host transmits the packet to a router for delivery.

> [!NOTE]
> The host determines the MAC address of the router for delivery, and the initiating host addresses the router explicitly, at the media access layer.

When a host on the network uses IPv4 to transmit a packet to a destination subnet, IPv4 consults the internal routing table to determine the appropriate router to ensure that the packet reaches the destination subnet. If the routing table does not contain any routing information about the destination subnet, IPv4 forwards the packet to the default gateway. The host assumes that the default gateway contains the required routing information.

In most cases, you can use a Dynamic Host Configuration Protocol (DHCP) server to assign the default gateway automatically to a DHCP client. This is more straightforward than manually assigning a default gateway on each host.
