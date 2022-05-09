In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, outbound email messages that are sent through EOP are automatically checked for spam and unusual sending activity.

Outbound spam from a user typically indicates a compromised account. Suspicious outbound messages are marked as spam (regardless of the spam confidence level or SCL). These messages are then routed through the [high-risk delivery pool](/microsoft-365/security/office-365-security/high-risk-delivery-pool-for-outbound-messages?azure-portal=true) to help protect the reputation of the service. In other words, to keep Microsoft 365 source email servers off of IP blocklists. Admins are automatically notified of suspicious outbound email activity and blocked users through alert policies.

EOP uses outbound spam policies as part of your organization's overall defense against spam. Admins can view, edit, and configure (but not delete) the default outbound spam policy.

For greater granularity, you can also create custom outbound spam policies that apply to specific users, groups, or domains in your organization. Custom policies always take precedence over the default policy, but you can change the priority (running order) of your custom policies.

You can configure outbound spam policies in the Microsoft 365 Microsoft 365 Defender portal or in PowerShell (Exchange Online PowerShell for Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes).

The basic elements of an outbound spam policy in EOP are:

 -  **The outbound spam filter policy**. Specifies the actions for outbound spam filtering verdicts and the notification options.
 -  **The outbound spam filter rule**. Specifies the priority and sender filters (who the policy applies to) for an outbound spam filter policy.

The difference between these two elements isn't obvious when you manage outbound spam policies in the Microsoft 365 Defender portal:

 -  **Creating a policy**. You're actually creating an outbound spam filter rule and the associated outbound spam filter policy at the same time using the same name for both.
 -  **Modifying a policy**. Settings related to the name, priority, enabled or disabled, and sender filters modify the outbound spam filter rule. All other settings modify the associated outbound spam filter policy.
 -  **Removing a policy**. The outbound spam filter rule and the associated outbound spam filter policy are removed.

Every organization has a built-in outbound spam policy named **Default**. This default policy that has the following properties:

 -  The policy is applied to all senders in the organization. This process occurs even though there's no outbound spam filter rule (sender filters) associated with the policy.
 -  The policy has the custom priority value **Lowest** that you can't modify. As such, the policy is always applied last. Any custom policies that you create always have a higher priority than the policy named **Default**.
 -  You can't delete the default policy.

To increase the effectiveness of outbound spam filtering, you can create custom outbound spam policies with stricter settings that are applied to specific users or groups of users.

### Use the Microsoft 365 Defender portal to create outbound spam policies

Creating a custom outbound spam policy in the Microsoft 365 Defender portal creates the spam filter rule AND the associated spam filter policy at the same time using the same name for both.

1.  In the Microsoft 365 Defender portal at [https://security.microsoft.com](https://security.microsoft.com/), go to **Email &amp; Collaboration &gt; Policies &amp; Rules &gt; Threat policies &gt; Anti-spam** in the **Policies** section.
2.  On the **Anti-spam policies** page, select **Create policy** and then select **Outbound** from the drop-down list that appears.
3.  The policy wizard opens. On the **Name your policy** page, configure these settings:
    
     -  Name: Enter a unique, descriptive name for the policy.
     -  Description: Enter an optional description for the policy.
    
    When you're finished, select **Next**.
4.  On the **Users, groups, and domains** page that appears, identify the internal senders that the policy applies to (recipient conditions):
    
     -  **Users**. The specified mailboxes, mail users, or mail contacts.
     -  **Groups**:
        
         -  Members of the specified distribution groups or mail-enabled security groups.
         -  The specified Microsoft 365 Groups.
     -  **Domains**. All senders in the specified accepted domains in your organization.
    
    Select inside the appropriate box, start typing a value, and select the value that you want from the results. Repeat this process as many times as necessary. To remove an existing value, select the **X** next to the value.
    
    For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.). However, the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.
    
    Multiple values in the same condition use OR logic (for example, *&lt;sender1&gt;* or *&lt;sender2&gt;*). Different conditions use AND logic (for example, *&lt;sender1&gt;* and *&lt;member of group 1&gt;*).
    
    **- Exclude these users, groups, and domains.** To add exceptions for the internal senders that the policy applies to (recipient exceptions), select this option and configure the exceptions. The settings and behavior are exactly like the conditions.
    
    When you're finished, select **Next**.
