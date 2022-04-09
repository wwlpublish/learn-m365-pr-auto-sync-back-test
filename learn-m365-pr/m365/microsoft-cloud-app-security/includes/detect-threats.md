When you understand how to protect data from accidental exposure, the next thing to consider, and one of the elements of the Defender for Cloud Apps framework, is protecting against cyberthreats and anomalies.

Microsoft Defender for Cloud Apps includes out-of-the-box anomaly detection policies that utilize user and entity behavioral analytics (UEBA) and machine learning to provide advanced threat detection across your cloud environment. It's important to note that anomaly detections are non-deterministic by nature. These detections only trigger when there's behavior that deviates from the norm.  

Although anomaly detection policies are automatically enabled, Microsoft Defender for Cloud Apps spends the first seven days learning about your environment. It looks at the IP addresses, devices, and locations your users access, identifies which apps and services they use, and calculates the risk score of all of these activities. This process contributes to the baseline, against which your environment and any alerts are compared. The detection policies also use machine learning to profile your users. If Microsoft Defender for Cloud Apps recognizes your users and their normal sign-in patterns, it can help reduce false positive alerts.

Anomalies are detected by scanning user activity and evaluating it for risk. The risk is evaluated by looking at more than 30 different indicators, grouped into the following risk factors:

- Risky IP address
- Login failures
- Admin activity
- Inactive accounts
- Location
- Impossible travel
- Device and user agent
- Activity rate

Microsoft Defender for Cloud Apps looks at every user session on your cloud and alerts you when something happens that's different from the baseline of your organization, or from the user's regular activity.

## Anomaly detection policy overview

The Microsoft Defender for Cloud Apps anomaly detection policies are configured to detect a variety of security issues. The most popular are:

- **Impossible travel**. Activities from the same user in different locations within a period that's shorter than the expected travel time between the two locations.
- **Activity from infrequent country**. Activity from a location that was not recently or never visited by the user, or by any user in the organization.
- **Malware detection**. Scans files in your cloud apps and runs suspicious files through Microsoft's threat intelligence engine to determine whether they're associated with known malware.
- **Ransomware activity**. File uploads to the cloud that might be infected with ransomware.
- **Activity from suspicious IP addresses**. Activity from an IP address that's been identified as risky by Microsoft Threat Intelligence.
- **Suspicious inbox forwarding**. Detects suspicious inbox forwarding rules set on a user's inbox.
- **Unusual multiple file download activities**. Detects multiple file download activities in a single session with respect to the baseline learned, which could indicate an attempted breach.
- **Unusual administrative activities**. Detects multiple administrative activities in a single session with respect to the baseline learned, which could indicate an attempted breach.

## Configure an anomaly detection policy

Now that you've learned about the anomaly detection policies, let's configure a discovery anomaly policy so you can see the steps to set it up and configure it for your environment. A discovery anomaly detection policy looks for unusual increases in cloud application usage. It looks at increases in downloaded data, uploaded data, transactions, and users for each cloud application. Then, each increase is compared to the baseline for the application. The most extreme increases trigger security alerts.

You can set filters to customize how you monitor application usage. Filters include an application filter, selected data views, and a selected start date. You can also set the sensitivity, which enables you to set how many alerts the policy should trigger.

This interactive guide walks you through the steps to configure an anomaly detection policy:

[:::image type="content" source="../media/detect-threats.png" alt-text="Detect threats and manage alerts with Microsoft Defender for Cloud Apps." border="false":::](https://aka.ms/DetectThreats-ManageAlerts-MCAS_InteractiveGuide)

### Fine-tune anomaly detection policies for suppression or surfacing alerts

Although anomaly detections only trigger when something happens outside the norm, they're still susceptible to false positives. Too many false positives can lead to alert fatigue, and you risk missing the important alerts in the noise. To help prevent this, you can fine-tune the detection logic in each policy to include different levels of suppression to address scenarios that can trigger false positive, such as VPN activities.

When creating or editing an anomaly detection policy, you determine its sensitivity according to the type of coverage you need. A higher sensitivity uses stricter detection logic algorithms. This allows you to adapt your detection strategies for each policy.

Before you fine-tune your policies, it helps to understand the options for suppressing an alert. There are three types of suppression:

| Suppression type | Description                |
| -------------------- | ------------------------------------------------------------ |
| **System**           | Built-in detections that are always suppressed.              |
| **Tenant**           | Common activities based on previous activity in the tenant. For  example, suppressing activities from an ISP previously alerted on in your  organization. |
| **User**             | Common activities based on previous activity of the specific user.  For example, suppressing activities from a location that is commonly used by  the user. |

 The sensitivity levels affect the suppression types differently:

| Sensitivity Level | Suppression types affected |
| --------------------- | ------------------------------ |
| Low                   | System, Tenant, and User       |
| Medium                | System, and User               |
| High                  | System Only                    |

You can also configure whether alerts for activity from infrequent country/region, anonymous IP addresses, suspicious IP addresses, and impossible travel should analyze failed and successful logins, or just successful logins.

### Adjust the anomaly detection scope policy to users and groups

Each anomaly detection policy can be independently scoped so that it applies only to the users and groups you want to include and exclude in the policy. For example, you can set the Activity from infrequent country detection to ignore a specific user who travels frequently.

To scope an anomaly detection policy:

1. Sign in to the Microsoft Defender for Cloud Apps Portal through your browser.
1. Select **Control** > **Policies**, and set the **Type** filter to **Anomaly detection policy**.
1. Select the policy you want to scope.
1. Under **Scope**, change the dropdown from the default setting of **All users and groups**, to **Specific users and groups**.
1. Select **Include** to specify the users and groups for whom this policy will apply. Any user or group not selected here won't be considered a threat or generate an alert.
1. Select **Exclude** to specify users for whom this policy won't apply. Any user selected here won't be considered a threat or generate an alert, even if they're members of groups selected under **Include**.

   :::image type="content" source="../media/anomaly-detection-policy.png" alt-text="Screenshot showing how to edit an Anomaly detection policy." lightbox="../media/anomaly-detection-policy.png":::

1. When you've completed the changes to the scope, select **Update** to commit the change.
