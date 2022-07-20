Attack surfaces are all the places where an organization is vulnerable to cyberthreats and attacks. An organization's attack surfaces include all the places where an attacker could compromise the organization's devices or networks. Reducing your attack surface means protecting your organization's devices and network. By doing so, attackers have fewer ways to attack. Configuring attack surface reduction rules can help. Attack surface reduction rules are one of many security features found in Microsoft Defender for Endpoint.

Attack surface reduction rules target certain software behaviors, such as:

 -  Launching executable files and scripts that attempt to download or run files.
 -  Running obfuscated or otherwise suspicious scripts.
 -  App behaviors that don't usually occur during normal day-to-day work.

Such software behaviors are sometimes seen in legitimate applications. However, these behaviors are often considered risky because they're commonly abused by attackers through malware. Attack surface reduction rules can constrain software-based risky behaviors and help keep organizations safe.

By reducing the different attack surfaces, organizations can help prevent attacks from happening in the first place.

### Before you begin

Organizations that plan to implement attack surface reduction rules must understand the capabilities of the systems that it will put in place. Understanding the capabilities will help it determine which attack surface reduction rules are most important for its protection. There are also several prerequisites that must be completed to prepare for an attack surface reduction deployment.

> [!CAUTION]
> This unit provides images and examples to help organizations decide how to configure attack surface reduction rules. These images and examples may not reflect the best configuration options for every organization's environment.

Before you start, review [Overview of attack surface reduction](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction?azure-portal=true), and [Demystifying attack surface reduction rules - Part 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420?azure-portal=true) for foundational information.

To understand the areas of coverage and potential effect, familiarize yourself with the current set of attack surface reduction rules by reviewing [Attack surface reduction rules reference](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference?azure-portal=true). While you're familiarizing yourself with the attack surface reduction rule set, take note of the per-rule GUID mappings. For more information, see [attack surface reduction rule to GUID matrix](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference?azure-portal=true).

Attack surface reduction rules are only one capability of the attack surface reduction capabilities within Microsoft Defender for Endpoint. This unit will go into more detail on deploying attack surface reduction rules effectively to stop advanced threats like human-operated ransomware and other threats.

### Rules by category

As outlined in [Use attack surface reduction rules to prevent malware infection](/microsoft-365/security/defender-endpoint/attack-surface-reduction?azure-portal=true), there are multiple attack surface reduction rules within Microsoft Defender for Endpoint that an organization can enable to protect itself. The following table displays the attack surface reduction rules, and it breaks them out by category.

| **Polymorphic threats**                                                                                                    | **Lateral movement and credential theft**                                                      | **Productivity application rules**                          | **Email rules**                                                             | **Script rules**                                           | **Miscellaneous rules**                                 |
| -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------- |
| Block executable files from running unless they meet a prevalence (1000 machines), age (24 hrs), or trusted list criteria. | Block process creations originating from PSExec and WMI commands.                              | Block Office apps from creating executable content.         | Block executable content from email client and webmail.                     | Block obfuscated JS/VBS/PS/macro code.                     | Block abuse of exploited vulnerable signed drivers. (1) |
| Block untrusted and unsigned processes that run from USB.                                                                  | Block credential stealing from the Windows local security authority subsystem (lsass.exe). (2) | Block Office apps from creating child processes.            | Block only Office communication applications from creating child processes. | Block JS/VBS from launching downloaded executable content. |                                                         |
| Use advanced protection against ransomware.                                                                                | Block persistence through WMI event subscription.                                              | Block Office apps from injecting code into other processes. | Block Office communication apps from creating child processes.              |                                                            |                                                         |
|                                                                                                                            |                                                                                                | Block Adobe Reader from creating child processes.           |                                                                             |                                                            |                                                         |

(1) **Block abuse of exploited vulnerable signed drivers** isn't currently available in MEM Endpoint security. You can configure this rule using [MEM OMA-URI](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction?azure-portal=true).

(2) While some attack surface reduction rules generate considerable noise, they won't block functionality. For example, if you're updating Chrome, it will access lsass.exe. Passwords are stored in lsass on the device. However, Chrome shouldn't be accessing local device lsass.exe. If the rule is enabled to block access to lsass, it will generate many events. Those events are good events because the software update process shouldn't access lsass.exe. Enabling this rule will block Chrome updates from accessing lsass, but it won't block Chrome from updating. This result is also true of other applications that make unnecessary calls to lsass.exe. The **block access to lsass** rule will block unnecessary calls to lsass. However, it won't block the application from running.

### Infrastructure requirements

Although multiple methods of implementing attack surface reduction rules are possible, this unit is based on an infrastructure consisting of:

 -  Azure Active Directory
 -  Microsoft Endpoint Management (MEM)
 -  Windows 10 and Windows 11 devices
 -  Microsoft Defender for Endpoint E5 or Windows E5 licenses

To take full advantage of attack surface reduction rules and reporting, it's recommended that organizations use a Microsoft 365 Defender E5 or Windows E5 license, and A5. For more information, see [Minimum requirements for Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/minimum-requirements?azure-portal=true).

Attack surface reduction rules can be configured using:

 -  Microsoft Endpoint Manager (MEM)
 -  PowerShell
 -  Group Policy
 -  MEM OMA-URI

Organizations that use a different infrastructure configuration than what's listed for **Infrastructure requirements** (above) can learn more about deploying attack surface reduction rules using other configurations by referencing the following article: [Enable attack surface reduction rules](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction?azure-portal=true).

> [!WARNING]
> Some rules don't work well if unsigned, internally developed application and scripts are in high usage. It's difficult to deploy attack surface reduction rules if code signing isn't enforced.

### Attack surface reduction rules dependencies

