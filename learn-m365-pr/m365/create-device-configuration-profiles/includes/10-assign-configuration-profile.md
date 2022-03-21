You create a profile, and it includes all the settings you entered. The next step is to deploy or "assign" the profile to your user or device groups. When it's assigned, the users and devices receive your profile, and the settings you entered are applied.

## Assign a device profile

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles**. All the profiles are listed.
3. Select the profile you want to assign > **Properties** > **Assignments** > **Edit**.

4. Select **Included groups** or **Excluded groups**, and then choose **Select groups to include**. When you select your groups, you're choosing an Azure AD group. To select multiple groups, hold down the **Ctrl** key, and select your groups.

5. Select **Review + Save**. This step doesn't assign your profile.
6. Select **Save**. When you save, your profile is assigned. Your groups will receive your profile settings when the devices check in with the Intune service.

## Use scope tags or applicability rules

When you create or update a profile, you can also add scope tags and applicability rules to the profile.

**Scope tags** are a great way to filter profiles to specific groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. [Use RBAC and scope tags for distributed IT](/mem/intune/fundamentals/scope-tags) has more information.

On Windows 10/11 devices, you can add **applicability rules** so the profile only applies to a specific OS version or a specific Windows edition. [Applicability rules](/mem/intune/configuration/device-profile-create#applicability-rules) has more information.

## User groups vs. device groups

Many users ask when to use user groups and when to use device groups. The answer depends on your goal. Here's some guidance to get you started.

### Device groups

If you want to apply settings on a device, regardless of who's signed in, then assign your profiles to a devices group. Settings applied to device groups always go with the device, not the user.

For example:

- Device groups are useful for managing devices that don't have a dedicated user. For example, you have devices that print tickets, scan inventory, are shared by shift workers, are assigned to a specific warehouse, and so on. Put these devices in a devices group, and assign your profiles to this devices group.

- You create a [Device Firmware Configuration Interface (DFCI) Intune profile/mem/intune/configuration/device-firmware-configuration-interface-windows) that updates settings in the BIOS. For example, you configure this profile to disable the device camera, or lock down the boot options to prevent users from booting up another OS. This profile is a good scenario to assign to a devices group.

- On some specific Windows devices, you always want to control some Microsoft Edge settings, regardless of who's using the device. For example, you want to block all downloads, limit all cookies to the current browsing session, and delete the browsing history. For this scenario, put these specific Windows devices in a devices group. Then, create an [Administrative Template in Intune](/mem/intune/configuration/administrative-templates-windows), add these device settings, and then assign this profile to the devices group.

To summarize, use device groups when you don't care who's signed in on the device, or if anyone signs in. You want your settings to always be on the device.

### User groups

Profile settings applied to user groups always go with the user, and go with the user when signed in to their many devices. It's normal for users to have many devices, such as a Surface Pro for work, and a personal iOS/iPadOS device. And, it's normal for a person to access email and other organization resources from these devices.

If a user has multiple devices on the same platform, then you can use [filters](/mem/intune/fundamentals/filters) on the group assignment. For example, a user has a personal iOS/iPadOS device, and an organization-owned iOS/iPadOS. When you assign a policy for that user, you can use [filters](/mem/intune/fundamentals/filters) to target only the organization-owned device.

Follow this general rule: If a feature belongs to a user, such as email or user certificates, then assign to user groups.

For example:

- You want to put a Help Desk icon for all users on all their devices. In this scenario, put these users in a users group, and assign your Help Desk icon profile to this users group.
- A user receives a new organization-owned device. The user signs in to the device with their domain account. The device is automatically registered in Azure AD, and automatically managed by Intune. This profile is a good scenario to assign to a users group.
- Whenever a user signs in to a device, you want to control features in apps, such as OneDrive or Office. In this scenario, assign your OneDrive or Office profile settings to a users group.

  For example, you want to block untrusted ActiveX controls in your Office apps. You can create an [Administrative Template in Intune](/mem/intune/configuration/administrative-templates-windows), configure this setting, and then assign this profile to a users group.

To summarize, use user groups when you want your settings and rules to always go with the user, whatever device they use. 

## Exclude groups from a profile assignment

Intune device configuration profiles let you include and exclude groups from profile assignment.

As a best practice:

- Create and assign profiles specifically for your user groups. Use [filters](/mem/intune/fundamentals/filters) to include or exclude devices of those users.
- Create and assign different profiles specifically for your device groups.

For more information on groups, see [Add groups to organize users and devices](/mem/intune/fundamentals/groups-add).