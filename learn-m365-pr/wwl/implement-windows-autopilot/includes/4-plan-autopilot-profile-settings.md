Windows Autopilot profiles control how Windows is installed on user devices. Profiles contain settings that are automatically set, and optional settings that must be manually set. If an organization [created a device group](/mem/autopilot/enrollment-autopilot?azure-portal=true), it can apply a Windows Autopilot deployment profile to each device in the group. Deployment profiles determine the deployment mode. They can also customize the out of box experience (OOBE) for an organization's end users.

### Automatically set options

The following table identifies the Autopilot settings that are automatically set.

| **Setting**                                               | **Description**                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Skip Cortana, OneDrive, and OEM registration<br>          | Skips the installation of consumer apps like Cortana and personal OneDrive. The device user can install these apps at a later time, as long as the user is a local admin on the device. The original manufacturer (OEM) registration is skipped because the device will be managed by Microsoft 365 Business Premium.<br> |
| Sign in experience with your company brand<br>            | If your company has an "[Add your company branding to Microsoft 365 Sign In page](/microsoft-365/admin/setup/customize-sign-in-page?azure-portal=true)," the device user will get that experience when signing in.<br>                                                                          |
| MDM auto-enrollment with configured Azure AD accounts<br> | The user identity will be managed by Azure Active Directory. Users will sign in to Windows and Microsoft 365 with their Microsoft 365 Business Premium credentials.<br>                                                                                                                                                   |

### Manually set options

The following table identifies the optional settings that must be manually set.

| **Setting**                                        | **Description**                                                                                                                      |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Skip privacy settings (Off by default)<br>         | If this option is set to On, the device user won't see the license agreement for the device and Windows when they first sign in.<br> |
| Don't allow the user to become the local admin<br> | If this option is set to On, the device user can't install any personal apps, such as Cortana.<br>                                   |

### Create an Autopilot deployment profile

Autopilot deployment profiles are used to configure the Autopilot devices. An organization can create up to 350 profiles per tenant.

1.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane.
2.  On the **Devices \| Overview** page, in the middle navigation pane under the **By platform** section, select **Window**s.
3.  On the **Windows \| Windows devices** page, in the middle navigation pane, select **Windows enrollment**.
4.  On the **Windows \| Windows enrollment** page, under the **Windows Autopilot Deployment Program** section, select **Deployment Profiles**.
5.  On the **Windows Autopilot deployment profiles** page, select the **+Create profile** option on the menu bar. In the drop-down menu that appears, select **Windows PC**. When you select this option, the **Create profile** wizard begins.
6.  On the **Basics** page, enter a **Name** and optional **Description**.
    
    :::image type="content" source="../media/create-autopilot-profile-basics-page-96b663fe.png" alt-text="Screenshot of the Create Profile wizard showing the Basics page for entering the profile name and description.":::
    
