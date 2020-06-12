Woodgrove is ready to deploy the update across the wider production environment. As the process manager, you’ll outline what the company needs to do to successfully deploy the update to users and their devices.

## Inputs

In the previous phase, you helped Woodgrove prepare outputs that it can use for Broad deployment. These are:

- A list of apps and devices not ready for Broad deployment
- Validate security and baseline settings

Woodgrove uses these artifacts to make decisions and carry out tasks for Broad deployment of the Windows 10 feature update.

## Decisions and tasks  

Woodgrove can take advantage of deployment rings to roll out the update across its environment. A deployment ring is a selection of devices that receive an update at the same time. For each ring, Woodgrove sets criteria that must be met before the update can be applied to the next ring. There are no set rules for the number of deployment rings available. An organization could decide to create deployment rings based on the geographic locations of its offices. It could also create deployment rings based on how critical devices are for the organization.

Woodgrove can use Desktop Analytics to identify that are devices ready for deployment. Woodgrove will then be able to create a single deployment ring, where devices identified as ready to receive the update go into a device collection in Configuration Manager, and Woodgrove can use that collection as a target for deployment of the update.

Alternatively, Woodgrove can also use the list of devices provided by Desktop Analytics, and perform additional administrative efforts to create multiple deployment rings based on its unique requirements. For example, Woodgrove can choose to create four deployment rings:

|Deployment ring  |Issues identified  |Passed validation?  |Deployment status  |
|---------|---------|---------|---------|
|1     |None|Yes|Completed|
|2     |None|Yes|Completed|
|3     |Drivers out of date|No|Paused|
|4     |--|--|--|

Each deployment ring contains a quarter of the devices in Woodgrove's total estate. Deployment would only continue to the next ring if no issues remain unresolved.

Woodgrove will complete different tasks during this part of the Deploy phase. These tasks are categorized into broader, high-level sections. The tasks should be assigned to the various roles in the process. You use the RACI model to create an example mapping, so Woodgrove can use it as a reference when assigning tasks:

|Task  |Process manager  |Application owner  |Application developers  |End-user computing  |Security  |Operations  |
|---------|---------|---------|---------|---------|---------|---------|
|Create Broad deployment ring|Informed|N/A|N/A|Responsible|N/A|Informed
|Assign devices|Informed|Consulted|N/A|Responsible|Informed|Consulted
|Implement operations updates     |Informed|N/A|N/A|Informed|N/A|Responsible
|Update bare metal process|Informed|Consulted|Consulted|Responsible|Consulted|Consulted
|Validate deployment process|Informed|N/A|N/A|Responsible|N/A|Informed
|Deploy feature update|Informed|Informed|Informed|Responsible|Informed|Consulted
|Support feature update|Informed|Informed|Consulted|Informed|Consulted|Responsible
|Review deployment success|Informed |Consulted|Informed|Informed|Informed|Responsible
|Obtain recommendations for improvements|Informed |Consulted|Consulted|Consulted|Consulted|Consulted

With Desktop Analytics, Woodgrove can use the same deployment plan it created during pilot testing to deploy to the rest of its devices. Here’s how the process works in the Desktop Analytics portal:

1. Review any apps that need to be approved for production deployment by marking them as "Ready".
1. Each device will automatically be moved to a production collection when all of its installed applications have been marked as "Ready".
1. Configuration Manager will then automatically deploy to Woodgrove’s production devices if the team has set a default automatic two-phase deployment.

## Outputs

During Broad deployment, Woodgrove will generate multiple artifacts that it can use for the next deployment cycle. This will help reduce cost, time, and effort involved in the deployment of future updates. Later, you'll see that Woodgrove can use these artifacts to map tools and practices against any issues noted during Broad deployment.

|Item  |Example  |Description  |
|---------|---------|---------|
|Deployment considerations|Document|Recommend tools and practices that can help improve Broad deployment in the next cycle|
|Infrastructure recommendations|Document|Recommend infrastructure related tools and practices that can help improve Broad deployment in the next cycle|
|Ops and innovation recommendations|Document|Recommend operations related tools and practices that can help improve Broad deployment in the next cycle|

