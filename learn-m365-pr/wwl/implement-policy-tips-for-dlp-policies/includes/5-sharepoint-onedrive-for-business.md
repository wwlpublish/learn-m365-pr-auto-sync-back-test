When a document on a OneDrive for Business site or SharePoint Online site matches a rule in a DLP policy that uses policy tips, the policy tips display special icons on the document:<br>

 -  If the rule sends a notification about the file, the **Warning** icon appears.
 -  If the rule blocks access to the document, the **Blocked** icon appears.

:::image type="content" source="../media/blocked-and-warning-icons-on-documents-122cdc12.png" alt-text="screenshot showing documents in OneDrive with blocked and warning icons":::


To take action on a document, you can select an item &gt; choose Information icon (the circle with the letter "i" in the middle) in the upper-right corner of the page to open the details pane &gt; **View policy tip**.

:::image type="content" source="../media/view-policy-tip-e328df29.png" alt-text="screenshot of a policy tip displayed for a document":::


The policy tip lists the issues with the content. If the policy tips are configured with these options, you can choose **Resolve**, and then either the **Override the policy tip** or **Report a false positive** option.

:::image type="content" source="../media/policy-tip-with-resolve-override-options-383497a7.png" alt-text="screenshot of a policy tip notification with resolve and override options":::


DLP policies are synced to sites and content is evaluated against them periodically and asynchronously. As a result, there may be a short delay between the time you create the DLP policy and the time you begin to see policy tips. There may be a similar delay from when you resolve or override a policy tip to when the icon on the document on the site goes away.

### Default text for policy tips on sites

By default, policy tips display messages for an item on a site similar to the messages in the following table. The notification text is configured separately for each rule. As a result, the text that's displayed differs depending on which rule is matched.

:::row:::
  :::column:::
    **If the DLP policy rule does this action:**
  :::column-end:::
  :::column:::
    **Then the default policy tip displays this message:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sends a notification but doesn't allow override.

  :::column-end:::
  :::column:::
    This item conflicts with a policy in your organization.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Blocks access, sends a notification, and allows override.

  :::column-end:::
  :::column:::
    This item conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Blocks access and sends a notification.

  :::column-end:::
  :::column:::
    This item conflicts with a policy in your organization. Access to this item is blocked for everyone except its owner, last modifier, and the primary site collection administrator.

  :::column-end:::
:::row-end:::


### Custom text for policy tips on sites

You can customize the text for policy tips separately from the email notification. Unlike custom text for email notifications, custom text for policy tips doesn't accept HTML or tokens. Instead, custom text for policy tips is plain text only with a 256-character limit.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”