One of the benefits of Microsoft 365 Apps for enterprise is that Microsoft provides new and updated features for Office apps on a set schedule. Enterprise administrators can control how often the users in their organization get these new features by specifying the update channel.

Update channels provide not only new features on a monthly basis, but also security and non-security updates. Non-security updates provide fixes for known issues and provide stability or performance improvements for Office.

There are three primary update channels - Current, Monthly Enterprise, and Semi-Annual Enterprise. The following sections outline of these channels.

### Current Channel

The Current Channel provides users with the newest Office features as soon as they're ready. Current Channel usually receives new features at least once a month. However, there's no set schedule for when those updates are released. Current Channel also receives other updates during the month, which include security and non-security updates. There's no set schedule for these updates, but there are generally two or three releases each month, including one on the second Tuesday of the month.

There's a dedicated preview version of the Current Channel known as Current Channel (Preview). It's recommended that organizations use Current Channel (Preview). This channel enables them to become familiar with the new features coming in the next feature release. There isn’t a set release schedule for Current Channel (Preview). In general, a new version of Current Channel (Preview) with new features is released at least a week or more before that new version is released to Current Channel. There may be several releases of Current Channel (Preview), with non-security updates, before that version's released to Current Channel.

The features in the Current Channel (Preview) should be deployed to a small, representative sample of users in an organization. Doing so will help identify any possible issues for the organization before those new features are released more broadly to the users that have Current Channel. Current Channel (Preview) also enables organizations to identify any possible issues they want Microsoft to fix before that version is released to Current Channel. Using Current Channel (Preview) can help reduce the number of non-security updates that are needed for Current Channel.

### Monthly Enterprise Channel

The Monthly Enterprise Channel provides users with new Office features each month. This channel is recommended if an organization only wants to receive one update per month on a predictable release schedule. Updates to the Monthly Enterprise Channel are released on the second Tuesday of the month. The features in the monthly update can include feature, security, and non-security updates.

There's no dedicated preview channel for Monthly Enterprise Channel like there is for Current Channel. However, an organization can have a representative sample of its users download and start using the new version as soon as it becomes available on the Office CDN. This practice enables users to become familiar with the new features in a monthly feature release of the Monthly Enterprise Channel. After that, it can let the new version roll out to the rest of the organization over the course of several days as Office automatically becomes aware that a new version is available on the Office CDN.

### Semi-Annual Enterprise Channel

The Semi-Annual Enterprise Channel is recommended for those select devices in an organization where extensive testing is needed before rolling out new Office features. For example, testing may be required to follow regulatory, governmental, or other organizational requirements. Testing may also be required when an organization can’t provide its users with new Office features on a more frequent basis than twice a year. Updates to Semi-Annual Enterprise Channel are released on the second Tuesday of the month. In January and July, the monthly update can include feature, security, and non-security updates. In other months, the update may include security and non-security updates.

There's a dedicated preview channel for the Monthly Enterprise Channel just like there is for the Current Channel. It's recommended that organizations use Semi-Annual Enterprise Channel (Preview) to become familiar with the new features coming in the next feature release of Semi-Annual Enterprise Channel. Semi-Annual Enterprise Channel (Preview) is released with new features twice a year, on the second Tuesday in March and September. This schedule provides the organization with four months before those same new features are released in Semi-Annual Enterprise Channel. Semi-Annual Enterprise Channel (Preview) also receives, if needed, security and non-security updates every month, on the second Tuesday of the month.

As with Current Channel (Preview), Semi-Annual Enterprise Channel (Preview) should be deployed to a small, representative sample of users in the organization. Doing so will help identify any possible issues for the organization before those new features are released more broadly to its users that have Semi-Annual Enterprise Channel. Organizations are also encouraged to use Semi-Annual Enterprise Channel (Preview) so they can identify any possible issues they want Microsoft to fix in the four months before that version is released to Semi-Annual Enterprise Channel. Once a version is released to Semi-Annual Enterprise Channel, the approval process for non-security updates becomes even more rigorous.

### Channel recommendations

Understanding the update channels is vital for Microsoft 365 Apps for enterprise deployments. Creating targeted users for piloting new versions is an important part of ongoing version management in enterprise companies.

 -  Current Channel is recommended because it provides users with the newest Office features as soon as they're ready.
 -  Monthly Enterprise Channel is recommended if an organization needs more predictable scheduling as to when these new Office features are released each month.
 -  Semi-Annual Enterprise Channel is recommended when an organization has a select group of devices that require extensive testing before receiving new features.

These recommendations are based on typical business requirements. However, many organizations must take into account multiple factors that will determine which update channel they should select for their deployment of Microsoft 365 Apps for enterprise. These factors include:

 -  Network bandwidth usage
 -  End-user training and support
 -  Line-of-business applications
 -  Other organizational requirements

:::image type="content" source="../media/m365-apps-for-enterprise-update-model-3c6a329c.jpg" alt-text="graphic shows why understanding the update channels is vital for Microsoft 365 Apps for enterprise deployments":::


### Configuring users for update channels

‎Enterprise administrators can select from the following methods for applying update channels to users:

 -  **Using the Microsoft 365 admin center.** Navigate to the **Organization settings** page, and under the **Services** tab, select **Office installation options**. Select whether updates should be installed as soon as they're ready (Current Channel), once a month (Monthly Enterprise Channel), or every six months (Semi-Annual Enterprise Channel). The recommended option is the Current Channel, or as soon as the updates are ready. If at any time an organization switches from every month to every six months, all users will lose any updates that are for a future release. There's no option for Deferred Channel within the Microsoft 365 admin center.<br><br>
 -  **Using the Office Deployment Tool (Office 2016 version).** With this method, the configuration.xml file can be edited to change the update channel to either Current, Monthly Enterprise, or Semi-Annual Enterprise. Different users can have different configuration.xml files to vary the release schedules per user.<br><br>
 -  **Using Group Policy.** The Office Administrative Template files include a configuration setting for how quickly updates will be supplied to users. Once an organization downloads the Template files, a Group Policy Object can be created to specify which of the update channels will be available to the user. This setting is located in the following folder: Configuration\\Administrative Templates\\Microsoft Office 2016 (Machine)\\Updates. The choices when enabling the Group Policy settings are Current, Monthly Enterprise, or Semi-Annual Enterprise.
