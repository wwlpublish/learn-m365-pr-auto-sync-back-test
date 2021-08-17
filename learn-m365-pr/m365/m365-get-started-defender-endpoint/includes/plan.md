First, you'll need to define your organization's current security architecture. This decision will then inform the tools you can use to onboard devices and the capabilities and features of Microsoft Defender for Endpoint that you will adopt.

Here you'll identify an architecture that is the closest to your current organization, review and then identify the tools that you can use.

:::image type="content" source="../media/plan-table-contents.png" alt-text="A diagram showing the three topics covered in this unit, architecture, tools, and capabilities.":::

## Identify architecture

You can use Microsoft Defender for Endpoint in your environment in different ways to meet your needs. The first step is to classify how your company is structured. Choose the architecture that best maps to your needs.

### Cloud-native

:::image type="content" source="../media/cloud-native.png" alt-text="Diagram explaining what a cloud native architecture looks like." border="false":::

You should choose a cloud-native architecture if your organization's devices are based in the cloud. For example, if all devices are managed by Microsoft Endpoint Manager, or if your organization would like to move to them in the future to be managed by Microsoft Endpoint Manager.

### Co-management

:::image type="content" source="../media/co-management.png" alt-text="Diagram explaining what a co-management architecture looks like." border="false":::

Choose co-management if you have a blended architecture, with devices managed by Microsoft Endpoint Manager and an on-premises configuration management solution.

### On-premises

:::image type="content" source="../media/on-premises.png" alt-text="Diagram explaining what an on-premises architecture looks like." border="false":::

Choose an on-premises architecture if all your devices are using either Configuration Manager or Active Directory Domain Services. Your organization can still benefit from using the power of the cloud-based Microsoft Defender for Endpoint.

## Select onboarding tools

Once you've identified your organization's architecture, you can identify the tools you'll use to onboard devices to Microsoft Defender for Endpoint. Each architecture type has a selection of tools to use for onboarding:

|Architecture|Tools|
|-|-|
|Cloud-native|Microsoft Endpoint Manager|
|Co-management|Microsoft Endpoint Manager, Configuration Manager|
|On-premises|Configuration Manager, Group Policy|

> [!NOTE]
> There are also other tools that you could use for non-Windows devices. For example, Puppet or Ansible on Linux. Use the Plan your Microsoft Defender for Endpoint deployment link in the **Learn more** section for more details.

## Identify deployment rings

Next, you need to define deployment rings. Using deployment rings, you onboard a set number of devices first, look for potential issues (using exit criteria), and then address those issues before you go to the next set of devices. This is useful for your scenario because you don't want to onboard all your devices in one go.

The recommended deployment ring structure to use with Microsoft Defender for Endpoint is as follows:

:::image type="content" source="../media/4-deployment-rings.png" alt-text="A diagram that shows the Deployment rings." border="false":::

Each ring represents a group of devices. The rings work like this:

|Deployment ring|Description|
|-|-|
|Evaluate|You choose a relatively small number of test devices (up to 50) to onboard. You test the devices in this ring to ensure that they meet your exit criteria before you move to the next ring. Exit criteria can include confirming whether the devices show up in the devices list and alerts are showing up in the dashboard. You can also run a detection test on the devices to confirm if the devices have been onboarded successfully.|
|Pilot|If the devices have passed the evaluation ring, you can then move up to this deployment ring. You choose more devices to onboard (between 50 to 100 devices). Then if the devices pass your exit criteria, you proceed to the next deployment ring.|
|Full deployment|If the devices have passed the pilot ring, you can move to this final ring, where you onboard the rest of your devices in increments. Use the **deployment** link in the **Learn more** section to access best practice material on how to do this.|

## Learn more

- [Plan your Microsoft Defender for Endpoint deployment](/microsoft-365/security/defender-endpoint/deployment-strategy)
