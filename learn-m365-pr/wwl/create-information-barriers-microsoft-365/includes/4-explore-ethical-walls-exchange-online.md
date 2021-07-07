An information barrier specific to Exchange Online is referred to as an ethical wall. It's a zone of non-communication between distinct departments of a business or organization. This zone is established to help prevent conflicts of interest that might result in the inappropriate release of sensitive information.

An ethical wall typically spans multiple methods of communication, such as telephone, e-mail, postal mail, and direct person-to-person communication. To make sure that no communication occurs between those users regulated by an ethical wall, some organizations go so far as to place entire departments on separate floors, or even in separate buildings, and to require that employees use separate entrances.

The following graphic shows what happens when users of the same company are restricted from sending messages to each other, but they still attempt to send each other mail. In this scenario, an NDR doc is returned back to the users who sent the mail once the mail hits the wall.

:::image type="content" source="../media/restricted-users-sending-email-df02bdfb.jpg" alt-text="graphic shows what happens when restricted users in a company still try to email one another":::


One example of where an ethical wall could be used is in an investment organization. Brokers aren't allowed to talk to market researchers who may have information that isn't available to the public. Because market researchers may have confidential information that could influence a broker, regulatory requirements frequently state that those two groups must be prevented from communicating in any way.

Exchange transport rules can be configured to support ethical walls by helping to prevent email messages from being sent between specific groups of recipients within your organization.

**Additional reading.** For more information about Exchange transport rules in Exchange Online, see [Mail flow or transport rules](https://technet.microsoft.com/library/jj919238%28v=exchg.150%29.aspx?azure-portal=true).

Exchange includes features that can help you prevent breaches of an ethical wall. However, Exchange can't prevent individuals from using other methods of communication to share information, such as:

 -  Private email accounts located outside the Exchange organization
 -  Network file shares
 -  Phone calls

> [!IMPORTANT]
> Given this situation, Exchange transport rules should be but one part of an overall suite of tools or processes that are deployed throughout your organization to help enforce an ethical wall policy.

One of the following options can be selected when creating a transport rule. These options control what happens to the message that the specified users try to send to one another.

 -  **Block.** The message is rejected, and a non-delivery report (NDR) is returned to the sender. This option also allows you to enter customized text that explains why the message was rejected. This text is displayed in the NDR that is returned to the sender.
 -  **Moderate.** The message is sent to a moderator for approval. If the moderator approves the message, it's sent to the recipient. If the moderator rejects the message, it isn't sent to the recipient. If you specify more than one moderator in the transport rule, only one of them needs to approve or reject the message. If multiple moderators respond, the first decision is applied, and all future decisions are ignored.

In a typical configuration, when a sender tries to send a message to a recipient who is on the other side of an ethical wall, Exchange rejects the message and returns an NDR to the sender. By default, the NDR informs the sender that their message couldn't be delivered because of policy restrictions.<br>

However, you can easily modify the NDR by customizing the delivery status notification (DSN) code and message that are used in the NDR. This process enables you to provide the sender with specific instructions or hypertext links that relate directly to the policies or regulations that prevented delivery.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”