Many organizations have users who prefer iPhones, iPads, and other iOS devices. You might need to ensure that your security extends to iOS devices as well by installing Microsoft Defender for Endpoint on them.

In Contoso, one division of the company, which originally was an independent graphic design agency, uses iOS devices predominantly. You want to ensure that these devices don't represent a weak point in your security.

Here, you'll learn about Microsoft Defender for Endpoint for iOS and how to deploy it in your organization.

## What is Microsoft Defender for Endpoint for iOS?

Microsoft Defender for Endpoint is an app that you can install on many different types of devices that protects that device against common threats such as viruses and insecure websites. Defender for Endpoint for iOS is the version of that product for Apple iPhones and iPads.

By deploying Defender for Endpoint to all your iOS devices, you ensure that users of those devices can't circumvent the protection you've configured for mobile devices in Microsoft Cloud App Security. For example, if an iOS user downloads a file that matches one of your indicators of compromise, it will generate an alert and can delete or quarantine the file, just as it would on a Windows computer.

> [!NOTE]
> Microsoft Defender for Endpoint for iOS is also known as Microsoft Defender ATP for iOS

## Deploying Microsoft Defender for Endpoint for iOS

Defender for Endpoint for iOS supports iOS devices that run iOS 11.0 and higher.

Any iOS user can install the Defender for Endpoint for iOS on their device from the App Store. Search in the App Store for Microsoft Defender.

If you have Microsoft Intune in your organization, and the iOS devices are enrolled in Intune, administrators can use it to deploy Defender for Endpoint to all iOS devices automatically. Follow these steps:

1. In the Microsoft Endpoint manager admin center, navigate to **Apps > iOS/iPadOS > Add**.
1. Select **iOS store** app.

    :::image type="content" source="../media/04-install-ios-app.png" alt-text="A screenshot of the Microsoft Endpoint manager admin center showing how to push an iOS app to iOS devices.":::

1. In the **Add app** page, search for **Microsoft Defender ATP**, and then in the results select **Microsoft Defender ATP**.
1. In the **Minimum operating system** list, select **iOS 11.0**, and then select **Next**.
1. In the **Assignments** page, in the **Required** section, select a group of iOS device users, and then select **Next**.
1. On the **Review + create** page, select **Create**.
1. Intune displays the app information page. To view installations of the app, under **Monitor**, select **Device install status**.

## Configure a compliance policy against jailbroken iOS devices

A jailbroken iOS device has fewer restrictions on users. For example, on such a device, you can install apps that haven't been approved for the App Store by Apple. As such, a jailbroken iOS device presents a greater risk of insecure apps and malware. Many administrators may want to prevent such devices from accessing their systems.

To deny access to jailbroken iPhones and iPads, follow these steps:

1. In Microsoft Endpoint Manager admin center, navigate to **Devices > Compliance policies**, and then select **Create Policy**.
1. Select **iOS/iPadOS** and then select **Create**.

    :::image type="content" source="../media/04-create-policy-ios.png" alt-text="A screenshot of the Microsoft Endpoint manager admin center showing how to create a new policy for iOS devices.":::

1. Enter a name for the new policy and then select **Compliance settings**.
1. In the **Device Health** section, next to **Jailbroken devices**, select **Block**, and then select **Next**.

    :::image type="content" source="../media/04-block-jailbroken-ios-devices.png" alt-text="A screenshot of the Microsoft Endpoint manager policy editor showing how to block jailbroken iOS devices.":::

1. In the **Actions for noncompliance** page, select the actions you want to take when the system detects a jailbroken device and then select **Next**.
1. In the **Assignments** page, select the user groups that you want the policy to apply to and then select **Next**.
1. To complete the new policy, select **Create**.