5.  On the **Protection settings** page that opens, configure the following settings:
    
     -  **Message limits**. The settings in this section configure the limits for outbound email messages from Exchange Online mailboxes:
        
         -  **Set an external message limi**t. The maximum number of external recipients per hour.
         -  **Set an internal message limit**. The maximum number of internal recipients per hour.
         -  **Set a daily message limit**. The maximum total number of recipients per day.
        
        A valid value is 0 to 10000. The default value is 0, which means the service defaults are used. For more information, see [Sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1?azure-portal=true).
        
        Enter a value in the box, or use the increase/decrease arrows on the box.
     -  **Restriction placed on users who reach the message limit**. Select an action from the drop-down list when any of the limits in the Protection settings section are exceeded.
        
        For all actions, the senders specified in the **User restricted from sending email alert** policy receive email notifications.
        
         -  **Restrict the user from sending mail until the following day**. This option is the default value. Email notifications are sent, and the user will be unable to send any more messages until the following day, based on UTC time. There's no way for the admin to override this block.
            
             -  The alert policy named **User restricted from sending email** notifies admins (through email and on the **Incidents &amp; alerts &gt; View alerts** page).
             -  Any recipients specified in the **Notify specific people if a sender is blocked due to sending outbound spam** setting in the policy are also notified.
             -  The user will be unable to send any more messages until the following day, based on UTC time. There's no way for the admin to override this block.
         -  **Restrict the user from sending mail**. Email notifications are sent, the user is added to **Restricted users** in the Microsoft 365 Defender portal, and the user can't send email until they're removed from **Restricted users** by an admin. After an admin removes the user from the list, the user won't be restricted again for that day.
         -  **No action, alert only**. Email notifications are sent.
     -  **Forwarding rules**. Use the settings in this section to control automatic email forwarding by Exchange Online mailboxes to external senders.
        
        Select one of the following actions from the **Automatic forwarding rules** drop down list:
        
         -  **Automatic - System-controlled**. Allows outbound spam filtering to control automatic external email forwarding. This option is the default value.
         -  **On**. Automatic external email forwarding isn't disabled by the policy.
         -  **Off**. All automatic external email forwarding is disabled by the policy.
        
        When automatic forwarding is disabled, the recipient will receive a non-delivery report (also known as an NDR or bounce message) if external senders send email to a mailbox that has forwarding in place. If the message is sent by an internal sender and the forwarding method is [mailbox forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding?azure-portal=true) (also known as *SMTP forwarding*), the internal sender will get the NDR. The internal sender doesn't receive an NDR if the forwarding occurred due to an Inbox rule.
     -  **Notifications**. Use the settings in the section to configure other recipients who should receive copies and notifications of suspicious outbound email messages:
        
         -  **Send a copy of suspicious outbound messages that exceed these limits to these users and groups**. This setting adds the specified recipients to the Bcc field of suspicious outbound messages. This setting only works in the default outbound spam policy. It doesn't work in custom outbound spam policies that you create.
            
            To enable this setting, select the check box. In the box that appears, select inside the box, enter a valid email address, and then press Enter or select the complete value that's displayed below the box.
            
            Repeat this step as many times as necessary. To remove an existing value, select the **X** next to the value.
6.  On the **Review** page that appears, review your settings. You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or select the specific page in the wizard.
    
    When you're finished, select **Create**.
7.  On the confirmation page that appears, select **Done**.

### Use PowerShell to configure outbound spam policies

As previously described, an outbound spam policy consists of an outbound spam filter policy and an outbound spam filter rule. In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately.

In Exchange Online PowerShell or standalone EOP PowerShell, the cmdlets used to configure outbound spam filter policies and outbound spam filter rules are different:

 -  **Outbound spam filter policies**. Use the **\*-HostedOutboundSpamFilterPolicy** cmdlets.
 -  **Outbound spam filter rules**. Use the **\*-HostedOutboundSpamFilterRule** cmdlets.

In PowerShell, you create the outbound spam filter policy first. You then create the outbound spam filter rule that identifies the policy the rule applies to.

When you remove an outbound spam filter policy from PowerShell, the corresponding outbound spam filter rule isn't automatically removed. Similarly, if you remove an outbound spam filter rule from PowerShell, the outbound spam filter policy isn't removed.

Creating an outbound spam policy in PowerShell is a two-step process:

1.  Create the outbound spam filter policy.
2.  Create the outbound spam filter rule that specifies the outbound spam filter policy that the rule applies to. An outbound spam filter rule can't be associated with more than one outbound spam filter policy.

You can configure the following settings on new outbound spam filter policies in PowerShell. These settings aren't available in the Microsoft 365 Defender portal until after you create the policy:

 -  Create the new policy as disabled (*Enabled* `$false` on the **New-HostedOutboundSpamFilterRule** cmdlet).
 -  Set the priority of the policy during creation (*Priority* *&lt;Number&gt;* on the **New-HostedOutboundSpamFilterRule** cmdlet).

> [!NOTE]
> A new outbound spam filter policy that you create in PowerShell isn't visible in the Microsoft 365 Defender portal until you assign the policy to an outbound spam filter rule.

#### Step 1: Use PowerShell to create an outbound spam filter policy

Use the following PowerShell command to create an outbound spam filter policy:

```powershell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

The following example creates a new outbound spam filter policy named **Contoso Executives**. The policy contains the following settings:

 -  The recipient rate limits are restricted to smaller values that the defaults.
 -  After one of the limits is reached, the user is prevented from sending messages.

```powershell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

#### Step 2: Use PowerShell to create an outbound spam filter rule

Use the following PowerShell command to create an outbound spam filter rule:

```powershell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Sender filters> [<Sender filter exceptions>] [-Comments "<OptionalComments>"]
```

The following example creates a new outbound spam filter rule named **Contoso Executives**. The rule contains the following settings:

 -  The outbound spam filter policy (**Contoso Executives)** is associated with the rule.
 -  The rule applies to members of the group named **Contoso Executives Group**.

```powershell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives"
```
