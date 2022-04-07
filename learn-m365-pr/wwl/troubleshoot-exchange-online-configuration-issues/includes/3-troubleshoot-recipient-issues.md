Managing and troubleshooting recipient issues is likely a significant part of any day in the life of an Exchange troubleshooting engineer. So, it's important you know how to identify and resolve recipient issues.

## Troubleshoot automatic email forwarding

Email forwarding can be a useful feature for some users, enabling them to automatically redirect emails from their work mailbox to an external mailbox. However, this poses a security risk, and the convenience of your users must be balanced against the needs of your organization to help guard against data leakage.

Exchange Online supports two types of automatic forwarding:

- **Inbox rules**. Users enable forwarding within their own mailbox.
- **Mailbox forwarding**. Sometimes referred to as SMTP forwarding. Administrators configure this setting on mailbox properties.

You can use outbound spam filter policies to control automatic forwarding to external recipients. There are three available options for controlling forwarding. These are:

- **Automatic - System-controlled**. This setting is effectively the same as Off and is the default setting.
- **On**. Automatic external forwarding is allowed and unrestricted.
- **Off**. Automatic external forwarding is disabled and results in an NDR to the sender.

Disabling automatic forwarding disables any Inbox rules or mailbox forwarding that redirect messages to external addresses.

> [!IMPORTANT]
> Automatic forwarding of messages between internal users isn't affected by the settings in outbound spam filter policies.

Potential conflicts can occur when you configure other controls to allow or block automatic email forwarding. For example, using:

- Remote domains to allow / block automatic email forwarding to some / all external domains.
- Conditions and actions in Exchange mail flow rules (transport rules) to detect and block automatically forwarded messages to external recipients.

> [!NOTE]
> If one setting allows external forwarding, but another setting blocks external forwarding, the block setting wins. 

If automatic forwarding is not behaving as expected, review the settings for remote domains, transport rules, user configured inbox rules, and mailbox forwarding to determine the cause and appropriate action. The following table describes some common scenarios and resulting outcome.

| Scenario| Result|
| :--- | :--- |
| Remote domain settings allow automatic forwarding and automatic forwarding in the outbound spam filter policy is set to Off.| Automatically forwarded messages to recipients in the affected domains are blocked.|
| Remote domain settings allow automatic forwarding and automatic forwarding in the outbound spam filter policy is set to Automatic - System-controlled.| Automatically forwarded messages to recipients in the affected domains are blocked.|
| Automatic forwarding in the outbound spam filter policy is set to On and you use mail flow rules or remote domains to block automatically forwarded email.| Automatically forwarded messages to affected recipients are blocked by mail flow rules or remote domains.|

## Troubleshoot matching issues with Azure AD

Many organizations maintain on-premises resources even though they also subscribe to Microsoft 365. In these situations, Azure AD Connect is used to synchronize some or all identities in the Active Directory Domain Services (AD DS) environment with the Azure AD environment.

Sometimes, a security principal, such as a user account, has been created in one environment, and you want to transfer the source of authority to the other environment. For example, you have a user created in Azure AD but now you want to manage and synchronize it from AD DS. You can transfer the source of authority for an object by using a process known as SMTP matching.

> [!NOTE]
> This process uses the object's SMTP address as a unique identifying characteristic. 

There are some limitations in using SMTP matching:

- You can run SMTP matching only on user accounts that have an Exchange Online email address. For mail-enabled groups and contacts, SMTP matching (Soft match) is supported based on proxy addresses.
- You can only use SMTP matching once for user accounts authored using Office 365 management tools. Thereafter, the Office 365 user account is bound to your on-premises user with an immutable identity value and not the primary SMTP address.
- You can't update the cloud user's primary SMTP address during SMTP matching because the primary SMTP address is the value that's used to link the on-premises user to the cloud user.
- You must ensure that no two users have the same SMTP address otherwise, the sync will fail, and you might receive an error message.

> [!NOTE]
> SMTP addresses are considered unique values.

### Use SMTP matching to synchronize an on-premises user to a cloud identity

Use the following procedure to match an on-premises user to a Microsoft 365 user account for directory synchronization:

