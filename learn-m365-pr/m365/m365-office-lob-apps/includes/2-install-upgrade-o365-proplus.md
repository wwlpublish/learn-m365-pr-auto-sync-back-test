![Step 3 highlighted on the deployment wheel](../media/step-3-office-and-lob-app-delivery-wheel-main.png)

![Step 3 icon](../media/step-3-icon.png)

You can deploy Office 365 ProPlus using several methods:

## Deploy Office with Click-to-Run technology

Office 365 ProPlus and Office 2019 are both installed using **Click-to-Run,** which replaces MSI-based packaging in previous Office deployments. Click-to-run provides faster installations, faster and more efficient updating, and cleaner uninstallation than previous methods. Programs delivered with Click-to-Run run in a virtual application environment on your computer. They coexist with other applications without conflict. They also use about half the disk space of an MSI-based package.

## Deploy Office with the Office Deployment Tool

Office applications are delivered and managed via the **Office Deployment Tool** (also known as the Office Customization Tool), which is the Office setup engine needed to download, configure, and customize your Office apps. With this tool, you can set the applications and languages to be installed, the method for updating the applications, application preferences, and installation experience settings.

![Office Customization Tool](../media/step-3-office-and-lob-app-delivery-media-7-50.png)

## Deploy Office with the System Center Configuration Manager

If you use System Center Configuration Manager (SCCM), you can use it for broad deployment of Office 365 ProPlus. SCCM has native support for the updated Office Customization Tool, package customization for Click-to-Run at install time, and native support for software update management after installation. 

![SCCM Deployment Settings](../media/step-3-office-and-lob-app-delivery-media-6-50.png)

## Deploy Office using Intune

If your organization uses Microsoft Intune, you can assign Office 365 ProPlus applications to Windows 10 devices. Intune supports both 32-bit and 64-bit versions of Office 365 ProPlus.

> [!NOTE]
> If you are upgrading to Office 365 ProPlus from a previous Office version, we recommend you uninstall versions of Office that use Windows Installer (MSI) as the installation technology. To help with this, you can use the Office Deployment Tool and specify the [RemoveMSI element]( /deployoffice/upgrade-from-msi-version) in your configuration.xml file.


