This section of the module is for Microsoft 365 or Office 365 admin who wants to set up the Cloud Voicemail feature for everyone in the business.

> [!NOTE]
> Cloud Voicemail supports depositing voicemail messages only in an Exchange mailbox and doesn't support any third-party email systems.

When a delegate answers a call on behalf of a delegator, notifications are not available in Cloud Voicemail. Users can receive notifications for missed calls.

## Cloud Voicemail for Teams users

For Teams users, Cloud Voicemail is automatically set up and provisioned. Note that a Phone System license is not required for Cloud Voicemail.

## Set up Cloud Voicemail for Exchange Server Mailbox Users

The following information is about configuring Cloud Voicemail to work with users who are online for Phone System but have their mailbox on Exchange Server.

1. Voicemail messages are delivered to users' Exchange mailbox via SMTP routed through Exchange Online Protection. To enable successful delivery of these messages, be sure that Exchange Connectors are configured correctly between your Exchange servers and Exchange Online Protection.

1. To enable Voicemail features, such as customizing greetings and visual voicemail in Microsoft Teams clients, connectivity from Microsoft 365 or Office 365 to the Exchange server mailbox via Exchange Web Services is required. To enable this connectivity, you must configure the new Exchange Oauth authentication protocol or run the Exchange Hybrid Wizard from Exchange 2013 CU5 or greater. Additionally, you must configure integration and Oauth between Skype for Business Online and Exchange server.
## Enabling protected voicemail in your organization

When someone leaves a voicemail message for a user in your organization, the voicemail is delivered to the user's mailbox as an email message attachment. Using mail flow rules to apply message encryption, you can prevent those voicemail messages from being forwarded to other recipients. When you enable protected voicemail, users can listen to protected voicemail messages by calling into their voicemail mailbox or by opening the message in Outlook, Outlook on the web, or in Outlook for Android or iOS. Protected voicemail messages can't be opened in Microsoft Teams.

To set up protected voicemail, do the following:

1. Go to [https://admin.microsoft.com](https://admin.microsoft.com/) and sign in using an account with global administrator permissions.

1. Select **Show all** and then go to **Admin centers** > **Exchange**.

1. In the Exchange Admin Center, select **Mail flow** > **Rules**.

1. Select **+** **Add**, and then select **Apply Office 365 Message Encryption and rights protection to messages**.

1. Provide a name for the new mail flow rule and then under **Apply this rule if**, select **The message properties** > **Include the message type** > **Voice mail**. Select **OK**.

1. Under **Do the following**, select **Apply Office 365 Message Encryption and rights protection to the message with,** and then select **Select one**. Under the **RMS template**, select **Do not forward**. Select **OK** and then **Save**.

