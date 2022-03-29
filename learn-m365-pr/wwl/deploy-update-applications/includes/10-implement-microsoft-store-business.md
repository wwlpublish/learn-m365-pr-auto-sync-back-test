For organizations that use Azure AD, Microsoft Store for Business is available without any additional fee. If an organization already has Azure AD, for example as part of an Azure or Microsoft 365 subscription, it can sign up with its Azure AD account and start using Microsoft Store for Business. If an organization doesn’t yet have Azure AD, it can create an Azure AD tenant as part of the Microsoft Store for Business sign-up process. Users who sign up for and create a Microsoft Store for Business account must be a global administrator in Azure AD.

Before you can start using Microsoft Store for Business, you must first sign up. The sign-up process is fast, straightforward, and similar to signing up for other cloud services:

1.  In your browser, go to [https://www.microsoft.com/business-store](https://www.microsoft.com/business-store), sign in with your Azure AD global administrator account.
2.  When you are signed in, select **Manage** and then accept the licensing agreement.
3.  You are now signed up for Microsoft Store for Business.

:::image type="content" source="../media/microsoft-store-business-manage-674627c7.png" alt-text="Sign up screen for Microsoft Store for Business.":::


After signing up for Microsoft Store for Business, you can start managing it. The user account that you used to sign up for Microsoft Store for Business is already a global administrator in your Azure AD tenant, and this user has all permissions. Other Azure AD tenant users can browse Microsoft Store for Business and install available apps, but they can’t manage it. If necessary, a global administrator can delegate permissions for Microsoft Store for Business tasks by assigning store roles to other company employees; for example, to acquire and distribute apps. You can assign roles only to Azure AD user accounts and not to groups.

You can assign four user roles to manage access to apps and to perform other tasks in Microsoft Store for Business:

 -  **Admin.** Users in this role can perform all tasks and assign roles to others.
 -  **Purchaser.** Users in this role can acquire apps, add them to the private store, and distribute apps to company users.
 -  **Basic purchaser.** Users in this role can acquire apps they own, add them to the private store, and distribute apps to company users.
 -  **Windows Defender Device Guard signer.** Users in this role can manage Windows Defender Device Guard settings.

When you sign up for Microsoft Store for Business, the following five apps automatically add to the private store: Microsoft Word Mobile, Microsoft Excel Mobile, Microsoft PowerPoint Mobile, Microsoft OneNote and Microsoft Sway. It can take up to 36 hours for the apps to become visible in the private store. If a user is in the Admin role, they can add additional apps to the private store. Users in the Purchaser or Basic purchaser role can purchase apps, but they can’t add them to the private store. Users in the Basic purchaser role also can’t license apps for offline use. Users in the Admin or Global Admin roles can add Microsoft Store for Business apps and LOB apps to a private store.

A user in the Admin role can manage the following settings in Microsoft Store for Business:

 -  **Account information and payment options.** You can modify organizational information, such as the address and value-added tax number, and you can add or modify payment options, such as credit card details.
 -  **Private store name.** You can modify the name of a private store.
 -  **Offline licensing.** If apps can be offline-licensed, download the app package and distribute it to users even if they don’t connect to Microsoft Store for Business and even if they don’t have an Azure AD account. Additionally, the user with the Admin role can configure this setting if offline-licensed apps display in Microsoft Store for Business.
 -  **Management tools.** You can add a management tool such as Intune or Configuration Manager to Microsoft Store for Business. Management tools can sync with Microsoft Store for Business, and you can use them to distribute apps from Microsoft Store for Business to company users.
 -  **Device Guard signing.** Apps that install from Microsoft Store for Business can be signed automatically and added to the code integrity policy. If you configure this option, employees can install apps from Microsoft Store for Business and run them on a device that is protected by Windows Defender Device Guard.
 -  **Permissions.** You can delegate permissions for Microsoft Store for Business and allow company users to perform certain management tasks in Microsoft Store for Business.
 -  **LOB publishers.** You can invite company developers or third-party vendors to submit their LOB apps to Microsoft Store for Business. These LOB apps can be available only in your organization’s private store and not in the public Microsoft Store.
