The prior unit examined malicious spoofing (as opposed to legitimate spoofing), whose purpose is to deliver a malicious email. Phishing is similar to malicious spoofing in that the sender of an email masquerades as a trustworthy entity. However, phishing differs from spoofing in that phishing tries to acquire sensitive information such as usernames, passwords, credit card information, social security numbers, and so on.

Phishing attacks come in various forms, from commodity-based attacks to targeted spear phishing or whaling. With the growing complexity of phishing attacks, it's difficult for even a trained eye to identify some of these sophisticated attacks.

By default, Microsoft 365 includes built-in features that help organizations protect its users from phishing attacks. Anti-phishing policies increase this protection; for example, by refining settings to better detect and prevent impersonation and spoofing attacks.

Anti-phishing protection is available in Exchange Online Protection (EOP) for Microsoft 365 organizations without Microsoft Defender for Office 365. Microsoft Defender for Office 365 contains more advanced anti-phishing features.

### Anti-phishing protection in EOP

Exchange Online Protection contains the following features that can help protect your organization from phishing threats:

 -  **Spoof intelligence.** Review spoofed messages from senders in internal and external domains, and allow or block those senders. For more information, see [Configure spoof intelligence in EOP](/microsoft-365/security/office-365-security/learn-about-spoof-intelligence?azure-portal=true).
 -  **Anti-phishing policies in EOP.** Turn spoof intelligence on or off, turn unauthenticated sender identification in Outlook on or off, and specify the action for blocked spoofed senders (move to Junk Email folder or quarantine). For more information, see [Configure anti-phishing policies in EOP](/microsoft-365/security/office-365-security/configure-anti-phishing-policies-eop?azure-portal=true).
 -  **Implicit email authentication.** EOP enhances standard email authentication checks for inbound email (SPF, DKIM, and DMARC) with sender reputation, sender history, recipient history, behavioral analysis, and other advanced techniques to help identify forged senders. For more information, see [Email authentication in Microsoft 365](/microsoft-365/security/office-365-security/email-validation-and-authentication?azure-portal=true).

### Anti-phishing protection in Microsoft Defender for Office 365

Microsoft Defender for Office 365 contains the following advanced anti-phishing features:

 -  **Anti-phishing policies.** Create new custom policies, configure anti-impersonation settings (protect users and domains from impersonation), mailbox intelligence settings, and adjustable advanced phishing thresholds. For more information, see [Configure anti-phishing policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/configure-atp-anti-phishing-policies?azure-portal=true). For more information about the differences between anti-phishing policies in EOP and anti-phishing policies in Microsoft Defender for Office 365, see [Anti-phishing policies in Microsoft 365](/microsoft-365/security/office-365-security/set-up-anti-phishing-policies?azure-portal=true).
 -  **Campaign Views.** Machine learning and other heuristics identify and analyze messages that are involved in coordinated phishing attacks against the entire service and your organization. For more information, see [Campaign Views in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/campaigns?azure-portal=true).
 -  **Attack simulator.** Admins can create fake phishing messages and send them to internal users as an education tool. For more information, see [Attack Simulator in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/attack-simulator?azure-portal=true).

### Managing Anti-phishing policies in Microsoft Defender for Office 365

Anti-phishing is managed in the Security &amp; Compliance Center. The default policy applies to all users within the organization and is a single view where you can fine-tune anti-phishing protection. Custom policies, which can be created and configured for specific users, groups, or domains within the organization, take precedence over the default policy for the scoped users.

There are several prerequisites to managing anti-phishing policies that you must be aware of, including:

 -  You must be a member of the Company administrators or Security admins role group.
 -  Most organizations typically set up multiple anti-phishing policies. Microsoft 365 enforces these policies in the order they're listed on the Anti-phishing page and ATP anti-phishing pages in the Security &amp; Compliance Center. Once you've reviewed the policy options, take some time to determine how many policies you'll need and the priority for each.
 -  Allow up to 30 minutes for your new or updated policy to be propagated to all Microsoft 365 datacenters.

### Anti-phishing policy options in Microsoft Defender for Office 365

As you set up or edit your anti-phishing policies in Microsoft Defender for Office 365, you can choose from several options that provide the most sophisticated and comprehensive protection, as described in the following table.

:::row:::
  :::column:::
    **This setting**
  :::column-end:::
  :::column:::
    **Does this action**
  :::column-end:::
  :::column:::
    **Use when you want to:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add users to protect
  :::column-end:::
  :::column:::
    

Defines which email addresses will be protected by the policy.


**Note**: You can add up to 60 internal and external addresses that you want to protect from impersonation.


  :::column-end:::
  :::column:::
    

Ensure that mail from outside your organization isn't an impersonation of one of the users on the list of users you're protecting. Examples of users you might want to protect are high-level executives, business owners, external board members, and so on.


