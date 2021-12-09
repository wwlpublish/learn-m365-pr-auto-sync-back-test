Microsoft 365 Defender, when it creates a new incident or if there's an update on an existing incident, can send an email notification to you or your security team. This email contains:

- The incident name
- The severity level
- The category of incident

Once you get the notification, you can go directly to the incident from the email and start your management and investigation right away.

## Permissions

To enable and configure email notifications, either you or a member of your security will need to have the **manage security settings** permission. Alternatively, any user with either Security Administrator or Global Administrator roles can set them up for you.

## Create rules for incident notifications

To start receiving notifications for new or progressing incidents, you'll need to create a new rule. Follow these steps to create a new rule and customize email notification settings.

1. From the Microsoft 365 Defender service
1. Select **Settings** then select **Microsoft 365 Defender**, and finally select **Incident email notifications**.
1. Next, you'll need to add an item. On the **Name email notification rule** page, provide:
   1. The **rule name**
   1. A **description** of the rule.
1. Next, you'll need to **configure the notification**:

   :::image type="content" source="../media/4-incidents-email-notification-settings-inline.png" lightbox="../media/4-incidents-email-notification-settings-expanded.png"alt-text="Screenshot showing the notification settings":::

   - **Alert severity** - Choose the alert severities that will trigger an incident notification. For example, if you only want to be informed about high-severity incidents, select High.
   - **Device group scope** - You can specify all device groups or select from the list of device groups in your tenant.
   - **Only notify on first occurrence per incident** - Select if you want a notification only on the first alert that matches your other selections. Later updates or alerts related to the incident won't send additional notifications.
   - **Include organization name in the email** - Select if you want your organization name to appear in the email notification.
   - **Include tenant-specific portal link** - Select if you want to add a link with the tenant ID in the email notification for access to a specific Microsoft 365 tenant.

1. Finally, you'll need to add one or more email addresses that will receive the incident notifications.

> [!NOTE]
> It's a good idea to test the notification and ensure each recipient receives it in their inboxes.

Once you've reviewed the notification settings, you can create the rule to start receiving incident notifications through email.
