The previous unit examined the steps you must complete in the New DLP policy wizard to choose locations to protect. This unit picks up in the wizard where the previous unit left off.

9.  The next page of the **New DLP policy** wizard, the **Policy settings** tab, displays the template’s default DLP rules. You can accept the default settings for conditions and actions or select **Use advanced settings** to create custom rules.
10. Select **Next**.
11. On the next screen you can select the actions, if the conditions from the previous screen apply. This example leaves the actions for the rules as they are.

12. Select **Next**.

The options on the **Policy settings** page are outlined in the following table.

:::row:::
  :::column:::
    

**Option**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Show policy tips to users and send them an email notification.


  :::column-end:::
  :::column:::
    

With this option, you can control whether users receive a policy tip in their application and an email notification when the conditions apply, and sensitive content is recognized.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Detect when content that’s being shared contains: At least 10 instances of the same sensitive information type (default value).


  :::column-end:::
  :::column:::
    

This threshold value separates the **Low** and **High** rules.

 -  If fewer than 10 instances (default) of the sensitive data are recognized, the **low** rule is applied.
 -  If there are 10 or more instances (default) of sensitive data, the **high** rule is applied.

With this option, you can separate between low and high violations of your DLP policy and define more or different actions for high violations.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Send incident report in email.


  :::column-end:::
  :::column:::
    

If the high rule violation is detected, send an incident report to the administrator or other custom recipients.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Restrict who can access the content and override the policy.


  :::column-end:::
  :::column:::
    

Restrict access to the elements with a high rule violation. You can also configure an Override option with an optional justification the user has to enter.


  :::column-end:::
:::row-end:::


<br>The wizard continues in the next unit, at which point you'll complete the policy and review the policy settings.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”