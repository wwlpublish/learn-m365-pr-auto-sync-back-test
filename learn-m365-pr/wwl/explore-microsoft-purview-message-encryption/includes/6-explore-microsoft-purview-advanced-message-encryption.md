Advanced Message Encryption helps customers meet compliance obligations that require more flexible controls over external recipients and their access to encrypted emails. With Advanced Message Encryption in Microsoft 365, you can:

 -  Control sensitive emails shared outside the organization with automatic policies.
 -  Track those activities through the encrypted message portal access logs.
 -  Configure these policies to identify sensitive information types such as customer content, Financial, or Health IDs.
 -  Use keywords to enhance protection.

Once you've configured the policies, you pair policies with custom branded email templates. You can then add an expiration date for extra control of emails that fit the policy. Admins can further control encrypted emails accessed externally through a secure web portal. They can do so by revoking access to the mail at any time.

> [!NOTE]
> You can only revoke and set an expiration date for emails sent to external recipients.

To use Microsoft Purview Advanced Message Encryption, an organization must have:

 -  A subscription that includes Microsoft Purview Advanced Message Encryption.
 -  Microsoft Purview Message Encryption already set up.

The key features in Microsoft Purview Advanced Message Encryption include:

 -  Create multiple branding templates.
 -  Revoke encrypted email.
 -  Set an expiration date for encrypted email.

These features are examined in the following sections:

### Multiple branding templates

With Microsoft Purview Advanced Message Encryption, you're not limited to a single branding template. Instead, you can create and use multiple branding templates. Adding custom branding also lets you enable tracking a revocation of encrypted messages. When you use custom branding, external recipients receive a notification email that contains a link to the message encryption portal. The mail flow rule determines which branding template is used by the notification email and message encryption portal. This way, your secure content isn't sent outside your organization.

If you have Microsoft Purview Advanced Message Encryption, you can create custom branding templates for your organization by using the **New-OMEConfiguration** cmdlet. Once you've created the template, you modify the template by using the **Set-OMEConfiguration** cmdlet. You can create multiple templates.

To create a new custom branding template:

1.  Using a work or school account that has global administrator permissions in your organization, start a Windows PowerShell session and connect to Exchange Online.
2.  Use the **New-OMEConfiguration** cmdlet to create a new template.
    
    ```powershell
    New-OMEConfiguration -Identity "<OMEConfigurationName>"
    ```
    
    For example:
    
    New-OMEConfiguration -Identity "Custom branding template"

### Revoke encrypted email

You can control sensitive emails shared outside the organization and enhance protection by revoking access through a secure web portal to encrypted emails. You can only revoke messages that users receive through the message encryption portal. In other words, email that has a custom branding template applied.

If a message was encrypted using Microsoft Purview Advanced Message Encryption, and you're a Microsoft 365 admin or you're the sender of the message, you can revoke the message under certain conditions. Admins revoke messages using PowerShell. As a sender, you revoke a message that you sent directly from Outlook on the web.

Admins and message senders can revoke encrypted emails if the recipient received a link-based, branded encrypted email. If the recipient received a native inline experience in a supported Outlook client, then you can't revoke the message.

Whether a recipient receives a link-based experience or an inline experience depends on the recipient identity type:

 -  Office 365 and Microsoft account recipients (for example, outlook.com users) get an inline experience in supported Outlook clients.
 -  All other recipient types, such as Gmail and Yahoo recipients, get a link-based experience.

Admins and message senders can revoke messages that are encrypted using encryption applied directly from Outlook on the web. For example, messages encrypted with the Encrypt Only option appear similar to the following screenshot.

:::image type="content" source="../media/ad-hoc-encryption-revoke-3b31f73f.png" alt-text="Screenshot showing Encrypt Only option in Outlook on the web.":::


#### How to revoke an encrypted message that you sent

You can revoke an email that you sent to a single recipient that uses a social account such as gmail.com or yahoo.com. In other words, you can revoke an email sent to a single recipient that received the link-based experience.

You can't revoke an email that you sent to a recipient that uses a work or school account from Office 365 or Microsoft 365, or a user that uses a Microsoft account, such as an outlook.com account.

To revoke an encrypted message that you sent, complete the following steps:

1.  In **Outlook on the web**, in your **Sent** folder, browse to the message you want to revoke.
2.  If the mail is revocable, you'll see the **Remove external access** link at the top of the message. Select this link to revoke the message.
3.  The message shows that its status is revoked.
    
    :::image type="content" source="../media/ad-hoc-encryption-revoked-message-7e4c3768.png" alt-text="Screenshot showing revoked encrypted message in Outlook on the web.":::
    

