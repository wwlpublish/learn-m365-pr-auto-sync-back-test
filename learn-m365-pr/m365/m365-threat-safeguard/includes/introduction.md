>[!IMPORTANT]
>Threat protection product names in Microsoft are changing. [Read more about this and other updates](https://www.microsoft.com/security/blog/?p=91813). We'll be updating names in products and in the Learn content in the near future.

**Azure Advanced Threat Protection (ATP)** is a cloud-based security solution that leverages your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

![The benefits of Azure ATP](../media/azure-benefits.png)

Azure ATP provides the following benefits:

- Monitor users, entity behavior, and activities with learning-based analytics
- Protect user identities and credentials stored in Active Directory
- Identify and investigate suspicious user activities and advanced attacks throughout the kill chain
- Provide clear incident information on a simple timeline for fast triage

## Monitor and profile user behavior and activities

Azure ATP monitors and analyzes user activities and information across your network, such as permissions and group membership. It then creates a behavioral baseline for each user. Azure ATP then identifies anomalies with adaptive built-in intelligence, giving you insights into suspicious activities and events, revealing the advanced threats, compromised users, and insider threats facing your organization. Azure ATP's proprietary sensors monitor organizational domain controllers, providing a comprehensive view for all user activities from every device.

[ ![Overview of user activities](../media/user-activities-view.png) ](../media/user-activities-view-magnify.png#lightbox)

## Protect user identities and reduce the attack surface

Azure ATP provides you invaluable insights on identity configurations and suggested security best-practices. Through security reports and user profile analytics, Azure ATP helps dramatically reduce your organizational attack surface, making it harder to compromise user credentials and advance an attack. Azure ATP's visual Lateral Movement Paths help you quickly understand exactly how an attacker can move laterally inside your organization to compromise sensitive accounts and assists in preventing those risks in advance. Azure ATP security reports help you identify users and devices that authenticate using clear-text passwords and provide additional insights to improve your organizational security posture and policies.

![Security Report user improvement suggestions](../media/security-report-improvement-action-cropped.png)

## Identify suspicious activities and advanced attacks across the cyber-attack kill-chain
 
Typically, attacks are launched against any accessible entity, such as a low-privileged user, and then quickly move laterally until the attacker gains access to valuable assets – such as sensitive accounts, domain administrators, and highly sensitive data. Azure ATP has a large range of detections across the Kill-chain from **reconnaissance** through to **compromised credentials** to **lateral movements** and **domain dominance**.

![Lateral movement across the kill chain](../media/lateral-movement-across-kill-chain.png)

For example, in the reconnaissance stage, LDAP reconnaissance is used by attackers to gain critical information about the domain environment. Information that helps attackers map the domain structure, as well as identify privileged accounts for use later. This detection is triggered based on computers performing suspicious LDAP enumeration queries or queries targeting sensitive groups.

Brute force attacks are a common way to compromise credentials. This is when an attacker attempts to authenticate with multiple passwords on different accounts until a correct password is found or by using one password in a large-scale password spray that works for at least one account. Once found, the attacker logs in using the authenticated account. Azure ATP can detect this when it notices multiple authentication failures occurring using Kerberos, NTLM, or use of a password spray.

The next stage is when attackers attempt to move laterally through your environment, using pass-the-ticket, for example. Pass-the-ticket is a lateral movement technique in which attackers steal a Kerberos ticket from one computer and use it to gain access to another computer by reusing the stolen ticket. In this detection, a Kerberos ticket is being used on two (or more) different computers.

Ultimately, attackers want to establish domain dominance. One method, for example is the DCShadow attack. This attack is designed to change directory objects using malicious replication. This attack can be performed from any machine by creating a rogue domain controller using a replication process. If this occurs, Azure ATP triggers an alert when a machine in the network tries to register as a rogue domain controller.

This is not the complete set of detections, but it shows the breadth of detections Azure ATP covers.
