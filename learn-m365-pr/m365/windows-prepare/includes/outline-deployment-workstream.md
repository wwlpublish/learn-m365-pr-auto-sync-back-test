Your manager wants to know how Woodgrove's infrastructure and configuration can be prepared for the Windows 10 feature update. As the process manager, you formalize the process and work with stakeholders to identify who should be involved in the preparation.

## Infrastructure tasks

Woodgrove will prepare its infrastructure for the update by implementing the changes identified in the Plan phase. To do this, you define what Woodgrove needs to do for the various components and tooling of its infrastructure, for example:

- Implement site server updates for Configuration Manager
- Update security tools like security agents or servers
- Update management tools like data loss prevention agents

Woodgrove's infrastructure includes many different components and tools. As the process manager responsible for the Windows 10 feature update, you need to validate that the environment won't be affected due to changes made to various parts of the infrastructure. Woodgrove will do this by:

1. **Reviewing all of the infrastructure changes** that Woodgrove identified in the Plan phase: It's important to understand the changes that need to be made and to detail how to implement them. This prevents issues later on.
1. **Validating changes**: Woodgrove will validate the changes for the infrastructure's components and tools to help understand how changes could affect its production environment.
1. **Implementing the changes**: Once the changes have been validated, Woodgrove can implement the changes across the wider infrastructure.

As the process manager, you oversee and keep track of the status of the tasks. You use the RACI model to create an example table that your organization can use for reference when assigning tasks to roles:

|*Task*  |Process manager  |End-user computing  |Application developer  |Operations |Security|
|---------|---------|---------|---------|---------|---------|
|*Review infrastructure changes*|Informed| Responsible|Informed|Informed|Informed|
|*Test and implement changes*|Informed|Responsible|Informed|Informed|Informed|
|*Implement and test operations changes*|Informed|Consulted|Informed|Responsible|Informed|

## Configuration tasks

Woodgrove must look at its environment's settings and outline how it will implement any necessary changes previously identified in the Plan phase to support the update. Consider what Woodgrove will need to do for the various settings and policies that currently underpin the environment.  Woodgrove will have to do the following:

- **Implement new security guidance**: New versions of Windows can include new features that improve your environment's security. Woodgrove's security teams will want to make appropriate changes to security-related settings. This is needed to keep customers and their data secure.
- **Update security baselines**: Security teams understand the relevant security baselines and will have to work to make sure all baselines match the required guidance.

However, Woodgrove's environment has many different settings and policies. It's important to only apply changes where they are necessary, and where a clear improvement can be gained for Woodgrove. Otherwise, Woodgrove's environment might face issues that will slow down the update process. Woodgrove needs to ensure the environment isn't affected adversely because of changes made to the various parts settings and policies. For example, for its security-related settings Woodgrove will do this by:

1. **Reviewing new security settings**:  The security team, together with end-user computing, are responsible for validating and deploying new security settings. So they will review the security settings to understand how they can best be configured to facilitate the update.
1. **Reviewing security baselines for changes**: Security teams will also review all the necessary security baselines to ensure the changes can be implemented and ensure your environment remains compliant.
1. **Implementing and validating security settings and baseline changes**: The security teams will implement all of the security settings and baselines, having addressed any potential outstanding issues.

## Outputs

As the process manager, you explain that Woodgrove will have to agree on whether its infrastructure is prepared to handle a pilot deployment of the update to a few devices. Woodgrove will do this by comparing its infrastructure against the deployment readiness criteria outlined in the Plan phase and agreeing whether it has met all the criteria (pass) or not (fail).  

Once Woodgrove has implemented all the necessary configuration changes, it will also have to capture the final version of settings and policies so they can be referenced for a pilot deployment against a select few devices. You explain that Woodgrove will create the following artifacts:

|Item  |Example format  |Description  |
|---------|---------|---------|
|Infrastructure and configuration go or no-go decision (Pilot deployment) |Meeting or email|Pass or fail results comparing against deployment readiness criteria.|
|Security and configuration baseline|Policy and configuration File|Final settings to be applied to devices for Pilot deployment.|
