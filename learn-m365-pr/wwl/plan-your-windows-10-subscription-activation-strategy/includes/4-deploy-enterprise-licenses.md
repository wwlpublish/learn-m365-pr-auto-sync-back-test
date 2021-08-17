Windows 10 Enterprise E3 or E5 licenses can be deployed by a company with either:

 -  Windows 10 Enterprise Subscription Activation
 -  Windows 10 Enterprise E3 in CSP and Azure Active Directory (Azure AD)

Devices must be running Windows 10 Pro version 1703 or newer (version 1803 or newer for firmware-embedded activation key). Licenses are automatically deployed and don't require a device restart.

Organizations can obtain Windows 10 Enterprise licenses in the following ways:

 -  **Firmware-embedded activation key**. If you purchased Windows 8 or newer devices, they probably have a firmware-embedded activation key. You can use Windows PowerShell to verify if an activation key is present. If it's present, Windows 10 version 1803 or newer will be automatically activated if you deploy it to such a device.
 -  **Enabling Subscription Activation with an existing Enterprise Agreement (EA)**. If you're an existing EA customer, you can get Windows 10 Enterprise E3 or E5 licenses for free, depending on your EA. You can then assign the licenses to Azure AD users or groups. By doing so, Windows 10 Pro devices will be automatically upgraded and activated when users sign in.
 -  **Enabling Subscription Activation without an existing EA**. The process of assigning Windows 10 Enterprise E3 or E5 licenses is the same. The only difference is that organizations must purchase the licenses from CSP before they can assign them.

Before an organization can start deploying Windows 10 Enterprise E3 or E5 licenses to users, it must sync the identities in the on-premises AD DS domain with Azure AD. This process is required because it ensures that users have a single identity they can use to access their on-premises apps and cloud services that use Azure AD, such as Windows 10 Enterprise E3 or E5. Having a single identity means that users can use their existing credentials to sign in to Azure AD and access the cloud services the organization provides and manages for them.

Windows 10 Enterprise E3 or E5 licenses can be assigned in several different ways:

 -  By using license assignment in the Azure portal.
 -  By using license assignment in the Microsoft 365 Admin Center.
 -  By uploading a spreadsheet.
 -  By using a PowerShell script.

After an Azure AD user with an assigned Windows 10 license signs in to a Windows 10 Pro version 1703 or newer device, Windows is automatically activated. You can verify that the Windows 10 Enterprise E3 or E5 subscription is activated in the **Settings** app, by selecting **Update &amp; Security** and then **Activation**, as shown in the following graphic.

:::image type="content" source="../media/windows-settings-app-c4fa1203.jpg" alt-text="screenshot of the Windows 10 Settings app":::


**Additional reading.** For more information, see [Deploying Windows 10 Enterprise licenses](https://docs.microsoft.com/windows/deployment/deploy-enterprise-licenses#win-10-activated-subscription-active?azure-portal=true).
