Exchange Online Protection (EOP) employs a robust set of features to protect against known malware and viruses to safeguard your tenant. However, you may not always agree on the final verdict that EOP places on a message. The Tenant Allow/Block List can be configured to manually override verdicts during mail flow for incoming messages. The Tenant Allow/Block List overrides only apply to incoming email messages and don't apply to intra-org messages.

Within the Tenant Allow/Block list in the Microsoft 365 Defender portal, you can specify the following types of manual overrides:

 -  Files to block.
 -  Files to allow.
 -  URLs to block.
 -  URLs to allow.
 -  Spoofed senders to allow or block.
 -  Sender emails or domains to block.
 -  Sender emails or domains to allow.

### Manage the Tenant Allow/Block List

Using the Microsoft 365 Defender portal, navigate to **Policies &amp; rule**s &gt; **Threat Policies** &gt; **Rules** section &gt; select **Tenant Allow/Block Lists**.

In the **Tenant Allow/Block Lists**, there are four tabs to select from. Refer to the following table to configure the **Tenant allow/Block Lists**:

> [!NOTE]
> In the Tenant Allow/Block Lists, you can only configure both allowed and blocked entries for spoofed senders. The sender, URL, or file entries to allow will need to go through the admin submissions process. This process is covered further down in this unit.

:::row:::
  :::column:::
    Entry
  :::column-end:::
  :::column:::
    Action
  :::column-end:::
  :::column:::
    Configuration
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Senders
  :::column-end:::
  :::column:::
    Block
  :::column-end:::
  :::column:::
    **Sender email addresses or domains:** Enter one sender (email address or domain) per line, up to a maximum of 20. For example, "contoso.com" and "user@fabrikam.com".**Never expire:** 

 -  Verify the setting is turned off and use the Remove on box to specify the expiration date for the entries.
    **or**
 -  Move the toggle to the right to configure the entries to never expire.

**Optional:** Enter description.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    URLs
  :::column-end:::
  :::column:::
    Block
  :::column-end:::
  :::column:::
    **Add URLs with wildcards:** Enter one URL per line, up to a maximum of 20. For example, "contoso.com/a/\*" and "1.2.3.4/\*". (For details about the syntax of URL entries, see [URL syntax for the Tenant Allow/Block List](/microsoft-365/security/office-365-security/tenant-allow-block-list?azure-portal=true#url-syntax-for-the-tenant-allowblock-list).)**Never expire:** 

 -  Verify the setting is turned off and use the Remove on box to specify the expiration date for the entries.
    **or**
 -  Move the toggle to the right to configure the entries to never expire.

**Optional:** Enter description.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    File entries
  :::column-end:::
  :::column:::
    Block
  :::column-end:::
  :::column:::
    **Add file hashes:** Enter one SHA256 hash value per line, up to a maximum of 20. For example, "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a".**Never expire:** 

 -  Verify the setting is turned off and use the Remove on box to specify the expiration date for the entries.
    **or**
 -  Move the toggle to the right to configure the entries to never expire.

**Optional:** Enter description.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Spoofed sender
  :::column-end:::
  :::column:::
    Allow/Block
  :::column-end:::
  :::column:::
    **Add new domain pairs with wildcards:** Enter one domain pair per line, up to a maximum of 20. For example, "contoso.com" and "166.22.0.0/24". (For syntax details, see [Domain pair syntax for spoofed sender entries in the Tenant Allow/Block List](/microsoft-365/security/office-365-security/tenant-allow-block-list?azure-portal=true#domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list))**Spoof type:** Select one of the following values:

 -  Internal: The spoofed sender is in a domain that belongs to your organization (an accepted domain).
 -  External: The spoofed sender is in an external domain.

**Action:** Select **Allow** or **Block**.**Note:** 

 -  Only the combination of the spoofed user and the sending infrastructure defined in the domain pair can be allowed or blocked from spoofing.
 -  When you configure an allow or block entry for a domain pair, messages from that domain pair no longer appear in the spoof intelligence insight.
 -  Entries for spoofed senders never expire.
 -  Spoof supports both allow and block.


  :::column-end:::
:::row-end:::


### Use the Microsoft 365 Defender Submission Portal

As noted in the section above, you can only add allowed entries for spoofed senders. You'll need to use the admin submission process to submit blocked messages for senders, URLs, or files. Microsoft manages the allowed entries on your behalf to remove unneeded or misconfigured entries. The process to submit a message to Microsoft for further review is outlined below:

1.  In the Microsoft 365 Defender portal, navigate to **Actions &amp; Submissions** &gt; **Submissions.**
2.  On the **Submissions** page, there's a dropdown menu to **Select the submission type**. There are three options to choose from with different corresponding actions:
    
     -  Email - a field to add the network message ID or upload the email file will be displayed along with a field to choose a recipient who had the issue.
     -  URL - a field to add the URL with be displayed.
     -  Email attachment - a field to upload the email attachment file will be displayed.
3.  Once the information above has been entered into the correct field, in the **Select a reason for submitting to Microsoft** section, select **Should not have been blocked (false positive)**.
4.  You'll be presented with the following options depending on the submission type selected in step 2:
    
     -  Email - turn on **Allow messages like this**.
     -  URL - turn on **Allow URLs like this**.<br>
     -  Email attachment - turn on **Allow files like this**.
5.  From the **Remove after** drop-down list, specify for how long you want the allow option to work.<br>
6.  When you're finished, select the **Submit** button.

For further reading, see [Add allows in the Tenant Allow/Block List.](/microsoft-365/security/office-365-security/manage-tenant-allows?azure-portal=true)
