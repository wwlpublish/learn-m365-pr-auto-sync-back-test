Woodgrove has missed out on taking advantage of new capabilities in the past, and has historically spent a lot of resource effort to update devices in the production environment. Your technical director wants to avoid this going forward. Your manager has asked you to outline a plan for how Woodgrove can modernize its environment to improve productivity, reduce cost, effort, and time related to Windows servicing.

## Inputs

You'll need to look at what new features and improvements are available, and assess your current situation to understand what you might need to do to modernize your environment.

### Investigate new features and improvements

Make sure to take advantage of resources that will help you monitor for improvements that are available for all of your tooling and components across your environment.

- **Review IT Pro features of Windows 10** – The "[what's new in Windows 10](/windows/whats-new/)" page lists improvements for IT pros. Reviewing these capabilities against your current environment can help to determine what features to communicate to remote workers, and what IT Professionals should use to support them.  
- **Join the Windows 10 TechCommunity** – Learn about technical best practices, the latest news, and trends related to Windows 10 at [TechCommunity](https://techcommunity.microsoft.com/t5/windows-10/ct-p/Windows10).
- **Configuration Manager** -  You can keep up to date by tracking all the new changes in each incremental [new version](/mem/configmgr/core/plan-design/changes/whats-new-incremental-versions).

The information you've collected from testing and tracking new features and capabilities will help you figure out how Woodgrove can modernize its environment.

## Assess your state

Assess the state of your environment to understand where you want to go. You can do this by defining high-level goals for your environment, along with which phase those goals are applicable to - for example:

|Phase  |Goal  |Type  |
|---------|---------|---------|
|- Plan<br/>- Prepare<br/>- Deploy|Reduce infrastructure upgrade effort|- Infrastructure<br/>- Configuration
|- Plan<br/>- Prepare<br/>- Deploy|Reduce testing effort|- Compatibility<br/>- Infrastructure<br/>- Configuration
|

From your goals, you can have a better understanding of what should be the aim for each component and tool in your environment. For example, Woodgrove might be using Windows Server Update Services (WSUS) today for software update management, but you could decide that you want to move to Windows Update for Business so that updates are delivered by the cloud-based Windows Update service for your organization.

### Decisions

Use the learnings from the investigations and assessment of your state to help you understand how you can invest in new tooling and capabilities. Ask what your organization will need to modernize its tools and capabilities from stakeholders in the process. For instance, critical application testing can be time consuming, so application developers could suggest automated testing to address this. You can outline your goal, along with what investments are needed to achieve that goal. For example, if your goal is to reduce testing effort, you can create the following outline:

|Investment  |Benefit  |Cost to implement  |Projected savings per feature update  |
|---------|---------|---------|---------|
|Automation for critical apps|Reduce resource effort to test quicker adoption of update|$|$|

### Tasks

Identify the tasks you'll have to carry out to modernize your organization's environment. You can do this by:

- **Determining infrastructure changes**. For example, the end-user computing group identifies that it will have to increase the capacity of the hardware that is running your infrastructure in order to accommodate the new capabilities.
- **Determine configuration changes**. The security group might decide that it will have to review security policy changes to ensure you still meet security baselines when moving encryption keys to a cloud-based service.

Create a proposal for changes your organization needs to carry out to modernize its environment. Your organization can then also determine what are its go or no-go criteria for proposed changes. The proposal should be reviewed and approved by someone with the authority to allocate the resources needed to implement the proposed changes. Once a proposal has been reviewed and approved, the proposed changes can then be implemented.

## Outputs

Create and update the following artifacts that will help you capture the details about your modernization approach for the next phase:

|Item  |Format  |Description  |
|---------|---------|---------|
|Approved capability and modernization improvements     |Word document|Capture details about the improvements along with the business value added by these improvements|
|Infrastructure and configuration remediation list|Spreadsheet|Capture configuration and infrastructure changes that need to be made to implement the approved improvements|
