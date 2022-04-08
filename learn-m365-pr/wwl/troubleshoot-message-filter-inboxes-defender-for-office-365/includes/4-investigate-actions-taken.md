Exchange Online Protection (EOP) scans messages as they arrive and may take action on them to protect users from spam, phishing attacks, and malicious code. If a message is marked as spam erroneously, you might need to find out why EOP marked it, so that future legitimate email can arrive at the right place.

In the marketing company that you work for, public-facing inboxes are the target of large volumes of spam and malicious emails. Exchange Online filters almost all of this material into quarantine or junk mail folders. However, sometimes a legitimate email is filtered when it should be placed in the correct inbox. When that happens, you must diagnose why.

Here, you’ll learn how to examine email headers to determine why Exchange Online Protection marked a message as spam.

## Actions that Exchange Online Protection (EOP) can take

When messages arrive in your Exchange Online organization, they are scanned by Exchange Online Protection (EOP). EOP can take different actions, depending on what it finds:

- If there are no concerns about the email, it’s delivered to the user’s inbox.
- If the email is likely to be bulk email or spam, it’s marked as spam and delivered to the user’s **Junk Email** folder in their mailbox.
- If the email contains a phishing attack, it’s sent to quarantine.
- If the email contains malware, it’s sent to quarantine.

Administrators can use policies to alter these default arrangements. For example, you could edit the default anti-spam policy to send all bulk emails and spam to quarantine instead of the user’s **Junk Email** folder.

It’s important to be able to investigate spam messages, find out why they’re marked as spam, and take appropriate actions to correct false-positives or false-negatives. You might also need to change policies if users are losing important emails.

## Determine why an email is marked as spam

In all Exchange Online organizations, incoming email is scanned by Exchange Online Protection (EOP) for signs that it may constitute spam, or include malware and other threats. EOP stores the results of its scan in three message headers that are added to emails. You can use these headers to determine why a message has been marked as spam:

- **X-Forefront-Antispam-Report.** This header stores information about how the message was processed by EOP and consists of field/value pairs. For example, if the message skipped spam filtering because the source IP address was in the IP allowlist, this header includes the **IPV:CAL** value. If the message was marked as spam because the sender was in the blocked senders list, the header includes the **SFV:SKB** value.
- **X-Microsoft-Antispam.** This header stores the Bulk Complaint Level (BCL) value. Larger values of BCL indicate that a message is highly likely to generate complaints and therefore highly likely to be spam. There might be other fields in this header but they are used exclusively by the Microsoft anti-spam team for diagnostic purposes.
- **Authentication-Results.** This header stores the results of email authentication based on the DNS SPF, DKIM, and DMARC records.

> [!NOTE]
> For more information about configuring the SPF, DKIM, and DMARC records in the DNS system, see the Learn module **Troubleshoot problems with mail flow**.

The following headers are from a message that was marked as spam:

``` powershell
X-Forefront-Antispam-Report:
    
CIP:64.99.140.10;CTRY:CA;LANG:en;SCL:5;SRV:;IPV:NLI;SFV:SPM;H:forward2.contoso.com;PTR:forward2.contoso.com;CAT:SPOOF;
    
X-Microsoft-Antispam: BCL:0;
```

Notice the following points:

- **BCL:0** in the **X-Microsoft-Antispam** indicates that EOP assessed that the content of the email was not likely to generate complaints.
- **SPM:5** indicates probable spam.
- **IPV:NLI** indicates that the IP address was not found on any reputation list.
- **SFV:SPM** indicates that the message was marked as spam by spam filtering.
- **CAT:SPOOF** indicates that an email address in the headers is likely to have been spoofed.

EOP has determined that the email probably has a spoof address, and so classified it as spam. The message was moved to the Outlook Junk Email folder on delivery.

The full range of fields and values possible in the anti-spam headers is large. For details, see the **Anti-spam message headers in Microsoft 365** link below.

## Learn more

- [Anti-spam protection in EOP](/microsoft-365/security/office-365-security/anti-spam-protection)
- [Configure anti-spam policies in EOP](/microsoft-365/security/office-365-security/configure-your-spam-filter-policies)
- [Anti-spam message headers in Microsoft 365](/microsoft-365/security/office-365-security/anti-spam-message-headers)
- [Protect against threats](/microsoft-365/security/office-365-security/protect-against-threats)
