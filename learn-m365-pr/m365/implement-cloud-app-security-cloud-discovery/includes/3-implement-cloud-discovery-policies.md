Microsoft Cloud App Security provides policy-driven mechanisms to help manage your users' behavior in the cloud. Policies enable you to detect and identify:

- Violations
- Risky behavior
- Suspicious data points and activities

## Policy types

The following table describes the available policy types.

| Policy type                               | Category          | Use                                                          |
| ----------------------------------------- | ----------------- | ------------------------------------------------------------ |
| Access policy                             | Access  control   | Provide  real-time monitoring and control over user sign-ins to your cloud apps |
| Activity  policy                          | Threat  detection | Enable you to  monitor user activities, or identify unexpectedly high rates of a specific  activity |
| Anomaly  detection policy                 | Threat detection  | Enable you to  identify unusual activities on your cloud. Detection is based on configured  risk factors |
| App discovery  policy                     | Cloud  Discovery  | Enable you to  set notification alerts when new apps are detected within your organization |
| Cloud Discovery  anomaly detection policy | Cloud  Discovery  | Leverage the  logs you use for discovering cloud apps and search for unusual occurrences |
| File policy                               | DLP               | Enable you to  scan cloud apps for sensitive data types, such as credit card details. You  can then apply governance actions to discovered data |
| Malware  detection policy                 | Threat  detection | Help you  identify potentially malicious files in your cloud storage and either approve  or revoke those files |
| OAuth app  policy                         | Threat  detection | Enable you to  determine which permissions an OAuth app requested and to automatically  approve or revoke that permission |
| Session  policy                           | DLP               | Enable real-time  monitoring and control over user activity in your cloud apps |

## Work with policies

To create policies, you use the Cloud App Security **Control** node. Select **Policies** to review existing, default policies.

:::image type="content" source="../media/policies-1.png" alt-text="A screenshot of the Policies page in Cloud App Security, displaying a list of policies sorted by Category.":::

To create a new policy, you can either:

- Use a template
- Create a query

To create a policy using a template:

1. Select **Templates** in the navigation pane.
2. Locate a suitable template and select **Create policy**.
3. Enter the required information and then select **Create**.

For example, if you're working in an Activity log, with files, or investigating accounts, you can create a policy based on a working query. To create a policy from a query, use the following procedure:

1. In **Activity log**, enter your query.
2. When you have defined the query, select **New policy from search**.

    :::image type="content" source="../media/new-policy.png" alt-text="A screenshot an Activity log query." lightbox="../media/new-policy.png":::

## Create an app discovery policy

As mentioned, app discovery policies enable you to set notification alerts when new apps are detected within your organization. To create a Cloud Discovery policy, use the following procedure:

1. In Cloud App Security, select **Control**, select **Policies**, and then select **Create policy**.
2. In the **Create policy** list, select **App discovery policy**.
3. Enter the following information:

   1. Policy name
   2. Policy severity (choose between **Low**, **Medium**, and **High**)
   3. **Category** is already defined as **Cloud Discovery**
   4. Optionally, enter a description
   5. Select filter options. You can filter on the following properties:
    - App tag
    - Apps and domains
    - Category
    - Compliance risk factor
    - General risk factor
    - Legal risk factor
    - Risk score
    - Security risk factor

   6. Apply the policy to either **All continuous reports** or **Specific continuous reports**.
   7. Optionally, select the **Trigger a policy match if all the following occur on the same day** check box. You can set criteria that the app must exceed daily to match the policy. Select one of the following criteria:

    - Daily traffic
    - Downloaded data
    - Number of IP addresses
    - Number of devices
    - Number of transactions
    - Number of users
    - Uploaded data

   8. In the **Alerts** section, you can enable an alert by email or text message (or both) for each matching event.

   > [!TIP]
   > You'll need to define the email addresses and phone numbers in the appropriate text boxes.

   9. Finally, in the Governance section, choose to tag discovered apps as:

    - Sanctioned
    - Unsanctioned
    - With a custom tag

   10. When all settings are configured, select **Create**.

For example, the following screenshot displays the settings for an app discovery policy where the administrator wants to learn about apps with the following properties:

- Category is Cloud storage, and with a risk score of between 0 and 2
- A policy match is triggered only if there are more than 100 users a day using the apps discovered
- When a match is triggered, email the user `admin@contoso.com`, but only up to five times per day

   :::image type="content" source="../media/policies-2.png" alt-text="a screenshot of the Create app discovery policy page. The administrator is creating a policy with the conditions listed in the preceding text.":::

## Create a Cloud Discovery anomaly detection policy

In addition to app discovery, you can use Cloud Discovery anomaly detection policies to discover cloud apps and search for unusual occurrences. These policies leverage the logs you use for discovering cloud apps. Creating an app anomaly detection policy is similar to a cloud app discovery policy.

1. In Cloud App Security, select **Control**, select **Policies**, and then select **Create policy**.
2. In the **Create policy** list, select **Cloud Discovery anomaly detection policy**.
3. Enter the following information:
    1. Policy name
    2. **Category** is already defined as **Cloud Discovery**
    3. Optionally, enter a description
    4. Select filter options. These are the same as for an app discovery policy.
    5. Apply the policy to either **All continuous reports** or **Specific continuous reports**.
    6. Then specify whether you want to filter usage based on user name, IP addresses, or both. Consider that selecting both might generate duplicate alerts as often, the same user is associated with the same IP.
    7. You can also specify a date from when you want to detect anomalous activity. Activity prior to the date is disregarded.

        >[!NOTE]
        >Activity prior to the specified date is used to establish the normal usage pattern.

    8. In the **Alerts** section, set the **Select anomaly detection sensitivity** value.
    9. You can then enable an alert by email or text message (or both) for each matching event.
    10. Finally, select **Create**.
