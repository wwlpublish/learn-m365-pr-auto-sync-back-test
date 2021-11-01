Let's examine how you can control Outlook for iOS and Android clients by using Enterprise Mobility + Security, or the built-in Microsoft Endpoint Manager (MEM) features of Microsoft 365.

## Use Enterprise Mobility + Security to manage Outlook for iOS and Android

Your Enterprise Mobility + Security subscription provides a versatile set of tools for managing mobile clients. For example, you can selectively wipe your company's data from a device, require data encryption, and block access from compromised or lost devices. This unit focuses on conditional access and app protection policies.

### Create a conditional access policy

Conditional access policies impose requirements that users and devices must satisfy before they connect to Exchange Online. You can assign different policies to different groups in your organization. This technique is useful, because more powerful administrators' accounts are targeted by attackers. It's sensible to apply stricter policies to administrative users than those for users with fewer permissions.  

To create a conditional access policy, follow these steps. In this example, the policy requires users to complete multifactor authentication:

1. In the Azure portal, go to **Azure Active Directory > Security > Conditional Access**, and then select **New Policy**.

    :::image type="content" source="../media/new-policy-conditional-access.png" alt-text="Screenshot of the Azure Active Directory showing the New Policy button.":::

1. Enter a descriptive name that will help other administrators to understand the purpose of the policy.  
1. Select **Users and groups** under **Assignments**. Add the groups to the **Include** list that you want the policy to apply to. In the **Exclude** list, add any groups that you don't want the policy to apply to. Click **Done**.  
1. Under **Cloud apps or actions > Include**, select **All cloud apps**, and then click **Done**.
1. Under **Conditions > Client apps > Configure**, select **Yes**, and then click **Done**.
1. Under **Access controls > Grant**, select **Grant access**, **require multi-factor authentication**, and then click **Select**.
1. To enable the new policy, under **Enable policy**, select **On**, and then click **Create**.

### Create an app protection policy

An app protection policy ensures that your organization's data remains secured, even when it's synchronized with a mobile device. For example, you can use app protection policies to prevent people from sharing your organization's data with other apps on the same device. You could also prevent anyone using screen capture tools to save an image of sensitive data. This could be shared with others, either deliberately or accidentally.  

In this example, you create a policy that prevents iOS devices from backing up your data or using copy and paste to transfer it to another app:

1. In **Microsoft Endpoint Manager admin center**, go to **Apps > App protection policies**, click **Create policy**, and then select **iOS/iPadOS**.

    :::image type="content" source="../media/create-app-protection-policy.png" alt-text="Screenshot of the App protection policies with the create policy button highlighted.":::

1. On the **Basics** page of the **Create Policy** wizard, enter a name and description for the policy. Use these values to make the purpose of the policy clear to other administrators. Select **Next**.

    :::image type="content" source="../media/create-policy-wizard.png" alt-text="Screenshot displaying the Create policy wizard. The Next button is highlighted." border="false":::
1. On the **Apps** page, select **Yes** next to **Target to apps on all devices**.
1. Select **All Apps** next to **Target policy to**.
1. On the **Data protection** page, select **Block** next to **Backup Org data to iTunes and iCloud backup**.
1. Select **Blocked** next to **Restrict cut, copy, and paste between other apps**, and then select **Next**.
1. Select **Next** on the **Access requirements** page and the **Conditional launch** page.
1. On the **Assignments** page, select **Next: Review + create**.
1. Click **Create**.

## Use Microsoft Endpoint Manager to manage Outlook Mobile

Microsoft Endpoint Manager (MEM) is a Microsoft 365 feature that you can use to manage mobile devices at no extra cost.  

Before you can use MEM to secure any devices, you have to activate it for Microsoft 365. Then you can create a device policy by following these steps:

1. In **Microsoft Endpoint Manager admin center**, go to **Devices > Compliance policies**.

    :::image type="content" source="../media/device-compliance-policies.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center, showing the Compliance policies.":::

1. Select **Create a policy**, then select the platform. For example, **iOS/iPadOS**.
1. Select **Create**.
1. Specify your security requirements on the **iOS compliance policy** page.

    :::image type="content" source="../media/create-device-protection-policy.png" alt-text="Screenshot of the Create device policy options.":::

> [!NOTE]
> The settings that you apply depend on the mobile operating system you are managing. For example, you can require a password for both iOS and Android devices, but only prevent simple passwords on iOS devices.

When the policy has been created, its settings are pushed to the devices the next time they connect to Microsoft 365. If the device connects to Microsoft 365 for the first time, the user will receive a notification that explains how to enroll it.  

## Learn more

[Managing Outlook for iOS and Android in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/manage-outlook-for-ios-and-android?azure-portal=true)
