Exchange Online uses transport rules to automatically process messages as they pass through your messaging infrastructure. Transport rules consist of four components:

- **Conditions**. You use conditions to determine which messages are managed by a rule.
- **Exceptions**. You define exceptions to determine which messages that meet your conditions should be excepted from the rule.
- **Actions**. You use actions to determine what happens to targeted emails. Actions include forwarding, deleting, adding recipients, and appending disclaimers.
- **Properties**. You define rule properties to control additional rule settings, such as validity period.


You can create mail flow rules in three ways:

- Create a mail flow rule in the Exchange admin center
- Use the `New-TransportRule` Exchange Online PowerShell cmdlet to create a rule
- Create a data loss prevention (DLP) policy

## Determine whether a transport rule or conditional routing rule is affecting mail flow

Since mail flow rules (transport rules) are configured with actions, it's important to know that some actions can prevent a message from being routed as intended by the sender. For example, messages can:

- Be forwarded for approval
- Be redirected
- Be blocked with or without notification
- Have a spam confidence level applied

These and other actions can result in a message not being routed to the intended recipient, or being dropped. The following screenshot displays the message a user received when a mail flow rule blocked the message.

:::image type="content" source="../media/mail-flow-1.png" alt-text="A screenshot that displays a message in Outlook on the web. The message explains why the message was blocked.":::

By tracing messages, you might be able to determine whether a mail flow rule is the cause of a dropped or misdirected message. The following screenshot shows a message trace for failed deliveries. The Events section is shown and identifies the failure and the reason. The name of the transport rule is **Test Rule**.

:::image type="content" source="../media/mail-flow-2.png" alt-text="A screenshot displays a message trace for a message that's been blocked by a mail flow rule. ":::

### Review transport rules

If you suspect that a mail flow rule is the culprit of messages being inappropriately dropped, bounced, or rerouted, then you should review the rules. You can review your existing mail flow rules by using:

- The Exchange admin center
- The `Get-TransportRule` PowerShell cmdlet
- The Microsoft 365 compliance portal

You can also use the Reports node in the Exchange admin center to review existing mail flow rules. In Exchange Admin center, select Mail flow, and then select the Exchange Transport Rule report. This report enables you to view matches for the mail flow rules that are set up for your organization.

### Review conditional routing rules

You can create mail flow rules that can be configured to route messages that meet specific conditions through a specified connector. These rules are known as conditional routing rules.

Typically, conditional routing rules are based on properties of the recipient object. For example, a rule might have the condition:

`The recipient … has specific properties including any of these words.`

The select user properties dialog box is used to select the properties that the recipient must have. For example, you could select **City**, **Country**, or other properties.

> [!TIP]
> Select **More options** to enable this capability.

The rule action would be:

`Redirect the message to …  <connector>.`

Where *connector* is the configured messaging connector.

To review these rules, you use the same procedure for other mail flow rules. The following screenshot displays the property of a mail flow rule that redirects messages to a specified connector.

:::image type="content" source="../media/mail-flow-3.png" alt-text="A screenshot displays a mail flow rule that redirects to a connector. ":::

> [!TIP]
> Use the `get-transportrule | Where-Object {$_.RouteMessageOutBoundConnector -ne $null} | ft Name, RouteMessageOutBoundConnector` command to list all mail flow rules by name that redirect to a named connector.

When you determine that a connector is being used, you should review the connector's configuration and verify that mail can be successfully routed through the connector. Each connector has a **Verify** option.

## Identify rules and policies that are applied during mail flow

To identify rules and policies that apply during mail flow, you should perform a test of mail flow within your organization. By sending messages in and out of your organization, and then performing a message trace against those messages, you can learn which rules and connectors are being used. You should then also validate any connectors you have identified.

## Troubleshoot issues where mail destined for one tenant is incorrectly routed to another tenant

If messages are being incorrectly routed, then you must determine which, if any, connectors are used to route email to those tenants. Then you should validate those connectors.

> [!TIP]
> You can use the Microsoft Remote Connectivity Analyzer to perform both inbound and outbound SMTP tests. 

## Reduce delivery delays

As a messaging administrator, it's your responsibility to try to ensure timely delivery of messages in your organization. There are many things that can impact message delivery time, including mail flow rules.

Mail flow rules can involve a lot of processing, particularly if there are many rules to process. Review the configured rules and, if necessary, consider streamlining the rules to reduce workload for message delivery.

> [!NOTE]
> Note: Consider that email might be delayed due to external issues, such as a problem with a recipient's email system. 

## Learn more

- [Run a message trace in the classic EAC in Exchange Online](/exchange/monitoring/trace-an-email-message/run-a-message-trace-and-view-results)
- [Scenario: Conditional mail routing in Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing)
- [Transport routing in Exchange hybrid deployments](/exchange/transport-routing)
- [Validate connectors in Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors)