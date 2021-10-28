Exchange Online Protection (EOP) is enabled by default for every message in Exchange Online. If your company only has cloud-only users and Exchange Online mailboxes, all messages sent to your organization pass through EOP before your users see them, and you don’t need to configure any special mail routing.

EOP isn't limited to just Exchange Online. There are three different ways of deploying Exchange Online Protection:

 -  **EOP with Exchange Online mailboxes**. This scenario is appropriate if you want EOP protection and all your mailboxes hosted in Exchange Online. It can help you reduce complexity because you don’t have to maintain on-premises messaging servers.
 -  **EOP with on-premises mailboxes (also known as EOP standalone)**. This scenario is appropriate if you have an existing mail-hosting infrastructure you want to use. It's also used when an organization's business requirements require that it keep mailboxes on-premises.
 -  **EOP with Exchange hybrid deployment**. Some organizations want cloud mailboxes in Exchange Online for most of their users, but they also want to keep some mailboxes on-premises only for certain users.

### Considerations for configuring your mail flow using EOP

Before you start the actual configuration of your mail routing, you should first review your mail flow requirements and answer the following questions:

 -  **Inbound mail flow.** Do you still want to use your on-premises anti-spam solution for inbound mail flow, or do you want to replace it with EOP completely?
 -  **Outbound mail flow.** Do you want to route outbound mail flow over your on-premises solution, or should all mail be routed over EOP equally?
 -  **Secure messaging with a trusted partner.** Do you use connectors with mandatory TLS encryption with a trusted partner that you need to consider?
 -  **Conditional mail routing.** Do you want to route emails for a defined recipient domain, or from a defined security group of senders over EOP?
 -  **Anti-spoofing.** Are you already using anti-spoofing solutions such as SPF, DKIM, and DMARC that you need to reconfigure when adding another trusted system like EOP to your mail flow?

Once you answer these questions, you’ll have a better idea as to your mail routing needs, and you can start configuring your solution.

### Configure mail flow using EOP with Exchange Online mailboxes

When all your users have mailboxes in Exchange Online and all your domain’s MX-records point to Microsoft 365, EOP is already set up to scan your inbound and outbound messages. No other configuration is necessary and no on-premises systems are present that you need to consider.

### Configure mail flow using EOP Standalone or a hybrid deployment

When analyzing whether to use EOP standalone or hybrid, you can decide for yourself if you want to replace your on-premises solution, or if you want to use both simultaneously to add a second layer to your mail protection.

> [!CAUTION]
> You can use two layers of anti-spam and email protection, but keep in mind that each solution uses its individual scanning and quarantine settings. As a result, implementing two solutions together can cause unpredictable mail flow issues when the scanning and quarantine settings of each solution conflict with one another. As a result, it’s recommended that organizations use EOP as their exclusive in- and outbound solution for message protection.

If you want to use EOP and you're still running your own email servers, whether they're on-premises or in a private cloud outside Microsoft 365, you must set up connectors to enable mail flow between EOP and your environment. For a hybrid deployment, those connectors are created by the Hybrid Configuration Wizard (HCW). For EOP standalone, you must create them yourself.

The following diagram shows how connectors work to switch your mail routing to EOP:

:::image type="content" source="../media/connectors-exchange-online-protection-866aa7b0.png" alt-text="diagram showing how connectors work to switch your mail routing to EOP":::


For connecting your on-premises environment to EOP, you must consider the role that the following connectors play in routing messages:

 -  **EOP outbound connector.** Delivers emails to your on-premises mail servers.
 -  **EOP inbound connector.** Accepts emails from your on-premises mail servers.
 -  **On-premises connector.** Send connector to send all outgoing mail to EOP.

Connectors are responsible for routing messages within an organization's controlled environment. However, in the outside world that includes the Internet, messages aren't routed using connectors. Instead, message routing uses MX records. Mail servers deliver email for domains to the servers that are resolved by checking the public domains’ MX records. As a result, an organization must configure its MX records for delivering messages to EOP or on-premises.

When EOP is implemented in a hybrid environment, it can be administered by using either the Exchange Admin Center or Windows PowerShell. However, if you're using EOP standalone, you can only use PowerShell cmdlets to configure your service.

**Additional reading**. For more information, see [Set up connectors to route mail between Office 365 and your own email servers](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”