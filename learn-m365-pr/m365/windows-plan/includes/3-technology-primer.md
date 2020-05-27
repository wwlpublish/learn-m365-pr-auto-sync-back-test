Woodgrove has many applications and device types in its environment. Some of these apps and devices are fundamental to core business activities. Other apps help workers in their roles, but aren’t fundamental to the operation of the business. You’ve been asked to report on how Woodgrove should handle these different apps and devices during the servicing process.

## App classification

Woodgrove needs to decide how it categorizes application importance for updates. You classify and prioritize applications to understand how to best apply updates across your environment, and also how to resolve any issues during the update process. You’ll need to assign application importance, based on the following categories:

:::image type="content" border= "false" source="../media/3-app-classification.png" alt-text="App classification":::

<!-- :::image type="content" border= "false" source="../media/.png" alt-text=""::: -->

When you've classified your applications, you should agree what each level of importance means to the organization regarding priority and severity, to ensure that issues can be triaged with the right level of urgency. The next step is to assign one of the following priority levels to each application. Example timelines are listed below:

|Priority Level  |Description  |
|---------|---------|
|Priority 1     |Any issues and risks identified must be quickly investigated and resolved.|
|Priority 2     |Start investigating risks and issues within two business days and fix them during the current deployment cycle.|
|Priority 3     |Start investigating risks and issues within 10 business days. You don’t have to fix them all within the current deployment cycle. However, all issues must be resolved by the end of the next deployment cycle.|
|Priority 4     |Start investigating risks and issues within 20 business days. You can fix them in the current or any future development cycle.|

Much like a risk assessment matrix, defining a severity level helps the organization understand what will happen to the deployment process. For example:

:::image type="content" border= "false" source="../media/3-severity.png" alt-text="Severity":::

## Servicing channels for Windows and Microsoft 356 Apps

Servicing channels help organizations to decide how often they want to apply updates across their environment. For example, Woodgrove can choose to quickly apply updates across devices that it uses for testing. Or, devices used for specialized functions could receive updates later.
The servicing channels for Windows are defined as follows:

|Servicing Channel  |Description  |
|---------|---------|
|Windows Insider Program     |You use this servicing channel to help test for potential compatibility problems with your critical applications. This servicing channel also lets you explore and test new feature updates before they're publicly available. It's recommended to have at least a few devices enrolled in the Windows Insider Program.|
|Semi-Annual Channel (recommended)     |This servicing channel is the default for commercial customers and gets new releases twice a year. If you're a Windows 10 Enterprise or Education customer, the H1 release (April-May) is serviced by Microsoft for 18 months from the initial release date. The H2 release (Oct-Nov) is serviced for 30 months.  If you're licensed for Windows 10 Professional, each release is serviced for 18 months.|
|Long Term Servicing Channel (LTSC)|This servicing channel is for devices that are used for specialized functions, like payment systems, or medical systems. These devices use an LTSC edition of Windows 10, and are updated only to ensure the devices stay functional and secure. Each release for this channel receives five years support, plus an additional five years through extended support. New releases occur approximately every three years. This servicing channel is only applied for Windows 10 if you have the Enterprise edition.
|

Review and confirm the Microsoft 365 Apps servicing channel for your company. You can use the following servicing channels:

:::image type="content" border= "false" source="../media/3-service-channels-m365.png" alt-text="M365 service channels":::