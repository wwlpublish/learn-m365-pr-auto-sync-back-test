Windows Defender Firewall with Advanced Security is a stateful, host-based firewall that blocks incoming and outgoing connections based on its configuration. Although you can perform a typical end-user configuration for Windows Defender Firewall by using the Windows Defender Firewall control panel item, you can perform advanced configuration in the Microsoft Management Console (MMC) snap-in named Windows Defender Firewall with Advanced Security.

The inclusion of this snap-in not only provides an interface for configuring Windows Defender Firewall locally, but also for configuring Windows Defender Firewall on remote computers and by using Group Policy. You also can use Windows PowerShell to configure Windows Defender Firewall policies throughout your environment. Windows Defender Firewall functions now integrate with settings for connection-security protection, which reduces the possibility of conflict between the two protection mechanisms.

:::image type="content" source="../media/monitor-connections-e2cce967.jpg" alt-text="Screenshot of the Advanced Security window for Monitor Connections.":::


### Monitoring options for Windows Defender Firewall with Advanced Security

You can use the Windows Defender Firewall with Advanced Security console to monitor security policies that you create in the Connection Security Rules node. However, you cannot view the policies that you create by using the IP Security Policy Management snap-in. These security options are for use with Windows client and Windows Server.

### Monitoring connection security rules

The Connection Security Rules node lists all of the enabled connection security rules with detailed information about their settings. Connection security rules define which authentication, key exchange, data integrity, or encryption you can use to form an SA. The SA defines the security that protects the communication from the sender to the recipient.

### Implementing Connection Security Monitor

You can implement the Connection Security Monitor as an MMC snap-in. It includes enhancements that you can use to view details about an active connection security policy that the domain applies or that you apply locally. Additionally, you can view Quick Mode and Main Mode statistics, filters, negotiation policies, and security associations. You also can use Connection Security Monitor to search for specific Main Mode or Quick Mode filters. To troubleshoot complex designs for connection-security policies, you can use Connection Security Monitor to search for all matches for filters of a specific traffic type.

### Changing default settings

You can change the Connection Security Monitor default settings, such as automatic refresh and DNS name resolution. For example, you can specify the time that elapses between IPsec data refreshes. Additionally, you can enable DNS name resolution for the IP addresses that you are monitoring. Note that there are some issues to consider when enabling DNS. For example, it only works in a specific filter view for Quick Mode and in SAs view for Quick Mode and Main Mode monitoring. There also is the possibility that you can affect a server’s performance if several items in the view require name resolution. Finally, the DNS record name resolution requires a proper pointer (PTR) resource record in DNS.

### Obtaining information about the active policy

You can get basic information about the current IP security policy in the Active Policy node of the IP Security Monitoring snap-in to the MMC. During troubleshooting, this is useful to identify which policy IPsec is applying to the server. Details such as the policy location and the time of its last modification provide key details when you are determining the current in-place policy.

To view the connection security rules in the active policy store, you can use the following Windows PowerShell command:

```
Show-NetIPsecRule –PolicyStore ActiveStore

```

### Main Mode SA and Quick Mode SA

The Main Mode SA is the initial SA that Windows establishes between two computers. This negotiates a set of cryptographic protection suites between both hosts. This initial SA allows Quick Mode key exchange to occur in a protected environment. The Internet Security Association Key Management Protocol or Phase 1 SA is another name for the Main Mode SA. Main Mode establishes the secure environment to other exchange keys, as IPsec policy requires.

A Quick Mode SA depends on the successful establishment of a Main Mode SA. An IPsec or Phase 2 SA is another name for a Quick Mode SA. This process establishes keys based on the information that the policy specifies. Quick Mode SAs establish protected transmission channels for the actual application IP data that the policy specifies.

#### Monitoring SAs

The Security Associations folder lists all of the Main Mode and Quick Mode SAs with detailed information about their settings and endpoints.

#### Main Mode

Main Mode statistics provide data about the total number of SAs created and invalid packet information.

#### Quick Mode

Quick Mode provides more-detailed information about connections. If you are having issues with an IPsec connection, Quick Mode statistics can provide insight into the problem.
