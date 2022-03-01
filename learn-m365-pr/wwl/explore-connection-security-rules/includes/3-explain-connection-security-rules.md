A connection security rule forces authentication between two peer computers before they can establish a connection and transmit secure information. Windows Defender Firewall with Advanced Security uses IPsec to enforce the following configurable rules:

 -  **Isolation**. An isolation rule isolates computers by restricting connections based on credentials, such as domain membership or health status. Isolation rules allow you to implement an isolation strategy for servers or domains.
 -  **Authentication exemption**. You can use an authentication exemption to designate connections that do not require authentication. You can designate computers by a specific IP address, an IP address range, a subnet, or a predefined group, such as a gateway.
 -  **Server to server**. A server-to-server rule protects connections between specific computers. This type of rule usually protects connections between servers. When you create the rule, you specify the network endpoints between which communications are protected. You then designate requirements and the authentication that you want to use.
 -  **Tunnel**. A tunnel rule allows you to protect connections between gateway computers, and typically, you use it when you are connecting across the Internet between two security gateways.
 -  **Custom**. There might be situations in which you cannot configure the authentication rules that you need by using the rules available in the New Connection Security Rule Wizard. However, you can use a custom rule to authenticate connections between two endpoints.

You can configure connection security rules by using Group Policy, Windows Firewall with Advanced Security, or Windows PowerShell.

### The relation between firewall rules and connection security rules

Firewall rules allow traffic through a firewall, but do not secure that traffic. To secure traffic with IPsec, you can create connection security rules. However, when you create a connection security rule, this does not allow the traffic through the firewall. You must create a firewall rule to do this if the firewall’s default behavior does not allow traffic. Connection security rules do not apply to programs and services. They apply only between the computers that are the two endpoints.
