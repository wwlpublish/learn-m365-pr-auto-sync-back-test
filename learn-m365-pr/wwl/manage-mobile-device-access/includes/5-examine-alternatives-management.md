Both Mobile Device Management (MDM) for Microsoft 365 and Microsoft Intune can be used to manage mobile devices in an organization. In fact, both MDM and Intune can be used in the same Microsoft 365 tenant.

Setting up both Intune and MDM enables you to decide which solution is best for specific users and their devices. If you have both options available, you can choose whether to manage a user's devices with either MDM for Microsoft 365 or the more feature-rich Intune solution.

There are key differences between the two solutions, each of which is described in the following table.

:::row:::
  :::column:::
    **Feature area**
  :::column-end:::
  :::column:::
    **MDM for Microsoft 365**
  :::column-end:::
  :::column:::
    **Microsoft Intune**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cost
  :::column-end:::
  :::column:::
    Included with many Microsoft 365 commercial subscriptions.
  :::column-end:::
  :::column:::
    Requires a paid subscription for Microsoft Intune or can be purchased with Enterprise Mobility Suite.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    How you manage devices
  :::column-end:::
  :::column:::
    Manage devices using the Security and Compliance Center in Microsoft 365.
  :::column-end:::
  :::column:::
    If you use Intune by itself, you can manage PCs from the cloud using the Intune admin console, with no infrastructure required.If you connect Intune to System Center 2012 Configuration Manager, you can manage all your devices (including PCs, Macs, Linux servers, and UNIX servers) and mobile devices from the Configuration Manager console.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Devices you can manage
  :::column-end:::
  :::column:::
    Cloud-based management for iOS, Android, and Windows devices.
  :::column-end:::
  :::column:::
    Cloud-based management for iOS, macOS X, Android, Windows 8.1 (Phone and PC) and later to include Windows devices.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Key capabilities
  :::column-end:::
  :::column:::
    Help ensure that Microsoft 365 corporate email and documents can be accessed only on phones and tablets that are managed by your company and that are compliant with your IT policies.
Set and manage security policies, like device level pin lock and jailbreak detection, to help prevent unauthorized users from accessing corporate email and data on a device when it's lost or stolen.
Remove Microsoft 365 company data from an employee’s device while leaving their personal data in place.
Details are included in [Capabilities of Basic Mobility and Security.](/microsoft-365/admin/basic-mobility-security/capabilities?azure-portal=true)
  :::column-end:::
  :::column:::
    MDM for Microsoft 365 capabilities, plus:
Help users securely access corporate resource with certificates, Wi-Fi, VPN, and email profiles.
Enroll and manage collections of corporate-owned devices, simplifying policy and app deployment.
Deploy your internal line-of-business apps and apps in stores to users.
Enable your users to securely access corporate information using the Office mobile and line-of-business apps they know. This process ensures data security by restricting actions like copy, cut, paste, and save as, to only those apps managed by Intune.
Enable more secure web browsing using the Intune Managed Browser app.
An Intune subscription also allows you to set up MAM (mobile app management) policies by using the Azure portal, even if user's devices aren't enrolled in Intune. See [Protect app data using MAM policies](/mem/intune/apps/app-protection-policy?azure-portal=true).

  :::column-end:::
:::row-end:::
