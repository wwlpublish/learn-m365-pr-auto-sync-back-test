As an IT administrator, you can use Microsoft Intune to manage the client apps that your company's workforce uses. This functionality is in addition to managing devices and protecting data. One of an admin's priorities is to ensure that end users have access to the apps they need to do their work, including Microsoft 365 Apps. In conjunction with Autopilot, Intune can automatically deploy Microsoft 365 Apps when deploying a new device or resetting an existing device.

However, before you can assign, monitor, configure, or protect apps, you must add them to Intune. One of the available app types is Microsoft 365 apps for Windows 10 devices. By selecting this app type in Intune, you can assign and install apps to devices you manage that run Windows 10. The available apps are displayed as a single entry in the list of apps in the Intune console within Azure.

You must use Microsoft 365 Apps licenses to activate Microsoft 365 Apps apps deployed through Microsoft Intune. Microsoft 365 Apps for business edition is supported by Intune, however you must configure the app suite of the Microsoft 365 Apps for business edition using XML data.

## Intune Microsoft 365 Apps configuration

Deploying Microsoft 365 Apps to devices in your organization is easy and flexible, providing multiple configuration options that suit your IT organization's needs. The Configuration designer offers an intuitive UI with all the necessary settings for adding new apps to Intune. You can also use the Office Customization Tool to create the configuration files and enter XML data into Intune.

You will need to enter information such as the App Suite Name, Description, Publisher, and Logo before moving onto defining the individual apps that will be part of the App Suite. The configuration designer will allow you to specify how the app is to be deployed, updated, and managed on the device. The available settings in the configuration designer are:

- **Office version** - Install the 32-bit or 64-bit version of Office.

- **Update Channel** - Choose how Office is updated and how often:

  - Monthly - Provide users with the newest features of Office as soon as they're available.
  - Monthly (Targeted) - Provide pilot users and application compatibility testers the opportunity to test the next Monthly Channel.
  - Semi-Annual - Provide users with new features of Office only a few times a year.
  - Semi-Annual (Targeted) - Provide pilot users and application compatibility testers the opportunity to test the next Semi-Annual Channel.

- **Remove MSI from end-user devices** - Choose whether you want to remove pre-existing Office .MSI apps from end-user devices. The installation won't succeed if there are pre-existing .MSI apps on end-user devices.

- **Automatically accept the app end user license agreement** - Select this option if you don't require end users to accept the license agreement.

- **Use shared computer activation** - Select this option when multiple users share a computer.

- **Languages** - Office is automatically installed in any of the supported languages that are installed with Windows on the end-user's device. Select this option if you want to install additional languages with the app suite.

After you choose a channel, you can optionally select Specific to install a specific version of Office for the selected channel on end user devices.
