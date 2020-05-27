Your manager isn’t sure how to approach infrastructure and configuration readiness to support Windows servicing. You’ve been asked to investigate how Woodgrove can define a repeatable process to ensure the environment’s infrastructure and configuration supports future Windows updates.

## Inputs

Previous deployments will help you understand what types of activities you’ll need to do to support the new update.

### Infrastructure updates

- **Assess the infrastructure used to deploy and manage Windows 10**: Confirm the support of the new Windows 10 feature update with your infrastructure management tooling, and determine the effort needed to update the infrastructure.

- **Microsoft endpoint Configuration Manager current branch**: The latest release of Configuration Manager provides support for all serviced versions of Windows 10, and support for the next Windows 10 feature update. The Configuration Manager update is serviced for 18 months after release.
- For those customers who use cloud-based infrastructure management tooling, such as Microsoft Intune, supportability challenges will be reduced as no on-premises or client-side products need to be updated.
- For third-party on-premises infrastructure tooling, confirm supportability and next steps with product support.

It's recommended to use data from previous deployments to get an idea of how long infrastructure changes take, previous challenges found when upgrading infrastructure, and the resources that need to be consulted/informed about the update.

### Configuration updates

Before you apply the Windows 10 feature update to your environment, you’ll need to assess and update the required configuration. This action will ensure security and capabilities are configured appropriately to support production devices. Organizations typically do the following tasks:

**Plan for security baseline updates**

Security baselines are designed to help ensure your devices are configured with Microsoft recommended guidance. Security risks and threats are constantly changing. Updating security baselines helps to secure your environment, and ensure new security features delivered as part of the Windows 10 feature update are configured correctly. Your organization is likely to have to implement different security baselines. Plan to review the following baselines:

- **Microsoft security baselines**. It's highly recommended that you implement security baselines from Microsoft. You can find them included with Microsoft’s Security Compliance Toolkit, which also provides tools to help you manage security baselines.
- **Industry or region-specific baselines**. Your industry or region might have its own security baselines that you need to adhere to for compliance or regulatory reasons. For example, if Woodgrove is a financial organization, it might need additional security configuration, compared to a retail company. Check to ensure any new baselines implemented support the version of Windows 10 you're deploying.

### Plan for configuration updates

Review and configure policies that will help your devices take advantage of any new Windows 10 features. Ensure devices are configured to apply updates when they're ready. The following items should be assessed ahead of implementation in the prepare phase:

- **Windows 10 Administrative templates**: Every Windows 10 feature update has a supporting Administrative template, which can be imported into a customer environment to support new features of the OS.
- **Optimize Windows 10 update adoption**: Review the set of policies in the link below to assist with configuring your devices to take updates, and keep them online during the update process. This approach helps devices with low activity stay online to download and install updates, ensuring they have a serviced version of Windows 10.  Follow Microsoft guidance for policies.

> [!TIP]
> You can find links to Microsoft guidance for policies, and the Microsoft Security Compliance Toolkit, in the **Learn more** section at the end of this module.

### Define operational readiness criteria

When you’ve deployed an update, you’ll need to make sure it isn’t introducing new operational issues. You’ll also ensure that, if incidents arise, the required documentation and processes are available. To achieve  outcome, work with your operations and support team to define acceptable trends, and what documents or processes need to be updated:

- **Call trend**. Define what percentage increase in calls about Windows 10 feature updates is acceptable, or might be supported.
- **Incident trend**. Define what percentage of increase in calls asking for support about Windows 10 feature updates is acceptable, or can be supported.
- **Support documentation**. Review supporting documentation that requires an update to support new infrastructure tooling or configuration as part of the Windows 10 feature update.
- **Process changes**. Define and update any processes that will change after the Windows 10 feature update.

Operations/support can help you determine if the appropriate information is being tracked at the moment. If it’s not being tracked, work out how to get hold of it, so you can gain the right insight.

## Tasks

Finally, you can begin to carry out the work needed to ensure your infrastructure and configuration will support the update. To help you keep track, you classify the work into the following overarching tasks:

- **Review infrastructure requirements**. Go over the details of requirements to support the update, and ensure they’ve all been defined.
- **Validate infrastructure against requirements**. Compare your infrastructure against the requirements that have been identified for the update.
- **Define infrastructure update plan**. Detail how your infrastructure will need to be changed to support the update.
- **Review current support volume**. Understand the current support volume to know how much of an effect the update has when it’s been deployed.
- **Identify gaps that require attention**. Identify issues that will need to be addressed to successfully deploy the update. For example, will an engineer have to research how a new feature that comes with the update might affect the infrastructure?
- **Define operational update plan**. Detail how your operational services and processes will need to be changed to support the update.

## Outputs

You now create the following updates for artifacts you can use for the next phase in the workstream:

:::image type="content" border= "false" source="../media/6-outputs.png" alt-text="Outputs":::