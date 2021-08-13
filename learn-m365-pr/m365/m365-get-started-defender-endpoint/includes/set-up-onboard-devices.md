There are different tools that you can use to onboard your organization's devices to Microsoft Defender for Endpoint based on your architecture needs. These tools include Microsoft Endpoint Manager, Microsoft Endpoint Configuration Manager, Group Policy, and more. As the security analyst, you're aware that your organization is using Microsoft Endpoint Manager to manage all of its devices. So, you'll learn how you can onboard your pilot devices using Microsoft Endpoint Manager.

## Set up a Microsoft Defender for Endpoint instance

Because Microsoft Defender for Endpoint is part of the Microsoft 365 Defender suite, an instance is created for Microsoft Defender for Endpoint when setting up Microsoft 365 Defender.

It works like this:

1. Microsoft 365 Defender onboarding is triggered automatically by the first user (who has the appropriate permissions) when they select any navigation pane item for Microsoft 365 Defender in the Microsoft 365 Defender portal.
1. This triggers the provisioning steps needed to set up Microsoft 365 Defender including a Microsoft Defender for Endpoint instance.

The process takes approximately two minutes.

## Connect Microsoft Defender for Endpoint with Microsoft Endpoint Manager

Before you start to onboard your devices, connect Microsoft Endpoint Manager with Microsoft Defender for Endpoint. The steps for how to do this are being updated at the time of writing. For the latest guidance, use the **Configure Microsoft Defender for Endpoint in Intune** link in the **Learn more** section of this unit.

## Use Microsoft Endpoint Manager to onboard devices

The deployment process using Microsoft Endpoint Manager consists of the following steps:

1. Create a group in Microsoft Endpoint Manager to assign configurations to target devices or users
1. Configure Microsoft Defender for Endpoint capabilities that you'll need using Microsoft Endpoint Manager.
1. Verify that your configuration policies for capabilities have been applied.

### Step 1: Create a group in Microsoft Endpoint Manager

You'll create a group for your pilot devices and users to apply configurations. You do this using the Microsoft Endpoint Manager portal:

:::image type="content" source="../media/4-navigate-groups-intune.png" alt-text="Screenshot showing the Microsoft Endpoint manager, and how to go to the Groups pane." lightbox="../media/4-navigate-groups-intune.png":::

### Step 2: Configure capabilities

You also need to configure the Microsoft Defender for Endpoint capabilities your organization is going to need. You configure the capabilities by creating a configuration policy profile for each capability separately using Microsoft Endpoint Manager. You configure the capabilities in the following order:

1. Configure endpoint detection and response
1. Configure next-generation protection
1. Configure attack surface reduction

#### Create configuration policy profiles for your capabilities

You configure the capabilities using Microsoft 365 Defender portal. You use the same general process when you're configuring endpoint detection and response, next-generation protection, or attack surface reduction. The configuration settings you select will be different depending on the capability you want to configure.

For example, to configure the endpoint detection and response capability, you create a policy profile for it to apply to your devices in Microsoft Endpoint Manager using the **Endpoint detection and response** pane in the portal:

:::image type="content" source="../media/4-create-endpoint-detection-response-profile.png" alt-text="Create a profile for endpoint detection and response." lightbox="../media/4-create-endpoint-detection-response-profile.png":::

You can use the Onboarding using Microsoft Endpoint Manager link in the **Learn more** section for detailed in-depth guidance on how create configuration policy profiles.

### Step 3: Verify that policies have been applied

Once you've created a profile, you'll confirm whether it has been applied to your pilot devices. You do this by selecting the profile you've created. For example, you can select the profile you've created for next-generation protection in the **Antivirus** pane:

:::image type="content" source="../media/4-next-generation-protection-profile-created.png" alt-text="Screenshot showing the Endpoint security, and how to select your profile." lightbox="../media/4-next-generation-protection-profile-created.png":::

> [!NOTE]
> It might take some time for your configuration policy to be applied.

You'll be taken to the policy profile overview pane:

:::image type="content" source="../media/4-profile-overview-pane.png" alt-text="Screenshot showing the Endpoint Manager admin center and the profile overview pane." lightbox="../media/4-profile-overview-pane.png":::

Here, you can check whether the profile has been applied successfully at multiple levels. For example, to check which devices it has been applied to successfully, you can select **Device status**:

:::image type="content" source="../media/4-profile-device-status.png" alt-text="Screenshot showing how to get to the Device status." lightbox="../media/4-profile-device-status.png":::

If the **Assignment status** shows as **Succeeded**, then that device has been onboarded successfully.

## Learn more

- [Configure Microsoft Defender for Endpoint in Microsoft Endpoint Manager](/mem/intune/protect/advanced-threat-protection-configure)
- [Onboarding using Microsoft Endpoint Manager](/microsoft-365/security/defender-endpoint/onboarding-endpoint-manager)
- [Full deployment](/microsoft-365/security/defender-endpoint/deployment-rings?view=o365-worldwide#full-deployment&preserve-view=true)
