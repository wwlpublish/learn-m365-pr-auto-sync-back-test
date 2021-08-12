It's good practice to specify a mailbox to receive messages that users report as malicious or not malicious. When users submit messages using the various reporting options, you can use this mailbox to intercept messages or receive copies of messages.

The following methods can be used to report email messages and files to Microsoft:

|Method|Description|
|-|-|
|Use Admin Submission to submit suspected spam, phish, URLs, and files to Microsoft|This is the recommended reporting method for admins in organizations with Exchange Online mailboxes.|
|Enable the Report Message or the Report Phishing add-ins|Messages reported with the add-ins are available in the Admin Submissions portal, Automated investigation and response results, the User-reported messages report, and Threat Explorer.|
|Report false positives and false negatives to Outlook|Submit false positives (good email that was blocked or sent to junk folder) and false negatives (unwanted email or phish that was delivered to the inbox) to Exchange Online Protection (EOP) using the Report Message feature.|
|Manually submit messages to Microsoft for analysis|Manually send attached messages to specific Microsoft email addresses for spam, not spam, and phishing.|
|Use mail flow rules to see what your users are reporting to Microsoft|This lets you create a mail flow rule that notifies you when users report messages to Microsoft for analysis.|
|Submit malware and non-malware to Microsoft for analysis|Use the Microsoft Security Intelligence site to submit attachments and other files.|

 > [!NOTE]
 > Data from submissions to Microsoft resides in the Office 365 compliance boundary in North American data centers. The data is reviewed by analysts on the engineering team to help improve the effectiveness of the filters.
