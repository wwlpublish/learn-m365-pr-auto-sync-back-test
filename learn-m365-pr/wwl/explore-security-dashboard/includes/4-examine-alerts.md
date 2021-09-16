The next set of tiles on the Security Dashboard is related to alerts. Alerts are a feature in the Microsoft 365 Security &amp; Compliance Center that is integrated across several programs, including:

 -  Data loss prevention
 -  Auditing
 -  Advanced Security Management
 -  Threat Intelligence

You can use the alert policy and alert dashboard tools in the Microsoft 365 Security and Compliance Center (SCC) to create alert policies. When users complete activities that match the conditions of an alert policy, the alert is generated. The Security Dashboard enables you to view the alerts that have been generated.

Alert policies build on and expand the functionality of activity alerts. They do so by letting you:

 -  categorize the alert policy.
 -  apply the policy to all users in your organization.
 -  set a threshold level for when an alert is triggered.
 -  decide whether to receive email notifications.

The Security Dashboard includes a **View alerts** page where you can:

 -  view and filter alerts.
 -  set an alert status to help you manage alerts.
 -  dismiss alerts after you've addressed or resolved the underlying incident.

Alert policies can be created to track things like user and admin activities and data loss incidents. They can also track malware threats in your organization. After choosing the activity you want to be alerted on, you can refine the policy by adding conditions, deciding when to trigger the alert, and who should receive notifications.

Several default alert policies are available to help you monitor activities, such as assigning admin privileges in Exchange Online, malware attacks, phishing campaigns, and unusual levels of file deletions and external sharing.

Alert policies are available for organizations with an Office 365 Enterprise or Office 365 US Government E1/G1, E3/G3, or E5/G5 subscription.

### How alert policies work

The following diagram provides a summarized overview of how alert policies work. It shows the alerts that are triggered when user or admin activity match the conditions of an alert policy. The numbered steps included in this alert workflow are described in detail following the diagram.

:::image type="content" source="../media/alert-policy-workflow-17c0a216.png" alt-text="diagram provides a summarized overview of how alert policies work by showing the alerts that are triggered when user or admin activity match the conditions of an alert policy":::


1.  An admin in your organization creates, configures, and turns on an alert policy by using the **Alert policies** page in the SCC. You can also create alert policies by using the **New-ProtectionAlert** cmdlet in SCC PowerShell. To create alert policies, you must be assigned the Manage Alerts role or the Organization Configuration role in the SCC.
2.  A user completes an activity that matches the conditions of an alert policy. For malware attacks, infected email messages sent to users in your organization trigger an alert.
3.  Microsoft 365 generates an alert that's displayed on the **View alerts** page in the SCC. Also, if email notifications are enabled for the alert policy, Microsoft 365 sends a notification to a list of recipients. The alerts that an admin or other users can see on the **View alerts** page is determined by the roles assigned to the user.
4.  An admin typically manages alerts in the SCC. Managing alerts consists of assigning an alert status to help track and manage any investigation.

### Alert policy settings

An alert policy consists of:

 -  a set of rules and conditions that define the user or admin activity that generates an alert.
 -  a list of users who trigger the alert if they complete the activity.
 -  a threshold that defines how many times the activity has to occur before an alert is triggered.

You also categorize the policy and assign it a severity level. These categorization and severity level settings help you manage alert policies (and the alerts that are triggered when the policy conditions are matched). They enable you to filter on these settings when managing policies and viewing alerts in the Security Dashboard. For example, you can view alerts that match the conditions from the same category or view alerts with the same severity level.

An alert policy consists of the following settings and conditions:

 -  **Activity the alert is tracking.** You create a policy to track an activity or in some case a few related activities. When a user completes the activity defined by the policy, an alert is triggered based on the alert threshold settings. Examples of activities include:
    
     -  Sharing a file with an external user by sharing it.
     -  Assigning access permissions
     -  Creating an anonymous link.

    > [!NOTE]
    > The activities that you can track depend on your organization's Office 365 Enterprise or Office 365 US Government plan. In general, activities related to malware campaigns and phishing attacks require an E5/G5 subscription or an E1/G1 or E3/G3 subscription with a Threat Intelligence add-on subscription.

 -  **Activity conditions.** For most activities, you can define other conditions that must be met to trigger an alert. The available conditions depend on the selected activity. Common conditions include:
    
     -  IP addresses, so that an alert is triggered when the user completes the activity on a computer with a specific IP address or within an IP address range.
     -  Whether an alert is triggered if a specific user or users completes that activity, of if any user in the organization completes that activity.
     -  Whether the activity is completed on a specific file name or URL.<br>
 -  **When the alert is triggered.** You can configure a setting that defines how often an activity can occur before an alert is triggered. This setting enables you to set up a policy to generate an alert:
    
     -  every time an activity matches the policy conditions.
     -  when a certain threshold is exceeded.
     -  when the occurrence of the activity the alert is tracking becomes unusual for your organization.

    > [!NOTE]
    > The ability to configure alert policies based on a threshold or based on unusual activity requires an E5/G5 subscription, or an E1/G1 or E3/G3 subscription with an Office 365 ATP P2 or Advanced Compliance add-on subscription. Organizations with an E1/G1 and E3/G3 subscription can only create an alert policy where an alert is triggered every time that an activity occurs.

 -  **Alert category.** To help with tracking and managing the alerts generated by a policy, you can assign one of the following categories to a policy:
    
     -  Data governance
     -  Data loss prevention
     -  Mail flow
     -  Permissions
     -  Threat management
     -  Others

    When an activity occurs that matches the conditions of the alert policy, the alert that's generated is tagged with the category defined in this setting. This design enables you to track and manage alerts that have the same category setting on the **View alerts** page in the SCC because you can sort and filter alerts based on category.

 -  **Alert severity.** Similar to the alert category, you can assign a severity attribute (**Low**, **Medium**, **High**, or **Informational**) to alert policies. Like the **Alert category**, when an activity occurs that matches the conditions of the alert policy, the alert that's generated is tagged with the same severity level that's set for the alert policy. Again, this design allows you to track and manage alerts that have the same severity setting on the **View alerts.** For example, you can filter the list of alerts so that only alerts with a **High** severity are displayed.

    > [!TIP]
    > When setting up an alert policy, consider assigning a higher severity to activities that can result in severely negative consequences, such as detection of malware after delivery to users, viewing of sensitive or classified data, sharing data with external users, or other activities that can result in data loss or security threats. This design can help you rank alerts and the actions you take to investigate and resolve the underlying causes.

 -  **Email notifications.** You can set up the policy so that email notifications are sent (or not sent) to a list of users when an alert is triggered. You can also set a daily notification limit so that once the maximum number of notifications has been reached, no more notifications are sent for the alert during that day. Besides email notifications, you or other administrators can view the alerts that are triggered by a policy on the **View alerts** page.

    > [!TIP]
    > Consider enabling email notifications for alert policies of a specific category or that have a higher severity setting.

