DLP policies detect sensitive information with more than a simple scanning of the text. Deep content analysis uses keyword matches, dictionary matches, the evaluation of regular expressions, internal functions, and other methods to detect content that matches your DLP policies. DLP policies are stored in a central policy store and then synchronized to the following content sources:

- Microsoft Teams channels and chat messages.
- Exchange Online, and from there to Outlook on the web and Outlook.
- OneDrive for Business sites.
- SharePoint Online sites.
- Office desktop programs (Excel, PowerPoint, and Word).

After the policy is synchronized to the right locations, it will start to evaluate content and enforce actions.

## Policy evaluation in OneDrive for Business and SharePoint Online sites

Because documents on SharePoint and OneDrive for Business sites are frequently changed by users, there's a possibility that your content can become compliant or non-compliant with DLP policies at any time. To mitigate this problem, DLP policies check documents frequently, looking for policy matches. Which is referred to as asynchronous policy evaluation.

## Asynchronous DLP policy evaluation

In an organization, documents are constantly changing. Documents are being created, shared, and edited. Which means that documents can become compliant or come in conflict with DLP policies. For example, a document that contained no personal data yesterday could be edited by someone who has introduced personal data. DLP policies frequently check documents in the background for policy matches. Which is called asynchronous DLP policy evaluation.

As users add or change documents, the search engine scans the content and updates its search index. In addition, the content is being scanned for sensitive information, and if any is found, it's stored securely in the search index. Because this is only stored in the search index, only the compliance team can access it, not typical users.

Each DLP policy that has been turned on runs in the background looking for content that patches a policy and applies actions to protect it from inadvertent leaks.

:::image type="content" source="../media/3-asynchronous-dlp-policy-evaluation.png" alt-text="Asynchronous DLP policy evaluation.":::

Content can be added to a document that can conflict with a DLP policy and conversely, content can be removed from a document to make it compliant with a DLP policy. For example, if a DLP policy was created to block the release of personal data, and a person's health record was added to a document, access to that document would be blocked. If the person's health data was removed, then the DLP policy would no longer block access.

## Policy evaluation in Microsoft Teams

A DLP policy that includes Microsoft Teams as a location, the policies are synced to user accounts and Microsoft Teams channels and chat messages. When someone attempts to share sensitive information in a Microsoft Teams chat or channel message, the message can be blocked or revoked as defined in the policy. In addition, documents that contain sensitive information and that are shared with guests (external users) won't open for those users. To learn more, see Data loss prevention and Microsoft Teams below.

## Policy evaluation in Exchange Online, Outlook, and Outlook on the web

DLP policies that include Exchange Online as a location are synced to Exchange Online and from there to Outlook and Outlook on the web. Users will see DLP policy tips as messages are being created and evaluated against DLP policies. DLP policies scan both the message and any attachments.

## Policy evaluation in the Office desktop programs

The ability to identify sensitive information and apply DLP policies work equally well in Excel, Word, and PowerPoint as it does in SharePoint Online and OneDrive for Business. Content in these Office programs is being continuously evaluated when the documents are opened and being worked on.

Policy tips might take a few seconds to appear if a user is working on a large document or if the user's computer is busy. DLP policy evaluation is designed to not affect program performance and should have minimal effect on productivity.
