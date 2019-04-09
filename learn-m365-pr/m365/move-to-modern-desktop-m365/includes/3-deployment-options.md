How you deploy Windows 10 and Office 365 ProPlus depends on your business requirements and your environment, including how much administrative control you want over the deployment, your network capacity, and the deployment tools you already use. 

You can choose from a variety of existing and new deployment tools for Windows 10 and Office 365 ProPlus, including Windows Autopilot and the Microsoft Deployment Toolkit for Windows, the Office Deployment Tool for Office, and Intune and Configuration Manager for both Windows and Office. As part of your deployment, you also choose whether to deploy Windows and Office from the cloud or from a local source on your network. 

![Deploy from a local source or from the cloud](../media/deploy-from-local-or-cloud.png)
*Download updates to a local distribution point or get them directly from the cloud* 

## Deployment options for Windows 10 

Windows 10 includes the following new deployment tools and methods:

- **Windows Autopilot**. Customize the out-of-box experience (OOBE) to deploy apps and settings that are pre-configured for your organization. Include just the apps your users need. Autopilot is the easiest way to deploy a new PC running Windows 10. You can also use it with Configuration Manager to upgrade Windows 7 or Windows 8.1 to Windows 10. 
- **In-place upgrade**. Upgrade a device’s operating system without reinstalling. You can migrate apps, user data, and settings from one version of Windows to another (like going from Windows 8.1 to Windows 10). You can also update from one release of Windows 10 to the next (like going from Windows 10, version 1803, to Windows 10, version 1809).
- **Dynamic provisioning**. Create a provisioning package to quickly configure one or more devices, even those without network connectivity. You create provisioning packages with the Windows Configuration Designer and can install them over a network, from removable media (like a USB drive), or in near field communication (NFC) tags or barcodes. 
- **Subscription activation**. Use a subscription to switch from one edition of Windows 10 to another. For example, you can switch from Windows 10 Pro to Windows 10 Enterprise. When a licensed user signs into a device (and they have credentials associated with a Windows 10 E3 or E5 license), the OS changes from Windows 10 Pro to Windows 10 Enterprise, and all the appropriate Windows 10 Enterprise features are unlocked. If the subscription expires (or is transferred to another user), the device reverts seamlessly to Windows 10 Pro edition, after a grace period of up to 90 days. 

In addition to those new tools, you can deploy Windows 10 with modern desktop management tools and existing tools in your organization, including Intune, Azure AD, and Configuration Manager. 

## Deployment options for Office 365 ProPlus 

To deploy Office 365 ProPlus, you first choose what deployment tool to use: 

- **Configuration Manager**. For enterprises that already use Configuration Manager to deploy and manage software, we recommend using it for Office deployment as well. Configuration Manager scales for large environments and  enables extensive control over installation, updates, and settings. It also has built-in features for deploying and managing Office and Windows. 
- **Office Deployment Tool**. For organizations that don't have Configuration Manager but still want to manage their deployment, you can use the Office Deployment Tool, which provides control over installation, updates, and settings. You can use this as a standalone tool or in conjunction with third-party software deployment tools. 
- **Microsoft Intune**. For organizations that want to deploy and manage Office from the cloud, Intune provides a cloud-based service that manages mobile devices and PCs, along with the applications on those devices (like Office 365 ProPlus). Intune can also be used to manage Windows 10 
on your PCs. 
- **Install directly from the Office 365 portal**. The simplest approach is to have your users install Office on their client devices directly from the Office 365 portal. This method requires the least amount of administrative setup but gives you less control over the deployment. You can, however, still define how frequently your users receive feature updates. This option requires that your users have local administrative rights on their client devices. 

As part of deploying with the Office Deployment Tool or Configuration Manager, you can create configuration files with the Office Customization Tool. These configuration files give you control over an Office installation, including defining which applications and languages are installed, how those applications should be updated, and application preferences. Similar options are available as part of the Intune deployment. 

Depending on the tool you choose to deploy with, you can also choose whether to deploy from the cloud or to download Office to a local source on your network and deploy from there. When possible, we recommend deploying Office from the cloud, as doing so will minimize your administrative overhead. When you deploy from the cloud, Office 365 ProPlus is delivered to client devices directly from the Office Content Delivery Network (CDN). If your network consideration requires you to deploy from a local source, Configuration Manager can be a good option to help manage the deployment and updates. 