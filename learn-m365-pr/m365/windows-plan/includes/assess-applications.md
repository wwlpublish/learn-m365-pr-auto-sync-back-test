Woodgrove has a lot of applications and device types in its environment. Some of these apps and devices are fundamental to core business activities. Other apps help workers perform their roles, but aren't fundamental to the operation of the business. You've been asked to report back on how Woodgrove should handle these different apps and devices during the servicing process.

## App classification

Woodgrove needs to decide how it wants to categorize application importance for updates. Classifying and prioritizing your applications helps you understand how to best apply updates across your environment, and also how to resolve issues that might arise during the update process.  To do that, you'll need to assign application importance based on the following classifications:

|Classification|Description  |
|---------|---------|
|Critical|These are the organization's most vital applications that handle core business activities and processes. If these applications were to experience downtime, the business or business unit wouldn't be able to function.|
|Important|These are applications that the organization's individual staff members need to support their productivity. Downtime here would affect individual users, but would only have minimal impact on the business.|
|Not important|There is no impact on the business if these applications experience downtime. |

Once you have classified your applications, you should agree what each level of importance means to the organization in terms of priority and severity, to ensure that issues can be triaged with the right level of urgency. The next step is to assign one of the following priority levels to each application:

|Priority level  |Description  |
|---------|---------|
|Priority 1|Any issues and risks identified must be investigated and resolved as soon as possible.|
|Priority 2|Start investigating risks and issues within two business days and fix them during the current deployment cycle.|
|Priority 3|Start investigating risks and issues within 10 business days. You don't have to fix them all within the current deployment cycle. However, all issues must be fixed by the end of the next deployment cycle.|
|Priority 4|Start investigating risks and issues within 20 business days. You can fix them in the current or any future development cycle.|

Much like a risk assessment matrix, defining a severity level helps the organization map what will happen to the deployment process, for example:

|Severity  |Impact  |Deployment state  |
|---------|---------|---------|
|1| Work stoppage  or loss of revenue.        |Deployment is stopped.|
|2|Productivity loss for a business unit.|Deployment is stopped for affected devices only. |
|3|Loss of productivity for individual users.|Deployment can continue but workaround guidance is provided for affected users if possible.|
|4|Minimal impact on users.|Deployment continues.|

### Servicing channels for Windows and Microsoft 365 Apps

Servicing channels make it possible for organizations to decide how often they want to apply updates across their environment. For example, Woodgrove can choose to apply updates across devices that it uses for testing as soon as possible. On the other hand, devices that are used for specialized functions can receive updates at a later time.
The servicing channels for Windows are defined as follows:

|Servicing Channel  |Description  |
|---------|---------|
|Windows Insider Program     |You can use this servicing channel to help you test for potential compatibility problems with your critical applications. This servicing channel also lets you explore and test out new feature updates before they're publicly available. It's recommended to have at least a few devices enrolled in the Windows Insider Program.|
|Semi-Annual Channel (Recommended)|This servicing channel is the default for commercial customers and gets new releases twice a year. For Windows 10 Enterprise and Education editions, the H1 release (April-May) is serviced by Microsoft for a period of 18 months from initial release date, and the H2 release (Oct-Nov) is serviced for 30 months. For Windows 10 Professional, each release is serviced for 18 months.|
|Long Term Servicing Channel (LTSC)|The servicing channel is for devices that are used for specialized functions, like payment systems or medical systems. These devices use an LTSC edition of Windows 10 and are updated only to ensure the devices stay functional and secure. Each release for this channel receives five years support, plus an additional five years through extended support. New releases occur approximately every three years. This servicing channel is only available for Windows 10 Enterprise editions.|

For Microsoft 365 Apps, you can use the following servicing channels:

|Servicing channel  |Description  |
|---------|---------|
|Semi-Annual Enterprise Channel     |Released in January and July. This channel is selected by default for commercial customers. Users will have to wait a longer time to consume new feature updates.|
|Current Channel     |Released in March and September. Use this channel to have users receive feature updates quicker than the Semi-Annual enterprise channel.|
|Monthly Enterprise Channel|If your environment doesn't have critical line-of-business applications, add-ins, or macros that need to be tested to determine if they work with an updated version of Microsoft 365 Apps, the Monthly Channel is the best way to provide new features to users in the quickest way. Rapid adopters of Windows are encouraged to use this servicing channel.|
