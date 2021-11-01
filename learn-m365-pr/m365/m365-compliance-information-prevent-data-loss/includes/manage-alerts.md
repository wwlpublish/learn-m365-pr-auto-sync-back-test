As noted earlier, part of the DLP policy creation process involves determining if you want to notify anyone when policies are triggered. You make those choices for each DLP policy rule you create. These alerts are displayed in the DLP Alerts (preview) dashboard and are governed by settings you configure in the Incident reports section of each data loss prevention policy rule. You can use the dashboard to both view and manage alerts.

You have flexibility in defining when alerts are sent. One option is to send an alert every time an activity matches the rule. A second option is to only send the alert when a threshold, like the number of times the policy was violated, or the volume of data reaches a specific threshold.

The image below shows the portion of the DLP policy rule configuration process where you specify incident reports. The configuration below sends an email to johannal@tenant.onmicrosoft.com and adds an alert to the DLP Alerts (preview) dashboard. Anyone with the rights to view DLP alerts will see the alert on the dashboard. Only the user(s) listed under Send and alert to admins when a rule match occurs will receive the email.

:::image type="content" source="../media/incident-reports.png" alt-text="Screenshot shows the Incident reports screen. The severity level is set to High and Send an alert is turned on." lightbox="../media/incident-reports.png":::

The image below shows the body of an email produced and sent to johannal@tenant.onmicrosoft.com when the high-severity alert has been triggered based on the configuration above. In this case, the activity that triggered the high-severity alert was a DLP policy that included a rule with an endpoint DLP setting to trigger enforcement when content containing sensitive data was uploaded to the cloud.

:::image type="content" source="../media/high-severity.png" alt-text="Screenshot shows a high severity alert." lightbox="../media/high-severity.png":::

When you click **View Alert Details** in the notification, you see the DLP Alerts (preview) view in the compliance center. Select the event that prompted the alert. (You can also get to the alerts by going to **Data loss prevention** > **Alerts (preview).**)

In this case, we see that the event was a file that included a high volume of U.K. financial data was copied to the cloud. While not shown in the image below, the administrator can initiate a workflow to manage each alert to resolution and/or send an email to another user informing them of the DLP policy violation.

:::image type="content" source="../media/alert-event-details.png" alt-text="Screenshot shows the details for an event that prompted a high severity alert.":::

## Learn more

[Configure and view alerts for DLP policies (preview) | Microsoft Docs](/microsoft-365/compliance/dlp-configure-view-alerts-policies)
