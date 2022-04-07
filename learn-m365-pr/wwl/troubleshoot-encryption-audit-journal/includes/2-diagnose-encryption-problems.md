øExchange Online has versatile features for encrypting emails to ensure that messages can only be read by the intended recipient. However, if the system is incorrectly configured, messages might not be protected, or users might be unable to open encrypted messages.

In your company that helps disadvantaged youth, emails often include personal information about your clients. It's vital that this information is protected against interception by third parties, both to protect your clients privacy and identity and to comply with data protection legislation. Recently, you've noticed that some emails that contain personal data are not encrypted as you expect. Also, some emails that have been encrypted by using Secure Multipurpose Mail Extensions (S/MIME) can't be opened. You need to troubleshoot these problems as quickly as possible.

Here, you'll learn how to diagnose problems with messages that have been encrypted with Office Message Encryption (OME) or S/MIME.

## Encrypt messages in Exchange

Emails can contain sensitive information, such as:

- Business-critical data that might compromise your competitiveness if it's disclosed to your rivals.
- Personal information on your employees or customers that might be covered by data protection legislation.
- Financial details such as bank account or credit card numbers.

By default, emails are sent in plain text and can be intercepted and examined by third parties. You should educate your users about the best use of emails and ensure they consider whether an email is the best way to send sensitive data to an internal or external recipient. However, some businesses might need to send sensitive emails and there are three different types of encryption in Exchange Online to protect that information and prevent interception:

- Office Message Encryption (OME). You can define mail transport rules that determine which messages are encrypted. Both internal and external recipients can receive and view encrypted messages by signing-in with a Microsoft account, by signing-in with a Microsoft 365 account, or by using a one-time pass code.
- Information Right Management (IRM). Encrypts messages and applies usage restrictions to them. For example, you can prevent a user from forwarding a protected message.
- S/MIME. Protects messages by signing or encrypting them. S/MIME is an international standard encryption protocol for emails and attachments that is supported by Exchange Online and Outlook clients.

Let's examine the different ways to troubleshoot encryption issues.

## Troubleshoot OME

OME is an encryption service built on **Azure Rights Management** (Azure RMS) that automatically encrypts messages that match a mail transport rule. The encrypted messages can be sent to any recipient, inside or outside your organization. Users don't have to use an Outlook client to read an encrypted message: they receive a link to a portal where they can read and reply to the message.

OME has the following advantages:

- You don't have to manage or install encryption keys and certificates. Exchange Online does these tasks for you.
- Users don't need to set up certificates on their computers.
- Senders don't need to remember to encrypt a sensitive message because the mail transport rules are automatically applied to matching messages.
- You can apply your company branding to the message viewing portal.

Some Microsoft 365 subscriptions also include **Advanced Message Encryption**, which is built on top of OME and grants extra capabilities to administrators:

- You can control sensitive emails shared outside your organization with automatic policies.
- You can add a custom email template and an expiration date to sensitive emails.
- You can revoke access to a sensitive email.

If you encounter problems with OME or Advanced Message Encryption in Exchange Online, use the following sections to help you troubleshoot.

### Investigate OME configuration

You can start troubleshooting OME in Exchange Online by using the `Get-IRMConfiguration` cmdlet to check whether OME is enabled for your organization:

```powershell
Get-IRMConfiguration
```

If OME is configured, this command will display `$True` for the `AzureRMSLicensingEnabled` property.

If sensitive content is arriving at recipient mailboxes unencrypted, it might be because the mail transport rules are not correctly set up. You can view the list of transport rule in the Exchange Admin Center (EAC):

1. In the EAC, go to **Mail flow > Rules**.
1. In the list of rules, you can see summary properties for each rule. To see full details, select the rule and then select **Edit**.

    :::image type="content" source="../media/02-transport-rules.png" alt-text="Screenshot showing the transport rules in the Exchange Admin Center.":::

1. To add encryption to the rule, under **Do the following**, select **Modify the message security**, and the select **Apply Office 365 Message Encryption and rights protection**.

