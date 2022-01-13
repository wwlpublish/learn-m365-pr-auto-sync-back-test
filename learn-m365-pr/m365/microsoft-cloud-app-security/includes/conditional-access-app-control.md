Cloud Discovery helps you understand what's happening in your cloud environment after the fact. While this process is important, your primary goal is to stop breaches and leaks in real time, before they put your organization at risk. You also need a way to enable users to bring their own devices to work while still protecting your organization from data leaks and data theft. Microsoft Defender for Cloud Apps integrates with identity providers (IdPs) to protect your data and devices with access and session controls through **Conditional Access App Control**. If you're using Azure Active Directory (Azure AD) as your IdP, these controls are integrated directly into Defender for Cloud Apps.

Conditional Access App Control lets you monitor and control user app access and sessions in real time. By integrating with Azure AD Conditional Access, it's easy to configure apps to work with Conditional Access App Control. It lets you selectively enforce access and session controls on your organization's apps based on any condition in Conditional Access. You can use conditions that define who (user or group of users), what (which cloud apps), and where (which locations and networks) a Conditional Access policy is applied. After you determine the conditions, you can route users to Defender for Cloud Apps where you protect data with Conditional Access App Control by applying access and session controls.

Azure AD includes built-in policies that you can configure for an easy deployment. After you configure the conditions of a Conditional Access policy in Azure AD, select **Session** under **Access controls**, and click **Use Conditional Access App Control**. If you choose to **use custom controls**, you'll define them in the Defender for Cloud Apps portal.

You can use access and session policies in the Defender for Cloud Apps portal to further refine filters and set actions to be taken on a user. With the access and session policies, you can:

- **Prevent data exfiltration**: Block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.
- **Protect on download**: Instead of blocking the download of sensitive documents, you can require them to be labeled and protected with Azure Information Protection. This action ensures that the document is protected and that user access is restricted in a potentially risky session.
- **Prevent upload of unlabeled files**: Enforce the use of labeling. Before a sensitive file is uploaded, distributed, and used by others, it's important to make sure that it has the right label and protection. You can block a file upload until the content is classified.
- **Monitor user sessions for compliance**: Monitor risky users when they sign in to apps and log their actions from within the session. You can investigate and analyze user behavior to understand where, and under what conditions, to apply session policies in the future.
- **Block access**: You can block access for specific apps and users depending on several risk factors. For example, you can block a user if they're using a client certificate as a form of device management.
- **Block custom activities**: Some apps have unique scenarios that carry risk; for example, sending messages with sensitive content in apps like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

For example, let's create a session policy in Microsoft Teams that blocks IM messages containing sensitive content. Assuming we previously created a Conditional Access policy with **Use custom controls** set under **Use Conditional Access App Control**, we start by creating a new session policy in Microsoft Defender for Cloud Apps.

We'll use an existing template for our new session policy. Select the **Block sending of messages based on real-time content inspection** policy template.

Under **Activity source** for the session policy, select **Send Teams message** as the application.

You then enable **Content Inspection**, where you'll define the sensitive information as matching a present expression, a custom expression, or any regular expression. When the expressions are defined, select **Block** under **Actions** to block the message, and to create alerts to notify administrators.

Now, when a user tries to send a sensitive message in Teams, they'll see a notification.
