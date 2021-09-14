Teams notifications and alerts gives you an ability to monitor Teams capabilities and receive alerts. For example, you can actively monitor the health of Teams devices such as IP Phones, collaboration bars, and others if they unexpectedly go offline.

Your organization can use Teams monitoring and alerting to do the following items:

* Automatically manage Teams capabilities
* Be alerted if they show something unexpected
* Take corrective actions to get things back on-track

## Teams monitoring rules 

Here's a list of the Teams monitoring rules currently available in the Teams admin center.

|Rule  |Monitoring capability|What's monitored? |
|---------|---------|---------|
|Device health status |Teams Devices | Pro-actively monitor Teams devices if they go offline.|

### Device health status

Device health monitoring in the Microsoft Teams admin center gives you an ability to proactively monitor the health of various Teams devices. Monitor the offline state of a device and receive alerts in real time if the monitored device in your organization goes offline.

|Field |Description  |
|--------|-------------|
|**Rule type**   |The device state rule helps you effectively manage. Teams devices and is classified as a device management type. In the future, more rules of device management type will be available to monitor other related capabilities (examples may include: unhealthy device and the sign-in status of device).|
|**Condition**   |You can monitor the health of devices if they go offline. |
|**Scope**   |You can specify how frequently you want to monitor device health status by mentioning the rule evaluation frequency. By default teams devices will be monitored in near real time if they go offline. |
|**Device users**   |You can specify which devices need proactive offline statue monitoring by selecting them based on signed-in users. |
|**Actions** > **Channel alert**   |In the Actions section, you can specify teams channels you want to get alerts for. Currently, a default team named **Admin Alerts and Notifications** and channel named **MonitoringAlerts** will be created where notifications will be delivered to. <BR/> <BR/> Global administrators and Teams administrators in your tenant will be automatically added to this default team.|
|**Actions** > **Webhook**   |You can also get notifications with an external webhook (optional). Specify an external public webhook URL in the webhook section where a JSON notification payload will be sent. <BR/> <BR/>  The notification payload, via webhooks, can be integrated with other systems in your organization to create custom workflows.<br/><br/> 

‎:::image type="content" source="../media/device-state-rule.png" alt-text="Teams devices state rule page":::

## Configure Teams monitoring rules

You must be a global admin in Microsoft 365 or a Teams admin to configure alerting rules. you also need the teams/channel creation permissions in your tenant for configuring device status rule.

1. Sign in to the **Teams admin center**.
2. From the left navigation, select **Notifications & alerts**.
3. Choose the rule you want to configure from **Rules**.

