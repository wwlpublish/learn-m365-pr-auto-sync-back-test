Though most networks to which you connect Windows-based devices currently provide IPv4 support, many also support IPv6. To connect computers that are running Windows to IPv6 based networks, you must understand the IPv6 addressing scheme and the differences between IPv4 and IPv6.

## IPv6 in Windows

Windows uses IPv6 by default. Windows includes several features that support IPv6, as described below.

### Windows dual stack

Windows supports both IPv6 and IPv4 in a dual stack configuration. The dual IP stack helps reduce maintenance costs by providing the following features:

 -  Shared transport and framing layer.
 -  Shared filtering for firewalls and IPsec.
 -  Consistent performance, security, and support for both IPv6 and IPv4.

When you connect to a new network that advertises IPv6 routability, Windows tests IPv6 connectivity, and it will only use IPv6 if IPv6 connectivity is actually functioning. Windows also supports a functionality called address sorting. This functionality helps the Windows operating system determine which protocol to use when applications that support both IPv4 and IPv6 addresses are configured for both protocol stacks.

### DirectAccess use of IPv6

DirectAccess enables remote users to access a corporate network anytime they have an Internet connection, because it does not require a virtual private network (VPN). DirectAccess provides a flexible corporate network infrastructure to help you remotely manage and update user PCs on and off a network. DirectAccess makes the end-user experience of accessing corporate resources over an Internet connection nearly indistinguishable from the experience of accessing these resources from a computer at work. DirectAccess uses IPv6 to provide globally routable IP addresses for remote access clients.

### Windows services can use IPv6

Windows services such as file sharing and remote access use IPv6 features, such as IPsec. This includes VPN Reconnect, which uses Internet Key Exchange version 2 (IKEv2), an authentication component of IPv6.

The Windows operating system supports remote troubleshooting capabilities such as Windows Remote Assistance and Remote Desktop. Remote Desktop enables administrators to connect to multiple Windows Server sessions for remote administration purposes. You can use IPv6 addresses to make remote desktop connections. Windows Remote Assistance and Remote Desktop use the Remote Desktop Protocol to enable users to access files on their office computers from other computers, such as their home computers.
