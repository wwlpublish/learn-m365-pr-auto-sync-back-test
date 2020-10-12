A policy-based approach to security enables you to apply your requirements to many different users and devices, by creating and managing a single object. In Teams, you can use Conditional Access policies and Microsoft Intune policies to enforce security.

## How Conditional Access policies work for Teams

Microsoft Teams relies heavily on Exchange Online, SharePoint, and Skype for Business Online for core productivity scenarios, like meetings, calendars, interop chats, and file sharing. Conditional Access policies that are set for these cloud apps apply to Microsoft Teams when a user directly signs in to Teams, on any client.

Microsoft Teams is supported separately as a cloud app in Azure Active Directory Conditional Access policies. Conditional Access policies that are set for the Microsoft Teams cloud app apply to Teams when a user signs in. However, without the correct policies on other apps like Exchange Online and SharePoint, users could still possibly access those resources directly.

## Devices and apps

Microsoft Teams integrates with Microsoft Endpoint Manager, which includes Microsoft Intune. Intune is a 100 percent cloud-based mobile device management (MDM) and mobile application management (MAM) provider for your apps and devices. It lets you control features and settings on Android, Android Enterprise, iOS/iPadOS, macOS, and Windows 10 devices.

## Learn more

- [Azure Active Directory Quickstart](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
