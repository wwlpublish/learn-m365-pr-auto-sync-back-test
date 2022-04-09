When an organization deploys Microsoft 365 Apps for enterprise from a local source, it must first download the software to a shared folder on its local network. The organization then uses the Office Deployment Tool (ODT) to deploy the applications from the shared folder.

The ODT is used to deploy Microsoft 365 Apps for enterprise from both the cloud and from a local source. The prior unit introduced you to the Office Deployment Tool. It also examined how to use the ODT to deploy Microsoft 365 Apps for enterprise from the cloud (the Office Content Delivery Network). Since you should now have a basic understanding of the ODT, this unit focuses on the steps used to deploy Microsoft 365 Apps for enterprise from a local source.

> [!NOTE]
> Both cloud and local source deployments recommend the same ODT best practices that were introduced in the prior unit. Refer to the prior unit to review the list of best practices.

Five of the eight steps required to deploy Microsoft 365 Apps for enterprise from a local source are the same that were used to deploy from the cloud. The following table provides a quick comparison between the two methods:

:::row:::
  :::column:::
    **Deploy Microsoft Apps for enterprise from the cloud**
  :::column-end:::
  :::column:::
    **Deploy Microsoft Apps for enterprise from a local source**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    Step 1: Create shared folders for Office installation files
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Step 1: Download the Office Deployment Tool
  :::column-end:::
  :::column:::
    Step 2: Download the Office Deployment Tool
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Step 2: Create a configuration file for the pilot group
  :::column-end:::
  :::column:::
    Step 3: Create a configuration file for the pilot group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Step 3: Create a configuration file for the broad group
  :::column-end:::
  :::column:::
    Step 4: Create a configuration file for the broad group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    Step 5: Download the Office installation package for the pilot group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    Step 6: Download the Office installation package for the broad group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Step 4: Deploy Office to the pilot group
  :::column-end:::
  :::column:::
    Step 7: Deploy Office to the pilot group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Step 5: Deploy Office to the broad group
  :::column-end:::
  :::column:::
    Step 8: Deploy Office to the broad group
  :::column-end:::
:::row-end:::


The following sections describe the steps involved in deploying Microsoft 365 Apps for enterprise from a local source.<br>

### Step 1: Create shared folders for Office installation files

Because you're deploying Microsoft 365 Apps for enterprise from a local source, you must begin by creating local shared folders to store the Office installation files. You'll create one parent folder and two child folders:

 -  One child folder for the pilot group, with the version of Office from Semi-Annual Enterprise Channel (Preview).
 -  Another child folder for the broad group, with version of Office from Semi-Annual Enterprise Channel.

This structure is similar to the one the Office Content Delivery Network (CDN) uses when deploying from the cloud.

1.  Create the following shared folders that will include all the Office installation files to be deployed:
    
     -  **\\\\Server\\Share\\M365.** Stores the ODT and the configuration files that define how to download and deploy Office.
     -  **\\\\Server\\Share\\M365\\SECP.** Stores the Microsoft 365 Apps installation files from Semi-Annual Enterprise Channel (Preview).
     -  **\\\\Server\\Share\\M365\\SEC.** Stores the Microsoft 365 Apps installation files from Semi-Annual Enterprise Channel.
2.  Assign **Read** permissions for your users. Installing Office from a shared folder only requires the user to have Read permission for that folder. As such, you should assign Read permission to everyone.

> [!NOTE]
> This unit uses just one shared folder on the network. However, many organizations make the Office installation files available from multiple locations. Using multiple locations can help improve availability and minimize the effect on network bandwidth. For example, if some of your users are located in a branch office, you can create a shared folder in the branch office. Those users can then install Office from the local network. You can use the Distributed File System (DFS) role service in Windows Server to create a network share that is replicated to multiple locations. For more information, see [DFS Management](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732006%28v=ws.11%29?azure-portal=true).<br>

### Step 2: Download the Office Deployment Tool

Download the ODT from the Microsoft Download Center to **\\\\Server\\Share\\M365**. If you've already downloaded the ODT, make sure you have the latest version.

After downloading the ODT, run the self-extracting executable file. This file contains the ODT executable (setup.exe) and a sample configuration file (configuration.xml).

### Step 3: Create a configuration file for the pilot group

To download and deploy Microsoft 365 Apps for enterprise to the pilot group, you use a configuration file with the ODT. To create the configuration file, it's recommended that you use the [Office Customization Tool](/deployoffice/admincenter/overview-office-customization-tool?azure-portal=true).

