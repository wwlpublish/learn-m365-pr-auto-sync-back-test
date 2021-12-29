When an organization's on-premises environment runs Hybrid coexistence, troubleshooting client connectivity becomes more complex. Not only must the organization manage its existing Exchange on-premises servers, but it must manage Exchange Online mailboxes. Clients like Outlook will connect both to:

 -  The on-premises servers, using the company's existing Autodiscover records, to find their mailbox location.
 -  Potentially to the Exchange Servers for services like Public Folder coexistence, or accessing Shared Mailboxes and Read/Write access to Calendars.

### Prepare for coexistence

It's essential that organizations consider the following items when preparing for coexistence:

 -  **Firewalls.** If an organization isn't using Modern Hybrid and the Hybrid Agent, it must connect public Exchange Servers to the internet. This connection can be through a supported Reverse Proxy or Load Balancer device. Connectivity from Exchange Online IP address ranges or URLs is required for classic hybrid. With Modern Hybrid, firewall rules to support inbound Exchange Online connectivity aren't necessary. However, in all scenarios, outbound HTTPS connectivity from Exchange Servers is required.
 -  **Certificates and DNS.** If an organization is running Modern Hybrid, then its clients will access the on-premises environment using the same methods they previously used, and it won’t need to update URLs or Digital Certificates. However, if an organization uses classic Hybrid, then it must have ensured that it uses trusted, third-party Digital Certificates for HTTPS services. As part of this process, the organization will typically have ensured that it uses valid Internal and External URLs and configured Autodiscover correctly. If it hasn't, then it may experience client certificate prompts or a failure for Hybrid functionality like Free/Busy or Mailbox moves to work. The organization must ensure its Digital Certificates have Subject Alternative Names that match the configured Internal and External URLs and DNS names. It can use the Remote Connectivity Analyzer to validate this situation.

### Troubleshoot client access in coexistence

When an organization troubleshoots client access in coexistence, the problem is often limited to a single protocol. For example, Outlook on the Web may not work, but Outlook will work. When troubleshooting, it's recommended that you test client access across all the protocols to identify the protocol(s) that aren't working. This approach will help the organization focus its troubleshooting to speed up the time for resolution.

The following troubleshooting steps often help find the problem for client access in coexistence scenarios:

 -  **Run the Outlook Test Email AutoConfiguration tool.** Run the tool to look for Autodiscover issues and namespace or certificate issues.
 -  **Test a new profile setup in Outlook.** This test indirectly validates Autodiscover and initial connectivity to the mailbox server. It also validates credential and permissions to the mailbox.
 -  **Run the Remote Connectivity Analyzer tool.** The [RCA tool](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true), which is useful in many client access scenarios, can help pinpoint configuration issues by automating a series of connectivity and discovery requests.

**Additional reading.** For more information, see [Troubleshoot a hybrid deployment](/exchange/hybrid-deployment/troubleshoot-a-hybrid-deployment?azure-portal=true).
