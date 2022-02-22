As the admin for your organization, you know that you need to manage updates across devices to ensure they stay up to date. This helps protect your organization from threats and vulnerabilities. Let’s look at how you can use Windows Update for Business to control and schedule updates for your organization’s devices.

## What is the deployment service?

The Windows Update for Business deployment service provides control over device updates by giving you the ability to approve, schedule, and safeguard content delivered from Windows Update.

The deployment service works with other Windows Update for Business capabilities, such as device policies and [Update Compliance](/windows/deployment/update/update-compliance-monitor). Let’s look at the following diagram:

:::image type="content" source="../media/2-pillars.png" alt-text="A diagram showing the pillars that underpin Windows Update." border="false":::

Windows Update for Business consists of three pillars:

- *Client policy* that you can use to manage update experiences and timing using tools like Group Policy and Configuration Service Provider (CSPs) policies
- *Deployment service APIs* for approving and scheduling specific updates using tools like Microsoft Graph and associated SDKs such as the PowerShell SDK
- *Update Compliance* for monitoring update deployment, which is available from the Azure Marketplace

The deployment service doesn’t save targeting configuration to devices. The service is in the cloud. The deployment service acts as a direct communication channel between a management tool like PowerShell and the Windows Update service. This gives you direct control of the approval and offering of content for devices.

You can use the deployment service to:

- Schedule update deployments to begin on a specific date.
- Stage deployments over a period of days or weeks using rich expressions.
- Bypass pre-configured Windows Update for Business policies to immediately deploy a security update.
- Ensure coverage of hardware and software in your organization through deployments tailored to unique device population(s).
- Safeguard devices from known issues.

The deployment service supports managing Windows feature updates and expediting Windows security updates. Features updates contain small or even significant features additions or changes to Windows. To learn more about the deployment service in the context of Windows Update for Business, please see the [Windows Update for Business deployment service documentation](/windows/deployment/update/deployment-service-overview) page.

## Understand the workflow

The workflow for using the deployment service consists broadly of three phases:

:::image type="content" source="../media/2-workflow.png" alt-text="A diagram representing the deployment workflow." border="false":::

- **Phase 1**: You select your target devices and approve content that you want to deploy. To do this you can use PowerShell, a Microsoft Graph app, or a management solution like Microsoft Endpoint Manager. Using your management tool, you send your content approval, scheduling, and device selection details to the deployment service.
- **Phase 2**: The deployment service then processes your content approval information and compares it with any previously approved content. The service then determines whether the device should receive the update and communicates with Windows Update.
- **Phase 3**: Windows Update then offers your approved content to your target devices the next time the devices check for updates.
