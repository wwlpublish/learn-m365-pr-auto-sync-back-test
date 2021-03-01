
You want to protect your organization, and facilitate productivity across the organization. You've decided that all Windows devices should stay in line the latest Windows updates. Microsoft offers different sets of tools and services that empower you with the flexibility and capabilities you need to update your devices.

In this unit, you’ll explore the tools and services you can use to update your Windows devices.

## Windows Update for Business

The cloud is a term for Microsoft’s endpoint that devices can connect to directly and get updates from; we call this endpoint Windows Update (WU). You can control which updates Microsoft offers you from WU using Windows Update for Business. Windows Update for Business allows you to manage WU updates using a Group Policy (GP) management tool or a mobile device management (MDM) tool.

### Group Policy management tools

Group Policy management tools use Group Policy Objects (GPO) to control device behavior and Windows update distribution. Group Policy management tools include:

- A local Group Policy Editor, which is built in to every premium edition device.
- The Group Policy Management Console (GPMC).
- Non-Microsoft management tools.

### Mobile device management tools

Mobile device management uses configuration service provider (CSP) policies and APIs to control device behavior and Windows update distribution. Some examples include:

- Microsoft Intune (now part of Microsoft Endpoint Manager (MEM)).
- Non-Microsoft MDM solutions.
  
There are over 50 different Windows update policies across Group Policies and CSPs. However, you only need to know about a fraction of them to successfully manage Windows updates.

## Connect your devices to WU to get Windows updates

:::image type="content" source="../media/2-connect-devices.png" alt-text="Figure 1. Connecting your devices":::

### Windows Server Update Services

There are a few different ways to get Windows updates. One way is using *Windows Server Update Services (WSUS)*. WSUS is a Windows Server server role that you can install to enable administrators to manage and distribute updates. A WSUS server can be the source of updates for other WSUS servers within the organization. The WSUS server that acts as an update source is called an upstream server. For more information, see [Deploy Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/deploy/deploy-windows-server-update-services?azure-portal=true).

WSUS can be useful for those who want to have a high-level of control over their updates. However, WSUS also requires a high level of overhead to manage, including updating by downloading media or installing updates from a USB drive. WSUS also requires that you sync updates to your WSUS server and then send these updates out to devices in your organization.

In this module, we will focus on using Windows Update. With WU, you use a management tool to tell the device and the Windows update server directly what should be offered. In turn, your device will connect directly to Microsoft’s Windows Update endpoint to receive updates.

### Microsoft recommendation

To select your update source, WSUS or WU, you must configure the source properly. To ensure that your devices are connected to WU, we recommend the following:

- **GP: Do not connect to any Windows Update Internet locations**. Do not enable this GP.
- **GP: Do not allow update deferral policies to cause scans against Windows Updates**. Do not enable this GP or the [Update/DisableDualScan](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
If you have specified an intranet Microsoft update service location, please ensure that you do enable one of the following:
- **GP: Specify preview builds and Feature Updates are received** or the [Update/DeferFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
- **GP: Specify when Quality Updates are received** or the [Update/DeferQualityUpdatesPeriodInDays]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update?azure-portal=true) CSP policy.
Once you have configured the scan source correctly to ensure your devices are connecting directly to Windows Update, you are now ready to manage what updates are offered.
