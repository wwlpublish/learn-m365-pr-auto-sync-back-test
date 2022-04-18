Alert policies have been fully integrated into the new Exchange admin center (EAC). You can use Alert policies to track events related to mail flow and view alerts generated when activities that match the configured conditions are met.

There are two types of Alert policies:

 -  **System policy.** a system-generated policy turned on by default. You have access to edit a limited number of settings for these policies and can choose the disable them, but not delete them.
 -  **Custom policy.** a user/tenant created policy. You can fully reconfigure these policy settings or chose to delete the policy as needed.

By default, several system-generated Alert policies are created for you that help to monitor activities:

:::row:::
  :::column:::
    Default Alert Policy
  :::column-end:::
  :::column:::
    Type
  :::column-end:::
  :::column:::
    Description
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Messages have been delayed
  :::column-end:::
  :::column:::
    System
  :::column-end:::
  :::column:::
    When Office 365 is unable deliver a message to your on-premises or partner servers via a connector, the message is queued in Office 365. This alert is triggered when the number of queued messages exceeds the policy threshold and have been queued for more than an hour.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Priority accounts' mail flow is unhealthy
  :::column-end:::
  :::column:::
    System
  :::column-end:::
  :::column:::
    Office 365 can monitor the mail flow for priority accounts set in your organization. This alert policy is triggered when the number of rejected or delayed messages for priority accounts exceeds the policy threshold.for more information about priority account tags, see [User tags in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/user-tags?azure-portal=true).
  :::column-end:::
:::row-end:::

### Permissions required for the management of Alert policies

Before you can access and manage Alert policies, you must have the following permissions assigned:

 -  For Full access, the messaging admin must be a member of Organization Management or Security Administrator role groups.
 -  For Read-Only access, the messaging admin must be a member of the Global Reader or Security Reader role groups.

### Create an Alert policy in the new Exchange admin center

To create and Alert policy, you should complete the following steps:

1.  In the EAC, on the left pane select **Mail flow &gt; Alert policies** and select **New alert policy.**
2.  Provide a name for your policy in the **Name** box, and a description for your policy in the **Description** box, then select **Next.**
3.  From the **Severity** drop-down list, select the appropriate severity level:
     -  **None**
     -  **High**
     -  **Medium**
     -  **low**
4.  From the **Trigger an alert when the following insight is generated** drop-down list, select one from the following insights:<br>
     -  **Mail loop.** Use this insight to determine when an email loop occurs. Typically, an email loop starts when office 365 thinks a recipient doesn't exist in the service. If the MX record for the recipient's domain points to Office 365, or if the destination messaging server thinks the recipient is in Office 365, the message is delivered back to Office 365, and the process repeats itself.
     -  **Slow transport rule.** A transport rule shouldn't take more than a few milliseconds to evaluate a message. Use this insight to determine if a transport rule contains inefficient conditions or actions, which could slow down mail flow.
     -  **New users forwarding.** use this insight to determine when newly created user starts forwarding emails from your organization to external domains.<br>
     -  **New domains being forwarded.** Use this insight to determine when a new remote domain starts receiving forwarded emails from your organization.
     -  **Cert Expiry.** Mail flow connectors rely on valid certificate for authentication and attribution. Use this insight to determine which certificates are expiring soon to avoid any potential mail service issues.
5.  Select **Next**.
6.  Provide the name or email address of the alert notification recipients in the **Email recipients** box.
7.  From the **Daily notification limit** drop-down list, select daily notification count.
8.  Select **Next**.
9.  Review the Alert policy settings and select **Create**. The Alert policy is now created.

> [!NOTE]
> When creating a new Alert policy, the **Category** drop-down list is disabled because **Mail flow** is the only supported category in the new Exchange admin console.

### View alerts in the new Exchange admin center

In addition to email notifications sent to configured email recipients, administrators with required permissions can view alerts in the new Exchange admin center by completing the following steps:

1.  In the EAC, on the left pane select **Mail flow &gt; Alerts.** You'll now see that the **Alerts** screen appears, displaying reports on the configured alert policies.
2.  Under the **Alert name** column, you can select an alert that you want to view details for. This will pop open the alert policy details screen.
3.  Selecting **View details** will elaborate details of the selected alert policy.