1. Choose a template that applies encryption, and then select **Save**.

    :::image type="content" source="../media/02-encryption-transport-rule.png" alt-text="Screenshot showing how to configure a mail transport rule that encrypts messages.":::

1. Select **OK** and then select **Save**.

Alternatively, you can use the following PowerShell commands to list all the rules in your organization:

```powershell
Get-TransportRule
```

After viewing the summary list, you can get full details of each rule:

```powershell
Get-TransportRule "Sensitive mail protection rule" | Format-List
```

You can also investigate mail transport rules by using the Test-IRMConfiguration cmdlet. This tool will test encryption and decryption between two recipients:

```powershell
Test-IRMConfiguration -Sender admin@contoso.com -Recipient serena.davis@contoso.com
```

The results of the test resemble the following:

```powershell
Results : Acquiring RMS Templates ...

           - PASS: RMS Templates acquired.  Templates available: Contoso - Sensitive View Only, Contoso  - Confidential, Do Not Forward.

       Verifying encryption ...

           - PASS: Encryption verified successfully.

       Verifying decryption ...

           - PASS: Decryption verified successfully.

       Verifying IRM is enabled ...

           - PASS: IRM verified successfully.

       OVERALL RESULT: PASS
```

### Support iOS clients

The iOS Mail client doesn't support OME and can't decrypt messages. If a user of this app receives an encrypted OME message, they'll see an error saying that they don't have rights to view the message.

The best way to work around this problem is to deploy Outlook for iOS to the device. Outlook has full support for OME encrypted messages.

If you can't deploy Outlook but you want iOS Mail users to be able to see the contents of these messages, you can configure Exchange Online to decrypt the messages before they are sent to the iOS device.

> [!IMPORTANT] 
> If you enable service-side decryption of message for iOS devices, messages are no longer protected on those devices. Your sensitive data can be intercepted as it's sent over the network. Be sure that this behavior is what you want before you enable this setting.

To manage service-side decryption, use the following PowerShell command:

```powershell
Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
```

> [!NOTE]
> On Android, non-Outlook clients behave differently to the iOS Mail client and don't require you to enable service-side decryption. Some clients, such as Gmail, provide a link to the protected message and require you to enter your email account credentials. Other clients show a single-use code and direct you to a page where you can enter it and view the protected message. As for iOS, the most seamless way to support protected message in Android is to deploy Outlook for Android.

### Expire and Revoke email with Advanced Message Encryption

If you're using OME with certain Microsoft 365 licenses, such as Enterprise E5, you can use Advanced Message Encryption to implement this extra functionality:

- You can create and use multiple branding templates for encrypted emails.
- For each branding template you can specify an expiration age. Messages sent using this template can't be read after they exceed that age.
- You can revoke messages at any time. Revoked messages are no longer readable, just like expired messages.

If a user can't access a message, if might be because it is revoked or expired. To check the status of a message, you'll need to obtain its message ID, which is in this format: `<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`

If you know some information about the message in question, such as its send date or subject line, you can locate it by using the **Message Trace** tool in the Microsoft 365 Security and Compliance Center. Once you've traced the message, select it in the list and then select **More Information** to see the message ID.

Now, you can use the following PowerShell command to find out if the message is revoked or expired:

```powershell
Get-OMEMessageStatus -MessageId "<Message ID>"
```

In the results, the Revoked column is True for revoked messages. The results also show the date and time when the message was received. You can compare this date and time to the expiration age set on the Advance Message Encryption template:

```powershell
Get-OMEConfiguration -Identity "Contoso expiration settings"
```

## Troubleshoot S/MIME in Exchange Online

S/MIME is a widely used and standardized protocol that you can use to secure emails. Because it's supported by so many email clients, you can use it to send email to almost anyone in the world, even if they're not using Outlook or Exchange. If the recipient can access and trust the right certificate, they will be able to read your email in their preferred client and they won't have to browse to a separate portal.

S/MIME provides two security techniques:

- **Digital Signatures.** If you digitally sign a message, the recipient can verify that it comes from you and that the content has not been altered since you signed it with your private key. The text of the message remains in plain text and can be viewed by anyone who intercepts the message.
- **Encryption.** If you encrypt a message, the content is hidden from third parties. Only the intended recipient of the message, who has the correct private key to decrypt it, can read the message.