Microsoft Defender Antivirus must be enabled and configured as primary anti-virus solution. It must also be in the following mode:

 -  Primary antivirus/antimalware solution
 -  State: Active mode

Microsoft Defender Antivirus can't be in any of the following modes:

 -  Passive
 -  Passive Mode with Endpoint detection and response (EDR) in Block Mode
 -  Limited periodic scanning (LPS)
 -  Off

**Additional reading**. For more information, see [Cloud-delivered protection and Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/cloud-protection-microsoft-defender-antivirus?azure-portal=true).

### Cloud Protection (MAPS) must be enabled

Microsoft Defender Antivirus works seamlessly with Microsoft cloud services. These cloud protection services, also referred to as Microsoft Advanced Protection Service (MAPS), enhances standard real-time protection, providing arguably the best antivirus defense. Cloud protection is critical to preventing breaches from malware and a critical component of attack surface reduction rules.

**Additional reading**. For more information, see [Turn on cloud-delivered protection in Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/enable-cloud-protection-microsoft-defender-antivirus?azure-portal=true).

### Microsoft Defender Antivirus components must be current versions

The following Microsoft Defender Antivirus component versions must be no more than two versions older than the most-currently-available version:

 -  **Microsoft Defender Antivirus Platform update version**. Microsoft Defender Antivirus platform is updated monthly.
 -  **Microsoft Defender Antivirus engine version**. Microsoft Defender Antivirus engine is updated monthly.
 -  **Microsoft Defender Antivirus security intelligence**. Microsoft continually updates Microsoft Defender security intelligence (also known as, definition and signature) to address the latest threats, and to refine detection logic.

Keeping Microsoft Defender Antivirus versions current helps reduce attack surface reduction rules' false positive results. It also improves Microsoft Defender Antivirus detection capabilities. For more information about the current versions and how to update the different Microsoft Defender Antivirus components, see [Microsoft Defender Antivirus platform support](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus?azure-portal=true).

### Attack surface reduction rules deployment steps

As with any new, wide-scale implementation that could potentially affect an organization's line-of-business operations, it's important to be methodical when planning and implementing attack surface reduction rules. Because of the powerful capabilities of attack surface reduction rules in preventing malware, careful planning and deployment of these rules is necessary to ensure they work best for an organization's unique customer workflows. For attack surface reduction rules to work, organizations must plan, test, implement, and operationalize attack surface reduction rules carefully.

:::image type="content" source="../media/attack-surface-reduction-rules-deployment-phases-8faeb141.png" alt-text="Diagram showing the deployment phases for Attack Surface Reduction rules, which include plan, test, implement, and operationalize.":::


> [!NOTE]
> For organizations that use a non-microsoft host intrusion prevention system (HIPS) and are transitioning to Microsoft Defender for Endpoint attack surface reduction rules: Microsoft advises them to run their HIPS solution side-by-side with their attack surface reduction rules deployment until the moment they shift from Audit to Block mode. These organizations must reach out to their third-party antivirus vendor for exclusion recommendations.

### Assess the effect of rules before deployment

An organization can assess how an attack surface reduction rule may affect its network by opening the security recommendation for that rule in [Microsoft Defender Vulnerability Management](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management?azure-portal=true).

:::image type="content" source="../media/attack-surface-reduction-recommendation-dce7fad6.png" alt-text="Screenshot of the Security recommendations page showing the recommended actions for an attack surface reduction rule.":::


### Audit mode for evaluation

Organizations should use [audit mode](/microsoft-365/security/defender-endpoint/audit-windows-defender?azure-portal=true) to evaluate how attack surface reduction rules would affect them if enabled. They should also run all rules in audit mode first so they can understand how the rules affect their line-of-business applications. Many line-of-business applications are written with limited security concerns. As such, they may perform tasks in ways that seem similar to malware. By monitoring audit data and [adding exclusions](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction?azure-portal=true) for necessary applications, organizations can deploy attack surface reduction rules without reducing productivity.

### Warn mode for users

Prior to warn mode capabilities, attack surface reduction rules that were enabled could be set to either audit mode or block mode. With the introduction of warn mode, whenever content is blocked by an attack surface reduction rule, users see a dialog box that indicates the content is blocked. The dialog box also offers the user an option to unblock the content. The user can then retry their action, and the operation completes. When a user unblocks content, the content remains unblocked for 24 hours, and then blocking resumes.

Warn mode helps an organization have attack surface reduction rules in place without preventing users from accessing the content they need to perform their tasks.

### Notifications and alerts

Whenever an attack surface reduction rule is triggered, a notification and an optional alert are displayed on the device.

 -  Organizations can [customize the notification](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment-implement?azure-portal=true) with their company details and contact information.
 -  When certain attack surface reduction rules are triggered, alerts can also be generated.

Any notifications and alerts that are generated can be viewed in the [Microsoft 365 Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139?azure-portal=true).

**Additional reading**. For more information about notification and alert functionality, see [Per rule alert and notification details](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference?azure-portal=true).

### Advanced hunting and attack surface reduction events

Organizations can use advanced hunting to view attack surface reduction events. To streamline the volume of incoming data, only unique processes for each hour are viewable with advanced hunting. The time of an attack surface reduction event is the first time that event is seen within the hour.

For example, let's assume that an attack surface reduction event occurs on 10 devices during the 2:00 PM hour. Suppose that the first event occurred at 2:15, and the last at 2:45. With advanced hunting, you'll see one instance of that event (even though it actually occurred on 10 devices), and its timestamp will be 2:15 PM.

**Additional reading**. For more information about advanced hunting, see [Proactively hunt for threats with advanced hunting](/microsoft-365/security/defender-endpoint/advanced-hunting-overview?azure-portal=true).
