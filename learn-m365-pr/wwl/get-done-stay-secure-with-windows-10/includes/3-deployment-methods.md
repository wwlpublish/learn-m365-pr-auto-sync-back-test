Deploying Windows 10 depends on a number of factors, such as the:

 -  Business requirements.
 -  Environment considerations.
 -  Amount of administrative control needed.
 -  Network capacity.
 -  Current deployment capabilities.

You can choose from a variety of existing and new deployment tools for Windows 10, including Windows Autopilot and the Microsoft Deployment Toolkit for Windows, and Intune and Configuration Manager for Windows. As part of your deployment, you also choose whether to deploy Windows from the cloud or from a local source on your network.

:::image type="content" source="../media/3-cloud-local-09f98009.png" alt-text="Cloud or local deployment":::


## Deployment options for Windows 10

Windows 10 includes the following new deployment tools and methods:

 -  **Windows Autopilot**. Customize the out-of-box experience (OOBE) to deploy apps and settings that are pre-configured for your organization. Include just the apps your users need. Autopilot is the easiest way to deploy a new PC running Windows 10. You can also use it with Configuration Manager to upgrade Windows 7 or Windows 8.1 to Windows 10.
 -  **In-place upgrade**. Upgrade a device’s operating system without reinstalling. You can migrate apps, user data, and settings from one version of Windows to another (like going from Windows 8.1 to Windows 10). You can also update from one release of Windows 10 to the next (like going from Windows 10, version 1803, to Windows 10, version 1809).
 -  **Dynamic provisioning**. Create a provisioning package to quickly configure one or more devices, even those without network connectivity. You create provisioning packages with the Windows Configuration Designer and can install them over a network, from removable media (like a USB drive), or in near field communication (NFC) tags or barcodes.
 -  **Subscription activation**. Use a subscription to switch from one edition of Windows 10 to another. For example, you can switch from Windows 10 Pro to Windows 10 Enterprise. When a licensed user signs into a device (and they have credentials associated with a Windows 10 E3 or E5 license), the OS changes from Windows 10 Pro to Windows 10 Enterprise, and all the appropriate Windows 10 Enterprise features are unlocked. If the subscription expires (or is transferred to another user), the device reverts seamlessly to Windows 10 Pro edition, after a grace period of up to 90 days.

> [!NOTE]
> Use Windows Autopilot to remotely deploy and configure Surface devices in a zero-touch process, right out of the box. The devices will be automatically enrolled and configured when they are first turned on. This process eliminates reimaging during deployment, which lets you implement new, agile methods of device management and distribution.

In addition to those new tools, you can deploy Windows 10 with desktop management tools and existing tools in your organization, like Microsoft Endpoint Manager, which includes Intune and Configuration Manager.
