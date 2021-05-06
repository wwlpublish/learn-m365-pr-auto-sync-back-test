Microsoft Defender for Endpoint enables you to control interactions between your devices and external systems closely. You can use these controls to intercept malicious attacks with no impact on the productivity of your users.

You want to understand how Microsoft Defender for Endpoint can reduce the attack surface that your systems present for exploitation by attackers. You'll use this information to plan a set of attack surface reduction rules to protect your users and data.

Here, you'll learn the capabilities that Microsoft Defender for Endpoint includes to minimize the opportunities malicious users have to compromise your systems.

## What is attack surface reduction?

To get business done, almost all computers and devices interact with external systems across networks or through removable hardware. For example, a user might:

- Access an internet site and download an executable program.
- Insert a USB drive to transfer data, documents, or applications.
- Install an app from a trusted on non-trusted source.
- Select a link in an email.

Any of these interactions might be a legitimate business activity, but they might also be part of malicious attacks. It's challenging to differentiate one from the other.

Attack surface reduction in Microsoft Defender for Endpoint is a set of controls that helps you to block attacks automatically while permitting legitimate actions. It consists of controls that you can impose on your endpoints that minimize the places where your organization is vulnerable to cyber threats. These controls include:

- **Hardware-based isolation for Microsoft Edge.** You can use these rules to run untrusted websites within an isolated container whenever they are opened in Microsoft Edge. Any malicious code in that container is unable to damage the device or its data.

    > [!NOTE]
    > Hardware-based isolation is also known as Microsoft Defender Application Guard.

- **Application control.** You can use application control rules to restrict the applications that users are allowed to run to an approved list. You can also control the code that runs in kernel mode. Application control rules can also block unsigned scripts and MSI installer files.
- **Web protection.** You can use web protection rules to intercept common web threats such as access to known malicious web sites. You can also filter access to web content by category. For example, you can block access to adult content or high-bandwidth sites.
- **Network protection.** You can use these rules to prevent access to dangerous domains from any application.
- **Controlled folder access.** You can use these rules to protect valuable data from malicious code, such as ransomware. Controlled folder access checks your app against a list of known, trusted apps. If your app is not on that list, it's prevented from accessing the controlled folders that you specify.
- **Exploit protection.** You can use these rules to apply a range of common exploit mitigation measures to Windows operating system processes and apps.
- **Network firewall.** You can use these rules to control how Windows Defender Firewall filters network traffic on your Windows computers.

## Audit mode

You may be concerned that attack surface reduction techniques might inadvertently impact your users' productivity. To address this issue, you can run attack surface reduction rules in **audit mode**.

In audit mode, a rule doesn't prevent any action - instead it records the event that would have been blocked. To review the events that would have been blocked, search for event ID 1122 in the Windows Event Viewer. These events appear in the Microsoft-Windows-Windows Defender/Operational log.

## Requirements

The full set of attack surface reduction rules and features is only supported if you have an enterprise license to run Windows 10. All rules are supported with a Windows Enterprise E3 license and above. For the greatest level of integration between attack surface reduction rules and Microsoft Defender for Endpoint, use an E5 license.

Hardware-based isolation for Microsoft Edge requires you to install the Microsoft Defender Application Guard on the Windows computer. The Application Guard requires:

- A 64-bit CPU.
- CPU virtualization extensions.
- At least 8 GB of RAM.
- 5 GB of available disk space.
- Windows 10.

## Attack surface reduction configuration tools

You can use many different tools to configure attack surface reduction rules:

- Microsoft Intune
- Microsoft Endpoint Configuration Manager
- Group Policy
- PowerShell cmdlets and scripts

For example, suppose you want to enable application control for all the computers in reception areas in your offices. You could place all those computers in the same Active Directory Organizational Unit and then apply a Group Policy Object (GPO) to that unit. In the GPO, enable navigate to **Computer Configuration\Administrative Templates\System\Device Guard** and then use the **Deploy Windows Defender Application Control** policy to specify the location of a deploy code integrity policy.