Woodgrove is ready to implement Pilot deployment of the update and, as the company’s process manager, you’ll outline what they need to do to complete this.

## Inputs

In the previous phase, you helped Woodgrove prepare outputs to use for Pilot deployment.  These are:

- A Pilot deployment device list
- The security and configuration baseline 
- A list of which applications will be assigned to deployment rings

Woodgrove will use these artifacts to make decisions and carry out tasks to pilot the Windows 10 feature update.

## Decisions and tasks  

To perform Pilot deployment successfully, Woodgrove makes decisions along the following lines:

- **App validation**: Consider what the validation process will be for application compatibility. For example, what’s the remediation process for any potential issues?
- **Deployment**: How will Woodgrove deploy to pilot devices? How will the organization ensure that deployment is scoped to apply only to selected pilot devices and users? To achieve this, Woodgrove could use Desktop Analytics to automatically deploy to the correct pilot devices. 
- **Capability and modernization**: How will Woodgrove obtain feedback on new capabilities and ensure that modernized infrastructure is actually benefiting them?

Woodgrove will have to complete several tasks during Pilot deployment, including:

-	**Validate deployment processes**: Where the company ensures it can deploy the update by validating its tools, settings, and ability to apply it across its environment.
-	**Deploy to devices**: Woodgrove deploys the update to pilot devices for testing, with appropriate configuration of policies to ensure an optimal user experience when receiving the update.
-	**Test and support devices**: The pilot group validates the update across the devices, and provides feedback to operations teams.
-	**Determine Broad deployment readiness**: Woodgrove uses the feedback and results of Pilot deployment to determine whether the update can be deployed broadly.

The tasks should also be assigned to the various roles in the process. You use the *Responsible, Accountable, Consulted, Informed* (RACI) model to create an example mapping that Woodgrove can use for reference:

|Task  |Process manager  |End-user computing  |Operations  |Security  |App owners and developers  |
|---------|---------|---------|---------|---------|---------|
|Assign pilot devices from Prepare phase to receive the update     |Informed|Responsible|Informed|N/A|N/A|
|Implement baseline updates|Informed|Responsible|N/A|Consulted|N/A|
|Implement operations updates|Informed|Informed|Responsible|N/A|N/A|
|Validate deployment process|Informed|Responsible|Informed|N/A|N/A
|Deploy to devices|Informed|Responsible|Consulted|N/A|N/A|
|Test and support devices|Informed|Consulted|Responsible|N/A|N/A|
|Determine Broad deployment readiness|Responsible|Consulted|Consulted|Consulted|Consulted|

To reduce time selecting devices for Pilot deployment, Woodgrove can use Desktop Analytics and Configuration Manager to deploy the update. For Pilot deployment, the organization might do the following:

1. Use Desktop Analytics devices recommended for Pilot deployment, adding or removing as Woodgrove sees fit. Use Configuration Manager collections by including or excluding devices appropriately.
1. Review and address any issues reported by Desktop Analytics in the portal.
1. Deploy the update using Configuration Manager. The team will need to select its deployment plan in Configuration Manager, and configure it using the Create Phased Deployment wizard.

## Outputs

During Pilot deployment, Woodgrove will generate multiple artifacts to use for Broad deployment, the next step in the process. These artifacts include:

|Item  |Example  |Description  |
|---------|---------|---------|
|Infrastructure and configuration go or no-go decision (Broad deployment)|Meeting or email|Pass or fail results compared against the deployment readiness criteria|
|Applications and devices to remediate (if needed)     |Spreadsheet|Operations provides this. Encouraged to include details about devices and applications that require remediation|
|Security and configuration baseline     |Policy and configuration file|Final settings to be applied to the rest of devices during Broad deployment|
