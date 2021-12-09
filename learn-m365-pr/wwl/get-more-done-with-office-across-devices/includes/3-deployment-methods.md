Microsoft 365 Apps can be installed individually by users on their devices, but to ensure that all users have all of the apps that they will need, it is often beneficial to deploy a customized selection of apps to users devices.

There are three methods to perform larger scale deployments of Microsoft 365 Apps that we’ll discuss below:

## Deploy Microsoft 365 Apps using Click-to-Run

Administrators can use the Office 365 Client Configuration Service to create a configuration file in the cloud that specifies the Microsoft 365 apps that are installed. The configuration file also specifies settings such as the update channel, the End User License Agreement (EULA), and whether to automatically apply updates.

Users install Office through Click-to-Run and the configuration is automatically applied to their installation.

## Deploy Microsoft 365 Apps from a local source

You can deploy Microsoft 365 Apps from a local source using the same steps as deploying Microsoft 365 Apps using Click-to-Run. With this approach, you download the files to a local server which has the benefit that many users are not downloading the same files from the Internet and consuming bandwidth. Furthermore, you can use this approach if users do not have a reliable Internet connection.

## Deploy Microsoft 365 Apps with Microsoft Endpoint Configuration Manager (current branch)

If your organization already uses Configuration Manager, we recommend upgrading to the current branch and using it to deploy Microsoft 365 Apps. You can deploy Office as an application using the Office Client Management dashboard and Office 365 Installer wizard in Configuration Manager. For more information, see [Deployment guide for Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

## Deploy Microsoft 365 interactive guide

In this interactive guide, you will explore three methods for deploying Office 365 to your organization. The techniques remain the same for Microsoft 365 Apps:

> [!VIDEO https://mslearn.cloudguides.com/guides/Deploy%20Office%20365%20ProPlus%20in%20your%20organization]
