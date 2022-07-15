Microsoft Endpoint security policies are designed to help organizations focus on the security of their devices and mitigate risk. The available tasks can help them:

 -  Identify at-risk devices.
 -  Remediate those devices.
 -  Restore them to a compliant or more secure state.

Security and enterprise administrators can use the **Endpoint security** node in the **Microsoft Endpoint Manager admin center** to:

 -  Configure device security.
 -  Manage security tasks for devices when those devices are at risk.

:::image type="content" source="../media/endpoint-security-overview-c36be17b.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center showing the endpoint security node.":::


The **Endpoint security** node groups the tools that are available through Intune. These tools will help an organization keep devices secure by enabling it to:

 -  **Review the status of all its managed devices**. Use the **All devices** view, where you can view device compliance from a high level. Then, drill-in to specific devices to understand which compliance policies aren't met so you can resolve them.
 -  **Deploy security baselines that establish best practice security configurations for devices**. Intune includes security baselines for Windows devices and a growing list of applications, like Microsoft Defender for Endpoint and Microsoft Edge. Security baselines are pre-configured groups of Windows settings that help an organization apply a configuration that's recommended by the relevant security teams.
 -  **Manage security configurations on devices through tightly focused policies**. Each Endpoint security policy focuses on aspects of device security, such as antivirus, disk encryption, firewalls, and several areas made available through integration with Microsoft Defender for Endpoint.
 -  **Establish device and user requirements through compliance policy**. With compliance policies, an organization can set the rules that devices and users must meet to be considered compliant. Rules can include OS versions, password requirements, device threat-levels, and more. When an organization integrates with Azure Active Directory (Azure AD) conditional access policies to enforce compliance policies, it can gate access to corporate resources for both managed devices, and devices that aren’t yet managed.
 -  **Integrate Intune with its Microsoft Defender for Endpoint team**. When an organization integrates with Microsoft Defender for Endpoint, it can gain access to security tasks. Security tasks closely tie Microsoft Defender for Endpoint and Intune together to help an organization's security team identify devices that are at risk. These tasks also provide detailed remediation steps to Intune admins who can then act on those remediation tasks.

> [!NOTE]
> For more reporting information about device configuration profiles, see [Intune reports](/mem/intune/fundamentals/reports?azure-portal=true).

The following sections examine the different tasks an organization can perform from the **Endpoint security** node of the Microsoft Endpoint Manager admin center. It also identifies the role-based access control permissions that are required to use them.

### Manage devices

The **Endpoint security** node includes an **All devices** view. This view displays a list of all devices from an organization's Azure Active Directory that are available in Microsoft Endpoint Manager.

From this view, you can select a device to display detailed information concerning the device. For example, you can view which policies a device isn't compliant with. You can also use access from this view to remediate issues for a device, including:

 -  Restarting a device.
 -  Starting a scan for malware.
 -  Rotating BitLocker keys on a Window 10 or later device.

**Additional reading**. For more information, see [Manage devices with endpoint security in Microsoft Intune](/mem/intune/protect/endpoint-security-manage-devices?azure-portal=true).

### Manage security baselines

Security baselines in Microsoft Endpoint Manager are pre-configured groups of settings. They're best practice recommendations from the relevant Microsoft security teams for the product. Intune supports security baselines for Windows 10 and later device settings, Microsoft Edge, Microsoft Defender for Endpoint Protection, and more.

An organization can use security baselines to rapidly deploy a best practice configuration of device and application settings to protect its users and devices. Security baselines are supported for devices that run Windows 10 version 1809 and later, and Windows 11.

Security baselines are one of several methods in Intune to configure settings on devices. When an organization manages device settings, it's important that it understands what other methods are in use in its environment that can configure its devices so that it can avoid conflicts.

**Additional reading**. For more information, see [Use security baselines to configure Windows devices in Intune](/mem/intune/protect/security-baselines?azure-portal=true).

### Review security tasks from Microsoft Defender for Endpoint

When an organization integrates Intune with Microsoft Defender for Endpoint, it can review security tasks in Intune that identify at-risk devices and provide steps to mitigate that risk. It can then use the tasks to report back to Microsoft Defender for Endpoint when those risks are successfully mitigated.

 -  An organization's Microsoft Defender for Endpoint team determines what devices are at risk within the company. It then passes that information to its Intune team as a security task. The security team can then create a security task for Intune that identifies the devices at risk and the vulnerability of each device. It can also provide guidance on how to mitigate that risk.
 -  The Intune administrators review security tasks and then act within Intune to remediate those tasks. Once mitigated, they set the status of the task to **Complete**, which communicates that status back to the Microsoft Defender for Endpoint team.

By using security tasks, both teams remain in synch as to which devices are at risk, and how and when those risks are remediated.

**Additional reading**. For more information about using Security tasks, see [Use Intune to remediate vulnerabilities identified by Microsoft Defender for Endpoint](/mem/intune/protect/atp-manage-vulnerabilities?azure-portal=true).

### Use policies to manage device security

Security administrators use the security policies found under the **Manage** section in the **Endpoint security** node. With these policies, they can configure device security without having to navigate the larger body and range of settings in device configuration profiles or security baselines.

:::image type="content" source="../media/endpoint-security-policies-e2e4a089.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center showing the endpoint security node with the Manage section highlighted.":::


Endpoint security policies are one of several methods in Intune to configure settings on devices. When managing settings, it's important for an organization to understand what other methods are in use in its environment that can configure its devices. This knowledge enables organizations to avoid conflicts.

