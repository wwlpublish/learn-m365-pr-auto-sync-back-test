Microsoft Defender for Endpoint gives you a range of powerful tools that you can use to intercept attacks and reduce the attack surface that your systems present.

You've identified that Microsoft Defender for Endpoint is likely to reduce the number of security compromises that your organization experiences each year. Now, you'd like to obtain complete information about these features so that you can plan a deployment and protect your users and data.

Here, you'll learn more details about how the attack surface reduction features work in Defender for Endpoint.

## Network protection

Network protections prevent your employees from accessing dangerous internet destinations and domains that might host components of malicious attacks. Network protection rules apply, regardless of the user's client application. Network protection uses and expands on Microsoft Defender SmartScreen to block all HTTP outbound calls to domains with bad reputations.

> [!NOTE]
> Network protection is supported on Windows 10 version 1709 and later and Windows Server version 1803 and later.

You can configure network protection by using group policy, PowerShell, or Mobile Device Management (MDM) configuration service providers (CSPs).

You can review network protection events by searching for event IDs 1125 and 1126 in the Windows Event Viewer. When you use network protection with Microsoft Defender for Endpoint, you'll get reports that show which requests were blocked and their destinations as part of alert investigation scenarios.

You can enable network protection by running this PowerShell command:

```powershell
Set-MpPreference -EnableNetworkProtection Enabled
```

In Microsoft Endpoint Manager:

1. Create or edit an endpoint protection configuration profile.
1. Under **Configuration Settings** in the profile flow, go to **Microsoft Defender Exploit Guard > Network filtering > Network protection**.
1. Select **Enable** or **Audit only**.

## Exploit protection

Hackers often try a list of well-known exploits that may work against poorly configured computers or devices without the latest updates. Exploit protection intercepts many common exploits and blocks them. For example, an arbitrary code guard prevents an attacker from loading their own code through a memory safety vulnerability and untrusted fonts are blocked to ensure that a common flaw in font processing can't be used to run attacking code. There is a long list of other techniques that exploit protection blocks.

> [!NOTE]
> Network protection is supported on Windows 10 version 1709 and later and Windows Server version 1803 and later.

You can configure exploit protection by using Intune, MDM, Microsoft Endpoint Manager, group policy, or PowerShell.

To review exploit protection events in Windows Event Viewer, search for events from the provider **Security-Mitigations**. In Defender for Endpoint advanced hunting, use this Kusto query:

```kusto
DeviceEvents
| where ActionType startswith 'ExploitGuard' and ActionType !contains 'NetworkProtection'
```

To enable exploit protection using Endpoint Manager: 

1. Navigate to **Endpoint Security > Attack surface reduction**.
1. Select **Create Policy > Platform**
1. Under **Profile**, select **Exploit Protection**, and then select **Create**.
1. Enter a name and a description, and then choose **Next**.
1. Select **Select XML File** and then browse to the exploit protection XML file. Select **Review + create**.
1. Under **Review + create**, review the configuration, and then choose **Create**.

## Application control

Applications in Windows are run in the security context of the user's account. That means that any application a user runs, including any app from a disreputable source, has that user's level of access to your information. This risk is acute for users with a high level of access to sensitive data such as HR personnel or company directors. To mitigate these risks, you can use application control to restrict the applications that are permitted to run on your computers and devices to trusted list. Application control can also restrict the programs that can run in kernel mode on Windows and block unsigned scripts and Microsoft Installer (MSI) files.

> [!NOTE]
> Application control policies can be applied to any Windows 10 or Windows Server 2016 and later device. To create policies, use Windows 10 version 1903 or later.

You can configure application control by using Intune, Microsoft Endpoint Configuration Manager, group policy, or PowerShell.

## Web protection

In Microsoft Defender for Endpoint, web protection consists of:

