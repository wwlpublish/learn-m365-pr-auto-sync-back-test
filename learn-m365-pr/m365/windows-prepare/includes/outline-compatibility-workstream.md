
Woodgrove has many critical applications that will need to be validated before Pilot deployment.  As the process manager, you'll have to ensure that these applications are compatible and ready for the update.

## Compatibility tasks

You explain that Woodgrove will carry out the following tasks to validate the compatibility of its applications and devices:

### Validate applications

Woodgrove has decided it wants to validate its critical applications for compatibility with the update. To do this, you suggest that Woodgrove should validate all of its critical and important applications.  You explain that there are different approaches that Woodgrove could use to validate its critical and important applications, for example:

|Validation Method  |Description  |
|---------|---------|
|Regression (full)|Applications go through full quality assurance probing. This should be done by people who are knowledgeable of the application and are able to validate the core functionality.|
|Smoke testing|The application goes through formal validation. A user validates the application following a detailed plan and they should ideally have limited, or no knowledge of the application they're validating.|
|Automated testing |This puts your applications through software that performs automated tests. The software will let you know whether the tests have been passed or failed. It will also provide detailed reporting for you automatically.|
|Test in pilot|Many pilot users are selected and they are asked to carry out the same tasks they do on a daily basis to validate the application. Applications normally undergo this type of testing in addition to one of the other validation methods.|
|Reactive response |Applications are validated in late pilot, and no specific users are selected. These are usually applications with low install bases and aren't handled by enterprise application distribution.|

Woodgrove decides that it will put its critical applications through regression testing. Critical and important applications will also be pilot tested.

As the process manager, you oversee and keep track of the status of all tasks. You use the *Responsible, Accountable, Consulted, Informed* (RACI) model to create an example table that your organization can use for reference when assigning tasks to roles:

|*Task*  |Process manager  |Application owner  |Application developer  |Independent software vendor|End-user computing|Operations|
|---------|---------|---------|---------|---------|---------|---------|
|*Define application test plan*|Informed|Consulted|Consulted|Consulted|Responsible|Consulted|
|*Test application*|Informed|Responsible|Consulted|Consulted|Informed|Informed|
|*Remediate in-house application*|Informed|Informed|Responsible|N/A|Informed|Informed|
|*Remediate vendor application*|Informed|Informed|N/A|Responsible|Informed|Informed|
|*Escalate failures*|Responsible|Informed|Informed|Informed|Informed|Informed|
|*Determine Pilot deployment readiness*|Responsible|Consulted|Consulted|N/A|Consulted|Consulted|

Woodgrove has many devices. There are several things Woodgrove will do to ensure that it achieves device readiness for all of the devices in the production environment before an update is applied.

### Identify users

Woodgrove has many users in different departments. These users have different backgrounds and workloads. Woodgrove must know which users are best suited for validating whether devices are ready for the update.  Woodgrove will have to determine which users to select. You suggest that Woodgrove should consider several factors, such as:

- **Location**: Woodgrove has many users in different physical locations. Can the users be supported and can they provide feedback from the region they're located in?
- **Application knowledge**: Do the users have the right knowledge of how the application works?
- **Technical ability**: Do the users have the right level of technical competence to be able to test scenarios and provide useful feedback?

To provide examples, you explain that the users Woodgrove selects for Pilot deployment could be volunteers who like to try out new features, frontline support members, and others. At the same time, Woodgrove should avoid using core users like department heads, project managers, and others.  Woodgrove decides that groups like operations, application owners, or developers will work together to help identify the most appropriate pilot users based on specific features or functionalities that need to be validated.

### Identify and configure devices

Your manager wants to know which devices to target, and how to ensure that they can be used for validation. You explain that there are different ways for Woodgrove to identify devices to use for validation. For example:

- **Through existing pilot devices**: Woodgrove will have devices enrolled in Desktop Analytics. It will use these devices for pilot testing when the device has critical or important applications installed.
- **By manual selection**: You explain that groups like operations can be involved to leverage their expertise to help decide which devices will be included manually based on factors like specifications, usage rates, and historic issue records.  

Woodgrove's devices run on different hardware models. Woodgrove should identify the number of device types that run critical and important applications. And compare them with the number of hardware models. This will help Woodgrove workout the total devices that need to be tested, to ensure that the different hardware models are covered.

You also explain that, because Woodgrove isn't allowing devices to receive driver updates directly from the internet, Woodgrove will also have to download and package drivers and ensure that all drivers are in working order.

You summarize that Woodgrove should identify and configure the right devices so it can gain the right insights from validation.  And to help it understand how to best perform a smooth broad deployment to all devices that are part of the wider environment.

## Prepare your applications and devices

You can prepare your applications and devices either using Desktop Analytics or without Desktop Analytics.

### Prepare with Desktop Analytics

Woodgrove can use Desktop Analytics to save time and reduce effort.  Desktop Analytics will help Woodgrove create an application and device inventory for the environment, and will maintain the inventory for Woodgrove. It helps Woodgrove simplify how it assigns application owners to all applications across the environment. Desktop Analytics will also automatically assign applications to critical, important, and not important. Additionally, it automatically identifies compatibility risks for applications across the environment and will provide recommendations on how to remediate risks.

:::image type="content" source="../media/5-compatibility-risk.png" alt-text="Compatibility risk assessed by Desktop Analytics":::

### Prepare without Desktop Analytics

If Woodgrove doesn't use Desktop Analytics to prepare its applications and devices, it will use resources across the business to carry out the following tasks:

- **Create and maintain an application and device portfolio**: Woodgrove will create a list of the applications that are used across the company and maintain this list for each feature update. Woodgrove would also spend time understanding the device types in the estate, to help to determine the applications that need to be validated and the devices that should be used for validation. 
- **Create and maintain a list that assigns applications to critical, important, and not important**: Woodgrove will need to create a list of all of its applications across its environment. It will go over each application based on a set of agreed criteria and assign each of them to an importance level. This list will also have to be updated as applications are added, removed, or change importance level over time.
- **Assign owners to critical applications**: Woodgrove will have to maintain a list that maps application owners to applications across the environment.
- **Investigate and identify compatibility issues**: Woodgrove would spend time and effort to find a way to identify compatibility issues for each application before Pilot deployment.
