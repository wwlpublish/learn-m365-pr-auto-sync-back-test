Alerts are the entry points to understanding your cloud environment more deeply. You might want to create new policies based on what you find. For example, you might see an administrator signing in from Greenland, and no one in your organization ever signed in from Greenland before. You can create a policy that automatically suspends an admin account when it's used to sign in from that location.

### Monitor alerts

It's a good idea to review all of your alerts and use them as tools for modifying your policies. If harmless events are being considered violations to existing policies, refine your policies so that you receive fewer unnecessary alerts.

1.  On the **Microsoft Defender for Cloud Apps** portal, select **Alerts** in the navigation pane.
2.  On the **Alerts** page, in the **Filters** section, select **Open** for the resolution status. This section of the dashboard provides full visibility into any suspicious activity or violation of your established policies. It can help you safeguard the security posture you defined for your cloud environment.
    
    :::image type="content" source="../media/alerts-page-defender-for-cloud-apps-f1b89217.png" alt-text="Screenshot of the Alerts page in the Microsoft Defender for Cloud Apps with the Open filter highlighted.":::
    

For each alert, you need to investigate and determine the nature of the violation and the required response.

 -  You can filter the alerts by **Alert type** or by **Severity** to process the most important ones first.
 -  Select a specific alert. Depending on what type of alert it is, you'll see various actions that can be taken before resolving the alerts.
 -  You can filter based on App. The apps listed are ones for which Microsoft Defender for Cloud Apps detected activities.
 -  There are three types of violations you'll need to deal with when investigating alerts:
    
     -  **Serious violations**. Require immediate response. Examples include:
        
         -  For a suspicious activity alert, you might want to suspend the account until the user changes their password.
         -  For a data leak you might want to restrict permissions or quarantine the file.
         -  If a new app is discovered, you might want to block access to the service on your proxy or firewall.
     -  **Questionable violations**. Require further investigation. Examples include:
        
         -  You can contact the user or the user's manager about the nature of the activity.
         -  Leave the activity open until you have more information.
     -  **Authorized violations or anomalous behavior**. Can result from legitimate use.
        
         -  You can dismiss the alert.

When you dismiss an alert, it's helpful if you submit feedback about why you're dismissing the alert. The Microsoft Defender for Cloud Apps team uses this feedback as an indication of the accuracy of the alert. It also uses this information to fine-tune our machine learning models for future alerts. If you select the **It's OK to contact me about this alert** box, in select cases Microsoft may contact you for additional information.

You can follow these guidelines in deciding how to categorize the alert:

 -  If legitimate use triggered the alert and it isn't a security issue, it could be one of these types:
    
     -  **Benign positive**. The alert is accurate but the activity is legitimate. You can dismiss the alert and set the reason to **Actual severity is lower** or **Not interesting**.
     -  **False positive**. The alert is inaccurate. Dismiss the alert and set the reason to **Alert is not accurate**.
 -  If any use triggered the alert and it's a security issue, then it will be:
    
     -  **True positive**. If the alert is related to an actual risky event that was either committed maliciously or unintentionally by an insider or outsider, you should set the event to **Resolve** after all appropriate action has been taken to remediate the event.
 -  If there's too much noise to determine the legitimacy and accuracy of an alert, dismiss it and set the reason to **Too many similar alerts**.

### Alert types

The following table provides a list of the types of alerts that can be triggered and recommends ways you can resolve them.

:::row:::
  :::column:::
    **Alert type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Recommended resolution**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Activity policy violation
  :::column-end:::
  :::column:::
    This type of alert is the result of a policy you created.
  :::column-end:::
  :::column:::
    To work with this type of alert in bulk, it's recommended that you work in the **Policy** center to mitigate them.

Fine-tune the policy to exclude noisy entities by adding more filters and more granular controls.

If the policy is accurate, the alert is warranted, and it's a violation you want to stop immediately, then consider adding automatic remediation in the policy.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    File policy violation
  :::column-end:::
  :::column:::
    This type of alert is the result of a policy you created.
  :::column-end:::
  :::column:::
    To work with this type of alert in bulk, it's recommended that you work in the **Policy** center to mitigate them.

Fine-tune the policy to exclude noisy entities by adding more filters and more granular controls.

If the policy is accurate, the alert is warranted, and it's a violation you want to stop immediately, then consider adding automatic remediation in the policy.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compromised account
  :::column-end:::
  :::column:::
    This type of alert is triggered when Microsoft Defender for Cloud Apps identifies an account that was compromised. A compromised account means there's a high probability the account was used in an unauthorized way.
  :::column-end:::
  :::column:::
    it's recommended that you suspend the account until you can reach the user and verify they change their password.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Inactive account
  :::column-end:::
  :::column:::
    This alert is triggered when an account hasn't been used in 60 days in one of your connected cloud apps.
  :::column-end:::
  :::column:::
    Contact the user and the user's manager to determine whether the account is still active. If not, suspend the user and terminate the license for the app.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New admin user
  :::column-end:::
  :::column:::
    Alerts you to changes in your privileged accounts for connected apps.
  :::column-end:::
  :::column:::
    Confirm the new admin permissions are required for the user. If they aren't, recommend revoking admin privileges to reduce exposure.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New admin location
  :::column-end:::
  :::column:::
    Alerts you to changes in your privileged accounts for connected apps.
  :::column-end:::
  :::column:::
    Confirm the sign-in from this anomalous location was legitimate. If it isn't, recommend revoking admin permissions or suspending the account to reduce exposure.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New location
  :::column-end:::
  :::column:::
    An informative alert about access to a connected app from a new location. It's triggered only once per country/region.
  :::column-end:::
  :::column:::
    Investigate the specific user's activity.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New discovered service
  :::column-end:::
  :::column:::
    This alert is an alert about Shadow IT. A new app was detected by Cloud Discovery.
  :::column-end:::
  :::column:::
    

For sanctioned apps:

 -  Assess the risk of the service based on the app catalog.
 -  Drill down into the activity to understand usage patterns and prevalence.
 -  Decide whether to sanction or unsanction the app.

For unsanctioned apps:


 -  You may want to block use in your proxy or firewall.
 -  If you have an unsanctioned app and a sanctioned app in the same category, you can export a list of users of the unsanctioned app. Then, contact them to migrate them to the sanctioned app.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Suspicious activity
  :::column-end:::
  :::column:::
    This alert lets you know that anomalous activity has been detected that isn't aligned with expected activities or users in your organization.
  :::column-end:::
  :::column:::
    Investigate the behavior and confirm it with the user.

This type of alert is a great place to start learning more about your environment and creating new policies with these alerts. For example, let's assume someone suddenly uploads a large amount of data to one of your connected apps. You can set a rule to govern that type of anomalous behavior.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Use of personal account
  :::column-end:::
  :::column:::
    This alert lets you know that a new personal account has access to resources in your connected apps.
  :::column-end:::
  :::column:::
    Remove the user's collaborations in the external account.
  :::column-end:::
:::row-end:::