1.  Go to the **Office Customization Tool** and configure the desired settings for your Microsoft 365 Apps installation. The following options are recommended:
    
     -  **Products**. Select **Microsoft 365 Apps for enterprise**. You can also include Visio and Project if you plan to deploy those apps.
     -  **Update channel**. Select **Semi-Annual Enterprise Channel (Preview)** for the installation package for the pilot group.
     -  **Language**. Include all the language packs you plan to deploy. It's recommended that you select the following options:
        
         -  **Match operating system.** This option automatically installs the same languages that are used by the operating system and any user on the client device.
         -  **Fallback to the CDN**. This option uses the Office CDN as a backup source for language packs.
     -  **Installation**. Select **Local source**, and type **\\\\Server\\Share\\M365\\SECP** for the source path. Office will be downloaded to and then installed from **\\\\server\\share\\M365\\SECP** on your network. This option is the only one in this step that's different between installing from the cloud and installing from a local source.
     -  **Updates**. To update your client devices automatically, select **CDN** and **Automatically check for updates**.
     -  **Upgrades**. Choose to automatically remove all previous MSI versions of Office. You can also choose to install the same language as any removed MSI versions of Office. If you do, make sure to include those languages in your installation package.
     -  **Other properties**. To silently install Office for your users, select **Off** for the **Display level** and **On** for the **Automatically accept the EULA**.
     -  **Application preferences**. Define any Office settings you want to enable, including VBA macro notifications, default file locations, and default file formats.
2.  When you complete the configuration, select **Export** in the upper right of the page, and then save the file as **config-pilot-SECP.xml** in the **\\\\Server\\Share\\M365** folder.

**Additional reading**. For more information about the configuration options, see [Configuration options for the Office Deployment Tool](/deployoffice/office-deployment-tool-configuration-options?azure-portal=true).

The Office installation files and Office updates will come from Semi-Annual Enterprise Channel (Preview).

### Step 4: Create a configuration file for the broad group

Using the Office Customization Tool, create the configuration file for the broad group.

1.  Go to Office Customization Tool and configure the desired settings for your Microsoft 365 Apps installation. It's recommended that you match the same options as the pilot group in Step 2, except for the following change:
    
     -  **Update channel**. Select **Semi-Annual Enterprise Channel** for the installation package for the broad group.
     -  **Installation.** Select **Local source** and type **\\\\Server\\Share\\M365\\SEC** for the source path. Office will be downloaded to and then installed from **\\\\server\\share\\M365\\SEC** on your network. This option is the only one in this step that's different between installing from the cloud and installing from a local source.
2.  When you complete the configuration, select **Export** in the upper right of the page, and then save the file as **config-broad-SEC.xml** in the **\\\\Server\\Share\\M365** folder.

This configuration file is used to download Office installation files and then deploy them to the broad group. The settings are exactly the same as the first configuration file, with one exception. The update channel is set to Semi-Annual Enterprise Channel rather than Semi-Annual Enterprise Channel (Preview).

### Step 5: Download the Office installation package for the pilot group

From a command prompt, run the ODT executable in download mode. The command must also reference the configuration file for the pilot group. The command should appear as follows:

\\server\share\M365\setup.exe /download \\server\share\M365\config-pilot-SECP.xml

The files should begin downloading immediately. After running the command, go to **\\\\server\\share\\M365\\SECP** and look for an Office folder with the appropriate files in it.

> [!NOTE]
> When you download Office to a folder that already contains that version of Office, the ODT will conserve your network bandwidth by downloading only the missing files. For example, if you use the ODT to download Office in English and German to a folder that already contains Office in English, only the German language pack will be downloaded.

You should complete the following troubleshooting steps if you run into problems:

 -  Verify you have the latest version of the ODT.
 -  Verify your configuration file and command reference the correct location.
 -  Review the log file in the **%temp%** folder.

### Step 6: Download the Office installation package for the broad group

From a command prompt, run the ODT executable in download mode. The command must also reference the configuration file for the broad group. The command should appear as follows:

\\server\share\M365\setup.exe /download \\server\share\M365\config-broad-SEC.xml

The files should begin downloading immediately. After running the command, go to **\\\\server\\share\\M365\\SEC** and look for an Office folder with the appropriate files in it.

### Step 7: Deploy Office to the pilot group

To deploy Office, you provide commands that users can run from their client computers. The commands run the ODT in configure mode and with a reference to the appropriate configuration file. The configuration file defines which version of Office to install on the client computer. Users who run these commands must have local admin privileges and must have read permissions to the share (\\\\server\\share\\M365).

From the client computers for the pilot group, run the following command from a command prompt with admin privileges:

\\Server\Share\M365\setup.exe /configure \\Server\Share\M365\config-pilot-SECP.xml

> [!NOTE]
> Most organizations will use this command as part of a batch file, script, or other process that automates the deployment. In those cases, you can run the script under elevated permissions. By default, the users won't need to have admin privileges on their computers.<br>

The Office installation should immediately start once you run this command. If you run into problems:

 -  Verify you have the latest version of the ODT.
 -  Verify your configuration file and command reference the correct location.
 -  Review the log file in the %temp% folder.

After Office has deployed to the pilot group, you can test Office in your environment, particularly with your hardware and device drivers.

### Step 8: Deploy Office to the broad group

After you've finished testing Office with the pilot group, you can deploy it to the broad group. To do so, run the following command from a command prompt with admin privileges:

\\Server\Share\M365\setup.exe /configure \\Server\Share\M365\config-broad-SEC.xml

This command is the same as the pilot group, except that it references the configuration file for the broad group. The Office installation should immediately start once you run this command.
