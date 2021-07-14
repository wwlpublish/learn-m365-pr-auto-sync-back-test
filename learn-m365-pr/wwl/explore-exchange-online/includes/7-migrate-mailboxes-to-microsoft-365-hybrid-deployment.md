The following scenarios describe different ways a hybrid environment can distribute email. Each scenario describes a unique request for handling email, followed by a recommended solution.

### Scenario 1: MX record points to Microsoft 365, and Microsoft 365 filters all messages.

**Situation:** I'm migrating my organization’s mailboxes to Microsoft 365. I want to:

 -  keep some mailboxes on our existing on-premises mail server.
 -  use Microsoft 365 as my spam filtering solution.
 -  send messages from my on-premises server to the Internet by using Microsoft 365. Microsoft 365 will send and receive all messages.

**Recommendation:** Most customers who need a hybrid mail flow setup should allow Microsoft 365 to do all their filtering and routing. It's recommended that you point your MX record to Microsoft 365 because this design provides for the most accurate spam filtering. For this scenario, your organization's mail flow setup will appear similar to the following diagram.

:::image type="content" source="../media/hybrid-mail-flow-scenario-1-72c3104d.png" alt-text="graphic showing hybrid mail flow in which the MX record points to Microsoft 365, and Microsoft 365 filters all messages":::


### Scenario 2: MX record points to Microsoft 365, and mail is filtered on-premises.

**Situation:** I'm migrating my organization’s mailboxes to Microsoft 365, and I want to keep some mailboxes on our existing mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises environment. All messages that come from the Internet to my cloud mailboxes, and the messages sent to the Internet from my cloud mailboxes, must route through my on-premises servers.

**Recommendation:** If you have business or regulatory reasons for filtering mail in your on-premises environment, it's recommended that you point your domain's MX record to Microsoft 365 and enable centralized mail transport. This setup provides optimal spam filtering and protects your organization's IP addresses. For this scenario, your organization's mail flow setup looks like the following diagram.

:::image type="content" source="../media/hybrid-mail-flow-scenario-2-0c358570.png" alt-text="graphic showing hybrid mail flow in which the MX record points to Microsoft 365, and centralized mail transport is enabled":::


### Scenario 3: MX record points to on-premises servers.

**Situation:** I'm migrating my organization’s mailboxes to Microsoft 365, and I want to keep some mailboxes on our existing mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages that come from the Internet to my cloud mailboxes, and the messages sent to the Internet from cloud mailboxes, must route through my on-premises servers. I need to point my domain's MX record to my on-premises server.

**Recommendation:** As an alternative to Scenario 2, you can point your domain's MX record to your organization's mail server instead of to Microsoft 365. Some organizations have a business or regulatory need for this setup, but filtering typically works better if you use Scenario 2. For this scenario, your organization's mail flow setup looks like the following diagram.

:::image type="content" source="../media/hybrid-mail-flow-scenario-3-9c4a9968.png" alt-text="graphic showing hybrid mail flow in which the MX record points to the on-premises server, and filtering happens on-premises":::


### Scenario 4: MX record points to on-premises server, which filters and provides compliance solutions for messages. On-premises server relays messages to the internet through Microsoft 365.

**Situation:** I'm migrating my organization’s mailboxes to Microsoft 365, and I want to keep some mailboxes on our existing mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages sent from my on-premises server must relay through Microsoft 365 to the internet. I need to point my domain's MX record to my on-premises server.

**Recommendation:**  The MX record for your domain needs to point to your on-premises IP address. To accomplish this task, use the following best practices:

1.  Add your custom domains in Microsoft 365. To prove that you own the domains, follow the instructions in [Add users and domains](/microsoft-365/admin/setup/add-domain).
2.  [Create user mailboxes in Exchange Online](https://technet.microsoft.com/library/jj907304%28v=exchg.150%29.aspx?azure-portal=true) or [move all users' mailboxes to Office 365](/Exchange/mailbox-migration/mailbox-migration).
3.  Update the DNS records for the domains that you added in step 1. (If you're unsure how to do update the DNS records, follow the instructions on [this page](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).) The following DNS records control mail flow:
    
     -  **MX record**: Point your MX record to your on-premises server in the following format: mail.&lt;domainKey&gt;.com For example, if your domain is contoso.com, the MX record should be: .mail.contoso.com.<br>
     -  **SPF record**: This record should list Microsoft 365 as a valid sender. It should also include any IP addresses from your on-premises servers that connect to EOP and any third parties that send email on behalf of your organization. For example, if your organization's mail server's Internet-facing IP address is 131.107.21.231, the SPF record for contoso.com should be:<br>v=spf1 ipv4: 131.107.21.231 include:spf.protection.outlook.com -all<br>
4.  In the Exchange Admin Center, use the connector wizard to [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx?azure-portal=true) for the following scenarios:
    
     -  Sending mail from Microsoft 365 to your organization's mail servers.
     -  Sending mail from your on-premises servers to Microsoft 365. In this case, you need to create a connector if any of the following scenarios apply to your organization:
        
         -  Your organization is authorized to send mail on behalf of your client, but your organization doesn't own the domain. For example, contoso.com is authorized to send email through fabrikam.com, which doesn't belong to contoso.com.
         -  Your organization relays non-delivery reports (NDRs) to the Internet through Microsoft 365.
         -  The MX record for your domain, contoso.com, points to your on-premises server, and users in your organization automatically forward messages to email addresses outside your organization. For example, kate@contoso.com has forwarding enabled, and all messages go to kate@tailspintoys.com. If john@fabrikam.com sends a message to kate@contoso.com, by the time the message arrives at Microsoft 365 the sender domain is fabrikam.com and the recipient domain is tailspin.com. The sender domain and the recipient domain don't belong to your organization.

:::image type="content" source="../media/hybrid-mail-flow-scenario-4-710c2994.png" alt-text="graphic showing hybrid mail flow in which the MX record points to the on-premises server, filtering happens on-premises, and Microsoft 365 sends messages to the internet":::
