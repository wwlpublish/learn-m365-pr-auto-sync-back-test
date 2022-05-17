As an IT administrator, you've received a request from the marketing team to use Surface devices in their showrooms so they can highlight their materials and do demonstrations. You know that Windows 10/11 supports kiosk mode operations and are keen to understand how this can be applied to Surface devices, to support the marketing team, while maintaining security and regulatory compliance.

There are several tasks to complete to configure and deploy a kiosk surface device. You'll see how to:

1. Create a kiosk Autopilot deployment profile.
1. Create a kiosk configuration profile.

## Create a kiosk Autopilot deployment profile

> [!NOTE]
> It is assumed that you have already created a kiosk user account.

You'll use Microsoft Endpoint Manager admin center to create the Autopilot deployment profile.

1. To begin, open <https://endpoint.microsoft.com/> in a private browser window and sign in with your administrator credentials.
1. From the Microsoft Endpoint Manager admin center home page, select **Devices** from the left navigation.
1. From the **Devices | Overview** page, under **device enrollment**, select **Enroll Device**.
1. From the **Enroll devices | Windows enrollment** page, select **Deployment Profiles** under **Windows Autopilot Deployment Program**.
1. From the **Windows Autopilot deployment profiles** page, on the menu, select **+ Create profile** **> Windows PC**.

    :::image type="content" source="../media/create-profile.png" alt-text="Screenshot showing the create profile screen.":::

1. On the **Create profile** page, in the **Name** box, enter **Kiosk Autopilot deployment**.
1. On the **Convert all targeted devices to Autopilot** field, select **Yes**.
1. Now select **Next**.
1. On the **Out-of-box experience (OOBE)** tab, select the **Deployment mode** menu, review the available options, and ensure **User driven** is selected.

    :::image type="content" source="../media/create-profile-2.png" alt-text="Screenshot showing the Out-of-box experience (OOBE) screen.":::

    > [!NOTE]
    > Self-deploying mode uses a device's Trusted Platform Module (TPM) 2.0 hardware to authenticate the device into an organization's Azure AD tenant.

1. On the **Apply device name** template, select **Yes**.
    1. In the **name** box, enter **KIOSK-%RAND:4%**.
1. When complete, select **Next**.
1. On the **Assignments** tab, under **Included groups**, select **Add groups**.

    :::image type="content" source="../media/create-profile-assignments.png" alt-text="Screenshot showing the assignments screen.":::

1. In the **Select groups to include** page, select **Windows Autopilot Enrollment** and then select **Select**.
1. On the **Create profile** page, select **Next**.
1. On the **Review + create** tab, review the profile configuration settings, and then select **Create**.

    :::image type="content" source="../media/create-profile-review.png" alt-text="Screenshot showing the review screen.":::

You've now created a kiosk Autopilot deployment profile. Next, you'll create a kiosk configuration profile.

## Create a kiosk configuration profile

A kiosk configuration profile defines how the kiosk will operate, including if it allows for single or multiple applications to be run, and what the default apps will be. To create this configuration profile, you'll use Microsoft Endpoint Manager. These steps will create a single app kiosk running Microsoft Edge.

1. In the Microsoft Endpoint Manager admin center (https://endpoint.microsoft.com), in the left navigation, select **Devices**.
1. On the **Devices | Overview** page, under **Policy**, select **Configuration profiles**.
1. In the **Devices | Configuration profiles** page, on the menu, select **+ Create profile**.
1. In the **Create a profile** pane, select the **Platform** menu, and then select **Windows 10 and later**.
1. Select the **Profile type** menu, select **Templates**, and select **Kiosk**.
1. Now select **Create**.
1. On the **Kiosk** page, in the **Name** box, enter **Single app kiosk mode**, and then select **Next**.
1. On the **Configuration settings** tab, select the **Select a kiosk mode** menu.
1. Select **Single app, full-screen kiosk**.
1. Select the **User logon type** menu, and then select **Azure AD user or group (Windows 10, version 1803 and later, or Windows 11)**.
1. Select **Add**.
1. In the **Select users or groups** pane, select **Kiosk User**, and then select **Select**.
1. Select the **Application type** menu, and then select **Add Microsoft Edge browser**.
1. In the **Edge Kiosk URL** box, enter **https://windows365.microsoft.com**.
1. Review the remaining settings, and then select **Next**.
1. On the **Assignments** tab, under **Included groups**, select **Add groups**.
1. In the **Select groups to include** pane, select **Windows Autopilot Enrollment**.
1. Now select **Select**.
1. On the **Assignments** tab, select **Next**.
1. On the **Applicability Rules** tab, select **Next**.
1. On the **Review + create** tab, review the settings, and then select **Create**.

You've now successfully created a kiosk configuration profile that can be applied to a Surface device. When the Surface device launches, and someone signs in as the kiosk user, they'll only be able to access Microsoft Edge and the target URL provided.
