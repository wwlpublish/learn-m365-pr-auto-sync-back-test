Depending on your organization's needs and requirements, Windows Autopilot supports a growing list of common scenarios that make transitioning to modern management a smooth process.

|||
| :--- | :--- |
| ![Icon indicating play video](../media/video_icon.png)| Watch this video to learn more about the various scenarios that are supported by Windows Autopilot.|

>[!VIDEO https://www.youtube.com/watch?v=7t7xaV8sm50]

## Windows Autopilot in User-driven mode

Windows Autopilot user-driven mode is designed to enable new Windows 10 devices to be transformed from their initial state, directly from the factory, into a ready-to-use state without requiring that IT personnel ever touch the device. The process is designed to be simple so that anyone can complete it, enabling devices to be shipped or distributed to the end user directly with simple instructions:

1. Unbox the device, plug it in, and turn it on.

1. Choose a language, locale and keyboard.

1. Connect it to a wireless or wired network with internet access.

1. Specify your e-mail address and password for your organization account.

After completing those simple steps, the remainder of the process is completely automated, with the device being joined to the organization, enrolled in Intune (or another MDM service), and fully configured as defined by the organization.

## Windows Autopilot in Self-deploying mode

Windows Autopilot self-deploying mode enables a shared device, such as a kiosk, digital sign or shared workstation, to be deployed with little to no user interaction. For devices with an Ethernet connection, no user interaction is required; for devices connected via Wi-fi, no interaction is required after making the Wi-fi connection.

Self-deploying mode joins the device into Azure Active Directory, enrolls the device in Intune (or another MDM service) leveraging Azure AD for automatic MDM enrollment, and ensures that all policies, applications, certificates, and networking profiles are provisioned on the device, leveraging the enrollment status page to prevent access to the desktop until the device is fully provisioned.

## Reset devices using Windows Autopilot

Windows Autopilot Reset removes personal files, apps, and settings and reapplies a device’s original settings, maintaining its identity connection to Azure AD and its management connection to Intune so that the device is once again ready for use. Windows Autopilot Reset takes the device back to a business-ready state, allowing the next user to sign in and get productive quickly and simply.

The Windows Autopilot Reset process automatically retains information from the existing device:

- Set the region, language, and keyboard to the originally-configured values.

- Wi-Fi connection details.

- Provisioning packages previously applied to the device, as well as a provisioning package present on a USB drive when the reset process is initiated.

- Azure Active Directory device membership and MDM enrollment information.

Windows Autopilot Resets can be triggered locally or remotely by IT staff.

## White glove deployments using Windows Autopilot

White glove deployments are for devices that will be fully set up by the OEM or member of the IT organization prior to deployment. In scenarios where bandwidth is a concern during deployment or complex configurations are needed, IT can pre-install applications and configurations prior to final delivery. The end user only needs to personalize their settings, polices, and account information before using their device.

## Deploy Windows 10 on existing Windows 7 or 8.1 devices

Windows Autopilot, along with System Center Configuration Manager, can be used to deploy Windows 10 to managed devices running Windows 7 or 8.1.  Apps, policies, and settings can all be preconfigured with Intune, so the devices are business ready after being wiped and reimaged with Windows 10.

