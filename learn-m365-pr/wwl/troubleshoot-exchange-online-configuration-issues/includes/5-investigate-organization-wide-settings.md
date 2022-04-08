There are numerous settings that you can configure at the organizational level. Since these settings impact many users, it's important to be able to identify and resolve configuration problems.

## Troubleshoot domain setup and configuration issues

Domain names are crucial to your organizational mail flow. Incorrect setup and configuration can easily result in significant disruption.

When your organization purchases a subscription to Microsoft 365, a domain name is assigned automatically that has a suffix ending in `.onmicrosoft.com`. This domain is the default name and is used as a fallback domain.

Most organizations will want to add their own custom domain name and enable the domain name to be used for messaging. For example, if your organizations name is Contoso, you might want to add the custom domain name `Contoso.com`.

The most common problem associated with domain setup is the initial configuration. When you add a custom domain, you must be able to demonstrate ownership of the domain. Typically, this ownership is shown by adding specific DNS records to the DNS zone for the domain.

> [!TIP]
> You can use the Microsoft 365 admin center or the Azure Active Directory admin center to add and initialize a custom domain. 

To add and verify a domain, open the Microsoft 365 admin center, and then use the following procedure:

1. In the navigation pane, expand **Settings** and click **Domains**.
1. Click **Add domain**.
1. In the **Add a domain wizard**, enter the domain name, and click **Use this domain**.
1. On the **How do you want to verify your domain** page; you can choose one of three methods:

    - Add a TXT record to the domain's DNS records
    - Add an MX record to the domain's DNS records
    - Add a text file to the domain's website

1. Choose the desired method, and click **Continue**.
1. On the **Verify you own this domain** page, follow the on-screen instructions to add the required information and then click **Verify**.

> [!NOTE]
> To add, modify, or remove domains, you must be a Domain Name Administrator or Global Administrator.

The following screenshot displays the verification requirements for the Contoso.com domain.

:::image type="content" source="../media/domain-verify.png" alt-text="A screenshot displays the Verify you own this domain page. Values are displayed for TXT name, TXT value, and TTL.":::

Clearly, you'll need to have management control over the DNS zone that supports your custom domain. After you've verified ownership of the domain, you must configure the required DNS settings to support inbound communication to your organization.

In the list of domains, select your custom domain and then select the **DNS records** tab. Click **Manage DNS**. You'll now need to create the required records in the DNS zone for your custom domain. This process might involve adding the required records yourself, or you can configure the name servers to point to Microsoft, and Microsoft 365 adds the required records.

> [!WARNING]
> These records are critical to service availability.

You'll need to add MX records, CNAME records, and TXT records to complete setup.

> [!IMPORTANT]
> Ensure you set up your users' mailbox settings to use the custom domain before completing these steps. 

You can use the Microsoft 365 admin center or the `Set-Mailbox` Exchange Online PowerShell cmdlet to update your users to use a new custom domain.

Within Microsoft 365 admin center:

1. Select the required user, on the menu, click **More actions**.
1. Click **Manage username and email**.
1. Click **Edit** and then select the new custom domain name from the drop-down list.
1. Click **Save changes**.
1. In PowerShell, use this command:

    ``` powershell
    Set-Mailbox -Identity "Serena Davis" -PrimarySmtpAddress "serena.davis@contoso.com"
    ````

## Troubleshoot allowed file types

One of the most challenging security management tasks facing messaging administrators, and those troubleshooting engineers, is the ability to control file attachments. Malicious content can be introduced in your organization through email file attachments.

Exchange Online enables you to use mail flow rules to inspect file attachments. To ensure only appropriate file types are allowed, you should inspect the current allowed file types in your mail flow rules. This technique is best performed using Exchange Online PowerShell. Use the `Get-TransportRule` cmdlet to review the settings in your mail flow rules. If changes are required, use the `Set-TransportRule` cmdlet.

Many mail flow rules are configurable and each is assigned a priority. The priority value can have a significant effect on the way rules are applied. To verify the current priority of rules, you can use the `-priority` parameter. For example: `Get-TransportRule | ft Name, Priority`.

## Troubleshoot mailbox plans

You can use Exchange mailbox plans to apply standardized settings to mailboxes for your recipients. Mailbox plans correspond to Microsoft 365 and Office 365 license types. So, when you add a new user and assign a license, the corresponding mailbox plan is assigned to that user's mailbox.

> [!NOTE]
> If you change the assigned license, the mailbox plan also changes. 

Typical mailbox plans are:

- ExchangeOnlineDeskless
- ExchangeOnlineEssentials
- ExchangeOnlineEnterprise
- ExchangeOnline

You can review the available mailbox plans for your organization using the `Get-MailboxPlan` cmdlet.

For each mailbox plan, there's a corresponding Client Access services (CAS) mailbox plan. When you assign a mailbox plan to a user by assigning a license, the corresponding CAS mailbox plan is also assigned. You can review the CAS mailbox plans using the `Get-CasMailboxPlan` cmdlet.

> [!IMPORTANT]
> The name of the mailbox plans and CAS mailbox plans match, and the relationship between them is permanent. 

If your users have inappropriate settings in their mailbox, you might need to update the mailbox plan settings using the `Set-MailboxPlan` cmdlet or, where appropriate, modifying the settings in the CAS mailbox plan using the `Set-CasMailboxPlan` cmdlet.

> [!IMPORTANT]
> Modifying these settings affects users you license after the changes. To modify existing users, you must use the `Set-Mailbox` and `Set-CasMailbox` cmdlets on the appropriate mailboxes.

You can review and modify the following mailbox plan settings:

- IssueWarningQuota
- MaxReceiveSize
- MaxSendSize
- ProhibitSendQuota
- ProhibitSendReceiveQuota
- RetainDeletedItemsFor
- RetentionPolicy
- RoleAssignmentPolicy

You can review and modify the following CAS mailbox plan settings:

- ActiveSyncEnabled
- ImapEnabled
- OwaMailboxPolicy
- PopEnabled

## Learn more

You can learn more here:

- [Manage accepted domains in Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)
- [Use mail flow rules to inspect message attachments in Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments)
- [Mailbox plans in Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/mailbox-plans)