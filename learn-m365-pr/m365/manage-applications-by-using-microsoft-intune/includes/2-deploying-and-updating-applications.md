As an IT administrator, you can use Microsoft Intune to manage the client apps that your company's workforce uses. This functionality is in addition to managing devices and protecting data. One of an administrator's priorities is to ensure that end users have access to the apps they need to do their work. This goal can be a challenge because:

- There are a wide range of device platforms and app types.
- You might need to manage apps on both company devices and users' personal devices.
- You must ensure that your network and your data remain secure.

Additionally, you might want to assign and manage apps on devices that are not enrolled with Intune. Intune offers a range of capabilities to help you get the apps you need on the devices you want to run them on.

Any app that has been integrated with the Intune App SDK or wrapped by the Intune App Wrapping Tool can be managed using Intune app protection policies. See the official list of [Intune-managed apps](/intune/apps-supported-intune-apps) available for public use.

The baseline requirements to use app protection policies on an Intune-manage app include:

- The end user must have an Azure Active Directory (Azure AD) account.
- The end user must have a license for Microsoft Intune assigned to their Azure Active Directory account.
- The end user must belong to a security group that is targeted by an app protection policy. The same app protection policy must target the specific app being used. App protection policies can be created and deployed in the Intune console in the Azure portal. Security groups can currently be created in the Microsoft 365 admin center.
- The end user must sign into the app using their Azure AD account.
