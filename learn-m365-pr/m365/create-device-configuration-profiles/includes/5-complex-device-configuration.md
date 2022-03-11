




## Group Policy analytics

Group Policy analytics is a tool and feature in Microsoft Endpoint Manager that analyzes your on-premises Group Policy objects (GPO). It helps you determine how your GPOs translate in the cloud. The output shows which settings are supported in MDM providers, including Microsoft Intune. It also shows any deprecated settings, or settings not available to MDM providers.

If your organization uses GPOs, and you want to move some workloads to Microsoft Endpoint Manager and Intune, then Group Policy analytics will help.

Currently, this feature provides importing and analysis. In a future release (no ETA), you'll be able to create a policy based off your imported GPO, and deploy the policy.

## Administrative templates

When managing devices in your organization, you want to create groups of settings that apply to different device groups. For example, you have several device groups. For GroupA, you want to assign a specific set of settings. For GroupB, you want to assign a different set of settings. You also want a simple view of the settings you can configure.

You can complete this task using Administrative Templates in Microsoft Intune. The administrative templates include thousands of settings that control features in Microsoft Edge version 77 and later, Internet Explorer, Microsoft Office programs, remote desktop, OneDrive, passwords, PINs, and more. These settings allow group administrators to manage group policies using the cloud.

The Windows settings are similar to group policy (GPO) settings in Active Directory (AD). These settings are built in to Windows, and are ADMX-backed settings that use XML. The Office and Microsoft Edge settings are ADMX-ingested, and use the ADMX settings in Office administrative template files and Microsoft Edge administrative template files. And, the Intune templates are 100% cloud-based. They offer a simple and straight-forward way to configure the settings, and find the settings you want.

Administrative Templates are built in to Intune, and don't require any customizations, including using OMA-URI. As part of your mobile device management (MDM) solution, use these template settings as a one-stop shop to manage your Windows client devices.

This article lists the steps to create a template for Windows client devices, and shows how to filter all the available settings in Intune. When you create the template, it creates a device configuration profile. You can then assign or deploy this profile to Windows client devices in your organization.

## Custom

Microsoft Intune includes many built-in settings to control different features on a device. You can also create custom profiles, which are created similar to built-in profiles. Custom profiles are great when you want to use device settings and features that aren't built in to Intune. These profiles include features and settings for you to control on devices in your organization. For example, you can create a custom profile that sets the same feature for every iOS/iPadOS device.

Custom settings are configured differently for each platform. For example, to control features on Android and Windows devices, you can enter Open Mobile Alliance Uniform Resource Identifier (OMA-URI) values. For Apple devices, you can import a file you created with the Apple Configurator or Apple Profile Manager.

For more information on configuration profiles, see What are Microsoft Intune device profiles?.

This article shows you how to create a custom profile for Android device administrator, Android Enterprise, iOS/iPadOS, macOS, and Windows. You can also see all the available settings for the different platforms.

## Settings catalog

Settings catalog lists all the settings you can configure, and all in one place. This feature simplifies how you create a policy, and how you see all the available settings. More settings are continually being added.

When you create the policy, you start from scratch. You add only the settings you want to control and manage. For example, you can use the settings catalog to create a BitLocker policy with all BitLocker settings, and all in one place in Intune.

Use the settings catalog as part of your mobile device management (MDM) solution to manage and secure devices in your organization.