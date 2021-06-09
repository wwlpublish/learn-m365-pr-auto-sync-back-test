When people work with sensitive content in the desktop versions of Excel, PowerPoint, and Word, policy tips can notify them in real time that the content conflicts with a DLP policy. This design requires that:

 -  The Office document is stored on a OneDrive for Business site or SharePoint Online site.<br>
 -  The site is included in a DLP policy that's configured to use policy tips.<br>

Office desktop apps automatically sync DLP policies directly from Microsoft 365. When a user opens a document, the corresponding desktop application scans the document to ensure that it doesn't conflict with the company's DLP policies. If a conflict occurs, the policy tip is displayed in real time.

> [!NOTE]
> Office desktop apps scan documents themselves to determine if DLP policy tips should be shown. They don't show policy tips that SharePoint Online sites or OneDrive for Business sites have already determined should be shown on a file. As a result, you may not always see a DLP policy tip in the desktop applications that you see in the SharePoint Online sites or OneDrive for Business sites. In contrast, the Office applications on the web only show DLP policy tips that SharePoint Online sites or OneDrive for Business sites have already determined should be shown.<br>

Depending on how you configure the policy tips in the DLP policy, people can choose to either:

 -  ignore the policy tip.
 -  override the policy with or without a business justification.
 -  report a false positive.

Policy tips appear on the desktop application's Message Bar, as seen in the following image.

:::image type="content" source="../media/policy-tip-excel-fba69be6.png" alt-text="screenshot of an excel spreadsheet displaying a policy tip":::


Policy tips also appear in the Backstage view (on the File tab).

:::image type="content" source="../media/policy-tip-backstage-view-553a0e61.png" alt-text="screenshot of a file backstage view showing a policy tip":::


If policy tips in the DLP policy are configured with these options, you can choose **Resolve to Override** a policy tip or **Report a false positive**.

:::image type="content" source="../media/policy-tip-file-info-view-d98c765a.png" alt-text="screenshot of a file backstage view showing a policy tip with options to resolve to override and report a false positive":::


In each of these Office desktop programs, people can choose to turn off policy tips. If they're turned off:

 -  Policy tips that are notifications won't appear on the Message Bar or Backstage view (on the File tab).
 -  Policy tips about blocking and overriding will still appear. Users will still receive the email notification.
 -  The document isn't exempt from any DLP policies that have been applied to it.

### Default text for policy tips in Office desktop apps

By default, policy tips display text similar to the messages displayed in the following table. These messages will be displayed on the Message Bar and Backstage view of an open document. The notification text is configured separately for each rule, so the text that's displayed differs depending on which rule is matched.

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
    This file conflicts with a policy in your organization. Go to the File menu for more information.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Blocks access, sends a notification, and allows override.

  :::column-end:::
  :::column:::
    This file conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked. Go to the File menu for more information.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Blocks access and sends a notification.

  :::column-end:::
  :::column:::
    This file conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked. Go to the File menu for more information.

  :::column-end:::
:::row-end:::


### Custom text for policy tips in Office desktop apps

You can customize the text for policy tips separately from the email notification. Unlike custom text for email notifications, custom text for policy tips doesn't accept HTML or tokens. Instead, custom text for policy tips is plain text only with a 256-character limit.
