To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personal information like credit card numbers or health records. With a data loss prevention (DLP) policy in the Microsoft 365 Defender portal, you can identify, monitor, and automatically protect sensitive information.

DLP policies are simple packages that contain sets of conditions, which are made up of mail flow rule conditions, exceptions, and actions that you create in the Exchange admin center (EAC) and then activate to filter email messages and attachments.

>[!CAUTION]
> You should enable your DLP policies in test mode before running them in your production environment. During such tests, it is recommended that you configure sample user mailboxes and send test messages that invoke your test policies in order to confirm the results.

## Configure a DLP policy from a template

Microsoft Exchange includes DLP policy templates. These templates contain pre-built sets of rules that can help you manage message data that is associated with several common legal and regulatory requirements. For example, Exchange includes templates to help you manage Gramm-Leach-Bliley Act (GLBA) data.

You can customize any of these DLP templates or use them as-is. DLP policy templates are built on top of mail flow rules that include new conditions or predicates and actions. DLP policies support the full range of traditional mail flow rules, and you can add the additional rules after a DLP policy has been established.

1. In the EAC, go to **Compliance management > Data loss prevention**, and then click **Add**.

2. Enter a name and description for the new policy.
3. Choose the template you want to use for this policy.
4. Select the mode or state. The new policy is not fully enabled until you specify that it should be. The default mode for a policy is **test without notifications**.
5. Click **Save** to finish creating the policy.

In addition to the rules including in a specific template, your organization may have additional expectations or company policies that apply to regulated data in your messaging environment. You can modify the basic templates to add actions so that your Exchange messaging environment complies with your own requirements.

After you save this new rule, you can edit the rules within the rule. For example, you might make specific people exempt from a policy. Another example is sending a notice and blocking delivery for any messages with sensitive content.

Some policies allow the addition of rules that invoke RMS for messages. You must have RMS configured on the Exchange server before adding the actions to make use of these types of rules.
For any of the DLP policies, you can change the rules, actions, exceptions, enforcement time period or whether other rules within the policy are enforced, and you can add your own custom conditions for each.

## Create a custom DLP policy

You can use a custom data loss prevention (DLP) policy to establish conditions, rules, and actions that can help meet the specific needs of your organization that may not be covered in one of the existing DLP templates.

To create a custom DLP policy without any existing rules:

1. In the EAC, go to **Compliance management > Data loss prevention**. Any existing policies that you have configured are shown in a list.
1. Click the arrow that is next to **Add +**, and select **New custom policy**.
    >[!NOTE]
    > If you click **Add +** instead of the *arrow*, you'll create a new policy *based on a template*.
1. Enter a name and description for the new rule.
1. Select the mode or state for this policy. The new policy is not fully enabled until you specify that it should be.
1. Click **Save** to create the new policy.
   Next you'll add rules or actions.
1. Double-click the policy that you just created. (You can also right-click the policy, and then select **Edit**).
1. On the **Edit DLP policy** page, click **Rules**.
1. Click **Add +** to add a blank rule. You can establish conditions by using all the traditional mail flow rules as well as the sensitive information rules.
In order to avoid confusion, use a unique name for each part of your policy or rule.
1. To add a new rule about sender notification or allowing overrides, click the *arrow* next to **Add +**.
1. Click **More options** to add additional conditions and actions for this rule, including time-bound limits of enforcement or effects on other rules in this policy.
1. Click **Save** to save your changes.

## Policy Tips in Exchange Online

Policy Tips are informative notices that are displayed to email senders while they're composing a message. You can use Policy Tips to alert users that they might be violating the business practices or regulations that you're enforcing with DLP policies.

To show Policy Tips to your email senders, add the **Notify the sender with a Policy Tip** action to your DLP policy rules. You can add this in the rules editor from the Exchange admin center.

You can add different types of Policy Tips - notify-only, block-message, or block-unless-override. 

### Create a notify-only Policy Tip to alert a user about sensitive information

1. In the EAC, in **Compliance management > Data loss prevention**, select the DLP policy that you want to add the Policy Tip to, and then select **Edit**.
1. On the **Edit DLP policy** page, select **Rules**.
1. To add a Policy Tip to an existing rule, highlight the rule, and select **Edit**.
   To add a new blank rule that you can fully customize, select **Add**, and then select **Create a new rule**.
1. Set **Apply this rule if** to **The message contains sensitive information**. This condition is required.
1. Select **Add**, and then select the sensitive information types you want the Policy Tip to flag. Select **Add**, then select **OK** and **OK** again.
1. Set **Do the following** to **Notify the sender with a Policy Tip**. Select an option in the **Choose whether the message is blocked or can be sent** list, and then select **OK**.
1. If you want to add additional conditions or actions, at the bottom of the window, select **More options**. You can use the following conditions with Policy Tips:
    - **The recipient is** (SentTo)
    - **The recipient is located** (SentToScope)
    - **The sender is** (From)
    - **The sender is a member of** (FromMemberOf)
    - **The sender is located** (FromScope)  

    You *can't* use the following actions:
    - **Reject the message and include an explanation** (RejectMessageReasonText)
    - **Reject the message with the enhanced status code of** (RejectMessageEnhancedStatusCode)
    - **Delete the message without notifying anyone** (DeleteMessage)
1. In **Choose a mode for this rule list**, select whether you want the rule to be enforced. It's a good idea to test the rule first.
1. Select **Save** to finish modifying the rule and save your changes.

### Create a block-message or a block-unless-override Policy Tip

Use a block-message Policy Tip with a rule that blocks sending a message with a problematic condition. You create the Policy Tip the same as the notify-only Policy Tip, but in addition to the **Notify the sender with a Policy Tip** action, also choose the **Block the message** action.

You can also create a policy that blocks a message from leaving the sender's outbox but also includes a user override. To do so, when you choose the action, select **Notify the sender with a Policy Tip** and **Block the message, but allow the sender to override and send**.

## Learn more

- [Create a DLP policy from a template](/exchange/security-and-compliance/data-loss-prevention/create-dlp-policy-from-template?azure-portal=true)
- [Integrating sensitive information rules with mail flow rules](/exchange/security-and-compliance/data-loss-prevention/integrate-sensitive-information-rules?azure-portal=true)
- [Policy Tips](/exchange/security-and-compliance/data-loss-prevention/policy-tips?azure-portal=true)
- [Video – Turn on & customize DLP policy tips for email](https://www.microsoft.com/videoplayer/embed/dd629bb7-063d-49f3-b7e1-8f2e0aa4de13?autoplay=false?azure-portal=true)