1. Obtain the primary SMTP address of the target Microsoft 365 user account.
1. In AD DS, using Active Directory Users and Computers, create a user account that matches the target Microsoft 365 user account.
1. Set the primary SMTP address of the new on-premises user account to match the primary SMTP address of the Microsoft 365 user.
1. Sync AD DS to Azure AD by using the following command on the computer installed with Azure AD Connect: 

    ``` powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

## Troubleshoot distribution list membership issues

Distribution lists (DLs) are a critical way of routing email to collections of users. It's important to understand how to troubleshoot distribution list membership issues to ensure the correct routing and delivery of email addresses within your organization.

A common symptom of a membership issue is failure to deliver email to mailboxes that you believe to have been added as members. It's worth noting that the following problems can also cause failure to deliver:

- It can take 60 minutes for distribution lists to be fully created and ready for management. Ensure you've waited at least 60 minutes before you send a test email to the DL.
- Sometimes, people create a Microsoft 365 Group instead of a DL. Verify that the group is, in fact, a DL and not a Microsoft 365 group.
- By default, no user outside of your organization can email a DL; this feature must be enabled by enabling the **Allow people outside of my organization to send email to this Distribution group** setting.

After you've made these determinations, you can investigate further. There are two types of distribution lists in Exchange Online:

- **Distribution list**. Has an assigned membership list that list's creator maintains. Is linked to an email address.
- **Dynamic distribution list**. You create a query that generates a membership list automatically.

Let's review these distribution list types in more depth.

### Troubleshoot assigned distribution group membership

Assigned membership means that Exchange Online administrators must add the desired members to the group. If you suspect a problem with the membership, review the current members and, if necessary, add or remove members from the group.

Depending on settings, users might be able to join or leave the DL without administrative intervention. So, it's possible that a user has made a membership list change by joining or leaving a group. By default, joining and leaving a group is configured to Open. This means any user can perform these tasks for their account.

For joining a DL, there are three settings:

- Open
- Closed
- Owner approval

For leaving a DL, there are two options:

- Open
- Closed

If users are removed from a DL, consider changing both these settings to **Closed**.

### Troubleshoot dynamic distribution group membership

If your organization uses a premium version of Azure AD, you can create dynamic DLs in addition to assigned DLs. To create a dynamic DL, you create a query based on properties such as recipient types and rules, as shown the following screenshot.

:::image type="content" source="../media/dynamic.png" alt-text="A screenshot shows the Users tab of the Add a group wizard. Adele Vance is the assigned owner, and the administrator has chosen to use a query to assign membership.":::

 If you experience problems with email delivery, review the assignment rules and, if necessary, correct any errors.

> [IMPORTANT]
> If you make changes, remember that these updates can take up to 24 hours to be provisioned.

But remember that, by default, only messages from people inside your organization can be routed to members of the DL. Ensure this setting is correctly configured.

## Troubleshoot issues with archive mailboxes

Exchange Online Archiving provides your users with the archive mailbox feature. This feature enables an archive mailbox that appears alongside a user's primary mailbox folders in Outlook or Outlook on the web. Your users can access the archive in the same way that they access their primary mailboxes.

If a user cannot access their archive mailbox, then you need to figure out why. It's important to understand that an administrator must enable the archive feature for specific users. You can do this using the Microsoft 365 Compliance console. It's always worth verifying that a user's mailbox is enabled for archive. In the console, use the following procedure for verification:

1. In the navigation pane, select **Information governance**.
1. Then in the details pane, select the **Archive** tab.
1. A list of users is returned, as shown in the following screenshot. The **Archive mailbox** column indicates the current archive status.
1. For selected users, click **Enable archive**.

    :::image type="content" source="../media/archive-status.png" alt-text="A screenshot of the Information governance page in the Compliance console. Some users have Archive mailbox enabled.":::

You can also use the `Get-Mailbox -filter * | ft Name, ArchiveStatus` command to retrieve the archive status for all mailboxes. You can then run the `Enable-Mailbox -Identity <username> -Archive` command to enable archive for a specific user.

If you're certain all the relevant mailboxes have been enabled, then you might need to investigate further. Common reasons for being unable to access the archive mailbox include:

- **Outlook desktop client version**. Ensure a recent version is installed.
- **Licensing**. A user requires a Microsoft 365 Apps for enterprise license to access this feature.
- **Full Access permission**. If a user requires full mailbox access to another user's primary and archive mailboxes, you must grant them the Full Access permission. This permission enables the display of the primary and online archive in Outlook Web App and Outlook.

    > [!IMPORTANT]
    > If you assign full mailbox access to a specific set of mailboxes through a security group, the members of the assigned group won't see the mailbox automapped to their Microsoft Outlook profile.

- **Outlook configuration**. Run the Support and Recovery Assistant tool to scan Outlook and review advanced diagnostics for known problems and details about the Microsoft Outlook configuration.

### Review auto-expanding archive mailboxes

You can use the auto-expanding archiving feature to enable additional storage space for archive mailboxes. After this feature is enabled, additional storage space is automatically added to a user's archive mailbox until it reaches the storage limit of 1.5 TB.

> [!TIP]
> You can turn on auto-expanding archiving for everyone in your organization or just for specific users.

Consider the following if you plan to implement auto-expanding archival.

- After you enable auto-expanding archiving for your organization (or for a specific user), you can't disable it.
- You can't adjust the storage quota for auto-expanding archiving.
- A user's archive mailbox must be enabled before you can enable auto-expanding archiving.
- A user must be assigned an Exchange Online Plan 2 license to enable the archive mailbox.

    > [!TIP]
    > If a user is assigned an Exchange Online Plan 1 license, assign them a separate Exchange Online Archiving license to enable their archive mailbox.

- After you turn on auto-expanding archiving, an archive mailbox is converted to an auto-expanding archive when the archive mailbox reaches 90 GB.

    > [!WARNING]
    > It can take up to 30 days for the additional storage space to be provisioned.

- Auto-expanding archiving prevents you from recovering or restoring an inactive mailbox.
- You must use Exchange Online PowerShell to enable auto-expanding archiving. Run the following Exchange Online PowerShell command to enable auto-expanding archiving for your organization: 

    ``` powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

    If you must verify the settings for a specific user, run the following command: 

    ``` powershell
    Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
    ```

## Learn more

- [Control automatic external email forwarding in Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding)
- [One or more objects don't sync when using Azure Active Directory Sync tool](/troubleshoot/azure/active-directory/objects-dont-sync-ad-sync-tool)
- [Manage dynamic distribution groups](/exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups)
- [Learn about auto-expanding archiving](/microsoft-365/compliance/autoexpanding-archiving)