#### Recipient experience for revoked encrypted emails

Once an email has been revoked, the recipient receives the following error when they access the encrypted email through the Microsoft Purview Message Encryption portal: **The message has been revoked by the sender.**

:::image type="content" source="../media/revoked-encrypted-email-message-a951443b.png" alt-text="Screenshot showing the error that a recipient receives when they access an encrypted email after it's been revoked.":::


### Set an expiration date for email encrypted by Microsoft Purview Advanced Message Encryption

You can use message expiration on emails that your users send to external recipients who use the message encryption Portal to access encrypted emails. You force recipients to use the message encryption portal to view and reply to encrypted emails sent by your organization by using a custom branded template that specifies an expiration date in Windows PowerShell.

As an Office 365 global administrator, when you apply your company brand to customize the look of your organization's email messages, you can also specify an expiration for these email messages. With Microsoft Purview Advanced Message Encryption, you can create multiple templates for encrypted emails that originate from your organization. Using a template, you can control how long recipients have access to mail sent by your users.

When an end user receives mail that has an expiration date set, the user sees the expiration date in the wrapper email. If a user tries to open an expired mail, an error appears in the message encryption portal.

You can only set expiration dates for emails to external recipients.

With Microsoft Purview Advanced Message Encryption, anytime you apply custom branding, Microsoft 365 applies the wrapper to email that fits the mail flow rule to which you apply the template. In addition, you can only use expiration if you use custom branding.

#### Create a custom branding template to force mail expiration by using PowerShell

1.  Connect to Exchange Online PowerShell with an account that has global administrator permissions in your organization.
2.  Run the New-OMEConfiguration cmdlet.
    
    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```
    
    Where:
    
    
     -  Identity is the name of the custom template.
     -  ExternalMailExpiryInDays identifies the number of days that recipients can keep mail before it expires. You can use any value between 1–730 days.

### Ensure all external recipients use the message encryption portal to read encrypted mail

Organizations can use custom branding templates to force recipients to receive a wrapper mail that directs them to read encrypted email in the message encryption portal instead of using Outlook or Outlook on the web. Organizations may want to take this action if they want greater control over how recipients use the mail they receive.

For example, if external recipients view email in the web portal, you can set an expiration date for the email, and you can revoke the email. These features are only supported through the message encryption portal. You can use the **Encrypt option** and the **Do Not Forward** option when creating the mail flow rules.

Complete the following steps to use a custom template to force all external recipients to use the message encryption portal and for encrypted email:

1.  Use a work or school account that has global administrator permissions in your organization and start a Windows PowerShell session and connect to Exchange Online.
2.  Run the **New-TransportRule** cmdlet:
    
    ```powershell
    New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
    ```
    
    where:
    
    
     -  mail flow rule name is the name you want to use for the new mail flow rule.
     -  option name is either **Encrypt-Only** or **Do Not Forward**.
     -  template name is the name you gave the custom branding template; for example, Message Encryption Configuration.
    
    For example, to encrypt all external email with the "Message Encryption Configuration" template and apply the **Encrypt-Only** option:
    
    ```powershell
    New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "Message Encryption Configuration"
    ```
    
    To encrypt all external email with the "Message Encryption Configuration" template and apply the **Do Not Forward** option:
    
    ```powershell
    New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate
    ```

### Microsoft Purview Advanced Message Encryption licensing

Microsoft Purview Advanced Message Encryption is included in the following subscriptions:

 -  Microsoft 365 Enterprise E5
 -  Office 365 E5
 -  Microsoft 365 E5 (Nonprofit Staff Pricing)
 -  Office 365 Enterprise E5 (Nonprofit Staff Pricing)
 -  Office 365 Education A5

If your organization has a subscription that doesn't include Microsoft Purview Advanced Message Encryption, you can purchase it with one of the following add-on's:

 -  Microsoft 365 E5 Compliance SKU add-on for Microsoft 365 E3
 -  Microsoft 365 E3 (Nonprofit Staff Pricing)
 -  Office 365 Advanced Compliance SKU add-on for Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Staff Pricing), Office 365 SKUs,
 -  Microsoft 365 E5/A5 Information Protection and Governance SKU add-on for Microsoft 365 A3/E3

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”