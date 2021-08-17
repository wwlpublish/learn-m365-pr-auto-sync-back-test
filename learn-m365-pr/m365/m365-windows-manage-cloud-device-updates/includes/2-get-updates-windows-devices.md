You want to protect your organization, and facilitate productivity across the organization. You've decided that all Windows devices should stay in line the latest Windows updates. Microsoft offers different sets of tools and services that empower you with the flexibility and capabilities you need to update your devices.

In this unit, you'll explore the tools and services you can use to update your Windows devices.

## Understand Windows Update for Business

The cloud is a term for Microsoft's endpoint that devices can connect to directly and get updates from; we call this endpoint Windows Update. You can control which updates Microsoft offers you from Windows Update using Windows Update for Business. Windows Update for Business allows you to manage Windows Update updates using a Group Policy management tool or a mobile device management (MDM) tool.

### Group Policy management tools

Group Policy management tools use Group Policy Objects to control device behavior and Windows update distribution. Group Policy management tools include:

- A local Group Policy Editor, which is built in to every premium edition device.
- The Group Policy Management Console (GPMC).
- Non-Microsoft management tools.

### Mobile device management tools

Mobile device management uses configuration service provider (CSP) policies and APIs to control device behavior and Windows update distribution. Some examples include:

- Microsoft Intune (now part of Microsoft Endpoint Manager (MEM)).
- Non-Microsoft MDM solutions.
  
There are over 50 different Windows update policies across Group Policies and CSPs. However, you only need to know about a fraction of them to successfully manage Windows updates.

## Connect your devices to Windows Update to get Windows updates

:::image type="content" source="../media/2-connect-devices.png" alt-text="Figure 1. Connecting your devices":::

### Understand Windows Server Update Services

There are a few different ways to get Windows updates. One way is using *Windows Server Update Services*. Windows Server Update Services is a Windows Server server role that you can install to enable administrators to manage and distribute updates. A Windows Server Update Services server can be the source of updates for other Windows Server Update Services servers within the organization. The Windows Server Update Services server that acts as an update source is called an upstream server. For more information, see [Deploy Windows Server Update Services](/windows-server/administration/windows-server-update-services/deploy/deploy-windows-server-update-services?azure-portal=true).

Windows Server Update Services can be useful for those who want to have a high level of control over their updates. However, Windows Server Update Services also requires a high level of overhead to manage, including updating by downloading media or installing updates from a USB drive. Windows Server Update Services also requires that you sync updates to your Windows Server Update Services server and then send these updates out to devices in your organization.

With Windows Update, you use a management tool to tell the device and the Windows Update server directly what should be offered. In turn, your device will connect directly to Microsoft's Windows Update endpoint to receive updates.

### Microsoft recommendation

To select your update source, Windows Server Update Services or Windows Update, you must configure the source properly. To ensure that your devices are connected to Windows Update, we recommend the following:

- **Group Policy: Do not connect to any Windows Update Internet locations**. Do not enable this Group Policy.
- **Group Policy: Don't allow update deferral policies to cause scans against Windows Updates**. Don't enable this Group Policy or the [Update/DisableDualScan](/windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
If you've specified an intranet Microsoft update service location, please ensure that you do enable one of the following:
- **Group Policy: Specify preview builds and Feature Updates are received** or the [Update/DeferFeatureUpdatesPeriodInDays](/windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
- **Group Policy: Specify when quality updates are received** or the [Update/DeferQualityUpdatesPeriodInDays]( /windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
Once you've configured the scan source correctly to ensure your devices are connecting directly to Windows Update, you're now ready to manage what updates are offered.
