The Microsoft Teams desktop client provides a full-featured experience and can be installed either individually by users or rolled out by IT in a mass deployment. Advantages of the Teams desktop client include auto-start, which ensures that you'll stay signed in and won't miss any important notifications, as well as more features and a more granular management experience.

## Installation options

The Teams desktop client comes with a stand-alone (.exe) installer for user installation and works with MSI for IT installations. It's also available by default as part of Microsoft 365 Apps. Anybody who has a Teams license can sign in to Teams via the web.

Administrators can perform a bulk deployment of the Teams desktop client to selected users or computers in their organization. Microsoft has provided MSI files (both 32-bit and 64-bit) that let administrators use Microsoft Endpoint Configuration Manager, Group Policy, or any third-party distribution mechanism for broad deployment. These files can be used to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign in on that machine. (You can disable auto launch after installing the app.) It's recommended that you deploy the package to the computer so that all new users of the machine will also benefit from this deployment.

> [!NOTE]
> If Teams was installed and later uninstalled, the MSI installation option won't install again unless Teams has been completely uninstalled.

## Installation considerations

The Windows desktop client is installed per user. The client can be installed without administrator permissions (though they are required on a Mac) and works with either the 32-bit or 64-bit architecture, though the 64-bit version is recommended. Minimum requirements include Office 2013 or higher.

## Client updates

The desktop client updates itself automatically, but users can also manually download updates. While Teams is installed by default with new installations of Microsoft 365 Apps, Teams follows its own update process and not that of other Office apps such as Word or PowerPoint.

Teams desktop client updates are released every two weeks after rigorous internal testing and validation. If a critical update is required, Teams will bypass this schedule and release the update as soon as it's available.

## Learn more

- [Hardware requirements for the Teams desktop app](/microsoftteams/hardware-requirements-for-the-teams-app?azure-portal=true)
- [Get clients for Microsoft Teams: Mac](/microsoftteams/get-clients#mac?azure-portal=true)
- [Manage configuration profiles](/microsoftteams/device-management#use-configuration-profiles-in-teams?azure-portal=true)
- [Manage device settings and firmware](/microsoftteams/device-management#manage-devices-in-teams?azure-portal=true)
- [Configure Microsoft Teams Rooms](/microsoftteams/room-systems/with-office-365?azure-portal=true)
