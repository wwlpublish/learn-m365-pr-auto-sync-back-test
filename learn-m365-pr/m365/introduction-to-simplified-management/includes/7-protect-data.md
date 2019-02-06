Every company has data that it must protect, including personally identifiable information (PII) such as social security numbers, credit card numbers, or company financial data. Over the years, governmental and other agencies have become interested in how we use and share data. Part of the protection a company must provide is ensuring that data is not purposefully or accidentally exposed to unauthorized people. 

## Data Loss Protection (DLP)
Microsoft 365 data loss protection (DLP) helps you:

- Identify and continuously monitor and report on sensitive information.
- Prevent accidental sharing of sensitive information.

You can create DLP policies to protect the following applications:

- Exchange Online
- SharePoint Online
- OneDrive for Business
- Desktop versions of Excel, PowerPoint, and Word 

Microsoft 365 also allows you to teach users about DLP policies and protect data without interrupting their work. You can set DLP policies to show a policy tip or send an email when users try to share protected information. You can allow users to override the policy and share information despite the policy. 

DLP reports are included in the Security & Compliance center.. These reports tell you the number of policy matches over time, and the number of times that policies were overridden or that users indicated that a policy rule created a false positive. This information can help you understand how DLP policies affect your business, and it also allows you to modify and improve your policies over time.

## Information Rights Management
You also need to protect data after it leaves the company. To meet this need, make data protection part of the document itself with Information Rights Management (IRM). An employee can create a document and then determine the level of protection that should apply to the document, such as preventing unauthorized users from opening the document. In some scenarios, protection can also be applied automatically based on conditions that the administrator defines.

Azure Information Protection uses Azure Rights Management (Azure RMS) to provide for IRM in Office 365. AIP is cloud-based and enables you to classify and protect documents and emails by using labeling. 

For example, imagine a user has entered information into an email message that the admin has identified as sensitive. AIP detects that information in the email and notifies the user: 

![Azure Information Protection screenshot](../media/7-aip.png)

You configure sensitivity labels, label policies, and sens  itive information types by using Security & Compliance from the Office 365 portal. 
 
![Security and compliance in Office 365](../media/7-security-o365.png)