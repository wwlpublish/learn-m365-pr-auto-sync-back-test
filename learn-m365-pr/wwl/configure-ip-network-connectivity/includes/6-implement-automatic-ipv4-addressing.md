It's important that you know how to assign static IPv4 addresses manually and support devices that use DHCP to assign IPv4 addresses dynamically.

:::image type="content" source="../media/automatic-ipv4-addressing-a5ba420b.jpg" alt-text="Diagrame showing the process of implementing IPv4.":::


## Static configuration

You can configure static IPv4 configuration manually for each of your network’s computers. When you perform IPv4 configuration, you must configure the:

 -  IPv4 address
 -  Subnet mask
 -  Default gateway
 -  Domain Name System (DNS) server

Static configuration requires that you visit each computer and input the IPv4 configuration. This method of computer management is time-consuming if your network has more than 10 to 12 computers. Additionally, making a large number of manual configurations heightens the risk of mistakes.

## DHCPv4

DHCPv4 enables you to assign IPv4 configurations automatically for a large number of computers without having to assign each one individually. The DHCP service receives requests for IPv4 configuration from computers that you configure to obtain an IPv4 address automatically. It also assigns IPv4 information from scopes that you define for each of your network’s subnets. The DHCP service identifies the subnet from which the request originated, and assigns IP configuration from the relevant scope.

DHCP helps simplify the IP configuration process. However, keep in mind that if you use DHCP to assign IPv4 information and the service is business-critical, you must:

 -  Include resilience in your DHCP service design so that the failure of a single server does not prevent the service from functioning.
 -  Configure the scopes on the DHCP server carefully. If you make a mistake, it can affect the whole network, and it can prevent communication.

## IPv4 alternate configuration

If you use a laptop to connect to multiple networks, such as networks at work and at home, each network might require a different IP configuration. Windows supports the use of Automatic Private IP Addressing (APIPA) and an alternate static IP address for this scenario.

When you configure Windows devices to obtain IPv4 addresses from DHCP, use the Alternate Configuration tab to control the behavior if a DHCP server is not available. By default, Windows uses APIPA to assign itself an IP address automatically from the 169.254.0.0 to 169.254.255.255 address range. This enables you to use a DHCP server at a location with DHCP and the need for internet access and the APIPA address range a location without DHCP but the need to communicate between computers (such as a workgroup), without reconfiguring IP settings. Additionally, this is useful for troubleshooting DHCP. If the computer has an address from the APIPA range, it is an indication that the computer cannot communicate with a DHCP server.
