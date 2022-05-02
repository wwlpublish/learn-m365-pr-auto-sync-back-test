People regularly send, receive, and share attachments, such as documents, presentations, spreadsheets, and more. It's not always easy to tell whether an attachment is safe or malicious just by looking at an email message. Safe Attachments is a feature in Microsoft Defender for Office 365 that:

 -  opens every attachment of a supported file type in a special hypervisor environment.
 -  checks to see if the attachment is malicious.
 -  takes appropriate action against malicious attachments to protect your organization.

Safe Attachments protects organizations by detecting malicious attachments even before anti-virus signatures are made available. It analyzes attachments that are common targets for malicious content. For example, different versions of Office files such as Word, PowerPoint, and Excel, PDFs, executable file types, and Flash files.

Let’s examine how Safe Attachments works:

1.  **Selecting attachments to test.** Safe Attachments works on email attachments that are received from both senders within an organization and external senders who are outside the organization. The feature protects an organization according to policies that are set by its Microsoft 365 Enterprise or security administrators. When a Safe Attachments policy is in place and someone covered by that policy views their email in Microsoft 365, their email attachments are checked. Appropriate actions are then taken based on the organization’s Safe Attachments policies.
2.  **Attachment testing.** Attachments are tested in virtual environments that run different versions of the Windows operating system and applications. The attachments are executed, or "detonated". They then undergo behavioral analysis to determine if the file executes malicious behavior. For example, a malicious attachment may install a Trojan horse. Or, it may install a virus that makes changes to the registry or system settings. These types of viruses result in the system and network being more vulnerable to attack.

> [!NOTE]
> Safe Attachments scanning takes place in the same region where your Microsoft 365 data resides.

Safe Attachments protection for email messages is controlled by Safe Attachments policies. There's no default Safe Attachments policy. However, the Built-in protection preset security policy provides Safe Attachments protection to all recipients (users who aren't defined in custom Safe Attachments policies). You can also create Safe Attachments policies that apply to specific users, group, or domains.

**Additional reading**. For more information, see:

 -  [Preset security policies in EOP and Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/preset-security-policies?azure-portal=true).
 -  [Set up Safe Attachments policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/set-up-safe-attachments-policies?azure-portal=true).

### Safe Attachment scenarios

The following table describes common scenarios for Safe Attachments in Microsoft 365 organizations that include Microsoft Defender for Office 365.

:::row:::
  :::column:::
    **Scenario**
  :::column-end:::
  :::column:::
    **Result**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Pat's Microsoft 365 E5 organization has no Safe Attachments policies configured.
  :::column-end:::
  :::column:::
    Pat is protected by Safe Attachments due to the Built-in protection preset security policy that applies to all recipients who aren't otherwise defined in Safe Attachments policies.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Lee's organization has a Safe Attachments policy that applies only to finance employees. Lee is a member of the sales department.
  :::column-end:::
  :::column:::
    Lee and the rest of the Sales department are protected by Safe Attachments due to the Built-in protection preset security policy. This policy applies to all recipients who aren't otherwise defined in custom Safe Attachments policies.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Yesterday, an admin in Jean's organization created a Safe Attachments policy that applies to all employees. Earlier today, Jean received an email message that included an attachment.
  :::column-end:::
  :::column:::
    Jean is protected by Safe Attachments due to that custom Safe Attachments policy.

Typically, it takes about 30 minutes for a new policy to take effect.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Chris's organization has long-standing Safe Attachments policies for everyone in the organization. Chris receives an email that has an attachment, and then forwards the message to external recipients.
  :::column-end:::
  :::column:::
    Chis is protected by Safe Attachments.

If the external recipients are in a Microsoft 365 organization, then the forwarded messages are also protected by Safe Attachments.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”