Exchange ActiveSync supports mobile device synchronization with Exchange Online. It's aimed at clients connecting over potentially high-latency and low-bandwidth networks, although that's not a requirement. Exchange ActiveSync is based on HTTP and WBXML. It enables mobile devices, such as smart phones, to access their organizational data from Microsoft Exchange. Users can even access their Exchange-based content while offline.

> [!NOTE]
> Exchange ActiveSync is enabled by default. 

## Managing mobile device access in Exchange ActiveSync

You can control which mobile devices can synchronize to Exchange Online by:

- Monitoring new mobile devices as they connect to your organization.
- Setting up rules that determine which types of mobile devices are allowed to connect.

> [!TIP]
> Regardless of which of these two methods you opt for, you can approve or deny access for any specific mobile device for a specific user at any time.

### Review Client Access Rules

You can use Client Access Rules to help control access to your Exchange Online organization. These rules use client properties or client access requests to determine access. For example, you can create a Client Access Rule that denies access to Exchange ActiveSync clients, or perhaps only denies access to those ActiveSync clients connecting from a specified IP address range. You use Exchange Online PowerShell to review and configure Client Access Rules.

> [!NOTE]
> The following procedures assume you've already installed the Exchange Online PowerShell module.

1. Open an elevated Windows PowerShell window and connect to your Exchange Online environment: `connect-exchangeonline -userprincipalname name`, where *name* is your administrative account.
1. Retrieve a list of Client Access Rules: `Get-ClientAccessRule`.
1. Review the details for rules by formatting as a list, and searching for those that include ExchangeActiveSync as a targeted protocol: `Get-ClientAccessRule | ft Name, AnyOfProtocols, Action`.

If any rules include the protocol `ExchangeActiveSync` and the `DenyAccess` action, then you'll need to investigate further to determine to which users the rule applies. The following screenshot displays a table containing one rule which denies access to Exchange ActiveSync connections.

:::image type="content" source="../media/client-access-rule.png" alt-text="A screenshot displays a table containing one rule which denies access to Exchange ActiveSync connections.":::

### Review Azure AD Conditional Access policies

When checking mobile device access for Exchange ActiveSync, you should also check Azure AD Conditional Access policies. Conditional Access is a feature of Azure AD that provides an additional layer of security before allowing users to connect to resources such as Exchange Online. Conditional Access checks for things such as user, device, and/or client app to automate decisions and enforce policies for accessing cloud apps or resources.

For example, a Conditional Access policy might state that if a user is using an Exchange ActiveSync client, then they are required to provide multi-factor authentication to sign-in to Exchange Online. Or perhaps even that they're not permitted to access Exchange Online at all. If your Exchange ActiveSync users can't connect to Exchange Online, you should verify whether they're being impacted by a Conditional Access policy.

To verify these settings, sign-in to the Azure Active Directory admin center, and then access **Azure AD Conditional Access** from **All** **services**. All policies are listed, but you'll only be interested in policies that display a State of On.

Open the appropriate policies, and then review the conditions and access controls. In the screenshot below, the Exchange ActiveSync policy is:

- Assigned to the All Sales Staff group
- Applies when users connect to Office 365 Exchange Online
- Applies when the users are using Exchange ActiveSync
- Blocks access

:::image type="content" source="../media/conditional-access.png" alt-text="A screenshot of the Exchange ActiveSync Azure AD conditional access policy with the settings described in the preceding text. ":::

## Collect and interpret Exchange ActiveSync logs

Sometimes, despite your best investigative efforts, you might not be able to identify a specific issue with a policy or rule. In these situations, it can be useful to review the Exchange ActiveSync logs. For example, suppose a user, Alex, is experiencing ongoing sync problems, you can use the following procedure to enable logging:

1. Open Exchange Online PowerShell and connect to your organization.
1. Run `Set-CASMailbox AlexW -ActiveSyncDebugLogging $true`
1. Reproduce the problem.
1. Run `Get-MobileDeviceStatistics -Mailbox AlexW -GetMailboxLog -NotificationEmailAddresses "admin@contoso.com"`

The admin account at Contoso now receives the logs associated with Alex's mobile device.

> [!TIP]
> To learn how to interpret the log contents, visit the following website: [Under The Hood: Exchange ActiveSync Mailbox Log Analysis](https://techcommunity.microsoft.com/t5/exchange-team-blog/under-the-hood-exchange-activesync-mailbox-log-analysis/ba-p/591224)

> [!NOTE]
> Debug logging is enabled for 48 hours in Exchange Online. After that, logging is disabled automatically.

## Troubleshoot connectivity issues with native Exchange ActiveSync

Not all users will use Outlook clients. Instead, they might opt to use the native email and calendaring apps built into their devices' operating systems. It's possible that some of these apps might use basic authentication, which might be blocked in your organization. To review your current organizational default Exchange authentication policies for your organization, open the **Microsoft 365 admin center**, and use the following procedure:

1. In the navigation pane, expand **Settings** and then click **Org settings**.
1. Scroll down and select **Modern authentication**.
1. The **Modern authentication** blade displays. You can enable basic authentication for the following client protocols:

    - Outlook client
    - Exchange ActiveSync
    - Autodiscover
    - IMAP4
    - POP3
    - Authenticated SMTP
    - Exchange Online PowerShell

The screenshot displays the Modern authentication blade in the Microsoft 365 admin center. Currently, basic authentication is not enabled.

:::image type="content" source="../media/authentication.png" alt-text="A screenshot that displays the Modern authentication settings in the Exchange Admin Center.":::

In addition to these organizational level settings, you can also configure specific authentication policies that change these default organizational settings for specific protocols or services. So for example, you can create an authentication policy that overrides the behavior for ActiveSync so that it can use Basic authentication. You then assign that policy to a specific collection of users.

> [!TIP]
> You manage all Exchange authentication policies by using Exchange Online PowerShell. 

For example, to create a policy to allow basic authentication for Exchange ActiveSync for sales users, run: `New-AuthenticationPolicy -Name "Sales ActiveSync auth policy" -AllowBasicAuthActiveSync`. You must then assign the policy using the `Set-User -Identity name -AuthenticationPolicy "Sales ActiveSync auth policy`".

To review authentication policies, run: `Get-AuthenticationPolicy`.

## Learn more

- [Get-MobileDeviceStatistics](/powershell/module/exchange/Get-MobileDeviceStatistics)
- [How to collect ActiveSync device logs to troubleshoot sync issues between mobile devices and Exchange Online](/exchange/troubleshoot/mobile-devices/issues-for-mobile-devices)