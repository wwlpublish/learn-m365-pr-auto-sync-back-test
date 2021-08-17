You're ready to implement pilot deployment of the update. As the company's process manager, here's the information you need.

## Inputs

In the previous phase, you helped your organization prepare outputs to use for pilot deployment. These are:

- A pilot deployment device list
- The security and configuration baseline
- A list of which applications will be assigned to deployment rings

You'll use these artifacts to make decisions and carry out tasks to pilot the Windows 10 feature update.

## Decisions and tasks  

To perform pilot deployment successfully, you'll make decisions along the following lines:

- **App validation**: Consider what the validation process will be for application compatibility. For example, what's the remediation process for any potential issues?
- **Deployment**: How will your team deploy to pilot devices? How will they ensure that deployment is scoped to apply only to selected pilot devices and users? To achieve this, your administrators could use Desktop Analytics to automatically deploy to the correct pilot devices.
- **Capability and modernization**: How will you obtain feedback on new capabilities and ensure that modernized infrastructure is actually benefiting them?

You'll have to ensure that several tasks are completed during pilot deployment, including:

- **Validate deployment processes**: Your team must ensure that it can deploy the update by validating its tools, settings, and ability to apply the update across its environment.
- **Deploy to devices**: Your team deploys the update to pilot devices for testing, with appropriate configuration of policies to ensure an optimal user experience when receiving the update.
- **Test and support devices**: The pilot group validates the update across the devices, and provides feedback to operations teams.
- **Determine broad deployment readiness**: Your team uses the feedback and results of pilot deployment to determine whether the update can be deployed broadly.

The tasks should be assigned to the various roles in the process. You use the *Responsible, Accountable, Consulted, Informed* (RACI) model to create an example mapping that your team can use as a reference for assigned tasks:

|Task  |Process manager  |End-user computing  |Operations  |Security  |App owners and developers  |
|---------|---------|---------|---------|---------|---------|
|Assign pilot devices from Prepare phase to receive the update     |Informed|Responsible|Informed|N/A|N/A|
|Implement baseline updates|Informed|Responsible|N/A|Consulted|N/A|
|Implement operations updates|Informed|Informed|Responsible|N/A|N/A|
|Validate deployment process|Informed|Responsible|Informed|N/A|N/A
|Deploy to devices|Informed|Responsible|Consulted|N/A|N/A|
|Test and support devices|Informed|Consulted|Responsible|N/A|N/A|
|Determine broad deployment readiness|Responsible|Consulted|Consulted|Consulted|Consulted|

To reduce time selecting devices for pilot deployment, you can use Desktop Analytics and Configuration Manager to deploy the update. For pilot deployment, your administrators might do the following:

1. Use Desktop Analytics devices recommended for pilot deployment, adding or removing as the team sees fit. Use Configuration Manager collections by including or excluding devices appropriately.
1. Review and address any issues reported by Desktop Analytics in the portal.
1. Deploy the update using Configuration Manager. The team will need to select its deployment plan in Configuration Manager, and configure it using the Create Phased Deployment wizard.

## Outputs

You'll have to ensure that your team generate multiple artifacts to use for broad deployment, the next step in the process. These artifacts include:

|Item  |Example  |Description  |
|---------|---------|---------|
|Infrastructure and configuration go or no-go decision (broad deployment)|Meeting or email|Pass or fail results compared against the deployment readiness criteria|
|Applications and devices to remediate (if needed)     |Spreadsheet|Operations provide this. Encouraged to include details about devices and applications that require remediation|
|Security and configuration baseline     |Policy and configuration file|Final settings to be applied to the rest of devices during broad deployment|
