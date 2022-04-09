Microsoft 365 Apps for enterprise can be deployed to client computers from the Office Content Delivery Network (CDN) by using the Office Deployment Tool (ODT).

### The Office Content Delivery Network

The Office Content Delivery Network is designed to optimize performance for users by:

 -  Distributing frequently accessed objects like images and JavaScript files over a high-speed global network.
 -  Reducing page load time.
 -  Providing access to hosted objects as close as possible to the user.

The CDN fetches your assets from a location called an *origin*. An origin can be a SharePoint site, a document library, or a folder that's accessible by a URL. The Office 365 CDN is separated into two basic types:

 -  **Public CDN**. Designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images such as company logos.
 -  **Private CDN**. Designed to be used for images (PNG, JPG, JPEG, etc.).

You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two. Both public and private options provide similar performance gains, but each has unique attributes and advantages.

Both public and private options provide similar performance gains, but each has unique attributes and advantages.<br>

 -  **Public origins**. Public origins within the Office 365 CDN are accessible anonymously. Hosted assets can be accessed by anyone who has the URL to the asset. As such, you should only use public origins to cache non-sensitive generic content such as JavaScript files, scripts, icons and images.
 -  **Private origins**. Private origins within the Office 365 CDN provide private access to user content. These assets include SharePoint Online document libraries, sites, and proprietary images. Access to content in private origins is secured by dynamically generated tokens. As such, it can only be accessed by users with permissions to the original document library or storage location. Private origins in the Office 365 CDN can only be used for SharePoint Online content. When you access assets in private origins, they can only be accessed through redirection from your SharePoint Online tenant.

### The Office Deployment Tool

The Office Deployment Tool is a command-line tool. It can be used to download and deploy Microsoft 365 Apps for enterprise to your client computers. The ODT gives you more control over an Office installation. You can define:

 -  Which products and languages are installed.
 -  How those products should be updated.
 -  Whether to display the install experience to your users.

The ODT is intended for administrators in enterprise environments working with hundreds or thousands of computers. The ODT can be downloaded from the Microsoft 365 admin center, or directly from the Microsoft Download Center.<br>

> [!NOTE]
> This unit covers the standard best practices and installation requirements for organizations that have chosen to deploy Semi-Annual Enterprise Channel.

The ODT is used to run the following tasks:

 -  Download Office source files.
 -  Install or remove Click-to-Run or customize installations.
 -  Apply software update policies.

Before you run the ODT, ensure your users have local admin privileges on their client devices. If they don't, then you should use your standard deployment tools and processes to install Office.<br>

The steps in this unit are based on the following best practices:

 -  Manage updates to Office automatically, without any administrative overhead.
 -  Build two Office installation packages:
    
     -  Semi-Annual Enterprise Channel for 64-bit
     -  Semi-Annual Enterprise Channel (Preview) for 64-bit

    Each installation package includes all the core Office apps. You can create another installation package if you also want to deploy the 32-bit version of Office.

 -  Deploy to two deployment groups:
    
     -  A pilot group that receives Semi-Annual Enterprise Channel (Preview)
     -  A broad group that receives Semi-Annual Enterprise Channel.

    In this scenario, the installation packages and deployment groups match exactly. In more complex deployments, you may have multiple deployment groups that use the same installation package.

You can customize these options to match the requirements for your organization. These requirements may include deploying to more than two groups, changing update channels, and deploying Visio and Project.

The following sections describe the steps involved in deploying Microsoft 365 Apps for enterprise from the Office CDN in the cloud.

### Step 1: Download the Office Deployment Tool

You use the Office Deployment Tool (ODT) to deploy Office from the Office CDN. The deployment tool is run from the command line. it uses a configuration file to determine what settings to apply when deploying Office.

1.  Create the shared folder **\\\\Server\\Share\\M365** and assign read permissions for your users. <br>
2.  Download the Office Deployment Tool from the Microsoft Download Center to \\\\Server\\Share\\M365. If you've already downloaded the ODT, make sure you have the latest version.
3.  After downloading the file, run the self-extracting executable file. This file contains the Office Deployment Tool executable (setup.exe) and a sample configuration file (configuration.xml).<br>

### Step 2: Create a configuration file for the pilot group

To download and deploy Microsoft 365 Apps for enterprise to the pilot group, you use a configuration file with the ODT. To create the configuration file, it's recommended that you use the [Office Customization Tool](/deployoffice/admincenter/overview-office-customization-tool?azure-portal=true).

1.  Go to the **Office Customization Tool** and configure the desired settings for your Microsoft 365 Apps installation. The following options are recommended:
    
     -  **Products**. Select **Microsoft 365 Apps for enterprise**. You can also include Visio and Project if you plan to deploy those apps.
     -  **Update channel**. Select **Semi-Annual Enterprise Channel (Preview)** for the installation package for the pilot group.
     -  **Language**. Include all the language packs you plan to deploy. It's recommended that you select the following options:
        
         -  **Match operating system.** This option automatically installs the same languages that are used by the operating system and any user on the client device.
         -  **Fallback to the CDN**. This option uses the Office CDN as a backup source for language packs.
     -  **Installation**. Select **Office Content Delivery Network (CDN)**.
     -  **Updates**. To update your client devices automatically, select **CDN** and **Automatically check for updates**.
     -  **Upgrades**. Choose to automatically remove all previous MSI versions of Office. You can also choose to install the same language as any removed MSI versions of Office. If you do, make sure to include those languages in your installation package.
     -  **Other properties**. To silently install Office for your users, select **Off** for the **Display level** and **On** for the **Automatically accept the EULA**.
     -  **Application preferences**. Define any Office settings you want to enable, including VBA macro notifications, default file locations, and default file formats.
2.  When you complete the configuration, select **Export** in the upper right of the page, and then save the file as **config-pilot-SECP.xml** in the **\\\\Server\\Share\\M365** folder.

**Additional reading**. For more information about the configuration options, see [Configuration options for the Office Deployment Tool](/deployoffice/office-deployment-tool-configuration-options?azure-portal=true).

> [!NOTE]
> The Office installation files and Office updates will come from Semi-Annual Enterprise Channel (Preview).

### Step 3: Create a configuration file for the broad group

Using the Office Customization Tool, create the configuration file for the broad group.

1.  Go to Office Customization Tool and configure the desired settings for your Microsoft 365 Apps installation. It's recommended that you match the same options as the pilot group in Step 2, except for the following change:
    
     -  **Update channel**. Select **Semi-Annual Enterprise Channel** for the installation package for the broad group.
2.  When you complete the configuration, select **Export** in the upper right of the page, and then save the file as **config-broad-SEC.xml** in the **\\\\Server\\Share\\M365** folder.

This configuration file is used to download Office installation files and then deploy them to the broad group. The settings are exactly the same as the first configuration file, with one exception. The update channel is set to Semi-Annual Enterprise Channel rather than Semi-Annual Enterprise Channel (Preview).

### Step 4: Deploy Office to the pilot group

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

### Step 5: Deploy Office to the broad group

After you've finished testing Office with the pilot group, you can deploy it to the broad group. To do so, run the following command from a command prompt with admin privileges:

\\Server\Share\M365\setup.exe /configure \\Server\Share\M365\config-broad-SEC.xml

This command is the same as the pilot group, except that it references the configuration file for the broad group. The Office installation should immediately start once you run this command.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”