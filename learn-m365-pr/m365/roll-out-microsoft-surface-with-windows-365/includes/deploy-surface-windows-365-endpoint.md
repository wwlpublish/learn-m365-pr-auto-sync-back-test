A Surface device provides a consistent out-of-box experience (OOBE) and integrates automatically with Microsoft Endpoint Manager. This seamless integration enables the device to be delivered directly from the factory and automatically provisioned when it is first turned on.

In this unit, you'll learn about the provisioning and deployment process of a Surface device from the factory to the user. You'll see how to provision a Windows 365 Cloud PC for your users, how to assign a Cloud PC license to a user, and how they can access it from their device. Finally, you can follow our interactive guide to create and deploy a cloud configuration profile using a Microsoft Endpoint Manager guided scenario.

## How to take a Surface device from factory to user with Windows Autopilot

Windows Autopilot, accessed via Microsoft Endpoint Management (MDM) admin center (<https://endpoint.microsoft.com>), lets you manage device policies, applications, and settings. When combined with Azure AD's identity services, it ensures users can access the applications and data they need.

Every Surface device is shipped from the factory with a clutter-free image of Windows, and a preinstalled full version of Office, ready for Autopilot configuration when turned on. At the factory, when a Surface device is allocated to the customer order, the device ID is automatically retrieved and stored in the Cloud.

There are two ways to enroll your Surface device, depending on how you ordered it. If you use a third-party Cloud Solution Provider (CSP), they'll take responsibility for the enrollment of the devices as soon as they're shipped from the factory. Or, if your IT department manages the order process, they'll make sure the devices are enrolled on your tenant. However, the process for both is the same. When the Surface devices are shipped from the factory, the device ID, type, and serial number are retrieved from Microsoft's cloud servers using Electronic Data Interface (EDI). This data is then used to enroll each Surface device into your tenant.

The IT department can use either the Azure AD portal or Microsoft Endpoint Manager admin center to create profiles that deploy the correct applications, policies, and settings to the Surface device when it's first used. This enables a zero-touch provisioning approach, which gives a consistent user experience, runs automatically, and doesn't require oversight by your IT department.

When the user unpacks and turns on the Surface device for the first time, and it has connected to your network, Windows 10/11 connects to the nearest Microsoft server, where it shares its unique device ID. Microsoft's servers check this ID against any that are enrolled. After it finds a match, it lets your tenant take over the deployment.

With the handover complete, the Intune instance on your tenant automatically pushes all applications, settings, and policies to the Surface device. After completion, the user can sign in and begin using their Surface device on your corporate network.

## Provision of a Windows 365 Cloud PC

To deploy a Surface device as a Windows 365 endpoint, you first need to provision a Windows 365 device. You'll want to set up varying types of Cloud PC for different departments or user types. For instance, your R&D department might need to run complex software that requires more computing power. In contrast, your marketing team may want more storage to support their demonstrations and materials. You can provide a machine for any need, all from Microsoft Endpoint Manager.

1. To get started, open <https://endpoint.microsoft.com> using a private browser, and sign in with your tenant's admin credentials.
1. Select **Devices** from the left navigation.
1. From the **Devices | Overview** page, and then from the **Provisioning** section, select **Windows 365**.
1. From the **Devices | Windows** 365 page, select the **Provisioning Policies** tab.
1. Select **Create Policy**, to create a provisioning policy to meet your organization's needs.

    :::image type="content" source="../media/create-provisoing-policy-general.jpg" alt-text="Screenshot showing the provisioning policy general screen.":::

1. The policy needs a name and, ideally, a description. Choose how the policy joined your tenant, and select the network. Then select **Next**.
1. Select the machine you want to create for this policy type. From the list, select the required image and select **Next**.

    :::image type="content" source="../media/create-provisoing-policy-image.jpg" alt-text="Screenshot showing the provisioning policy image screen.":::

1. Select which groups this provisioning policy applies to. First, select all the groups that apply from the list. When you've selected all the groups, select **Next**.

    > [!NOTE]
    > Note that any user in the selected groups who has a Windows 365 Cloud PC license will have a Cloud PC provisioned for them.

    :::image type="content" source="../media/create-provisioning-policy-assignments.png" alt-text="Screenshot showing the provisioning policy groups to include screen.":::

1. Review the policy settings. When you're ready, select **Create**.

    :::image type="content" source="../media/create-provisioning-policy-review.png" alt-text="Screenshot showing the provisioning policy review screen.":::

1. Depending on the number of Cloud PCs that need to be provisioned in this policy, it can take from minutes to hours for the process to finish. When it's completed, you'll see it appear in the provisioning policy list.

    :::image type="content" source="../media/provisioning-policy-list.png" alt-text="Screenshot showing the provisioning policy list screen.":::

If you've previously assigned a Windows 365 Cloud license to a user, each individual in that group will automatically have a Cloud PC provisioned for them. Otherwise, you'll need to assign a Cloud PC license to each user, which we'll cover next.

## Assign a Windows 365 Cloud PC to a user

So far, you've seen how to configure and provision a Surface device using Microsoft Endpoint Manager admin center. Now you'll see how to create a Windows 365 license that can be used on a Surface device.

1. To get started, open <https://admin.microsoft.com> using a private browser, and sign in using your tenant's admin credentials.
1. From the Microsoft 365 admin center, select the **search box** and find the user you want to assign the Windows 365 license.
1. When the user has been selected, a pane will appear showing such details as their username, what groups they're in and their role. Next, select the **Licenses and apps** tab.
1. From the list of the available licenses, scroll down until you find either a Windows 365 Business or a Windows 365 Enterprise license. Select the box against the corresponding license and select **Save Changes**.
1. As soon as you've assigned the Windows 365 Cloud PC license to the user, a new Windows 365 Cloud PC will be provisioned for them, as long as they're a member of the provisioning group.

## Sign in to your Windows 365 Cloud PC from a Surface device

After you've provisioned a Windows 365 Cloud PC and assigned the user a Windows 365 license, they'll be ready to start. They'll need to sign in to the Windows 365 portal and choose how they want to access the Cloud PC.

1. To access the Windows 365 Cloud PC, open <https://windows365.microsoft.com> in your browser, and sign in with your organization's user credentials.
1. From the Windows 365 portal, you can either download Remote Desktop to your Surface device-if it hasn't already been installed-or open your Cloud PC in a browser window.

    :::image type="content" source="../media/windows-365-portal.png" alt-text="Screenshot showing the Windows 365 Portal screen.":::

    This image shows access to a Windows 10 Cloud PC through the browser, with Teams and Office preinstalled.

    :::image type="content" source="../media/windows-365-browser.png" alt-text="This image shows access to a Windows 10 Cloud PC through the browser.":::

For the best experience, you should access your Cloud PC using the remote desktop application.

## Interactive guide

In this interactive guide, you'll create and deploy a cloud configuration profile using a Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) guided scenario. Select the image to open the interactive guide in a new tab. When you've finished, close the new tab to return here.

\<\<Insert Image and Click Link to the published Interactive here>>
