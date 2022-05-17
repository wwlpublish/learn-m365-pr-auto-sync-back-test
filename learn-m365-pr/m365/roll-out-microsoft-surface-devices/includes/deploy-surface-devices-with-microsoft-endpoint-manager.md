Surface devices that have been enrolled to Windows Autopilot in Microsoft Endpoint Manager can be safely shipped directly to your employees.

Your administrators are used to preconfiguring and installing software before they ship new devices to employees. How will users get the software they need? How will it be configured?

In this unit, you'll learn how Windows Autopilot lets you deploy Surface devices without anyone in your administration team having to switch on, or even open the box. The first step is to create a deployment group that Surface devices will be added to when they join Azure Active Directory. To configure software that will be installed, you'll create an application profile and assign it to your deployment group. You'll then see that the devices will be automatically configured with your chosen settings and install preconfigured versions of software like Outlook.

## Create a deployment group

You create a deployment group in the Microsoft Endpoint Manager admin center with these steps:

1. In your browser, go to the Microsoft Endpoint Manager admin center at <https://endpoint.microsoft.com>.
1. In the left navigation, select **Groups**.
1. In the **Groups | All groups** pane, on the menu, select **New group**.
1. On the **New Group** pane, set the following values:
   - **Group type**: Security
   - **Group name**: Windows Autopilot Enrollment
   - **Membership type**: Dynamic Device
   - **Dynamic device members**: Add dynamic query
1. To the right of **Rule syntax**, select **Edit**.
1. In the **Rule syntax** box, enter this rule:

    ```sql
    (device.devicePhysicalIDs -any _ -contains "[ZTDId]")
    ```

1. Select **OK**.
1. On the menu, select **Save**.
1. In the **New Group** pane, select **Create**.

With this group set up, your administrators will create a deployment profile.

## Create a deployment profile

Now that you've created a deployment group, you can set up a deployment profile in the Microsoft Endpoint Manager admin center with these steps:

1. In the left navigation, select **Devices**.
1. In the **Devices | Overview** pane, under **Device enrollment**, select **Enroll devices**.
1. In the **Enroll devices | Windows enrollment** pane, under **Windows Autopilot Deployment Program**, select **Deployment Profiles**.
1. In the **Windows Autopilot deployment profiles** pane, on the menu, select **+ Create profile.**
1. In the menu, select **Windows PC**.
1. On the **Create profile** pane, in the **Name** box, enter **Windows Autopilot profile**.
1. To the right of the **Convert all targeted devices to Autopilot**, select **Yes** and then select **Next**.
1. On the **Out-of-box experience (OOBE)** tab, review the settings, and then select **Next**.
1. On the **Assignments** tab, under **Included groups**, select **Add groups**.
1. In the **Select groups to include** pane, select **Windows Autopilot Enrollment** (the group you just created), and then choose **Select**.
1. On the **Create profile** pane, select **Next**.
1. On the **Review + create** tab, select **Create**.

## Create an application policy

This is how to configure the applications installed during the OOBE. To create an application policy and assign it to the deployment group, follow these steps:

1. In the Microsoft Endpoint Manager admin center, in the left navigation, select **Apps**.
1. In the **Apps | Overview** pane, select **All apps**.
1. In the **Apps | All apps** pane, on the menu, select **+ Add**.
1. In the **Select app type** pane, select the **App type** menu and then, under **Microsoft 365 Apps**, select **Windows 10 and later**.
1. Review the select app type, and then choose **Select**.
1. On the **Add Microsoft 365 Apps** page, on the **App suite information** tab, select **Next**.
1. On the **Configure app suite** tab, select the **Select Office apps** menu, and then review the default apps.
1. Under **App suite information**, select the **Update channel** menu, and then select **Monthly Enterprise Channel**.
1. Select **Next**.
1. On the **Assignments** tab, under **Required**, select **Add group**.
1. In the **Select groups** pane, select **Windows Autopilot Enrollment**, and then choose **Select**.
1. On the **Assignments** tab, select **Next**.
1. Review the configured app suite, and then select **Create**.

Now that your administrator team has created the configurations they want, the Surface devices are ready to be sent out to your employees.

## User-driven Windows Autopilot deployment

The Windows Autopilot user-driven mode lets you deploy Surface devices and have them automatically configure from their factory state to a ready-to-use state. On receiving their Surface device, employees need to follow these steps:

1. Unbox the Surface device, plug it in, and turn it on.
1. Choose a language (only required when multiple languages are installed), locale, and keyboard.
1. Connect it to a wireless or wired network with internet access.
1. Sign in with their organization's email address and password.
1. Wait for Windows Autopilot to complete the device configuration and log them in.

The rest of the deployment process is automated. The device will complete these steps:

- Download a Windows Autopilot profile that will define any changes to the out-of-box experience.
- Use the credentials provided to join your organization's Azure Active Directory.
- Enroll itself in Intune.
- Get configured as defined by the organization.
- Download additional software (like the Office apps).

## Pre-provisioned Windows Autopilot deployment

There's another option if you have employees who need to have their device business ready when they switch it on. In these cases, you can pre-provision the Surface device for the employee before sending it to them. This does require some extra work for you.

The first step is to create a new deployment profile. Follow the steps above but, at the OOBE tab step, next to the **Allow pre-provisioned deployment**, select **Yes**.

:::image type="content" source="../media/windows-autopilot-preprovisioned-profile-settings.png" alt-text="Screenshot showing the OOBE tab with Allow pre-provisioned deployment as Yes and Language set to User select.":::

To allow for easier access to the pre-provisioning mode, select **User select** for the **Language (Region)**.

To complete the pre-provisioning on each Surface device, follow these steps:

1. Boot the device.
1. On the first OOBE screen, press the Windows key five times.
1. Choose **Windows Autopilot provisioning**, then select **Continue**.
   :::image type="content" source="../media/windows-autopilot-provisioning.png" alt-text="Screenshot of the OOBE window on a Surface device showing the Windows Autopilot provisioning option selected.":::
1. Validate the information displayed. If any changes are needed, make the changes, and then select **Refresh** to download the updated Autopilot profile details again.
1. Select **Provision** to begin the provisioning process.
1. A green status screen appears with information about the device, including the same details presented previously. For example, Autopilot profile, organization name, assigned user, and QR code. The elapsed time for the pre-provisioning steps is also provided.
1. Select **Reseal** to shut down the device. At that point, the device can be sent to the employee.
   :::image type="content" source="../media/windows-autopilot-configuration-success.png" alt-text="Screenshot of the Windows Autopilot Configuration success screen.":::

You've seen the two ways to deploy devices to your employees. You can reduce your workload by setting up Surface devices for end-user deployment. For your employees whose time is critical, you can preprovision their devices, so they're business ready when they switch them on.
