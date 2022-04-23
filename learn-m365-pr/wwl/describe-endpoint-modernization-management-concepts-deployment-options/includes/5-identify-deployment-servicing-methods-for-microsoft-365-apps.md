**Microsoft 365 Apps** can be installed individually by users on their devices. But it's often beneficial to manage updates and deploy a customized selection of apps to users’ devices to ensure that all users have the apps they need. There are four methods to perform larger-scale deployments of Microsoft 365 Apps that we’ll discuss in the following list:

 -  **Deploy from a local source with Configuration Manager.** Manage your deployment with Configuration Manager, and download and deploy Office from distribution points on your network.
 -  **Deploy from the cloud with the Office Deployment Tool (ODT).** Manage your deployment with the ODT and use the **Office Customization Tool** to create a configuration file in the cloud that specifies the Microsoft 365 apps that are installed. The commands run the ODT in configure mode and with a reference to the appropriate configuration file, which defines the version of Office to install on the client computer.
 -  **Deploy from a local source with the Office Deployment Tool (ODT).** Manage your deployment with the ODT, and download and deploy Office from a local source on your network.
 -  **Self-install from the cloud.** Manage your deployment from the Office portal and have your users install Office on their client devices directly from the portal.

After you deploy Microsoft 365 Apps, Microsoft strongly recommends that you keep them up to date as new features and updates are released. For more information on deployment methods, see [Deployment guide for Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps?azure-portal=true).

#### Deploy Microsoft 365 interactive guide

In this interactive guide, you'll explore three methods for deploying Office 365 to your organization. The techniques remain the same for Microsoft 365 Apps.

> [!VIDEO https://mslearn.cloudguides.com/guides/Deploy%20Office%20365%20ProPlus%20in%20your%20organization]

### Types of updates channels for Microsoft 365 Apps

One of the benefits of Microsoft 365 Apps is that Microsoft provides new and updated features for Office apps regularly. For example, adding improved translation capabilities to Word or adding support for 3D animations in PowerPoint. Microsoft provides you options, called update channels, that allow you to control how often your organization gets these new feature updates.

As needed, Microsoft also provides each update channel with two other types of updates that are released on the second Tuesday of every month:

 -  **Security updates,** such as updates that help keep Office protected from potential malicious attacks.
 -  **Non-security updates (quality updates),** such as updates that provide stability or performance improvements for Office.

Here are the three primary update channels for Microsoft 365 Apps:

 -  **Current Channel** receives feature updates at least once a month, but there's no set schedule of one the updates are released. This channel also receives security and non-security updates around two or three times a month, including one on the second Tuesday of the month. Microsoft recommends this channel because it provides users with the newest Office features as soon as they’re ready.
 -  **Monthly Enterprise Channel** receives feature updates once a month, on the second Tuesday of the month. This monthly update can include feature, security, and non-security updates. Microsoft recommends this channel if you want to provide your users with new Office features once a month on a predictable release schedule.
 -  **Semi-Annual Enterprise Channel** receives feature updates every six months, in January and July on the second Tuesday of the month. This update can include feature, security, and non-security updates. Microsoft recommends this channel only for those select devices in your organization where extensive testing is needed before rolling out new Office features.

The update channel of Microsoft 365 Apps you deploy to the users in your organization can depend on several factors, such as application compatibility testing and user readiness. Not all users in your organization need to be on the same update channel. For example, you can provide your training department with current channel so they can start learning about the new Office features, while the rest of your organization is on semi-annual enterprise channel.

The update channel that you choose for Microsoft 365 Apps doesn’t have to match the update channel for Windows client. For more information about update channels for Microsoft 365 apps, see [Overview of update channels for Microsoft 365 Apps](/DeployOffice/overview-update-channels?azure-portal=true).

:::image type="content" source="../media/5-office-updates-cadfb3ff.png" alt-text="Update frequency":::


### How updates are installed for Microsoft 365 Apps

Microsoft 365 Apps checks for updates regularly, and they're downloaded and installed automatically. There aren’t separate downloads for feature, security, or non-security updates. The updates are cumulative, so the most current update includes all the updates that have been previously released for that update channel. While updates are being downloaded, your users can continue to use Office apps. After they're downloaded, all the available updates for that update channel will install at the same time. If any Office apps are open, your users will be prompted to save their work and close the apps, so that the updates can finish installing.
