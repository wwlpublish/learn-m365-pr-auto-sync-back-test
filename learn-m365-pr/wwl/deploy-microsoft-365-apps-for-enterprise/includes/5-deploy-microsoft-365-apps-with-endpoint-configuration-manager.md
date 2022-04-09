In a managed deployment, the IT Administrator first downloads the Microsoft 365 Apps for enterprise software to the local network. Following this download, some form of push mechanism deploys it to users. This unit examines how to use Configuration Manager (current branch) to deploy Microsoft 365 Apps for enterprise to users. Starting in version 1910, Configuration Manager is now part of Microsoft Endpoint Manager.

Microsoft Endpoint Manager is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. This design enables organizations to continue using their existing Configuration Manager investments. At the same time, they can take advantage of the power of the Microsoft cloud at their own pace.

If an organization already uses Configuration Manager, it's recommended they upgrade to the current branch and use it to deploy Microsoft 365 Apps for enterprise. Configuration Manager scales for large environments and provides extensive control over installation, updates, and settings. It also has built-in features to make it easier and more efficient to deploy and manage Office, including:

 -  The Office Client Management dashboard, where you can deploy Office and monitor updates.
 -  Integration of the Office Customization Tool for Click-to-Run. This feature means administrators always have access to the latest Click-to-Run deployment and management features.
 -  Fully supported method of removing existing versions of Office from a client during deployment.
 -  Deployment of application settings for Office, including VBA macro notifications, default file locations, and default file formats.
 -  Peer cache, which can help with limited network capacity when deploying updates to devices in remote locations.

> [!NOTE]
> This unit covers the standard best practices and installation requirements for organizations that have chosen to deploy Semi-Annual Enterprise Channel.

If you're not familiar with Configuration Manager, see [Introduction to Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) before continuing on with this unit.

The steps in this unit are based on the following best practices:

 -  Build two Office applications for deployment:
    
     -  One application uses Semi-Annual Enterprise Channel for 64-bit.
     -  The other application uses Semi-Annual Enterprise Channel (Preview) for 64-bit.

    Each application includes all the core Office apps. If you want to deploy the 32-bit version of Office instead, you can select that option when creating the application. To deploy both 64-bit and 32-bit, you can create another application.

 -  Deploy to two collections:
    
     -  One collection represents your pilot group, which receives Semi-Annual Enterprise Channel (Preview).
     -  The other collection represents the broad group, which receives Semi-Annual Enterprise Channel.

You can customize these options to match the requirements for your organization. You can also deploy to more than two collections, change update channels, and deploy Visio and Project.

### Step 1 - Review and update your Configuration Manager infrastructure

From an infrastructure standpoint, deploying Microsoft 365 Apps with Configuration Manager is similar to other software deployments and doesn't require any special customization. That said, the following options can make your Office deployment easier and more efficient:

 -  Use the current branch of Configuration Manager.
 -  Enable peer cache on your client devices. Peer cache is a feature in the current branch of Configuration Manager. It can help with limited network capacity when deploying updates to client devices in remote locations. Office can benefit both during initial deployment and later servicing with updates from peer cache.
 -  Deploy Office as an application using the Office Client Management dashboard and Office 365 Installer wizard in Configuration Manager. The dashboard and wizard enable all the Configuration Manager features designed for Office. These features include removal of existing versions of Office and the ability to define application preferences.

You must also complete the following requirements:

 -  Enable internet access for your client devices so they can activate Microsoft 365 Apps for enterprise after installation.
 -  The computer running the Configuration Manager console requires Internet Explorer (IE) 11 or greater and needs internet access through HTTPS port 443. The Office 365 Client Installation Wizard uses a Windows standard web browser API to open **https://config.office.com**. If an internet proxy is used, the user must be able to access this URL.
 -  Add the following sites to the Trusted Sites list if you have Enhanced Security Configuration enabled for IE (which is enabled by default on Windows Server): **https://.office.com** and **https://.officeconfig.msocdn.com**

