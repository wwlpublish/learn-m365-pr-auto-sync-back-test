Users can run self-service installations by signing in to the Microsoft 365 portal and selecting the software installation option. While this approach doesn't require much administrative setup, it does provide for limited control over the deployment (in contrast with managed deployments). For example, administrators can't control where computer users install Microsoft 365 Apps for enterprise, but they can disable all Microsoft 365 Apps for enterprise deployments for a specific user.

In a user-driven deployment:

 -  Office always streams from the Internet to the computer by using Click-to-Run technology; local source locations aren't supported.
 -  Users must have a Microsoft 365 account and be provisioned for Microsoft 365 Apps for enterprise.
 -  Users must have administrative rights to the local computer.
 -  Microsoft 365 Apps for enterprise installs Microsoft 365 updates automatically in the background from the Internet. You can't change this behavior.

The following graphic shows that Microsoft 365 Apps for enterprise and all its client applications are downloaded and installed from Microsoft. No installation media is involved.

:::image type="content" source="../media/m365-apps-for-ent-download-screenshot-9a310d3c.jpg" alt-text="graphic shows that Microsoft 365 Apps for enterprise and all its client applications are downloaded and installed from Microsoft":::


### Obstacles to a successful self-service installation of Microsoft 365 Apps for enterprise

When planning a Microsoft 365 Apps for enterprise user self-deployment, it's important to consider the obstacles that often prevent successful installations. These obstacles typically include:

 -  **Lack of information technology (IT) expertise.** In an enterprise software deployment, you must understand tools such as the Office Deployment Tool, Group Policy, and Configuration Manager before you use them as part of Microsoft 365 client roll-outs.
 -  **End of support for Windows XP.** This issue causes the Microsoft 365 Apps for enterprise setup to fail.
 -  **Incorrect licenses.** Prevents successful user activation.
 -  **Bandwidth limitations.** Limited bandwidth during deployment prevents successful streaming of Microsoft 365 Apps for enterprise binaries.
 -  **Users without local admin rights.** Click-to-Run deployments require that users must have administrative rights to the local computer.
