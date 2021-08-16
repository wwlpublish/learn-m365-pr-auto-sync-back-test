Microsoft Defender for Endpoint includes a range of attack surface reduction capabilities to secure your organization's devices and systems without hindering productivity. You can use attack surface reduction capabilities to help prevent malicious attacks by closing gaps and reducing vulnerability.

Here, you'll get an explanation of what attack surface reduction is in Microsoft Defender for Endpoint, including an overview of the different controls it provides.

## What is attack surface reduction?

To get business done, almost all users, including yourself, interact with external systems across networks or through removable hardware. For example, a user might:

- Access an internet site and download an executable program.
- Insert a USB drive to transfer data, documents, or applications.
- Install an app from a trusted on non-trusted source.
- Select a link in an email.

Any of these interactions might be a legitimate business activity, but they might also be part of malicious attacks. It's challenging to differentiate one from the other.

Attack surface reduction in Microsoft Defender for Endpoint is a set of controls that helps you to block potentially unwanted actions automatically while permitting legitimate actions. It consists of controls that you can impose on your endpoints that minimize the places where your organization is vulnerable to cyber threats. These controls include:

- **Hardware-based isolation for Microsoft Edge:** You can use these rules to run untrusted websites within an isolated container whenever they are opened in Microsoft Edge. Any malicious code in that container is unable to damage the device or its data.

    > [!NOTE]
    > Hardware-based isolation is also known as Microsoft Defender Application Guard.

- **Application control:** Applications in Windows are run in the security context of the user's account. That means that any application a user runs, including any app from a disreputable source, has that user's level of access to your organization's information. This risk is acute for users with a high level of access to sensitive data such as Human Resources personnel or company directors. To mitigate these risks, you can use application control to restrict the applications that are permitted to run on your devices to list of trusted apps.
- **Web protection:** Comes in two forms:
  - **Web threat protection**. You can use it locks access to sites that host phishing attacks, malware, exploits, and to other untrusted sites. Web threat protection works for Microsoft Edge, Chrome, Firefox, and other browsers.
  - **Web content filtering**. You can use this protection to filter access to websites based on their content categories. As well as blocking access to unsafe sites, you can use filtering to prevent access to non-malicious sites that don't conform to regulations, that host legal but unsound content, or that cause other concerns.

- **Network protection:** You can use network protection to prevent your users from accessing dangerous internet destinations and domains that might host components of malicious attacks. Your network protection rules will apply, regardless of the applications that your users are using.
- **Controlled folder access:** You can protect valuable data from malicious code, such as ransomware. Controlled folder access checks your app against a list of known, trusted apps. If your app is not on that list, it's prevented from accessing the controlled folders that you specify.
- **Exploit protection:** Hackers often try a list of well-known exploits that may work against poorly configured computers or devices without the latest updates. You can use exploit protection to intercept many common exploits and blocks them. For example, you can prevent an attacker from loading their code through a vulnerability related to a device's memory, or you can block untrusted fonts to ensure that a common flaw in font processing can't be used to run attacking code.
- **Reputational analysis**. You can use reputational analysis in Microsoft Defender for Endpoint to protect users from phishing attacks, malicious websites, and other threats. With reputation analysis, you can check the reputation of each file that a user downloads, or website that a user visits. For example, you can alert them to the threat, block them from downloading the content, or prevent them from executing any code from that source.
- **Attack surface reduction rules**. Attack surface reduction rules protect against risky behaviors, such as launching scripts that attempt to download or run files, running scripts that seem suspicious, or performing behaviors that generally do not fit normal day-to-day work. The next section, "Use attack surface reduction rules", goes into more details about the rules that are available with Microsoft Defender for Endpoint.

## Attack surface reduction configuration tools

You can use many different tools to configure attack surface reduction:

- Microsoft Endpoint Manager
- Microsoft Endpoint Configuration Manager
- Group Policy
- PowerShell cmdlets and scripts

You can use the links in the **Learn more** section for detailed guidance on these tools.

## Learn more

- [Turn on network protection](/microsoft-365/security/defender-endpoint/enable-network-protection)
- [Enable exploit protection](/microsoft-365/security/defender-endpoint/enable-exploit-protection)
- [Application Control for Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)
- [Protect your organization against web threats](/microsoft-365/security/defender-endpoint/web-threat-protection)
- [Enable controlled folder access](/microsoft-365/security/defender-endpoint/enable-controlled-folders)
- [Hardware-based isolation in Windows 10](/microsoft-365/security/defender-endpoint/overview-hardware-based-isolation)
