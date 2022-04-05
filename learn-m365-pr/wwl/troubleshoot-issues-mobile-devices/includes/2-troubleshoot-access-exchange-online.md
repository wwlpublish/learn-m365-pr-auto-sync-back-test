It's a rare organization whose users don't require mobile device access to email and their schedules. Consequently, Exchange Online engineers must understand the issues around mobile device connectivity, and how to troubleshoot that connectivity.

## Verify settings for email apps

If a user can't connect their mobile device, one very simple thing to check before anything else is that a particular mobile feature or protocol (an *email app*) hasn't been disabled for a specific user. In the **Exchange admin center**, select the appropriate user mailbox, and then select **Manage email apps** settings. Ensure that the required access is enabled, as displayed in the following screenshot.

:::image type="content" source="../media/check-email-apps.png" alt-text="A screenshot displays the Manage settings for email apps blade in Exchange admin center. All apps are enabled. ":::

You can also use Exchange Online PowerShell to change these settings. For example, the following command blocks Outlook on the web, Exchange ActiveSync, and POP3:

``` powershell
Set-CASMailbox "AlexW" -OWAEnabled $false -PopEnabled $false -ActiveSyncEnabled $false
```

> [!NOTE]
> The preceding procedure assumes that you've already installed the Exchange Online PowerShell module and connected to your Exchange Online environment. 

Assuming the user has the required email apps enabled, and they're still experiencing connectivity issues, you should perform further investigation.

