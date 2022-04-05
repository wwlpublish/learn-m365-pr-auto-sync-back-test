Exchange Online supports two types of authentication:

- **Basic**. Used by client apps to connect to services and endpoints. Put simply, this type of authentication means the client app, such as Microsoft Outlook, sends a username and password with every request. Those credentials are often stored or saved on the device. Sometimes known as legacy authentication.
- **Modern**. Based on OAuth 2.0 token authorization, it provides many benefits and improvements that help mitigate the issues in basic authentication. For example:

    - OAuth access tokens have a limited usable lifetime
    - OAuth access tokens are specific to the apps and resources for which they are issued
    - Multifactor authentication is also simple to enable and enforce with Modern authentication

> [!NOTE]
> Basic authentication is often enabled by default on many servers and services and is comparatively easy to set up.  

Basic authentication poses security risks and challenges, and organizations are seeking to implement modern authentication to mitigate those risks and challenges. Consequently, Microsoft are removing the ability to use Basic authentication in Exchange Online for the following clients:

- Exchange ActiveSync
- POP and IMAP
- Remote PowerShell
- Exchange Web Services
- Offline Address Book
- Microsoft Outlook for Windows and macOS

## Troubleshoot Exchange authentication policies

If a user cannot connect a client app, such as Microsoft Outlook, to Exchange Online, then this change in authentication might be the culprit.

> [!TIP]
> Remember that Client Access Rules can prohibit or allow access based on authentication types. It's worth reviewing your Client Access Rules if you experience sign-in problems.

To review the current organizational default Exchange authentication policies for your organization, open the **Microsoft 365 admin center**, and use the following procedure:

1. In the navigation pane, expand **Settings** and then click **Org settings**.
1. Scroll down and select **Modern authentication**.
1. The **Modern authentication** blade displays. You can then configure the following behavior:

    - Turn on modern authentication for Outlook 2013 for Windows and later (default)
    - Allow access to basic authentication protocols:
      - Outlook client
      - Exchange ActiveSync
      - Autodiscover
      - IMAP4
      - POP3
      - Authenticated SMTP
      - Exchange Online PowerShell

The screenshot displays the **Modern authentication** blade in the Microsoft 365 admin center. The administrator has deselected all options for basic authentication.

:::image type="content" source="../media/authentication.png" alt-text="A screenshot that displays the Modern authentication settings in the Exchange Admin Center.":::

In addition to these organizational level settings, you can also configure specific authentication policies that change these default organizational settings for specific protocols or services. So for example, you can create an authentication policy that overrides the behavior for Autodiscover so that it can use Basic authentication. You then assign that policy to a specific collection of users.

> [!TIP]
> You manage all Exchange authentication policies by using Exchange Online PowerShell. 

For example, to create a policy to allow basic authentication for IMAP for sales associates, run:

``` PowerShell
New-AuthenticationPolicy -Name "Sales Associates IMAP auth policy" -AllowBasicAuthImap
```

Then, to assign the new policy to the sales associates, run:

```powershell
$SalesUsers = Get-User -ResultSize unlimited -Filter "(RecipientType -eq 'UserMailbox') -and (Title -like '*Sales Associate*')"

$Sales = $SalesUsers.MicrosoftOnlineServicesID

$Sales | foreach {Set-User -Identity $_ -AuthenticationPolicy "Sales Associates IMAP auth policy"}
```

To review authentication policies, run: `Get-AuthenticationPolicy`.

## Troubleshoot modern authentication problems

Although modern authentication offers many security benefits, you might encounter problems during the transition from basic authentication.

> [!NOTE]
> Modern authentication is now the default. 

### Choose supported clients

You can help avoid problems that might arise with modern authentication by using supported clients. These are:

- Outlook 2013 or newer on Windows devices
- Outlook 2016 or newer for macOS
- Outlook for iOS and Android
- Mail for iOS 11.3.1 or later

### Be aware of multiple accounts in Outlook

Some users report that when modern authentication is enabled, they cannot connect to their mailboxes. This behavior is often associated with users that have multiple mailboxes configured in Outlook. A known issue in Outlook creates a miscommunication between Outlook and Windows.

When this problem arises, the mailbox shows **Disconnected** in the status bar.

You'll most likely see this issue if more than one mailbox is added to the Outlook profile, and at least one of these mailboxes uses a login account that is not the same as the user's Windows login. This miscommunication causes Windows to provide the default credential instead of the appropriate account credential required to access the mailbox.

The best approach to resolving this problem is to recreate the user's Outlook profile.

## Troubleshoot Outlook on the web (OWA) sign-in issues

By default, Outlook on the web is enabled in Exchange Online, permitting clients to connect to their mailboxes and other Exchange resources from a supported web browser, such as Microsoft Edge. However, if a user experiences problems with Outlook on the web, there are a couple of things to check.

### Verify Client Access Rules

It's worth verifying that there's no Client Access Rule prohibiting access. When you check for configured Client Access Rules, search for any rule that controls access for the `OutlookWebApp` protocol. This protocol is used by Outlook on the web.

For example, to retrieve a list of Client Access Rules, open Windows PowerShell, connect to Exchange Online, and run:

``` powershell
Get-ClientAccessRule | FT Name, AnyOfProtocols, Action
```

If a rule exists that references the `OutlookWebApp` protocol with an Action of `DenyAccess`, you'll need to think about reconfiguring the rule to enable the access required by your users.

### Verify Outlook on the web mailbox policies

Outlook on the web mailbox policies enable you to determine which features are available using Outlook on the web. The presence of a policy shouldn't prohibit a user from accessing their mailbox using Outlook on the web, but it might reduce expected functionality.

You can review the current policies in the Classic Exchange Admin Center, but it's probably quicker and easier to use Exchange Online PowerShell. Run `Get-OwaMailboxPolicy` to review a list of policies and their settings. If you need to change a setting, use the `Set-OwaMailboxPolicy` cmdlet. For example:

``` powershell
Set-OwaMailboxPolicy -Identity Default -CalendarEnabled $true
```

This command enables the calendar feature for users of Outlook on the web.

## Troubleshoot Outlook sign-in loop

Users sometimes experience sign-in loops when they open Outlook. These loops can be caused by a number of possible situations, including:

- Having multiple work and school accounts on the device.
- Experiencing proxy server pre-authentication issues.
- Using an app password instead of an account password.
- Using multifactor authentication with an outdated Outlook version.

These are often symptoms that appear after enabling modern authentication. In these situations, the best approach is to clear the Credential Manager in Windows, and then recreate the Outlook profile.