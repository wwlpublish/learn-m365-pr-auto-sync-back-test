Your manager isn't sure about how to approach infrastructure and configuration readiness to support Windows servicing. You've been asked to investigate how Woodgrove can define a repeatable process to ensure the environment's infrastructure and configuration can support future Windows updates.

## Inputs

Previous deployments can help you understand what types of activities you'll need to do to support the new update.

### Infrastructure updates

Assess the infrastructure used to deploy and manage Windows 10. Confirm the support of the new Windows 10 feature update with your infrastructure management tooling, and determine the effort needed to update the infrastructure.

- Microsoft Endpoint Configuration Manager Current Branch – the latest release of Configuration Manager provides support for all serviced versions of Windows 10, and support for the next Windows 10 feature update. The Configuration Manager update is serviced for 18 months after release
- For those customers that use cloud-based infrastructure management tooling such as Microsoft Intune, supportability challenges will be reduced as no on-premises or client-side products need to be updated.
- For non-Microsoft on premises infrastructure tooling, confirm supportability and next steps with product support.

It is recommended to use data from previous deployments to get an idea of how long infrastructure changes take, previous challenges encountered when upgrading infrastructure, and the resources that need to be consulted, or informed about the update.

### Configuration updates

Before you can apply the Windows 10 feature update to your environment, you'll need to assess and update required configuration to ensure security and capabilities are configured appropriately, to support production devices. Organizations typically perform the following tasks:

#### Plan for Security baseline updates

Security baselines are designed to help you ensure your devices are configured with Microsoft recommended guidance. Security risks and threats are constantly changing, and updating security baselines helps to secure your environment and ensure new security features delivered as part of the Windows 10 feature update are configured accordingly. There are different security baselines your organization will in all likelihood need to implement. Plan to review the following:

- **Microsoft security baselines**: It is highly recommended that you implement security baselines from Microsoft. You can find them included with Microsoft's [Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319), which will also provide you with tools to help manage your security baselines.
- **Industry or region-specific baselines**: Your industry or region may have its own security baselines that you need to adhere to for compliance or regulatory reasons. For example, if Woodgrove is a financial organization, it may have more required security configurations than a retail organization. Check to ensure any new baselines implemented support the version of Windows 10 you are deploying.

#### Plan for configuration updates

Review and configure policies that will help your devices take advantage of any new Windows 10 features, and ensure devices are set to apply updates when they are ready. The following items should be assessed ahead of implementation in the Prepare phase:

- **Windows 10 Administrative Templates** – Every Windows 10 feature update has a supporting administrative template, which can be imported into a customer environment to support new features of the operating system.
- **Optimize Windows 10 update adoption** – review the [set of policies](https://aka.ms/UpdateVelocity) to assist with setting your devices to take updates, and keep them online while the update process is happening. This approach helps devices with low activity stay online to download and install updates, ensuring they have a serviced version of Windows 10.

### Define operational readiness criteria

When you've deployed an update, you'll need to make sure the update isn't introducing new operational issues. And you'll also ensure that if incidents arise, the needed documentation and processes are available. To achieve this, work with your operations and support team to define acceptable trends and what documents or processes require updating:

- **Call trend**: Define what percentage increase in calls relating to Windows 10 feature updates are acceptable or can be supported.
- **Incident trend**: Define what percentage of increase in calls asking for support relating to Windows 10 feature updates are acceptable or can be supported.
- **Support documentation**: Review supporting documentation that requires an update to support new infrastructure tooling or configuration as part of the Windows 10 feature update.
- **Process changes**: Define and update any processes that will change as a result of the Windows 10 feature update.

Operations or support can help you determine if the appropriate information is being tracked at the moment, and if it's not being tracked, work out how to get a hold of it so you can gain the right insight.

## Tasks

Finally, you can begin to carry out the work needed to ensure your infrastructure and configuration can support the update. To help you keep track, you can classify the work into the following overarching tasks:

- **Review infrastructure requirements**: Go over the details of requirements to support the update, and ensure they've all been defined.
- **Validate infrastructure against requirements:** Compare your infrastructure against the requirements that have been identified for the update.
- **Define infrastructure update plan**: Detail how your infrastructure will need to be changed to support the update.
- **Review current support volume:** Understand the current support volume to understand how much of an effect the update has when it's been deployed.
- **Identify gaps that require attention:** Identify issues that will need to be addressed to successfully deploy the update. For example, will your infrastructure engineer have to research how a new feature that comes with the update might affect the infrastructure?
- **Define operational update plan:** Detail how your operational services and processes will need to be changed to support the update.

## Outputs

You will now be able to create the following updates artifacts that you can use for the next phase in the workstream:

|Item  |Example format  |Description  |
|---------|---------|---------|
|Deployment readiness go or no-go criteria     |Word document|Detail the deployment readiness and supportability|
|Infrastructure and configuration remediation list     |Word document|- Detail infrastructure management tools required <br/>- Detail security and configuration baseline changes needed
|Operations update plan     |Word document|Outline approach to updating operation processes|
