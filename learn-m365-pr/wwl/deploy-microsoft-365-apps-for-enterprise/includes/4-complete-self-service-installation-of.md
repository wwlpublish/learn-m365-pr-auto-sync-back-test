Users can run self-service installations by signing in to the Microsoft 365 portal and selecting the software installation option. While this approach doesn't require much administrative setup, it does provide for limited control over the deployment (in contrast with managed deployments). For example, administrators can't control where computer users install Microsoft 365 Apps for enterprise. However, they can disable all self-service installations of Microsoft 365 Apps for enterprise.

In a user-driven deployment:

 -  Office always streams from the Internet to the computer by using Click-to-Run technology. Local source locations aren't supported with this method.
 -  Users must have a Microsoft 365 account and be provisioned for Microsoft 365 Apps for enterprise.
 -  Users must have administrative rights to the local computer.
 -  Microsoft 365 Apps for enterprise installs Microsoft 365 updates automatically in the background from the Internet. You can't change this behavior.

The following graphic shows that Microsoft 365 Apps for enterprise and all its client applications are downloaded and installed from Microsoft. No installation media is involved.

:::image type="content" source="../media/m365-apps-for-ent-download-screenshot-9a310d3c.jpg" alt-text="graphic shows that Microsoft 365 Apps for enterprise and all its client applications are downloaded and installed from Microsoft":::


### Obstacles to a successful self-service installation of Microsoft 365 Apps for enterprise

When planning a Microsoft 365 Apps for enterprise user self-deployment, it's important to consider the obstacles that often prevent successful installations. These obstacles typically include:

 -  **Lack of information technology (IT) expertise.** In an enterprise software deployment, you must understand the tools that can be used as part of a Microsoft 365 client roll-out. These tools include:
    
     -  Office Deployment Tool
     -  Group Policy
     -  Configuration Manager
 -  **Incorrect licenses.** Prevents successful user activation.
 -  **Bandwidth limitations.** Limited bandwidth during deployment prevents successful streaming of Microsoft 365 Apps for enterprise binaries.
 -  **Users without local admin rights.** Click-to-Run deployments require that users must have administrative rights to the local computer.

### Prohibit all users from installing Microsoft 365 Apps for enterprise

Microsoft 365 includes a global Office download setting that controls the downloading of mobile and desktop apps for all users. This setting can be turned Off to prohibit users from downloading Microsoft 365 Apps for enterprise. Complete the following steps to turn off this setting:

1.  In the **Microsoft 365 admin center**, select **...Show all** in the navigation pane. Select **Settings**, and then within the group, select **Org Settings**.<br>
2.  In the **Org settings** window, the **Services** tab is displayed by default. Scroll down through the list of services and select **Office installation options**.<br>
3.  In the **Office installation options** pane that appears, the **Feature Updates** tab is displayed by default. Select the **Installation** tab that appears next to it.<br>
4.  Under the A**pps for Windows and mobile devices** section, the **Office (includes Skype for Business)** check box is currently selected. Select this check box to clear it. Clearing this check box turns this feature Off, which prohibits users from downloading Microsoft 365 Apps for enterprise.
5.  Select **Save**.<br>
