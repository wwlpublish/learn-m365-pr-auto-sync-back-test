Beyond fundamental and protective device configuration profiles, you should be aware of the following configuration control and concepts that Microsoft Intune provides. Intune provides a wide variety of device configuration control. These following areas can help you become familiar with the total configuration capabilities offered by Intune.

## Group Policy analytics

If you are using Microsoft Endpoint Configuration Manager to managing your on-premises devices and endpoints, you should be aware of Group Policy analytics. Group Policy analytics is a feature and tool in Microsoft Endpoint Manager that analyzes your on-premises Group Policy objects (GPOs). GPOs are primarily used on-premises to configure settings on Windows computers, but also can include remote Windows devices. In device management, GPOs help control security and features in the Windows OS, Internet Explorer, Office apps, and more. Group policy provides the capability to manage a large number of Active Directory Domain Services (AD DS) computer and user objects through a centralized, one-to-many model. Group Policy settings are contained in a group policy object and linked to one or more AD DS service containers—sites, domains, and organizational units (OUs). Note that devices do not have to be domain-joined to apply GPOs.

Group Policy analytics helps you determine how your GPOs translate in the cloud. The output shows which settings are supported in MDM providers, including Microsoft Intune. It also shows any deprecated settings, or settings not available to MDM providers.

If your organization uses GPOs, and you want to move some workloads to Microsoft Intune, then Group Policy analytics will help. Currently, this feature provides importing and analysis.

## Administrative templates

When managing devices in your organization, you want to create groups of settings that apply to different device groups. For example, suppose you have two device groups. For the first group, you want to assign a specific set of settings. For the second group, you want to assign a different set of settings. You also want a simple view of the settings you can configure. You can complete this task using Administrative Templates in Microsoft Intune. Administrative Templates include thousands of settings that control features in Microsoft Edge version 77 and later, Internet Explorer, Microsoft Office programs, remote desktop, OneDrive, passwords, PINs, and more. These settings allow group administrators to manage group policies using the cloud.

## Custom profiles

In addition to using built-in Intune settings to control different features on a device, you can also create custom profiles. Custom profiles are great when you want to use device settings and features that aren't built in to Intune. These profiles include features and settings for you to control on devices in your organization. For example, you can create a custom profile that sets the same feature for every iOS/iPadOS device.

Custom settings are configured differently for each platform. For example, to control features on Android and Windows devices, you can enter Open Mobile Alliance Uniform Resource Identifier (OMA-URI) values. For Apple devices, you can import a file you created with the [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) or [Apple Profile Manager](https://support.apple.com/profile-manager).

For more information about crating custom device configuration profiles, see [Create a profile with custom settings in Intune](/mem/intune/configuration/custom-settings-configure).

## Settings catalog

The settings catalog lists all the settings you can configure on Windows and macOS devices. This feature simplifies how you create a device configuration policy, and how you view all the available settings. Also, more settings are continually being added.

When you create a device configuration profile using the settings catalog, you start from scratch. You add only the settings you want to control and manage. For example, you can use the settings catalog to create a BitLocker profile with all BitLocker settings, and all in one place in Intune.

For more information about the setting catalog, see [Use the settings catalog to configure settings on Windows and macOS devices](/mem/intune/configuration/settings-catalog).