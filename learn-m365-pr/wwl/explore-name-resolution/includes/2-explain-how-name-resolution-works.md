Name resolution is the process of converting computer names to IP addresses. Name resolution is an essential part of computer networking because it is easier for users to remember names than abstract numbers, such as an IPv4 or IPv6 address. Windows supports a number of different methods for resolving computer names, such as DNS, Windows Internet Name Service (WINS), and local hosts or LMHOSTS resolution.

:::image type="content" source="../media/name-resolution-48242466.jpg" alt-text="Slide showing a diagram of the envisioning process.":::


### Computer names

A host name is a user-friendly name that is associated with a host’s IP address and identifies it as a TCP/IP host. A host name can be no more than 255 characters in length, and must contain only alphanumeric characters, periods, and hyphens. A host name is an alias or a fully qualified domain name (FQDN).

> [!NOTE]
> An alias is a single name associated with an IP address, and the host name combines an alias with a domain name to create the FQDN.

The elements of the name include periods as separators. Applications use the structured FQDN on the Internet. An example of an FQDN is payroll.contoso.com.

A **NetBIOS** name is a nonhierarchical name that some older apps use. A 16-character NetBIOS name identifies a NetBIOS resource on a network. A NetBIOS name represents a single computer or a group of computers. NetBIOS uses the first 15 characters for a specific computer’s name and the final sixteenth character to identify a resource or service on that computer. An example of a NetBIOS name is NYC-SVR2\[20h\].

### Methods for resolving names

There are a number of ways in which apps resolve names to IP addresses. DNS is the Microsoft standard for resolving host names to IP addresses. Apps also use DNS to do the following:

 -  **Locate domain controllers and global catalog servers**. Apps use this functionality when you sign in to Active Directory Domain Services (AD DS).
 -  **Resolve IP addresses to host names**. Apps use this functionality when a log file contains only a host’s IP address.
 -  **Locate a mail server for email delivery**. Apps use this functionality for the delivery of all Internet email.

When an app specifies a host name, TCP/IP uses the DNS resolver cache, DNS, and Link-Local Multicast Name Resolution when it attempts to resolve the host name. The Hosts file is loaded into the DNS resolver cache.

> [!NOTE]
> If NetBIOS over TCP/IP is enabled, TCP/IP also uses NetBIOS name resolution methods when resolving single-label, unqualified host names.

Depending on the configuration, Windows resolves host names by performing the following actions:

1.  Checking whether the host name is the same as the local host name.
2.  Searching the DNS resolver cache which is populated from the local Hosts file.
3.  Sending a DNS request to its configured DNS servers.

> [!NOTE]
> Windows can use Link-Local Multicast Name Resolution for networks that do not have a DNS server.
