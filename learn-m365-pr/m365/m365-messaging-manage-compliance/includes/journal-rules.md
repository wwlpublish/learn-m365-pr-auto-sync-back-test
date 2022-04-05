Journaling is the ability to record all communications, including email communications, in an organization for use in the organization's email retention or archival strategy. To meet an increasing number of regulatory and compliance requirements, many organizations must maintain records of communications that occur when employees perform daily business tasks.

A journal rule defines which messages to record from which addresses and where to store them (in a journaling mailbox). When a journal rule records a message, it records it with a journal report, which is then submitted to the journaling mailbox. The original message that matches the journal rule is included unaltered as an attachment to the journal report. The body of a journal report contains information from the original message such as the sender email address, message subject, message-ID, and recipient email addresses. This is also referred to as *envelope journaling*, and is the only journaling method supported by Microsoft 365.

>[!NOTE]
> The number of journal rules you can create is determined by which Microsoft license your organization has. Check [Journal, Transport, and Inbox rule limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#journal-transport-and-inbox-rule-limits?azure-portal=true) before you implement journal rules in your production environment.

## Create a journal rule

You can create a journal rule by using the Exchange admin center or by using the `New-JournalRule` Exchange Online PowerShell cmdlet. For this unit, we'll use the Exchange admin center.

1. In the EAC, go to **Compliance management > Journal rules**, and then click **Add +**.
2. Provide a name for the new journal rule, and then compete the following fields:

   - **If the message is sent to or received from**: Specify the recipient that the rule will target. You can either select a specific recipient or apply the rule to all messages.
   - **Journal the following messages**: Specify the scope of the journal rule. You can choose only internal messages, only external messages, or all messages regardless of origin or destination.
   - **Send journal reports to**: Enter the address for the journaling mailbox that will receive all the journal reports.
3. Click **Save** to create the journal rule.

You can modify a journal rule in the Exchange admin center or by using the `Set-JournalRule` cmdlet.

## Enable or disable a journal rule

You can enable or disable a journal rule.

> [!IMPORTANT]
> When you disable a journal rule, the journaling agent will stop journaling messages targeted by that rule. While a journal rule is disabled, any messages that would have normally been journaled by the rule aren't journaled. Make sure that you don't compromise the regulatory or compliance requirements of your organization by disabling a journaling rule.

To enable or disable a journal rule:

1. In the EAC, go to **Compliance management > Journal rules**.
   You'll see a list of the journal rules.
1. To enable a rule, select the check box in the **On** column next to the rule's name.
1. To disable a rule, clear the check box.

## Learn more

[Journaling in Exchange Online](/exchange/security-and-compliance/journaling/journaling?azure-portal=true)
