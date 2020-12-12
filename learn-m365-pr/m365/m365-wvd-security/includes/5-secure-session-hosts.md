Customers can take several actions and use a variety of tools to help secure their WVD deployment. The following table lists some of the best practices for securing your WVD ecosystem.

| **Best Practice**                                            | **Result**                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Subscribe to Azure Security Center Standard                  | Use the ASC security score to improve your overall security. |
| Require multifactor authentication                           | Enhance user authentication.                                 |
| Enable conditional access                                    | Manage risks before you grant users’ access.                 |
| Collect audit logs                                           | Review user and administrator activity.                      |
| Use RemoteApp                                                | Reduce risk by only letting the user work with a subset of the remote machine exposed. |
| Monitor usage with Azure Monitor                             | Create service health alerts to receive notifications for the WVD service. |
| Enable endpoint protection                                   | Protect your deployment from known malware.                  |
| Install an endpoint detection and response (EDR) product     | Use EDR to provide advanced detection and response capabilities. |
| Enable threat and vulnerability management assessments       | Help identify problem spots through vulnerability assessments for server operating systems. |
| Fix software vulnerabilities in your environment             | When a vulnerability is identified, you must fix it. This applies to virtual environments as well. |
| Establish maximum inactive time and disconnection policies   | Sign users out when they're inactive to preserve resources and prevent unauthorized access. |
| Set up screen locks for idle sessions                        | Prevent unwanted system access by configuring WVD to lock a machine's screen during idle time and requiring authentication to unlock it. |
| Don't grant your users administrator access to virtual desktops | Manage software packages by using Configuration Manager.     |
| Consider which users should access which resources           | Limit host connection to internet resources.                 |
| Restrict operating system capabilities                       | Strengthen the security of your session hosts.               |
| In the WVD host pools, limit device redirection under RDP Properties | Prevent data leakage.                                        |

## Enable endpoint protection by using Microsoft Defender for Endpoint

One of the best practices is to enable endpoint protection, which you can do by using Microsoft Defender for Endpoint, previously known as Microsoft Defender Advanced Threat Protection. Microsoft Defender for Endpoint is typically used on-premises but can also be used in a VDI environment.

To deploy Microsoft Defender for Endpoint on your WVD VMs in their host pools, you can enroll the VMs into Azure Security Center. Security Center provides a license as part of its standard offering. You should also use auto provisioning. The auto-provisioning settings in Security Center have a toggle for each type of supported extension. When you enable auto-provisioning of an extension, you assign the appropriate **Deploy** **if not exists** policy to make sure that the extension is provisioned on all existing and future resources of that type.

{!Note] Enable auto-provisioning of the Log Analytics agent. When automatic provisioning is turned on for the Log Analytics agent, Security Center deploys the agent on all supported Azure VMs and any new ones that are created.

### Microsoft Endpoint Manager integration with Intune

The Microsoft 365 stack includes Microsoft Endpoint Manager.  Configuration Manager, Microsoft Intune, Desktop Analytics, co-management, and Windows Autopilot are all services included in Endpoint Manager. T

Microsoft Intune can be used to create and check for compliance, and deploy apps, features, and settings to your devices using Azure. Intune is also integrated with Azure AD for authentication and authorization. It also integrates with Azure Information Protection for data protection. You can use Intune with the Microsoft 365 suite of products. The following table describes some of the main functionalities of Intune.

| **Functionality**                 | **Description**                                              |
| --------------------------------- | ------------------------------------------------------------ |
| Device management                 | BYOD or organization-owned enrolled devices in Intune, receive rules and settings through policies that you configures to match your organizations security policies. |
| App management                    | Mobile application management (MAM) in Intune can be bring app management on organization-owned devices and personal devices. |
| Compliance and conditional access | Intune integrates with Azure AD to enable a broad set of access control scenarios. |

Application control moves away from an application trust model where all applications are assumed trustworthy to a model where applications must earn trust before they can run. Windows 10 includes two technologies that you can use for application control: Windows Defender Application Control and AppLocker.

## Windows Defender Application Control

Windows 10 introduced Windows Defender Application Control, which organizations can use to control the drivers and applications that can run on their Windows 10 clients. Note that initially in Windows 10, Windows Defender Application Control was known as configurable code integrity. Configurable code integrity carries no specific hardware or software requirements other than running Windows 10. It was also one of the features which contained the now-defunct Device Guard.

## AppLocker

AppLocker advances the app control features and functionality of software restriction policies. AppLocker contains capabilities and extensions that you can use to create rules to allow or deny apps from running, based on unique identities of files. You can also use them to specify which users or groups can run those apps.

AppLocker helps reduce administrative overhead and the organization's cost of managing computing resources by decreasing the number of helpdesk calls that result from users running unapproved applications. By using AppLocker, you can:

- Define rules based on file attributes that persist across application updates, such as the publisher name (derived from the digital signature), product name, file name, and file version. You can also create rules based on the file path and hash.
- Assign a rule to a security group or an individual user.
- Create exceptions to rules. For example, you can create a rule that allows all users to run all Windows binaries except the Registry Editor (Regedit.exe).
- Use audit-only mode to deploy the policy and understand its impact before enforcing it.
- Create rules on a staging server, test them, export them to your production environment, and then import them into a Group Policy Object (GPO).
- Simplify creating and managing AppLocker rules by using Windows PowerShell cmdlets for AppLocker.

AppLocker includes default rules for each rule collection. These rules help ensure that the files that are required for Windows to operate properly are allowed in an AppLocker rule collection. The default rules block many scripts, Windows installer packages, and executables. The default rules also allow members of the local Administrators group to run all Windows Installer files. The default rules are:

- **Allow members of the Everyone group to run digitally signed Windows Installer files**.
- **Allow members of the Everyone group to run all Windows Installer files located in the Windows\Installer folder**.
- **Allow members of the local Administrators group to run all scripts**.

Unlike Software Restriction Policies (SRPs), each AppLocker rule collection functions as an allowed list of files. Only the files that are listed within the rule collection can run. This configuration makes it easier to determine what will occur when an AppLocker rule is applied. Because AppLocker functions as an allowed list by default, if no rule explicitly allows or denies a file from running, AppLocker's default deny action will block the file.
