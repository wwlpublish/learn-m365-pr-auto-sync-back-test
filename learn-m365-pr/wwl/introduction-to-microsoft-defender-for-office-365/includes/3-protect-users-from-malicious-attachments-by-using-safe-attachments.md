People regularly send, receive, and share attachments, such as documents, presentations, spreadsheets, and more. It's not always easy to tell whether an attachment is safe or malicious just by looking at an email message. Safe Attachments is a feature in Microsoft Defender for Office 365 that:

 -  opens every attachment of a supported file type in a special hypervisor environment.
 -  checks to see if the attachment is malicious.
 -  takes appropriate action against malicious attachments to protect your organization.

Safe Attachments protects organizations by detecting malicious attachments even before anti-virus signatures are made available. It analyzes attachments that are common targets for malicious content, such as different versions of Office files such as Word, PowerPoint, and Excel, PDFs, executable file types, and Flash files.

Let’s examine how Safe Attachments works.

 -  **Selecting attachments to test.** Safe Attachments works on email attachments that are received from senders in your organization and external senders who are outside of the organization. The feature protects your organization according to policies that are set by your Microsoft 365 Enterprise or security administrators. When a Safe Attachments policy is in place and someone covered by that policy views their email in Microsoft 365, their email attachments are checked. Appropriate actions are then taken based on the organization’s Safe Attachments policies.
 -  **Attachment testing.** Attachments are tested in virtual environments that run different versions of the Windows operating system and applications. The attachments are executed, or "detonated". They then undergo behavioral analysis to determine if the file executes malicious behavior. For example, a malicious attachment may install a Trojan horse. Or, it may install a virus that makes changes to the registry or system settings that result in the system and network being more vulnerable to attack.

### Safe Attachments example

Depending on how your policies are defined, people can continue working without ever knowing they were sent malicious files. For example, suppose that George receives an email message that has an attachment. It's not obvious to George whether that attachment is safe or contains malware designed to steal his user credentials.

In George's organization, a security administrator previously defined a Safe Attachments policy. With the Safe Attachments policy in place, the email attachment is opened and tested in a Microsoft 365 virtual environment before George receives it.

If the attachment is safe, it will open as expected when George selects it. If the attachment is determined to be malicious, it will be removed from the email message but made available to the organization’s security administrators and analysts for research.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”