Certificates underpin both these techniques. You must ensure that certificates are distributed to recipients and that those certificates are trusted by both parties.

To use S/MIME in Exchange Online requires administrators to configure:

1. An on-premises Active Directory system, that publishes S/MIME certificates for each user. You can't use Azure AD for this purpose. You can either publish the S/MIME certificates with your own Windows Certificate Authority (CA) or purchase them from a third-party CA. If you publish your own certificates, you must ensure that recipients trust your certificates by installing your CA certificate on their client computers. Publish the S/MIME certificates in each user's **UserSMIMECertificate** or **UserCertificate** attributes.
1. A virtual certificate collection in Exchange Online. In this step you obtain the CA certificate, and intermediate certificates if you're using them, and import them into Exchange Online by using the `Set-SmimeConfig` cmdlet.
1. The Azure AD Connect tool to synchronize directory data, including the certificates, with Azure AD.
1. the users' client software, such as Outlook, to use S/MIME encryption or signatures.

> [!NOTE]
> It's beyond the scope of this troubleshooting module to describe the setup steps for S/MIME in Exchange Online in full. For more details see "Configure S/MIME for message signing and encryption in Exchange Online" in the Learn more section, below.

If your users are not able to encrypt, sign, or decrypt S/MIME emails correctly, use the steps outlined in the following sections to diagnose the problem.

### Check the email client configuration

Start by checking that the user has correctly configured their email client to sign or encrypt messages. In Outlook, for example:

1. Select **File > Options** and then select **Trust Center**.
1. Under **Microsoft Outlook Trust Center**, select **Trust Center Settings** and then select **Email Security**.

    :::image type="content" source="../media/02-outlook-trust-center.png" alt-text="Screenshot showing the Outlook Trust Center.":::

1. Under **Encrypted Mail**, select **Settings**.
1. Under **Certificates and Algorithms**, use the **Choose** buttons to configure the certificates. If no certificates are available, use the following sections to check their distribution.

    :::image type="content" source="../media/02-outlook-certificates.png" alt-text="Screenshot showing how to check certificates in Outlook.":::

### Check the certificates in the users Exchange Online mailbox

If the S/MIME certificate distribution is working correctly, the certificates will be present in the Exchange Online mailbox. You can check these certificates by using the following PowerShell command:

```powershell
Get-Mailbox serena.davis@contoso.com | FT UserPrincipalName,UserCertificate,UserSMimeCertificate
```

If the certificates are present, the UserCertificate or UserSMimeCertificate column will include data.

You can also use the following PowerShell command to check the configuration of the virtual certificate collection in Exchange Online:

```powershell
Get-SmimeConfig
```

If certificates are not present, check the S/MIME configuration in your Exchange Online organization. For full information, visit the **Configure S/MIME in Exchange Online** link in the **Learn more** section below.

## Learn more

- [Email encryption](/microsoft-365/compliance/email-encryption)
- [What is Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
- [Activate rights management in the admin center](/microsoft-365/enterprise/activate-rms-in-microsoft-365)
- [What is Azure Information Protection?](/azure/information-protection/what-is-information-protection)
- [Message Encryption](/microsoft-365/compliance/ome)
- [Set up new Message Encryption capabilities](/microsoft-365/compliance/set-up-new-message-encryption-capabilities)
- [Manage Office 365 Message Encryption](/microsoft-365/compliance/manage-office-365-message-encryption)
- [Define mail flow rules to encrypt email messages](/microsoft-365/compliance/define-mail-flow-rules-to-encrypt-email)
- [Revoke email encrypted by Advanced Message Encryption](/microsoft-365/compliance/revoke-ome-encrypted-mail)
- [S/MIME for message signing and encryption in Exchange Online](/exchange/security-and-compliance/smime-exo/smime-exo)
- [Configure S/MIME in Exchange Online](/exchange/security-and-compliance/smime-exo/configure-smime-exo)
