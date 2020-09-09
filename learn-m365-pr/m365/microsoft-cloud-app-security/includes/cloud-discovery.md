You can use Cloud Discovery to see what's happening in your network. You'll see both the cloud apps you expect and the apps you don't expect, signs of Shadow IT, non-sanctioned apps that may not be compliant with your security and compliance policies. Cloud Discovery analyzes your traffic logs against a catalog of over 16,000 cloud apps. Cloud Discovery ranks each app and scores it based on more than 80 risk factors to provide you visibility into cloud use, Shadow IT, and the risk Shadow IT poses into your organization.

The Cloud Discovery dashboard provides an at-a-glance overview of what kinds of apps are being used, your open alerts, and the risk levels of the apps in your organization. You can also see who your top app users are and where each app comes from (on an App Headquarter map). You can filter the data collected by Cloud Discovery to generate specific views depending on what you're most interested in.

:::image type="content" source="../media/cloud-discovery-dashboard.png" alt-text="Screenshot showing the cloud discovery dashboard":::

## Review the Cloud Discovery Dashboard

Your first step is to get a general picture of your cloud apps. Start at the Cloud Discovery dashboard. Move through the elements of the dashboard in the following order to understand what's happening in your organization.

1. Start with the **High-level usage overview** to see the overall cloud app use. You can see the **top users** and **source IP addresses**. Based on this information, identify which users in your organization use cloud apps the most. You'll want to pay attention to these users going forward.
1. Dive one level deeper to see which category of apps your org uses most. See how much of this usage is in **Sanctioned** apps.
1. Go even deeper on the **Discovered apps** tab. See all the apps in a specific category.

:::image type="content" source="../media/discovered-apps.png" alt-text="Screenshot showing the discovered apps":::

1. Review the risk score for the discovered apps in the **App risk overview**. Each discovered app is assessed against risk factors like security factors and compliance and regulatory measures and given a risk score between 1-10.

1. View where discovered apps are located (based on their headquarters) in the **App Headquarters map**.

1. If you find an app that poses a risk to your organization, you can flag it as **Unsanctioned** in the **Discovered apps** pane.

:::image type="content" source="../media/unsanction.png" alt-text="Screenshot showing the unsanctioned applications":::

If your organization is using Microsoft Defender Advanced Threat Protection (or a similar solution), any unsanctioned app is automatically blocked.

If you don't have a threat protection solution, you can run a script against the data source to block the app. Then users will see a notification that the application is blocked when they try to access it.

:::image type="content" source="../media/notification.png" alt-text="A screenshot of the notification your users will see if they try to access a blocked, unsanctioned app.":::
