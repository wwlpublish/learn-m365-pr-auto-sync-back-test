Endpoint data loss prevention (Endpoint DLP) extends the activity monitoring and protection capabilities of DLP to sensitive items on Windows devices. Once devices are onboarded into the Microsoft 365 compliance center, the information about what activities (like copying to USB devices or printing) users perform on sensitive items is visible to those who have access to activity explorer in the Microsoft 365 compliance center. You can also take the extra step of auditing or restricting those activities via data loss prevention policies.

This unit walks you through the additional steps required to use Endpoint DLP:

1. Confirm your devices meet requirements
2. Onboard devices
3. Configure global Endpoint DLP settings

## Confirm devices meet requirements

Windows devices that you plan on monitoring with Endpoint DLP must meet the system requirements. Review the [requirements](/microsoft-365/compliance/endpoint-dlp-getting-started#prepare-your-endpoints) before you onboard devices.

## Onboard devices

Before you can include Windows devices in DLP policies, you need to *onboard* them, or enable data collection.

To enable data collection from a device, the account onboarding the device must be a member of any of these roles:

- Global admin
- Security admin
- Compliance admin

Use the following steps to add an account to a role:

1. In the Microsoft 365 admin center, select **Roles**.
2. In the **Azure AD** tab, select **Show all roles**.
3. Select one of the roles and add the user account.

Give users only the access they need by assigning the least-permissive role.

### Onboarding options

Onboarding and offboarding are handled via scripts you download from the **Device onboarding** center. The center has custom scripts for each of these deployment methods:

- Local script (up to 10 machines)
- Group policy
- Microsoft Endpoint Configuration Manager
- Mobile Device Management/Microsoft Intune
- VDI onboarding scripts for non-persistent machines

In the Microsoft 365 compliance center, select **Settings**, then select **Device Onboarding** to view a list of monitored devices and download the packages used to onboard or offboard devices using your preferred deployment method.

:::image type="content" source="../media/device-onboarding.png" alt-text="Screenshot shows the Device Onboarding page with the Local script selected as the deployment method." lightbox="../media/device-onboarding.png":::

### Onboarding using local script

We'll use the *Local script (for up to 10 machines)* script to onboard devices. The local script is meant for testing purposes - you can see how Endpoint DLP will affect your devices and environments before you roll it out in your production environment.

Here are the instructions for onboarding a Windows device using a local script.

1. On the **Device onboarding** page in the compliance center, select **Onboarding**.
2. Select **Local script (for up to 10 machines)** under **Deployment method**.
3. Select **Download package**, and then save the DeviceComplianceOnboardingPackage.zip file.
4. Extract the DeviceComplianceOnboardingPackage.zip file to a location accessible from the device you want to onboard, like a network share or the local device's Desktop. (You may need to bypass any messages or errors stating that downloading the file may harm your device and is not safe.)
5. In the Windows Explorer or wherever you extracted the files, right-click **DeviceComplianceLocalOnboardingScript.cmd**, then select **Run as Administrator**.
6. If a **User Account Control** window appears, select **Yes**.
7. Follow the prompts on the screen to onboard the device.

## Configure global Endpoint DLP settings

Global Endpoint DLP settings apply to all existing and new DLP policies that protect content on Windows devices. But these settings only apply to content impacted by DLP policies, not every item in, for example, the user's Documents folder.

In the Microsoft 365 compliance center left menu, go to **Data loss prevention** > **Endpoint DLP settings** to configure global settings.

Here are the settings available to you:

- **File path exclusions**: Exclude specific paths from DLP monitoring, alerting, and policy enforcement. Use the setting for file paths that are too active or that don't contain files you want to protect. You can use wildcards, system variables, and other options to refine which file paths you include or exclude. You can see in the following image an exclusion for the `C:\Temp` folder and all subfolders. All other folders on the device will be monitored.

   :::image type="content" source="../media/file-path-exclusions.png" alt-text="Screenshot shows the File Path exclusions part of the Endpoint DLP settings page." lightbox="../media/file-path-exclusions.png":::
  
- **Unallowed apps**: Prevent specific applications from accessing files protected by your policies. You can use the **Access by unallowed apps** setting to define what happens when one of your users tries to access protected data by using one of the specified apps. You can choose to allow the activity, allow but audit, block, or block the activity but let the user override the restriction. In this example, we've blocked Microsoft WordPad from opening any file that is protected by DLP policy. Other apps, like Microsoft Word, can open the same file.

   :::image type="content" source="../media/unallowed-apps.png" alt-text="Screenshot shows the Unallowed apps part of the Endpoint DLP settings page." lightbox="../media/unallowed-apps.png":::

  The following image shows a notification a user will see when they try to access the data with WordPad. The app isn't entirely blocked, so the user can select **Allow** to override the policy.

   :::image type="content" source="../media/unallowed-apps-allow.png" alt-text="Screenshot shows the notification a user will see for a blocked app when they can override the block." lightbox="../media/unallowed-apps-allow.png":::

- **Unallowed browsers**: Prevent browsers from accessing files protected by your policies. When you configure this setting, users will be prompted to access protected files using Microsoft Edge. You can block any of the 10 browsers included in the policy, or you can add your own. Although you can block a single browser, consider blocking all web browsers that do not respect Endpoint DLP policies.

   The image below shows the notification the user will receive if they try to upload protected content using a blocked browser. Notice the suggestion to access the file using Microsoft Edge.

   :::image type="content" source="../media/blocked-browser.png" alt-text="Screenshot shows the notification a user sees if they try to upload protected content with a blocked browser." lightbox="../media/blocked-browser.png":::

- **Service domain restrictions**: Even if you've prevented all unsupported browsers from accessing sensitive data, sometimes you might also want to block supported browsers, like Microsoft Edge, from uploading protected content to specific web services. Service domain restrictions control whether sensitive files protected by your policies are allowed or blocked from accessing specific service domains from Microsoft Edge. Choose *Block* to prevent certain domains from accessing these files or *Allow* to specify safe domains. For example, the setting in the image below blocks users from uploading protected content to Dropbox even when using Microsoft Edge.

   :::image type="content" source="../media/block-service-domains.png" alt-text="Screenshot shows the Service domains window with www.dropbox.com listed as a blocked service domain." lightbox="../media/block-service-domains.png":::

   This is the notification that a user gets when they try to upload  protected content into Dropbox. Notice that the user can override the restriction because the policy was configured with the option to allow override. The policy could as easily have been configured to prevent it from being overridden.

   :::image type="content" source="../media/dropbox.png" alt-text="Screenshot shows a Microsoft Edge window with a notification window displayed. The notification tells the user that they can't upload the data they are trying to upload." lightbox="../media/dropbox.png":::

   >[!NOTE]
   > Unless you've added other browsers to the **Unallowed browsers** list, user can still upload the protected content by using a different browser. Be sure to add the other browsers in use in your organization to the unallowed browsers list if you want service domain restrictions to work correctly.

## Learn more

- [Learn about Microsoft 365 Endpoint data loss prevention | Microsoft Docs](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Get started with Endpoint data loss prevention | Microsoft Docs](/microsoft-365/compliance/endpoint-dlp-getting-started)
- [Using Endpoint data loss prevention | Microsoft Docs](/microsoft-365/compliance/endpoint-dlp-using)
- [Data loss prevention device onboarding | Microsoft Docs](/microsoft-365/compliance/device-onboarding)