The **Manage** section also includes **Device compliance** and **Conditional access** policies. These policy types aren't security policies for configuring endpoints. Instead, they're important tools for managing devices and access to corporate resources.

**Additional reading**. For more information about using security policies, see [Manage device security with endpoint security policies](/mem/intune/protect/endpoint-security-policy?azure-portal=true).

### Use device compliance policy

Device compliance policies enable an organization to establish the conditions by which devices and users are allowed to access its network and company resources. The [available compliance settings](/mem/intune/protect/device-compliance-get-started#next-steps?azure-portal=true) depend on the platform being used, but common policy rules include:

 -  Requiring devices to run a minimum or specific OS version.
 -  Setting password requirements.
 -  Specifying a maximum allowed device threat-level, as determined by Microsoft Defender for Endpoint or another Mobile Threat Defense partner.

In addition to the policy rules, compliance policies support [Actions for non-compliance](/mem/intune/protect/actions-for-noncompliance?azure-portal=true). These actions are a time-ordered sequence of actions that will be applied to non-compliant devices. Actions include:

 -  Sending email or notifications to alert device users about non-compliance.
 -  Remotely locking devices.
 -  Retiring non-compliant devices.
 -  Removing company data that's on non-compliant devices.

**Additional reading**. For more information, see [Set rules on devices to allow access to resources in your organization using Intune](/mem/intune/protect/device-compliance-get-started?azure-portal=true)

### Configure conditional access

An organization can protect its devices and corporate resources by using Azure Active Directory (Azure AD) [Conditional Access policies](/mem/intune/protect/endpoint-security#configure-conditional-access?azure-portal=true) with Intune. Azure AD conditional access policies enforce compliance policies. By doing so, conditional access can use the compliance data to gate access to corporate resources for both managed devices, and from devices that you don't manage.

Intune passes the results of your device compliance policies to Azure AD. Azure AD then uses conditional access policies to enforce which devices and apps can access your corporate resources. Conditional access policies also help to gate access for devices that aren’t managed by Intune. They can also use compliance details from the [Mobile Threat Defense partners](/mem/intune/protect/mobile-threat-defense?azure-portal=true) that an organization integrates with Intune.

Two common methods of using conditional access with Intune include:

 -  **Device-based conditional access**. Ensures only managed and compliant devices can access network resources.
 -  **App-based conditional access**. Uses app-protection policies to manage access to network resources by users on devices that aren't managed with Intune.

**Additional reading**. For more information about using conditional access with Intune, see [Learn about Conditional Access and Intune](/mem/intune/protect/conditional-access?azure-portal=true).

### Set up integration with Microsoft Defender for Endpoint

When an organization integrates Microsoft Defender for Endpoint with Intune, it improves its ability to identify and respond to risks. While Intune can integrate with several Mobile Threat Defense partners, when an organization uses Microsoft Defender for Endpoint, it gains a tight integration between Microsoft Defender for Endpoint and Intune with access to deep device protection options, including:

 -  Seamless communication between Microsoft Defender for Endpoint and Intune administrators about devices at risk, how to remediate them, and confirmation when those risks are mitigated.
 -  Streamlined onboarding for Microsoft Defender for Endpoint on clients.
 -  Use of Microsoft Defender for Endpoint device risk signals in Intune compliance policies and app protection policies.
 -  Access to Tamper protection capabilities.

**Additional reading**. For more information about using Microsoft Defender for Endpoint with Intune, see [Enforce compliance for Microsoft Defender for Endpoint with Conditional Access in Intune](/mem/intune/protect/advanced-threat-protection?azure-portal=true).

### Role-based access control requirements

For a user to manage tasks in the **Endpoint security** node of the Microsoft Endpoint Manager admin center, the user account must:

 -  Be assigned a license for Intune.
 -  Have role-based access control permissions equal to the permissions provided by the built-in Intune role of Endpoint Security Manager. The **Endpoint Security Manager** role grants access to the Microsoft Endpoint Manager admin center. This role can be used by individuals who manage security and compliance features, including:
     -  security baselines
     -  device compliance
     -  conditional access
     -  Microsoft Defender for Endpoint

**Additional reading**. For more information, see [Role-based access control with Microsoft Intune](/mem/intune/fundamentals/role-based-access-control?azure-portal=true)

### Avoid policy conflicts

Many of the settings that an organization can configure for devices can be managed by different features in Intune. These features include but aren't limited to:

 -  Endpoint security policies
 -  Security baselines
 -  Device configuration policies
 -  Windows enrollment policies

For example, the settings found in Endpoint security policies are a subset of the settings that are found in **endpoint protection** and **device restriction** profiles in device configuration policy. These settings are also managed through various security baselines.

One way to avoid conflicts is to NOT use different baselines, instances of the same baseline, or different policy types and instances to manage the same settings on a device. To avoid conflicts of this nature, an organization should plan which methods it will use to deploy configurations to different devices. When multiple methods or instances of the same method are used to configure the same setting, an organization should ensure that its different methods either agree or aren't deployed to the same devices.

If conflicts occur, an organization can use Intune's built-in tools to identify and resolve the source of those conflicts.

**Additional reading**. For more information, see [Troubleshoot policies and profiles in Intune](/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune?azure-portal=true) and [Monitor your security baselines](/mem/intune/protect/security-baselines-monitor#troubleshoot-using-per-setting-status?azure-portal=true).
