People regularly send, receive, and share attachments, such as documents, presentations, spreadsheets, and more. It's not always easy to tell whether an attachment is safe or malicious just by looking at an email message. In fact, the rising number of ransomware and trojan attacks nowadays proves it’s even hard for professionals to spot potentially harmful attachments.

Safe Attachments is a feature in Microsoft Defender for Office 365. It's designed to protect organizations by detecting malicious attachments even before anti-virus signatures are made available. That makes it an ideal solution to protect against unknown attack vectors and to react fast on new threats, such as modified harmful PDF documents or Word files that can conduct ransomware attacks. Safe Attachments analyzes attachments that are common targets for malicious content, such as:

 -  different versions of Office files such as Word, PowerPoint, and Excel
 -  PDFs
 -  executable file types
 -  Flash files

### The Safe Attachments process

To implement Safe Attachments, you must first define one or more Safe Attachments policies. These policies control how Safe Attachments protection is employed at the organization. A Safe Attachments policy determines:

 -  which emails undergo Safe Attachments testing.
 -  what actions are taken on attachments that are determined to be malicious.

The Safe Attachments process involves the following steps:<br>

1.  **Select attachments to test based upon Safe Attachment policies**. Safe Attachments works on email attachments that are received from senders in your organization and external senders who are outside of the organization. The feature protects your organization according to policies that are set by your Microsoft 365 Enterprise or security administrators. When a Safe Attachments policy is in place and someone covered by that policy views their email in Microsoft 365, their email attachments are selected for checking.
2.  **Test selected attachments**. Attachments are tested in virtual environments that run different versions of the Windows operating system and applications. The attachments are executed, or detonated, and undergo a behavioral analysis to determine if the file executes malicious behavior. For example, an attachment may install a Trojan horse or a virus that makes changes to the registry or system settings that result in the system and network being more vulnerable to attack.
3.  **For each malicious file, complete the action defined in the Safe Attachments policy**. When an attachment is determined to be malicious, appropriate actions are taken against the attachment. The actions are based on the organization’s Safe Attachments policy that was applied to the original email that carried the attachment.

Depending on how your policies are defined, people can continue working without ever knowing they were sent malicious files.

For example, suppose that George receives an email message that has an attachment. It’s not obvious to George whether that attachment is safe or contains malware designed to steal his user credentials. In George's organization, a security administrator defined a Safe Attachments policy a few days earlier. Now, with the Safe Attachments feature in place, the email attachment is opened and tested in a Microsoft 365 virtual environment before George receives it. If the attachment is safe, it will open as expected when George selects it. If the attachment is determined to be malicious, it will be removed and can be researched by the organization’s security administrators and analysts.

### Safe Attachments policy settings

When Safe Attachments policies are set up for your organization, there are several options for how email attachments are handled. The following table identifies these options.<br>

:::row:::
  :::column:::
    **Option**
  :::column-end:::
  :::column:::
    **Effect**
  :::column-end:::
  :::column:::
    **Use when you want to:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Off
  :::column-end:::
  :::column:::
    Attachments aren't scanned for malware by Safe Attachments. Messages are still scanned for malware by anti-malware protection in EOP.
  :::column-end:::
  :::column:::
    

Turn scanning off for selected recipients.

Prevent unnecessary delays in routing internal mail.

This option isn't recommended for most users. You should only use this option to turn off Safe Attachments scanning for recipients who only receive messages from trusted senders.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Monitor
  :::column-end:::
  :::column:::
    Delivers messages with attachments and then tracks what happens with detected malware.

Delivery of safe messages may be delayed due to Safe Attachments scanning.


  :::column-end:::
  :::column:::
    See where detected malware goes in your organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Block
  :::column-end:::
  :::column:::
    Prevents messages with detected malware attachments from being delivered.

Messages are quarantined. By default, only admins (not users) can review, release, or delete the messages.

Automatically blocks future instances of the messages and attachments.

Delivery of safe messages may be delayed due to Safe Attachments scanning.


  :::column-end:::
  :::column:::
    Protects your organization from repeated attacks using the same malware attachments.

This option is the default value. It's also the recommended value in Standard and Strict preset security policies.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Replace
  :::column-end:::
  :::column:::
    Removes detected malware attachments.

Notifies recipients that attachments have been removed.

Messages that contain malicious attachments are quarantined. By default, only admins (not users) can review, release, or delete the messages.

Delivery of safe messages may be delayed due to Safe Attachments scanning.


  :::column-end:::
  :::column:::
    Raise visibility to recipients that attachments were removed because of detected malware.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Dynamic Delivery
  :::column-end:::
  :::column:::
    Delivers messages immediately, but replaces attachments with placeholders until Safe Attachments scanning is complete. Messages that contain malicious attachments are quarantined. By default, only admins (not users) can review, release, or delete the messages.
  :::column-end:::
  :::column:::
    Avoid message delays while protecting recipients from malicious files.
  :::column-end:::
:::row-end:::


#### Dynamic Delivery

Depending on how Safe Attachments policies are configured, email recipients can experience a minor delay in email delivery while their attachments are scanned. Of all the Safe Attachments options, only the Dynamic Delivery option enables organizations to avoid message delays.

It does so by sending the body of an email message through to the recipient with a placeholder for each email attachment. The placeholder remains until a copy of the attachment is scanned and determined to be safe by Safe Attachments. Most PDFs and Office documents can be previewed in safe mode while Safe Attachments scanning is underway. If an attachment isn't compatible with the Dynamic Delivery previewer, email recipients see an attachment placeholder until Safe Attachments scanning is complete.

 -  As each attachment is cleared, it's available to be opened or downloaded.
 -  If an attachment is determined to be malicious, it's sent to quarantine, where someone on your organization's security team (such as a Microsoft 365 Global Administrator or Security Administrator) can manage quarantined messages in Microsoft 365.

With Dynamic Delivery, email recipients can read and respond to their email messages right away, knowing that their attachments are being analyzed.

There are certain scenarios in which Dynamic Delivery isn't supported, including:

 -  Email messages that are in public folders.
 -  Email messages that are routed out of and then back into the user's mailbox using custom rules.
 -  Messages that are moved (automatically or manually) out of the hosted mailbox and into other locations, including archive folders.
 -  Messages that are deleted.
 -  A user's mailbox search folder that is in an error state.
 -  Messages encrypted with Secure/Multipurpose Internet Mail Extensions (S/MIME).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”