> [!TIP]
> You can review other options for this cmdlet here: [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

## Troubleshoot mobile device access

If a user can't connect to Exchange Online from their mobile device, you must be able to determine why, and then resolve the problem. When users attempt to connect, their connection attempt is compared with settings in a number of locations, including:

- Device mailbox policies
- Device Access Rules
- Azure AD Conditional Access policies

### Review mobile device mailbox policies

You can configure mobile device mailbox policies to secure your users' devices when connecting to Exchange Online. Settings apply to iOS and Android devices. These settings include:

- Require a password
- Specify the minimum password length
- Allow a numeric PIN or require special characters in the password
- Designate how long a device can be inactive before requiring the user to re-enter a password
- Wipe a device after a specific number of failed password attempts

If you have access to the Classic Exchange admin center, you can review the current policies:

1. Select **mobile** in the navigation pane.
1. In details, click the **mobile device mailbox policies** tab.
1. Select the required policy and click **Edit** to review or update the settings.
1. Click **Save** if you make changes you want to retain.

> [!TIP]
> A default policy exists. There are no security settings configured in the default policy. 

You can also use Exchange Online PowerShell to review and assign the configured policies. In fact, using PowerShell is recommended because the Classic Exchange admin center only enables you to configure a subset of available settings.

> [!NOTE]
> If necessary, install the Exchange Online PowerShell module and connect to your Exchange Online environment. 

To review available policies, use the `Get-MobileDeviceMailboxPolicy` cmdlet. After you've checked the requirements of any assigned policy, you can advise the user to reconfigure their device security settings to match.

> [!TIP]
> If the device is enrolled in Microsoft Intune, and the user has an Enterprise Mobility + Security license, you can manage the user's device using Configuration profiles, including settings that control security. It's also possible to create App Protection policies that can help manage these settings, even when devices aren't enrolled in MDM. 

### Review Device Access Rules

If device mailbox policies aren't the issue, then you can review Device Access Rules. These rules are used to limit device connectivity. By default, no such rules exist. To review configured rules, use the `Get-ActiveSyncDeviceAccessRule` cmdlet. If you want to verify that there are no rules in place that will block iOS and Android devices, run the following command:

``` powershell
Get-ActiveSyncDeviceAccessRule | Where-Object { $_.AccessLevel -eq "Block" -and $_.QueryString -like "Outlook*" } | Format-Table Name, AccessLevel, QueryString -AutoSize
```

If any rules are listed in the output, you must review and, if necessary, edit the settings in those rules to enable access. You can use the `Set-ActiveSyncDeviceAccessRule` cmdlet to makes changes.

## Review mobile device access states and device statistics

It's also possible to review information that relates to a user's specific devices. This technique is particularly useful when a device is blocked. You can use the following PowerShell cmdlets:

- **Get-Mobiledevice**. Retrieves the list of devices in your organization that have active partnerships for the specified user or users.
- **Get-MobiledeviceStatistics**. Retrieves the list of mobile devices configured to synchronize with a specified user's mailbox and return a list of statistics about those devices.

For example, the following command retrieves device information for the user AlexW and formats the output in a selective table displaying device operating system, client app type, device access state, and device access state reason.

``` powershell
Get-Mobiledevice -Mailbox "AlexW" | ft DeviceOS, ClientType, DeviceAccessState, DeviceAccessStateReason
```

In this instance, all of Alex's devices have access through the global access setting, as shown in the following screenshot.

:::image type="content" source="../media/get-mobiledevice.png" alt-text="A screenshot of the output from the Get-MobileDevice cmdlet using syntax that precedes this image.":::

The following command retrieves the statistics for the smart phone that's configured to synchronize with Alex's mailbox:

``` powershell
Get-MobileDeviceStatistics -Mailbox "AlexW"
```

### Review the ABQ list to identify blocked or quarantined devices

The device access state can be Allowed, Blocked, or Quarantined (ABQ) as a result of the application of device access rules or defaults. It's usual for an administrator to start by either blocking or quarantining devices as they attempt access using a global default. Then the administrator adds additional Device Access Rules that allow access for devices that meet specific criteria. These days, Active Directory (Azure AD) Conditional Access is often used to make this latter determination (see below).

For example, if an administrator issued the following command, all mobile access defaults to quarantined:

``` powershell
Set-ActiveSyncOrganizationSettings -DefaultAccessLevel Quarantined
```

Options for default access level are Allow, Quarantine, or Block.

> [!TIP]
> You can also use the Classic Exchange admin center to configure these default settings, and to customize Quarantine notification messages. 

If some users' devices are not able to gain access, review the state of the devices by using: 

``` powershell
Get-Mobiledevice | ft UserDisplayName, DeviceOS, ClientType, DeviceAccessState, DeviceAccessStateReason`
```

You can then review the specific devices that are quarantined and, if desired, change the state to blocked or allowed by using the Classic Exchange admin center:

1. In the navigation pane, select **Mobile**.
1. In the details pane, in the **Quarantined Devices** list, click the relevant device and then click either **Allow** or **Block**.

> [!IMPORTANT]
> If you check the device access state reason again, it displays as Individual. 

It's important to understand why a device is being blocked or quarantined. It's likely an oversight of policy configuration, and you should review the rules and policies we've discussed to determine the specific cause.

### Review Azure AD Conditional Access policies

Azure AD Conditional Access enables you to provide more robust mobile device access control. It's necessary to review Azure AD Conditional Access policies. For example, if you create and configure a Conditional Access policy with the following settings, Device Access Rules are not applied to devices targeted by this Conditional Access policy. The required settings are:

- Assignments: Choose the appropriate users or groups
- Cloud apps or actions: Office 365 Exchange Online
- Conditions:

    - Device platforms: iOS and/or Android, depending on your requirements
    - Client apps: Mobile apps and desktop clients

- Access controls: Grant access, but:

    - Require device to be marked as compliant and/or
    - Require approved client app and/or
    - Require app protection policy

> [!IMPORTANT]
> Only Outlook Mobile can satisfy the two conditions.  

It's important that if you experience connectivity issues from mobile devices, you must check not only the Device Access Rules, but also Azure AD Conditional Access policies.

> [!TIP]
> Your organization requires Azure AD Premium and Microsoft Intune with Compliance policies to configure the required Conditional Access policy.

## Learn more

- [Set-CASMailbox](/powershell/module/exchange/set-casmailbox)
- [Securing Outlook for iOS and Android in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/secure-outlook-for-ios-and-android)
- [Mobile device mailbox policies in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/mobile-device-mailbox-policies)
- [Get-MobileDevice](/powershell/module/exchange/Get-MobileDevice)
- [Upcoming Exchange Online Device Access and Conditional Access changes with Outlook mobile](https://techcommunity.microsoft.com/t5/exchange-team-blog/upcoming-exchange-online-device-access-and-conditional-access/ba-p/1464261)