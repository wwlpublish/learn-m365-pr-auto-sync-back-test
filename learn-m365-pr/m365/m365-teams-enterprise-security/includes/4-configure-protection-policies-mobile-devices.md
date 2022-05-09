An app protection policy is a collection of rules that govern how data, assets, and resources are accessed.  Typically, an app protection policy is applied to a specific application to govern how the app will interact with your organizations data.

In an ideal world, an app protection policy would be applied to a device managed by your IT department that is either enrolled in Microsoft Intune, or through a third-party Mobile device management (MDM) solution.  However, there is a trend towards employees using their own devices, typically called bring your own device (BYOD) which aren't managed or enrolled with Microsoft Intune or a MDM solution.  App protection policies can be applied to managed/enrolled and BYOD devices.

### Benefits of using app protection policies

Application protection policies provide a number of essential benefits:

- Protecting your company data at the app level.
- End-user productivity isn't affected and polices don't apply when using the app in a personal context.
- App protection policies make sure that the app-layer protections are in place.
- MDM, in addition to MAM, makes sure that the devise is protected.

The app protection policy organizes data protection into three distinct levels, each building on the elements in the previous framework:

#### Enterprise basic data protection (level 1)

This is an entry level configuration and makes sure that all apps are protected with a PIN and all data is encrypted. It also gives selective wipe operations.

#### Enterprise enhanced data protection (level 2)

This configuration is the most applicable to mobile users who access work data as it introduces a minimum operating system requirement, and data leak prevention mechanisms.

#### Enterprise high data protection (level 3)

This level of configuration is applied for users that are accessing high risk data.  It introduces app protection policy Mobile Threat Defense, enhanced PIN config, and advanced data protection mechanisms.

### Create a mobile app protection policy

To create an app protection policy for your apps, you'll need to follow a modern Intune process that'll result in a new app protection policy.

1. Sign into the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/), the select **Intune portal**.
1. In the **Intune portal**, choose **Apps** > **App protection policies**. This selection opens the **App protection policies details**, where you create new policies and edit existing policies.
1. Select **Create policy** and select either **iOS/iPadOS** or **Android**. The **Create policy** pane is displayed.
1. On the **Basics** page, add the name of this app protection policy and add the description. The **Platform** value is set based on your above choice.

    :::image type="content" border="false" source="../media/4-create-policy.png" alt-text="Screenshot of the Create policy page."  lightbox="../media/4-create-policy.png":::

1. Select **Next** to display the **Apps** page.
The **Apps** page allows you to choose how you want to apply this policy to apps on different devices. You must add at least one app.

    > [!NOTE]
    > Organizations can add multiple apps that can be governed by a single policy. For example, Teams, SharePoint, Outlook, and OneDrive are commonly managed Microsoft apps that can share a single app protection policy.

1. Select **Next** to display the Data protection page.
This page provides settings for data loss prevention (DLP) controls, including cut, copy, paste, and save-as restrictions. These settings determine how users interact with data in the apps that this app protection policy applies.
1. Select **Next** to display the **Access requirements** page.
This page provides settings to allow you to configure the PIN and credential requirements that users must meet to access apps in a work context.
1. Select **Next** to display the **Conditional launch** page.
This page provides settings to set the sign-in security requirements for your app protection policy. Select a **Setting** and enter the **Value** that users must meet to sign in to your company app. Then select the **Action** you want to take if users do not meet your requirements. In some cases, multiple actions can be configured for a single setting.
1. Select **Next** to display the Assignments page.
The Assignments page allows you to assign the app protection policy to groups of users. You must apply the policy to a group of users to have the policy take effect.
1. Select **Next**: Review + create to review the values and settings you entered for this app protection policy.
1. When you are done, select **Create** to create the app protection policy in Intune.

## Learn more

- [App Protection Policy]( /mem/intune/apps/app-protection-policies)
- [Intune supported applications]( /mem/intune/apps/apps-supported-intune-apps)
