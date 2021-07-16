As administrators it's impossible to control what information a caller may divulge in a voicemail message. If you're worried that such messages may include confidential or business-critical information, you can consider encrypting messages or disabling their transcription into text.

Suppose, in your firm of financial advisors, you know clients often discuss highly sensitive information during phone calls with their advisor. You've been told they sometimes include such information in voicemail messages. You have a legal responsibility to protect this information, so you want to investigate how to protect it, without disabling the voicemail service.

Here, you'll learn about protected voicemail, voicemail policies, and how to control transcription for voice messages.

## Protect voicemail with encryption

When someone leaves a voicemail message for a user in your organization, the voicemail is delivered to the user's mailbox as an email message attachment. Using mail flow rules to apply message encryption, you can prevent those voicemail messages from being forwarded to other recipients. When you enable protected voicemail, users can listen to protected voicemail messages by calling into their voicemail mailbox or by opening the message in Outlook, Outlook on the web, or in Outlook for Android or iOS. Protected voicemail messages can't be opened in Skype for Business.

> [!IMPORTANT]
> For users who are online for Phone System but have their mailbox on Exchange Server, Voicemail messages are delivered to users' Exchange mailbox via SMTP routed through Exchange Online Protection. To enable successful delivery of these messages, please be sure that Exchange Connectors are configured correctly between your Exchange servers and Exchange Online Protection. See **Use Connectors to Configure Mail Flow**, a link is in **Learn more** section below.

To set up protected voicemail, do the following:

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com) using an account with global administrator permissions.
1. Select **Show all** and then go to **Admin centers** > **Exchange**.
1. In the Exchange Admin Center, select **Mail flow** > **Rules**.
1. Select **+ Add**, and then select **Apply Office 365 Message Encryption and rights protection to messages**.
1. Provide a name for the new mail flow rule and then under **Apply this rule if**, select **The message properties** > **Include the message type** >**Voice mail**. Select **OK**.
1. Under **Do the following**, select **Apply Office 365 Message Encryption and rights protection to the message with** and then select **Select one**. Under **RMS template**, select **Do not forward**. Select **OK** and then **Save**.

> [!NOTE]
> If the **RMS template** list is empty, you need to set up Message Encryption. For more information about setting up Message Encryption, see the following articles. Links can be found in the **Learn more** section below:
>
> - **Set up new Message Encryption capabilities**
> - **Configuring and managing templates for Azure Information Protection**
> - **Do Not Forward option for emails**

## Setting voicemail policies in your organization

> [!WARNING]
> For Skype for Business customers, disabling voicemail through a Microsoft Teams calling policy might also disable the voicemail service for your Skype for Business users.

Voicemail transcription is enabled by default and transcription profanity masking is disabled by default for all organizations and users; however, you can control them by using the **Set-CsOnlineVoicemailPolicy** and **Grant-CsOnlineVoicemailPolicy** cmdlets.

Voicemail messages received by users in your organization are transcribed in the region where your Microsoft 365 organization is hosted. The region where your tenant is hosted might not be the same region where the user receiving the voicemail message is located. To view the region where your tenant is hosted, go to the Organization profile page and then select **View details** next to Data location.

> [!IMPORTANT]
> You can't create a new policy instance for transcription and transcription profanity masking using the **New-CsOnlineVoiceMailPolicy** cmdlet, and you can't remove an existing policy instance using the **Remove-CsOnlineVoiceMailPolicy** cmdlet.

You can manage the transcription settings for your users using voicemail policies. To see all available voicemail policy instances, you can use the **Get-CsOnlineVoicemailPolicy** cmdlet.

:::image type="content" source="../media/3-get-csonlinevoicemailpolicy.png" alt-text="Screenshot showing the results of the Get-CsOnlineVoiceMailPolicy cmdlet":::

## Turning off transcription for your organization

Because the default setting for transcription is on for your organization, you may want to disable it by using **Set-CsOnlineVoicemailPolicy**. To do this, run:

```powershell
Set-CsOnlineVoicemailPolicy -EnableTranscription $false
```

## Turning on transcription profanity masking for your organization

Transcription profanity masking is disabled by default for your organization. If there's a business requirement to enable it, you can enable transcription profanity masking by using **Set-CsOnlineVoicemailPolicy**. To do this, run:

```powershell
Set-CsOnlineVoicemailPolicy -EnableTranscriptionProfanityMasking $true
```

## Turning off transcription for a user

User policies take precedence over the organizational default settings. For example, if voicemail transcription is enabled for all of your users, you can assign a policy to disable transcription for a specific user by using the **Grant-CsOnlineVoicemailPolicy** cmdlet.

To disable transcription for a single user, run:

```powershell
Grant-CsOnlineVoicemailPolicy -PolicyName TranscriptionDisabled -Identity sip:amosmar@contoso.com
```

## Turning on transcription profanity masking for a user

To enable transcription profanity masking for a specific user, you can assign a policy to enable transcription profanity masking for a specific user by using the **Grant-CsOnlineVoicemailPolicy** cmdlet.

To enable transcription profanity masking for a single user, run:

```powershell
Grant-CsOnlineVoicemailPolicy -PolicyName TranscriptionProfanityMaskingEnabled -Identity sip:amosmar@contoso.com
```

> [!IMPORTANT]
> The voicemail service in Microsoft 365 and Office 365 caches voicemail policies and updates the cache every 4 hours. Policy changes that you make can take up to 4 hours to be applied.

## Learn more

- [Use Connectors to Configure Mail Flow](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Email encryption](/microsoft-365/compliance/email-encryption)
- [Set up new Message Encryption capabilities](/microsoft-365/compliance/set-up-new-message-encryption-capabilities)
- [Configuring and managing templates for Azure Information Protection](/information-protection/deploy-use/configure-policy-templates)
- [Do Not Forward option for emails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails)
