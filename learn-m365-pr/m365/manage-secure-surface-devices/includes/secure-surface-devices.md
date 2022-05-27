When staff in an organization adopt a flexible hybrid approach to working, the challenge of maintaining a secure device increases. As operating systems adopt more sophisticated built-in security mechanisms, anyone who seeks to exploit loopholes can move towards attacking the firmware on the device.

Microsoft has solved this issue by managing and controlling the hardware design, keeping the development of the firmware in-house, using a UEFI, and deploying updates automatically to all Surface devices.

By controlling every aspect of the Surface device, Microsoft provides a consistent experience that can be organized through Microsoft Endpoint Manager.

Here, you'll learn how to create an enrollment policy to enable Windows Hello on all enrolled devices, and how to configure passwordless login using the authenticator app.

### Create a policy to use Windows Hello

Surface devices allow individuals to use biometrics to authenticate themselves. Windows Hello allows users to create long complex passwords but still easily log in with their face or fingerprint.

Using an enrollment policy, you can configure any aspect of the Surface device and its behavior. Here, we'll show you how to configure a Surface device to use Windows Hello.

1. Sign in to Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) using your admin credentials.
1. From the home page, select **Devices**.
1. You'll use the device enrollment option, so select **Enroll devices**.
1. Under the **Windows enrollment** page, from the **General** section, select **Windows Hello for Business**.

    :::image type="content" source="../media/windows-enrollment-portal.png" alt-text="Screenshot of the Windows enrollment dashboard.":::

1. From the **Windows Hello for Business** pane, you'll need to change the setting for **Configure Windows Hello for Business**, from **Not configured**, to **Enabled**.

    :::image type="content" source="../media/windows-hello-configure.png" alt-text="Screenshot of the Windows Hello for Business configuration screen.":::

1. While the focus here has been to just enable Windows Hello for Business, you can also add any extra configuration settings that you need. These include using Trusted Platform Module (TPM), PIN length, using uppercase letters and special characters in the PIN, whether biometric authentication is allowed, and others.

    :::image type="content" source="../media/windows-hello-configure-extra.png" alt-text="Screenshot of the Windows Hello for Business extra configuration screen.":::

1. When you're happy with your settings, select **Save** to create the policy.

## Configure passwordless login that uses the Microsoft Authenticator app

One of the key weaknesses of any security system is the password. While most organizations will enforce a strong password policy, the password is still the weak link. One way to improve this is by implementing multi-factor authentication. This uses a secondary device, typically a phone or dongle, to supply biometrics or some other token to support your login. Microsoft has developed a software authenticator, which is used to verify the login attempt.

Here, you'll discover how to configure your Surface device to use the Microsoft Authenticator app.

### Enable combined security information using Azure Active Directory

First, make sure that your users are able to use the combined security information features.

1. Sign in to the Azure Active Directory admin center (<https://aad.portal.azure.com>) using your admin credentials.
1. From the home page, select **Azure Active Directory**.
1. In the **Overview** page, under **Manage**, select **Users**.
1. In the **Users | All users** page, select **User settings**.

    :::image type="content" source="../media/active-directory-admin-center.png" alt-text="Screenshot of the Azure Active Directory Users configuration screen.":::

1. From the **User Settings** pane, go to the bottom of the page, and locate **User features**. Select the **Manage user feature settings** option.

    :::image type="content" source="../media/active-directory-user-settings.png" alt-text="Screenshot of the User settings screen.":::

1. On the **User features** page, you'll have three options:

   - Users can use preview features for My Apps.
   - Users can use the combined security information experience.
   - Administrators can access My Staff.

    For now, set the **Users can use the combined security information experience** to **All**.

    :::image type="content" source="../media/active-directory-user-features.png" alt-text="Screenshot of the User features screen.":::

    > [!NOTE]
    > Your tenant might already have this enabled by default. If that is the case, you can close the page.

1. If you made a change, select **Save**.

You've now allowed your users to explore other authentication methods.

### Enable passwordless phone sign-in using Azure Active Directory

Finally, to use an authenticator, you must configure the security authentication methods.

1. In the Azure Active Directory admin center, in the left navigation, select **Azure Active Directory**.
1. In the **Contoso | Overview** pane, under **Manage**, select **Security**.
1. In the **Security | Getting started** pane, under **Manage**, select **Authentication methods**.
1. In the **Authentication methods | Policies** pane, under **Method**, select **Microsoft Authenticator**.
1. On the **Microsoft Authenticator settings** page, on the **Basics** tab, under **ENABLE**, select **Yes**.
1. Under **Target**, verify **All users** is selected.
1. Under **Name**, to the right of **All users**, select the ellipsis (**...**) and then select **Configure**.
1. In the **Configure** pane, select the **Authentication mode** menu.
1. Review the available options, select **Any**, and then select **Done**.
1. On the **Microsoft Authenticator settings** page, select **Save**.

## Interactive guide

In this interactive guide, you'll see how to create and deploy a security policy to a cloud-managed Surface device. To start the interactive, select the image below, and it will open in a new browser tab. When you've completed the interactive guide, close the interactive guide tab and you'll be returned here.

[![Interactive guide](../media/interactive-placeholder-image.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/manage-surface-across-the-device-lifecycle/a18-lp01m03-manage-and-secure-surface-devices/index.html?azure-portal=true)