- **Web threat protection.** Web threat protection blocks access to sites that host phishing attacks, malware, exploits, and to other untrusted sites. Web threat protection works for Microsoft Edge, Chrome, Firefox, and other browsers. 
- **Web content filtering.** Web content filtering allows you to filter access to websites based on their content categories. As well as blocking access to unsafe sites, you can use filtering to prevent access to non-malicious sites that don't conform to regulations, that host legal but unsound content, or that cause other concerns.

> [!NOTE]
> At the time of writing, web content filtering is in public preview.

Because web protection is based on network protection, you enable it in the same way as for network protection, by using group policy, PowerShell, or MDM CSPs.

Turn on web content filtering by using Microsoft Defender Security Center portal:

1. From the left-hand navigation menu, select **Settings > General > Advanced Features**.
1. Scroll down to **Web content filtering**.
1. Select **On** and then select **Save**.

To create a web filtering policy:

1. Select **Add policy** on the **Web content filtering** page in **Settings**.
1. Enter a name and select the categories to block. 
1. Specify the policy scope. Select the device groups to specify where to apply the policy. Only devices in the selected device groups will be prevented from accessing websites in the selected categories.
1. Save the policy.

> [!NOTE]
> It may take up to two hours for a new policy to apply to all your devices.

## Controlled folder access

Controlled folder access is designed to help protect sensitive and valuable data from ransomware, data theft, and other threats. When you enable controlled folder access, you specify a list of protected folders on each computer. Controlled folder access permits an app to modify data in those folders, only if they are on a list of trusted apps. 

The list of trusted apps is configured automatically. For example, apps that are widely used and have never exhibited malicious behavior are added to the trustworthy list. You can also add apps manually. 

> [!NOTE]
> Before you enable controlled folder access, you must enable Microsoft Defender Antivirus real-time protection.

To enable controlled folder access by using Intune:

1. Go to **Device configuration > Profiles > Create profile**.
1. Enter a name for the profile, select **Windows 10 and later** and **Endpoint protection**.
1. Go to **Configure > Windows Defender Exploit Guard > Controlled folder access** and then select **Enable**.
1. Select **OK** to save your changes.
1. Select the **Assignments** profile, and then assign to **All Users & All Devices**
1. Select **Save**.

To enable controlled folder access by using PowerShell:

1. Start PowerShell and select **Run as administrator**.
1. Run this command:

    ```powershell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

## Hardware-based isolation

Hardware-based isolation provides an extra level of protection to users of Microsoft Edge and Microsoft Office applications who need to access untrusted sites or open untrusted files.

Administrators configure a list trusted internet locations. Any other source is considered untrusted. When a user tries to open an untrusted source, Edge or the Office app is opened in the Microsoft Defender Application Guard, which is an isolated Hyper-V-enabled container. From within the Application Guard container, any malicious code can't access data on the host computer or run code on the host computer. 

The Application Guard implement hardware-isolation and so has these requirements:

- A 64-bit CPU.
- CPU virtualization extensions.
- At least 8 GB of RAM.
- 5 GB of available disk space.
- Windows 10 version 1709 or later.

To install Application Guard:

1. In Windows Control Panel, select **Programs**, and then select **Turn Windows features on or off**.
1. Select the **Microsoft Defender Application Guard** checkbox, and then select **OK**.

Alternatively, run PowerShell and administrator and then execute this PowerShell command:

```powershell
Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
```

## Reputation analysis

Microsoft Defender for Endpoint can use Microsoft Defender SmartScreen and reputational analysis to protect users from phishing attacks, malicious websites, and other threats. Reputational analysis uses the Microsoft Intelligent Security Graph to identify threats. The Graph is an AI solution that analyses trillions of signals and identifies common attacks. It stores sources of those attacks and assigns them a reputation score.

You can configure policies that govern what users experience when they access resources with a low reputation. For example, you can alert them to the threat, block them from downloading any content, or prevent them from executing any code from that source. 

You will be able to see reputational events in the Microsoft Defender Security Center and get full information about what happened and why any content was blocked.