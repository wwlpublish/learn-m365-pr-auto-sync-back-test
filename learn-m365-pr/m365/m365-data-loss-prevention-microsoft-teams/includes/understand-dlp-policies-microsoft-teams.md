Data loss prevention capabilities are now available in Microsoft Teams chat and channel messages including private channel messages. You can create policies to prevent the sharing of sensitive information in a Teams channel or chat session.

Data Loss Protection (DLP) for Microsoft Teams blocks sensitive content when shared with Microsoft Teams users who have:

- guest access in teams and channels; or
- external access in meetings and chat sessions.

DLP for external chat sessions will only work if both the sender and the receiver are in Teams Only mode and using Microsoft Teams native federation. DLP for Teams doesn't block messages in interop with Skype for Business or non-native federated chat sessions.

> [!IMPORTANT]
> DLP for Teams is only supported when the user has a mailbox that is in Exchange Online.

## Protecting sensitive information in messages

If someone is trying to share sensitive information in a Teams chat or channel with guests (external users) for which there's a DLP policy defined to prevent this, messages with sensitive information sent to external users will be deleted. Which happens automatically, and within seconds, according to how your DLP policy is configured.

## Protecting sensitive information in documents

If someone is trying to share a document with guests in a Microsoft Teams channel or chat, and the document contains sensitive information and you have a DLP policy defined, the document won't open for those users. Your DLP policy must include SharePoint and OneDrive in order for protection to be in place. (This is an example of DLP for SharePoint that shows up in Microsoft Teams, and as such requires that users are licensed for Microsoft Purview Data Loss Prevention (included in Office 365 E3), but doesn't require users to be licensed for Office 365 Advanced Compliance.)