7.  If you want all devices in the assigned groups to automatically convert to Autopilot, set the **Convert all targeted devices to Autopilot** option to **Yes**. By doing so:
     -  All corporate owned, non-Autopilot devices in assigned groups will register with the Autopilot deployment service.
     -  Personally owned devices won't be converted to Autopilot.Allow 48 hours for the registration to be processed. When the device is unenrolled and reset, Autopilot will enroll it. After a device is registered in this way, disabling this option or removing the profile assignment won't remove the device from the Autopilot deployment service. You must instead [remove the device directly](/mem/autopilot/add-devices#delete-autopilot-devices?azure-portal=true).
    
    > [!NOTE]
    > Converting all targeted devices to Autopilot isn't supported for transforming a hybrid Azure AD device into an Azure AD Autopilot device.
8.  Select **Nex**t.
9.  On the **Out-of-box experience (OOBE)** page, select the **Deployment mode** field. In the drop-down menu that appears, select one of the following options:
     -  **User-driven**. Devices with this profile are associated with the user enrolling the device. User credentials are required to enroll the device.
     -  **Self-deploying (preview)**. Requires Windows 10, version 1809 or later. Devices with this profile aren't associated with the user enrolling the device. User credentials aren't required to enroll the device. When a device has no user associated with it, user-based compliance policies don't apply to it. When self-deploying mode is used, only compliance policies targeting the device will be applied.
    
        > [!NOTE]
        > Options that appear dimmed or shaded are currently not supported by the selected deployment mode.
10. In the **Join to Azure AD as** field, select **Azure AD joined**.
11. In the remaining fields on the **Out-of-box experience (OOBE)** page, configure the following options:
     -  **Microsoft Software License Terms**. Required Windows 10, version 1709 or later. Select whether to show the end-user license agreement (EULA) to users.
     -  **Privacy settings.** Select whether to show privacy settings to users.
     -  **Hide change account options**. Requires Windows 10, version 1809 or later. Select whether to show the change account options on the company sign-in and domain error pages. This option requires [company branding to be configured in Azure Active Directory](/azure/active-directory/fundamentals/customize-branding?azure-portal=true).
     -  **User account type**. Select the user's account type (**Administrator** or **Standard** user). The user joining the device can be a local Administrator by adding them to the local Admin group. The user can't be enabled as the default administrator on the device.
     -  **Allow pre-provisioned deployment**. Requires Windows 10, version 1903 or later. Select **Yes** to allow pre-provisioning support.
        
        > [!NOTE]
        > The white glove feature has been renamed to pre-provision. References to White Glove OOBE in Intune refer to the Autopilot [pre-provisioning](/mem/autopilot/pre-provision?azure-portal=true) process. When setting this option to No (blocking pre-provisioning), you can still press the Windows key five times during OOBE to invoke pre-provisioning and progress down that path. However, Intune will later enforce this setting and you'll encounter a red screen indicating pre-provisioning failure with error code 0x80180005.
     -  **Language (Region)**. Choose the language to use for the device. This option is available in all **Deployment modes** starting with Windows 10 version 2004.
     -  **Automatically configure keyboard**. If a **Language (Region)** is selected, select **Yes** to skip the keyboard selection page. This option is available in all **Deployment modes** starting with Windows 10 version 2004.
        
        > [!NOTE]
        > Language and keyboard settings requires ethernet connectivity. Wi-fi connectivity isn't supported because of the requirement to choose a language, locale, and keyboard to make that Wi-fi connection.
     -  **Apply device name template**. Requires Windows 10, version 1809 or later, and Azure AD join type. Select **Yes** to create a template to use when naming a device during enrollment. Names must be 15 characters or less, and can have letters, numbers, and hyphens. Names can't be all numbers. Use the [%SERIAL% macro](/windows/client-management/mdm/accounts-csp?azure-portal=true) to add a hardware-specific serial number. Or, use the [%RAND:x% macro](/windows/client-management/mdm/accounts-csp?azure-portal=true) to add a random string of numbers, where x equals the number of digits to add. You can only provide a prefix for hybrid devices in a [domain join profile](/mem/autopilot/windows-autopilot-hybrid#create-and-assign-a-domain-join-profile?azure-portal=true).
12. Select **Next**.
13. On the **Assignments** page, you can select whether to include or exclude groups of devices in this profile.
    
    :::image type="content" source="../media/create-autopilot-profile-assignments-page-5b8a6b24.png" alt-text="Screenshot of the Create Profile wizard showing the Assignments page.":::
    
14. If you want to include all devices on this profile, select **+Add all devices** under the **Included groups** section.
15. If you want to include specific groups of devices on this profile:
    1.  Select **Add groups** under the **Included groups** section.
    2.  On the **Select groups to include** pane that appears, select the groups you want to include in this profile and then select the **Select** button.
16. If you want to exclude specific groups of devices from this profile:
    1.  Select **+Add groups** under the **Excluded groups** section.
    2.  On the **Select groups to exclude** pane that appears, select the groups you want to exclude in this profile and then select the **Select** button.
17. Select **Next**.
18. On the **Review + create** page, select the **Create** button to create the profile.
    
    :::image type="content" source="../media/create-autopilot-profile-create-review-page-2929a5ff.png" alt-text="Screenshot of the Create Profile wizard showing the Create and Review page.":::
    

> [!NOTE]
> Intune will periodically check for new devices in the assigned groups. It will then begin the process of assigning profiles to those devices. This process can take several minutes to complete. Before deploying a device, verify this process has completed. You can check under **Devices** &gt; **Windows** &gt; **Windows enrollment** &gt; **Devices** (under **Windows Autopilot Deployment Program,** where you should see the profile status change from **Unassigned** to **Assigning** and finally to **Assigned**.
