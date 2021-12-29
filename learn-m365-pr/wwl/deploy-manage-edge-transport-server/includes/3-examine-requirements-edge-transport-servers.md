The Edge Transport server role differs from the Exchange Mailbox role because an organization can install the Edge Transport Server role on Windows Server 2019 computers that aren't members of its internal Active Directory. This configuration makes it easier and more secure to deploy Edge Transport servers in a perimeter network.

:::image type="content" source="../media/edge-infrastructure-requirements-4f00da80.png" alt-text="Diagram showing the infrastructure requirements for the Edge Transport server role":::


### Edge Transport server deployment considerations

You should consider the following factors when deploying Edge Transport servers:

 -  The Edge Transport server can't be combined with any other Exchange Server role. To provide increased security, the Edge Transport server must be installed on a separate computer, which can be virtual or physical.
 -  The Edge Transport server shouldn't be installed on a computer that's a member of the internal Active Directory. However, it can be installed in a perimeter network forest or workgroup.
 -  The computer running the Edge Transport server must have an FQDN.
 -  Active Directory communications shouldn't be allowed through the firewall that protects the internal network from the perimeter network. Doing so can cause security issues, such as allowing an unauthorized user to retrieve your email addresses directly from Active Directory and then use them for spam. Instead, the Edge Transport server uses Active Directory Lightweight Directory Services (AD LDS) to store configuration and recipient information. AD LDS doesn't contain all the information from Active Directory. Instead, it synchronizes only the required information, such as email addresses.
 -  The Edge Transport server should be deployed on a perimeter network to ensure network isolation from both the internal network and the internal Exchange servers. This configuration provides a higher level of security for the rest of the Exchange Server organization, which should be located behind a firewall on a separate internal network.
 -  The external firewall must be configured on the perimeter network to allow inbound and outbound SMTP traffic to and from the Edge Transport server. The internal firewall must allow SMTP traffic between the Edge Transport server and one or more internal Exchange 2016 or later servers (Port 25/TCP). The firewall must also allow outbound traffic towards the perimeter network for synchronization from Active Directory to AD LDS (Port 50636/TCP).
 -  The firewall configuration required for Edge Transport servers is greatly simplified because the server doesn't need to be an internal domain member.
 -  If the Edge Transport server routes email directly to the Internet, the server must be configured with the IP addresses for DNS servers that can resolve DNS names on the Internet.
