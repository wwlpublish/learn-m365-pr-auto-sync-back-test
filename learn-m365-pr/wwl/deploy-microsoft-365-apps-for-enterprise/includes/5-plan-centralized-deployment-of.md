In a managed deployment, the IT Administrator first downloads the Microsoft 365 Apps for enterprise software to the local network. Following this download, some form of push mechanism deploys it to users. The following software distribution tools are examples of mechanisms that can be used to manage push installations:

 -  Configuration Manager
 -  Intune
 -  Non-Microsoft software distribution
 -  Group Policy sign-in scripts
 -  Scripted installation

Group Policy computer startup scripts can be used to deploy Microsoft 365 Apps for enterprise. Similar command lines and scripts are typically part of an electronic software distribution. These command lines and scripts can be built into System Center and Microsoft Deployment Toolkit (MDT) task sequences.

You must run Click-to-Run installations as a local administrator when using both Group Policy and the Office Deployment Tool. For example, Group Policy startup scripts must run from the computer context and not the user context. In doing so, the computer account must have access to the installation path to run the installation and get updates. Configuration Manager or Remote Desktop can be used in cases where users don't have admin rights.

### Configuring managed deployments

For Click-to-Run, you must configure the Office client through Group Policy and the Office Deployment Tool. You can't use the Office Customization Tool (OCT), even though you may have done so with past volume-licensed Office 2013 Professional Plus media. The following tools can be used to complement each other:

 -  **Office Deployment Tool.** The Office Deployment Tool uses xml to customize the deployment experience by:
    
     -  assigning which products to install (Microsoft 365 Apps for enterprise, Microsoft 365 Business Premium, Visio, or others).
     -  choosing 32-bit or 64-bit installations.
     -  choosing which applications to exclude.
     -  choosing which update branch to assign to the user.
     -  adding specific language versions.
     -  removing previous deployments or languages.
 -  **Group Policy.** This tool can be used to manage all other Office settings, including which applications to block from certain users.
