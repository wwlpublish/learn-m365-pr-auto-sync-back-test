In a hybrid deployment, you usually have mailboxes hosted on both on-premises Exchange Servers and in Exchange Online in the cloud. This arrangement can cause extra issues with email delivery for you to resolve.

In your digital camera manufacturing company, mail flow was working well in your on-premises Exchange Server organization. Now that you've started the migration to Exchange Online, some e-mails are not reaching their intended destination and you need to diagnose why.

Here, you'll learn how to investigate the email headers that might store diagnostic information in a hybrid deployment and troubleshoot issues with network applications and certificates.

## Hybrid components

In a hybrid Exchange deployment, you have Exchange Online in the cloud and Exchange Servers on-premises. Mailboxes, public folders, and other recipients can be in both cloud and on-premises environments. To users, the hybrid deployment appears to be a single Exchange system, with one global address list, unified DNS domains, and no barriers to communication between mailboxes regardless of their location. Hybrid deployments are sometimes used to enable a gradual migration from Exchange Server to Exchange Online or to support a long-term cloud and on-premises email strategy.

Hybrid Exchange deployments use the following components to create seamless experiences for users:

- **Hybrid Configuration Wizard (HCW).** When you set up your hybrid Exchange system, you use the HCW to gather all the required information, to create all the necessary objects, and to configure the on-premises and cloud systems.
- **Azure AD Connect.** Azure AD Connect is used to synchronize user and recipient data between your on-premises Active Directory Forest and Azure Active Directory.
- **Hybrid Agent.** The Hybrid Agent removes some of the challenges you can face when you configure an Exchange Hybrid environment. The agent, which is built on the same technology as the Azure Application Proxy, removes some requirements for external DNS entries, certificate updates, and inbound network connections through your firewall to enable Exchange hybrid features. These features include Free/Busy sharing and online mailbox moves. The Hybrid Agent supports free/busy and mailbox migrations. Mail flow, directory synchronization, and other hybrid features are not included.

> [!NOTE]
> It's beyond the scope of this troubleshooting course to describe the complete functionality and setup of a hybrid Exchange organization. For more information, see the links in the Learn more section below.

If email is not reaching the right recipients in your hybrid system, use the following sections in this unit to investigate the problem. For other hybrid problems, see later units in this module.

## Transport options

In a hybrid Exchange deployment, an email's route to its recipient depends on the location of the recipient:

- If a message is sent between mailboxes in your Exchange Online system and Exchange Server on-premises, it's an internal email.
- If a message is sent to a mailbox in Exchange Online or Exchange Server from an address outside your organization, it's an external incoming email.
- If a message is sent from a mailbox in Exchange Online or Exchange Server to an address outside your organization, it's an external outgoing email.

Internal emails are authenticated, encrypted, and transferred using Transport Layer Security (TLS) between on-premises Exchange Servers and Exchange Online.

You must decide and document whether incoming email should arrive first at Exchange Online, or at Exchange Server on-premises. Implement this decision by using your DNS MX records.

When you complete the HCW, you choose how outgoing mail is routed:

- **Through Exchange Online.** This configuration is recommended for organizations without specific compliance requirements around mail transport because it doesn't place extra load on your on-premises servers.
- **Through Exchange Server on-premises.** This arrangement is known as **Centralized mail transport**. With centralized mail transport, you can route all mail from mailboxes in an Exchange Online organization through the on-premises organization before they are delivered to the Internet. Centralized mail transport is only recommended for organizations with specific compliance-related transport needs. Use this configuration when in compliance scenarios where all mail to and from the Internet must be processed by on-premises servers.

If you experience problems with mail flow in your hybrid system, start your troubleshooting process by checking where incoming mail should arrive in your organization and whether outgoing mail is supposed to flow through Exchange Server on-premises or Exchange Online. This information will help you to understand where problems might arise.

## Hybrid configuration log

A good place to start your troubleshooting for any problem in hybrid Exchange is to check the hybrid configuration log. When you complete the HCW to establish your hybrid system, the tool stores all the changes it makes in the log file. You can compare the contents of this file to your plan to check whether the HCW was completed correctly.

