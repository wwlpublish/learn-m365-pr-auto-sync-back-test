It's important that you monitor alerts raised by Cloud App Security. Alerts are your entry point into identifying potential security threats and other issues within your apps.

## Alert types

To help you monitor and investigate suspicious or malicious activity, there are a large number of alert types, some of which are listed below:

- Compromised account
- Inactive account
- New admin user
- New admin location
- Suspicious activity
- Impossible travel alert 
- Mass admin activity alert
- Suspicious IP address alert

## Work with alerts

You can easily review your apps by selecting **Alerts** in the navigation pane of the Cloud App Security portal.

:::image type="content" source="../media/alerts-2.png" alt-text="A screenshot of the Alerts page in the Cloud App Security portal.":::

If you can tell at a glance that the alert is of little interest, you can select the **Action** (ellipsis) button. Choose between:

- Close as false positive. Select this reason if you confirm the activity is not malicious.
- Close as benign. Select this option if you decide that the activity is suspicious, but not malicious.
- Close as true positive. Select this reason if you determine the activity is malicious.

> [!TIP]
> When you close an alert, you are prompted to give a reason. You can also select the option to send Microsoft feedback about the alert and its closure.

Alternatively, to review the details, select the alert in which you're interested. After reviewing the details, select the **Close alert** button. Then choose **False positive**, **Benign**, or **True positive**. You can also select the Action (ellipsis) button and select either:

- Mark as unread. Choose this option if you want to investigate further, but don't want the alert to be dismissed until you have done so.
- Adjust policy. Choose this option if you want to make changes to the policy that resulted in the alert, perhaps to improve future alert matches.

In the screenshot below, the administrator is resolving an alert relating to an Activity from infrequent country.

:::image type="content" source="../media/dismiss-alert.png" alt-text="A screenshot of the detail page for an Activity from infrequent country alert. The administrator has selected the **Action** button and is about to adjust the policy from which the alert was raised.":::

To adjust the policy, select **Adjust policy** from the **Actions** list. The policy opens. Depending on the policy type, you can change the details such as Scope, Alerts, and Governance actions.

> [!TIP]
> The number of open alerts of detected by the policy is displayed in the upper right of the Edit policy page.

After you resolve an alert, the Alerts page displays updated information. You can use the STATUS option to review alerts that are OPEN or CLOSED, or both. When reviewing CLOSED alerts, the Resolution type is updated with the reason you gave for the closure. You can also choose to filter Alerts using the Resolution type. For example, the following screenshot displays the available options for Resolution type.

:::image type="content" source="../media/resolution.png" alt-text="A screenshot of the Alerts page. The administrator has entered an advanced query for Resolution type. ":::