### RBAC permissions required to view alerts

The Role Based Access Control (RBAC) permissions assigned to users in your organization determine which alerts a user can see on the **View alerts** page. The management roles assigned to users (based on their membership in role groups in the SCC) determine which alert categories a user can see on the **View alerts** page. Here are some examples:

 -  Members of the Records Management role group can view only the alerts that are generated by alert policies that are assigned the Data Governance category.
 -  Members of the Compliance Administrator role group can't view alerts that are generated by alert policies that are assigned the Threat Management category.
 -  Members of the eDiscovery Manager role group can't view any alerts because none of the assigned roles provide permission to view alerts from any alert category.

This design (based on RBAC permissions) lets you determine which alerts can be viewed (and managed) by users in specific job roles in your organization.

While there are many roles in the Security and Compliance Center, only certain roles provide permissions necessary to view alerts from the six different alert categories. The following table identifies those selected roles that can view alerts in the SCC. A check mark indicates that a user who is assigned that role can view alerts from the corresponding alert category listed in the top row.

> [!NOTE]
> You can also view the roles assigned to a role group in the SCC. Go to the **Permissions** page and select a role group. The assigned roles are listed on the flyout page.

| <p><b>Role</b></p>                         | <p><b>Data governance</b></p> | <p><b>Data loss prevention</b></p> | <p><b>Mail flow</b></p> | <p><b>Permissions</b></p> | <p><b>Threat Management</b></p> | <p><b>Others</b></p> |
|:------------------------------------------ |:-----------------------------:|:----------------------------------:|:-----------------------:|:-------------------------:|:-------------------------------:|:--------------------:|
| <p>Compliance Administrator</p>            |           <p>X</p>            |              <p>X</p>              |        <p> </p>         |         <p>X</p>          |            <p> </p>             |       <p>X</p>       |
| <p>DLP Compliance Management</p>           |           <p> </p>            |              <p>X</p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>Manage Alerts</p>                       |           <p> </p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p>X</p>       |
| <p>Organization Configuration</p>          |           <p> </p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p>X</p>       |
| <p>Record Management</p>                   |           <p>X</p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>Retention Management</p>                |           <p>X</p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>Role Management</p>                     |           <p> </p>            |              <p> </p>              |        <p> </p>         |         <p>X</p>          |            <p> </p>             |       <p> </p>       |
| <p>Security Administrator</p>              |           <p> </p>            |              <p>X</p>              |        <p> </p>         |         <p>X</p>          |            <p>X</p>             |       <p>X</p>       |
| <p>Security Reader</p>                     |           <p> </p>            |              <p>X</p>              |        <p> </p>         |         <p>X</p>          |            <p>X</p>             |       <p>X</p>       |
| <p>View-Only DLP Compliance Management</p> |           <p> </p>            |              <p>X</p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>View-only Manage Alerts</p>             |           <p> </p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p>X</p>       |
| <p>View-only Recipients</p>                |           <p> </p>            |              <p> </p>              |        <p>X</p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>View-only Record Management</p>         |           <p>X</p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |
| <p>View-only Retention Management</p>      |           <p>X</p>            |              <p> </p>              |        <p> </p>         |         <p> </p>          |            <p> </p>             |       <p> </p>       |

**Additional reading.** For more information on alerts, see [Alert policies in the Security and Compliance Center](/office365/securitycompliance/alert-policies?azure-portal=true).

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Assign RBAC permissions for alert notification testing](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M3-L3-E3-T1/index.html?azure-portal=true).

The alerts a user can see on the **View alerts** page are dependent on the user's assigned RBAC roles, which determine the depth of insight and control a user has. This simulation guides you through the steps to assign the RBAC permissions that are necessary for a user to test alert notifications in the fictitious company known as Adatum Corporation. In this simulation, you'll assign Lynne Robbins the appropriate RBAC permissions in the Security and Compliance Center that enable Lynne to view alerts and receive alert notifications.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”