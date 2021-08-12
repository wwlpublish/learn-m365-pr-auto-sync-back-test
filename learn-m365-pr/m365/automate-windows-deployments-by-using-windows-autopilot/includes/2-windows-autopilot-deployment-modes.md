Depending on your organization's needs and requirements, Windows Autopilot supports a growing list of common scenarios that make transitioning to modern management a smooth process.

|||
| :--- | :--- |
| ![Icon indicating play video](../media/video-icon.png)| Watch this video to learn more about the various scenarios that are supported by Windows Autopilot.|

>[!VIDEO https://www.youtube.com/embed/7t7xaV8sm50]

## Windows Autopilot in User-driven mode

Windows Autopilot user-driven mode is designed to enable new Windows 10 devices to arrive directly from the factory, in a ready-to-use state without requiring IT personnel to ever touch the device. The process is so simple that anyone can complete it, enabling devices to be shipped to the end user with simple instructions:

1. Unbox the device, plug it in, and turn it on.
1. Choose a language, locale, and keyboard.
1. Connect it to a wireless or wired network with internet access.
1. Specify your e-mail address and password for your organization account.

The remainder of the process is entirely automated, with the device being joined to the organization, enrolled in Intune, and fully configured as defined by the organization.

## Windows Autopilot in Self-deploying mode

Windows Autopilot self-deploying mode enables a shared device, such as a kiosk, digital sign, or shared workstation, to be deployed with little to no user interaction. For devices with an Ethernet connection, no user interaction is required; for devices connected via Wi-fi, no interaction is required after making the Wi-fi connection.

Self-deploying mode joins the device into Azure Active Directory, enrolls the device in Intune leveraging Azure AD, and ensures that all policies, applications, certificates, and networking profiles are provisioned on the device. The enrollment status page prevents access to the desktop until the device is fully provisioned.

## Reset devices using Windows Autopilot

During a reset, Windows Autopilot Reset removes personal files, apps, and settings from a device and then reapplies the device's original settings. Throughout the process, the device maintains its identity connection to Azure AD and its management connection to Intune so that the device is once again ready for use. Windows Autopilot Reset takes the device back to a business-ready state, allowing the next user to sign in and get productive quickly and simply.

The Windows Autopilot Reset process automatically retains information from the existing device:

- Set the region, language, and keyboard to the originally configured values.
- Wi-Fi connection details.
- Provisioning packages previously applied to the device, as well as a provisioning package present on a USB drive when the reset process is started.
- Azure Active Directory device membership and MDM enrollment information.

Windows Autopilot Resets can be triggered locally or remotely by IT staff.

## White glove deployments using Windows Autopilot

White glove deployments are for devices that will be configured by the OEM or member of the IT organization before deployment. In scenarios where bandwidth is a concern during deployment or complex configurations are needed, IT can pre-install applications and configurations before final delivery. The end user only needs to personalize their settings, policies, and account information before using their device.

## Deploy Windows 10 on existing Windows 7 or 8.1 devices

Windows Autopilot, along with System Center Configuration Manager, can be used to deploy Windows 10 to managed devices running Windows 7 or 8.1. Apps, policies, and settings can all be preconfigured with Intune, so the devices are business ready after being wiped and reimaged with Windows 10.
