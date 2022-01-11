Customers can take several actions and use multiple tools to help secure their Azure Virtual Desktop deployment. The following table lists some tested suggestions for securing your Azure Virtual Desktop deployment.

|**Best practice**| **Result**                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|Enable Azure Security Center for its cloud security posture management (CSPM) features| Use the CSPM feature of the security score to improve your overall security.|
|Require multi-factor authentication|Enhance user authentication.|
|Enable Conditional Access|Manage risks before you grant users access.|
|Collect audit logs|Review user and administrator activity.|
|Use RemoteApp|Reduce risk by letting the user work with only a subset of the remote machine exposed.|
|Monitor usage with Azure Monitor| Create service health alerts to receive notifications for the Azure Virtual Desktop service.|
|Enable endpoint protection|Protect your deployment from known malware.|
|Install an endpoint detection and response (EDR) product|Use EDR to provide advanced detection and response capabilities.|
|Enable threat and vulnerability management assessments|Help identify problem spots through vulnerability assessments for server operating systems.|
|Fix software vulnerabilities in your environment| When a vulnerability is identified, on-premises or in a virtual environment, you must fix it.|
|Establish maximum inactive time and disconnection policies|Sign out users when they're inactive to preserve resources and prevent unauthorized access. |
|Lock setup screen for idle sessions|Prevent unwanted system access by configuring Azure Virtual Desktop to lock a machine's screen during idle time and requiring authentication to unlock it.|
|Don't grant your users administrator access to virtual desktops|Manage software packages by using Configuration Manager.|
|Consider which users should access which resources|Limit host connection to internet resources.|
|Restrict operating system capabilities|Strengthen the security of your session hosts.|
|In the Azure Virtual Desktop host pools, limit device redirection under RDP properties|Prevent data leakage.|

## Enable endpoint protection by using Microsoft Defender for Endpoint

To help secure a company's endpoints, we recommend that you configure Microsoft Defender for Endpoint. It was previously known as Windows Defender for Endpoint. Microsoft Defender for Endpoint is typically used on-premises but can also be used in a virtual desktop infrastructure (VDI) environment.

To deploy Microsoft Defender for Endpoint on your Azure Virtual Desktop VMs, enroll the VMs into Azure Security Center. Security Center provides a license as part of its standard offering.

You should also use automatic provisioning. The settings for automatic provisioning in Security Center have a toggle for each type of supported extension. When you enable automatic provisioning of an extension, you assign the appropriate **DeployIfNotExists** policy to make sure that the extension is provisioned on all existing and future resources of that type.

> [!NOTE]
> Enable automatic provisioning of the Log Analytics agent. When automatic provisioning is turned on for the Log Analytics agent, Security Center deploys the agent on all supported Azure VMs and any new ones that are created.

### Microsoft Endpoint Manager integration with Microsoft Intune

Microsoft 365 includes support for the Microsoft Endpoint Manager admin center and Microsoft Endpoint Configuration Manager.

You can use Microsoft Intune to create and check for compliance. You can also use it to deploy apps, features, and settings to your devices that use Azure.

Microsoft Intune is integrated with Azure Active Directory (Azure AD) for authentication and authorization. It also integrates with Azure Information Protection for data protection. You can use Microsoft Intune with the Microsoft 365 suite of products.

The following table describes some of the main functionalities of Microsoft Intune.

|**Functionality**| **Description**|
| --------------------------------- | ------------------------------------------------------------ |
|Device management|User-owned and organization-owned enrolled devices in Microsoft Intune receive rules and settings through policies that you configure to match your organization's security policies. |
|App management|Mobile application management in Microsoft Intune can bring app management on organization-owned devices and personal devices.|
|Compliance and Conditional Access|Intune integrates with Azure AD to enable a broad set of access control scenarios.|

Application control moves from an application trust model that assumes all applications are trustworthy. The new model demands that applications earn trust before they can run. Windows 10 includes two technologies for application control: Windows Defender Application Control and AppLocker.

### Windows Defender Application Control

Windows 10 introduced Windows Defender Application Control. Organizations can use this feature to control the drivers and applications that can run on their Windows 10 clients.

Initially in Windows 10, Windows Defender Application Control was known as configurable code integrity. Configurable code integrity carries no specific hardware or software requirements other than running Windows 10. It was also one of the features that contained the now-defunct Device Guard.

### AppLocker

We recommend using AppLocker as part of your overall application control strategy. It allows predefined applications to run on your systems.

AppLocker control policies restriction rules are based on:

- File attributes such as the digital signature
- Product name
- File name
- File version

The default rules block many scripts, Windows Installer packages, and executable files.

AppLocker includes default rules for each rule collection to ensure that the files required for Windows to operate properly are allowed in an AppLocker rule collection. The default rules also allow members of the local Administrators group to run all Windows Installer files. The default rules are:

- Allow members of the Everyone group to run digitally signed Windows Installer files.
- Allow members of the Everyone group to run all Windows Installer files located in the Windows\Installer folder.
- Allow members of the local Administrators group to run all scripts.

An AppLocker rule collection functions as an allowed list of files. Only the files that are listed in the rule collection can run. This configuration makes it easier to determine what will occur when an AppLocker rule is applied. Because AppLocker functions as an allowed list by default, if no rule explicitly allows or denies a file from running, AppLocker's default deny action will block the file.
