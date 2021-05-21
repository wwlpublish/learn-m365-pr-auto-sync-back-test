The previous unit examined the steps required to update user notifications for an existing policy. This unit continues the update process. In this example, it focuses on a user's ability to override a message block.

User notifications are effective in educating users about an organization’s compliance requirements. But DLP was also designed to achieve compliance by not interrupting or delaying the business workflow. This goal is accomplished by enabling an administrator to configure user overrides so that users can override a block with a business justification.

The following figure displays an email from a user to someone outside of their organization. Because this user has attached a document that includes the personal credit card information of other employees, a policy tip is automatically displayed along with an override option. The policy tip indicates that the email won't be sent unless the user selects the override option to bypass the organization’s policy.

:::image type="content" source="../media/email-message-with-policy-tip-60115b29.png" alt-text="screenshot of an email message showing a policy tip":::


The previous example showed a policy tip being applied to an email sent through Exchange. This next example is a policy tip displayed within an Excel spreadsheet document. In this case, an override notification is displayed in the **Backstage** view on the **File** tab.

:::image type="content" source="../media/excel-backstage-view-with-policy-tip-75e9538c.png" alt-text="screenshot of a policy tip displayed within the backstage view of an Excel spreadsheet document":::


### Assigning User overrides to a policy

When defining the actions for a rule, restricting access is only enforced in the **High volume of content detected** rule. The default action in the **Low volume of content detected** rule is to notify the user. In this continuing example, you'll update the policy by customizing the user overrides setting in the **Low volume of content detected** rule. You'll turn on the setting and require a business justification to override the policy.

26. In the list of tabs across the top of the **Low volume of content detected** window, select **User overrides**.
27. In the **User overrides** section, select the toggle switch to turn user overrides **On**.<br>:::image type="content" source="../media/policy-tip-override-pane-0c842193.png" alt-text="screenshot showing user overrides pane":::
    
28. Turning this switch **On** displays two user override options. Select the **Require a business justification to override** checkbox.<br><br>:::image type="content" source="../media/policy-tip-override-options-07fe6552.png" alt-text="screenshot showing user overrides options":::
    

You'll continue updating the policy in the next unit, which covers incident reports.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”