The HCW creates the log on the on-premises Exchange server where the HCW was run and within the user profile for the administrator who ran the HCW. The default location is: **%UserProfile%\AppData\Roaming\Microsoft\Exchange Server Configuration**.

## Headers

As for emails in any SMTP system, emails headers are important for diagnosing mail flow issues in Exchange hybrid. There are two headers that relate to specific hybrid mail flow decisions made by Exchange. If you have mail flow problems in a hybrid deployment, examine these headers and check that their behavior is as described:

### X-MS-Exchange-Organization-MessageDirectionality

This header can have one of two values:

- **Originating.** Exchange marks a message as originating if it was sent from one of your on-premises Exchange servers or from one of your Exchange Online mailboxes.
- **Incoming.** Exchange marks a message as incoming if it was sent to an accepted SMTP domain but doesn't match a tenant connector of type **OnPremises**.

When you run the HCW, it creates a tenant connector of type OnPremises that is used to deliver mail to the on-premises Exchange Servers.

### X-MS-Exchange-Organization-AuthAs

This header can have one of two values:

- **Internal.** Exchange marks a message as internal if it was sent by an authenticated client, including Outlook connected to a mailbox or through the SMTP AUTH protocol.
- **Anonymous.** Exchange marks a message as anonymous if it was sent without authentication. For example, messages from external SMTP servers and relays or messages submitted to an SMTP pickup directory are marked as anonymous.

Messages that arrive in Exchange Online from Exchange Servers in a hybrid organization should be marked as internal. That's because, when HCW creates the inbound connector from Exchange on-premises to Exchange Online, it sets the **CloudServiceMailEnabled** property to **True**.

## Systems between Exchange Online and Exchange Server

You shouldn't place any systems that modify SMTP headers between on-premises and cloud servers in your Exchange hybrid system. A firewall that permits traffic on TCP port 25 is supported if it makes no changes to SMTP headers.

Some more sophisticated mail filtering and security solutions might change headers and cause problems with mail flow in your hybrid organization. If the message is not marked as originating and internal, Exchange treats it as incoming and anonymous, which means it will be subject to anti-spam filtering by Exchange Online Protection, transport rules might be applied, and other policies might take action.

The result might be that messages from your own users, sent with proper authentication from Outlook clients, might be sent to junk email folders or to quarantine when they should be considered secure.

## Certificates to secure email flow

Certificates are used for several purposes in an Exchange hybrid system to secure communications between cloud and on-premises servers. If you're troubleshooting mail flow problems, investigate the certificates that secure the TLS communications between on-premises and cloud Exchange servers. These certificates must:

- Have been issued by a third-party certificate authority that is trusted by both Exchange Online and the on-premises servers.
- Include the SMTP protocol in the list of assigned services in the certificate.
- Be installed on the on-premises servers.
- Not have passed their expiration date.

Use the Certificates management console on on-premises Exchange Servers to make these checks. Alternatively, you can use the `Get-ExchangeCertificate` cmdlet in PowerShell:

``` PowerShell
Get-ExchangeCertificate | FL
```

In the results, check that:

- `IsSelfSigned` returns `False`.
- `RootCAType` returns `ThirdParty`.
- `Services` returns values that include `SMTP`.
- `NotAfter` returns a date in the future.
- `Status` returns valid.

## Learn more

- [Exchange Server hybrid deployments](/exchange/exchange-hybrid)
- [Transport routing in Exchange hybrid deployments](/exchange/transport-routing)
- [Transport options in Exchange hybrid deployments](/exchange/transport-options)
- [Demystifying and troubleshooting hybrid mail flow: when is a message internal?](https://techcommunity.microsoft.com/t5/exchange-team-blog/demystifying-and-troubleshooting-hybrid-mail-flow-when-is-a/ba-p/1420838)
- [Troubleshoot a hybrid deployment](/exchange/hybrid-deployment/troubleshoot-a-hybrid-deployment)
- [Certificate requirements for hybrid deployments](/exchange/certificate-requirements)