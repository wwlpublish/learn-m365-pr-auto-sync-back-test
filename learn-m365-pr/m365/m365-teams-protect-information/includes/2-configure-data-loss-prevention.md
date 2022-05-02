To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information includes financial data or personal identity data, such as credit card numbers, social security numbers, or health records.

With a data loss prevention (DLP) policy, you can identify, monitor, and automatically protect sensitive information across all Microsoft 365 services.

## How DLP policies work

When a DLP policy looks for a sensitive information type, such as a credit card number, it doesn't just identify a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords
- Internal functions to validate checksums or composition
- Regular expressions to find pattern matches
- Other content examination techniques

These methods help DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt people's work.

## What DLP policies do

With a DLP policy, you can:

- **Identify sensitive information** in locations such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams. For example, you can identify documents containing a credit card number that's stored in any OneDrive for Business site.
- **Prevent the accidental sharing of sensitive information**. For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document, or block the email from being sent.
- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word**. Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.
- **Help users to stay compliant**. You can educate users about DLP policies and help them remain compliant without blocking their work. If a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification, and display a policy tip that allows them to override the policy if there's a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.
- **View DLP reports** showing content that matches your organization's DLP policies. To assess how your business is complying with a DLP policy, you'll see how many matches each policy and rule has over time. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported.

You create and manage DLP policies on the **Data loss prevention** page in the Microsoft 365 Defender portal.

## DLP policies for Microsoft Teams

If your organization has DLP, you can define policies to prevent people from sharing sensitive information in a Microsoft Teams channel or chat session. A DLP policy can also prevent sensitive information being shared with external users. To create a new DLP policy, you must be assigned a role that has permissions to edit DLP them.

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com).
1. Choose **Data loss prevention** > **Policy** > **+ Create a policy**.
1. Choose a **template** > **Next**.
1. On the **Name your policy tab**, enter a name and description, and choose **Next**.
1. On the **Choose locations** tab, keep the default setting of all locations, or select **Let me choose specific locations**, add specific locations, and choose **Next**.
1. Choose **Next**.
1. On the **Policy settings** tab, under **Customize the type of content you want to protect**, keep the default **Simple settings**, or choose **Use advanced settings**, and then select **Next**.

Simple settings are designed for the most common requirements of a DLP policy. Advanced settings give you complete control to change each setting.

1. On the **Policy settings** tab, under **What do you want to do if we detect sensitive info?** either keep the default policy tips and email notifications or customize them.
1. When you've finished reviewing or editing settings, choose **Next**.
1. On the **Policy settings** tab, under **Do you want to turn on the policy or test things out first?** choose a setting. Then select **Next**.
1. Choose the **Review your settings** tab. Select **Edit** to make changes or select **Create**.

Allow approximately one hour for your new policy to work its way through your datacenter and sync to user accounts.

> [!NOTE]
> To make sure documents that contain sensitive information aren't shared inappropriately in Teams, turn on SharePoint sites and OneDrive accounts, and Teams chat and channel messages.

## Sensitive information in messages

If someone attempts to share sensitive information in a Teams chat or channel with guests (external users) and you have a DLP policy defined to prevent this occurring, the message is deleted. This deletion happens automatically, and within seconds, according to how your DLP policy is configured.
DLP for Microsoft Teams blocks sensitive content when shared with users who have either:

- **Guest access** in teams and channels.
- **External access** in meetings and chat sessions.

DLP for external chat sessions only works if both the sender and the receiver are in Teams Only mode and using Microsoft Teams native federation. DLP for Teams doesn't block messages in interop with Skype for Business or non-native federated chat sessions.

## Sensitive information in documents

If a Microsoft Teams user attempts to share sensitive information in a document with guests, either in a Teams channel or chat, and a DLP policy is defined to prevent this happening, the document won't open for those users. The DLP policy must include SharePoint and OneDrive because they're used by Teams to share the document.
Users must have a license for Microsoft 365 DLP, which is included in Microsoft 365 E3. However, users don't require a license for Microsoft Purview.

## Policy tips

Policy tips help to educate and explain to users when an action conflicts with a DLP policy, such as if a message is blocked. If someone attempts to share a social security number in a Microsoft Teams channel, for example, the **What can I do?** link opens a dialog box. The sender then has options to resolve the issue. There might be an option to override the policy or notify an admin to review and resolve it. You can customize policy tips, providing you have permission to edit DLP policies.

## Add Microsoft Teams to existing DLP policies

To add Microsoft Teams as a location to existing DLP policies, you must have permissions to edit them.

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com).
1. Choose **Data loss prevention** > **Policy**.
1. Select a policy and review the **Locations** section. If **Teams chat and channel messages** is listed, you don't need to do anything. If it isn't listed, select **Edit**.
1. In the **Status** column, turn on the policy for Teams chat and channel messages.
1. Keep the default settings of all accounts or specify which accounts to include or exclude.
1. Select **Save**.

Allow approximately one hour for the changes to work their way through your datacenter and sync to user accounts.

## Learn more

- [Overview of data loss prevention](/microsoft-365/compliance/data-loss-prevention-policies)
- [Data loss prevention and Microsoft Teams](/microsoft-365/compliance/dlp-microsoft-teams)
- [Permissions](/microsoft-365/compliance/data-loss-prevention-policies)