### Step 2 - Review your collections

The deployment groups that you defined in your deployment plan are represented as collections in Configuration Manager. For each deployment group, make sure you have a specific collection. As a standard best practice, it's recommended that you create two deployment groups:

 -  A pilot group that receives Semi-Annual Enterprise Channel (Preview).
 -  A broad group that receives Semi-Annual Enterprise Channel.

In more complex deployments, you would use multiple deployment groups.

### Step 3 - Create and deploy the Office application to the pilot group

The Office installation packages are represented as applications in Configuration Manager. For each deployment group that you defined in your deployment plan, you should create a unique Office application using the following steps:

1.  In the **Configuration Manager** console, navigate to **Software Library &gt; Overview &gt; Office 365 Client Management**.
2.  Select **Office 365 Installer** in the upper-right pane. The Office 365 Client Installation Wizard opens.
3.  On the **Application Settings** page, provide a name and description for the app, enter the download location for the files, and then select **Next**. The location must be specified as **\\\\server\\share**.
4.  On the **Office Settings** page, select **Go to the Office Customization Tool**. Configure the desired settings for your Microsoft 365 Apps for enterprise installation. The following options are recommended:
    
     -  **Software.** Select Microsoft 365 Apps for enterprise (if you're licensed for it). You can also include Visio and Project if you plan to deploy those products.
     -  **Update channel**. Choose Semi-Annual Enterprise Channel (Preview) for the installation package for the pilot group.
     -  **Languages**. Include all the language packs you plan to deploy.
     -  **Upgrades**. Choose to automatically remove all previous MSI versions of Office.
     -  **Other properties**. To silently install Office for your users, select **Off** for the **Display level** and **On** for the **Automatically accept the EULA**.
     -  **Application settings**. Define any Office settings you want to enable, including VBA macro notifications, default file locations, and default file formats.
5.  When you complete the configuration, select **Submit**.
6.  On the **Deployment** page, select **Yes** to deploy the application, and then select **Next**.
7.  On the **General** page, select a collection to deploy to, and then select **Next**. The collection should match the deployment group that receives the Office application you defined.
8.  Configure the remainder of the wizard pages as you would for a typical application deployment.
9.  Complete the wizard. After you create and deploy Microsoft 365 Apps for enterprise using the Office 365 Installer, Configuration Manager won't manage the Office updates by default. Instead, Office will update automatically. To enable Microsoft 365 Apps for enterprise to receive updates from Configuration Manager, see [Manage updates to Microsoft 365 Apps with Microsoft Endpoint Configuration Manager](/deployoffice/manage-microsoft-365-apps-updates-configuration-manager).

### Step 4 - Create and deploy the Office application to the broad group

After you've finished testing Office with the pilot group, you can repeat the above steps to create and deploy an Office application to the broad group. When defining the application, include the same options you did with the pilot group, except select Semi-Annual Enterprise Channel for the update channel.

### Step 5 - Review exit criteria

You can use the Office 365 Client Management dashboard to ensure you deployed the correct Office package to your client devices. This dashboard provides charts for the following information:

 -  Number of Office 365 clients
 -  Office 365 client versions
 -  Office 365 client languages
 -  Office 365 client channels

To view the Office 365 Client Management dashboard in the Configuration Manager console, go to **Software Library &gt; Overview &gt; Office 365 Client Management**. At the top of the dashboard, use the **Collection** drop-down setting to filter the dashboard data by members of a specific collection.

In the dashboard, make sure you see the Office versions, languages, and update channels that you deployed for each collection.

> [!IMPORTANT]
> If the data isn't displaying, you may need to enable hardware inventory and select the Office 365 ProPlus Configurations hardware inventory class. For more information, see [Configure hardware inventory](/mem/configmgr/core/clients/manage/inventory/configure-hardware-inventory).<br>