This list of protected users is different from the list of people to which the policy applies, or rather, for which the policy is enforced. You define the list of people to which the policy applies in the Applied to section of the policy options.


For example, if you add Jenna Glover &lt;jenglov@contoso.com&gt; as a user to protect, then apply the policy to the group “All Users”. This setting would ensure that a mail that appeared to impersonate "Jenna Glover" sent to a user in the “All Users” group would be acted on by the policy.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add domains to protect
  :::column-end:::
  :::column:::
    Allows you to choose which domains you want to protect from impersonation. You can specify that the policy includes all your custom domains, a comma-separated list of domains, or a combination of the two. If you choose the **Automatically include domains that I own** option, and you later add a domain to your Microsoft 365 organization, this anti-phishing policy will be in place for the new domain.
  :::column-end:::
  :::column:::
    Whenever you want to ensure that mail from outside your organization isn't an impersonation of one of the domains defined in your list of verified domains or that of a partner domain.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Choose actions
  :::column-end:::
  :::column:::
    

Choose the action to take when Microsoft 365 detects an impersonation attempt against the users and domains you added to the policy. You can choose different actions for users and domains in the same anti-phishing policy. These actions apply to any incoming email that has been identified by Microsoft 365 as impersonating a user account or domain that is under the protection of this anti-phishing policy. The actions you can choose from include:

 -  **Quarantine message.** Email will be sent to Microsoft 365 quarantine. When you choose this option, the email isn't sent to the original recipient.
 -  **Redirect message to another email address.** Email will be sent to the email address you specify. You can specify multiple email addresses. When you choose this option, the email isn't sent to the original recipient.
 -  **Move message to the recipients' Junk email folder.** Email will be sent to the recipients' Junk email folder. When you choose this option, the email is still sent to the original recipient but isn't placed in the recipient's inbox.
 -  **Deliver the message and add other addresses to the Bcc line.** Email will be delivered to the original recipient. The users you identify will also be added to the bcc line of the message before it's delivered. When you choose this option, the email is still sent to the original recipient's Inbox.
 -  **Don't apply any action.** Email will be delivered to the original recipient's Inbox. No other action will be taken on the email message.
 -  **Turn on phishing protection tips.** Enables anti-phishing safety tips in email.


  :::column-end:::
  :::column:::
    Take an action on messages that Microsoft 365 has determined to be an impersonation of a user or domain as defined in the policy.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Enable mailbox intelligence
  :::column-end:::
  :::column:::
    Enables or disables mailbox intelligence for this policy. You can only enable mailbox intelligence for cloud-based accounts, that is, accounts whose mailbox is hosted entirely in Microsoft 365.
  :::column-end:::
  :::column:::
    When you want to enhance impersonation results for users based on each user's individual sender map. Mailbox intelligence is built around the people you send and receive mail from. This intelligence allows Microsoft 365 to customize the impersonation policy at a user-level to better handle false positive results.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add trusted senders and domains
  :::column-end:::
  :::column:::
    Defines email addresses and domains that won't be considered impersonations by this policy. Messages from the sender email addresses and domains you add as trusted senders and domains won't ever be classified as an impersonation-based attack. As a result, the actions and settings in this policy won't be applied to messages from these senders and domains.
  :::column-end:::
  :::column:::
    When users interact with domains or users that trigger impersonation but are considered to be safe. For example, if a partner has the same/similar display name or domain name as a user defined on the list.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Applied to
  :::column-end:::
  :::column:::
    

Defines the recipients whose incoming email messages will be subject to the rules of the policy. You can create conditions and exceptions for the recipients associated with the policy.


For example, you can create a global policy for your organization by applying the rule to all recipients in your domain.


You can also create exception rules, such as a rule that doesn't scan email messages for a specific group of recipients.


  :::column-end:::
  :::column:::
    Each policy must be associated with a set of users, for example, users in a particular group or domain.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Advanced phishing thresholds
  :::column-end:::
  :::column:::
    

Defines the level of settings for how phishing messages are handled. The options include:

 -  **Standard.** Email suspected to be phishing is handled in the standard way.
 -  **Aggressive**. Email suspected to be phishing with a high or high degree of confidence are handled by the system in the same way.
 -  **More aggressive.** Email suspected to be phishing with a medium, high, or high degree of confidence are handled by the system in the same way.
 -  **Most aggressive.** Email suspected to be phishing with a low, medium, high, or high degree of confidence are handled by the system in the same way.


  :::column-end:::
  :::column:::
    When you want to be more aggressive in the treatment of potential phishing messages within Microsoft 365. For example, messages with a high probability of being phishing emails will have the most aggressive actions taken on them, while messages with a low probability have less aggressive actions taken. This setting also impacts other parts of the filtering system that combine signals together. The chance of moving good messages increases as the level of settings increases.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”