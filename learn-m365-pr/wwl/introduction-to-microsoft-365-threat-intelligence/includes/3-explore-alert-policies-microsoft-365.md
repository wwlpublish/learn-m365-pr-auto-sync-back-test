Alerts are the basis of all incidents and indicate the occurrence of malicious or suspicious events in your environment. Alerts are typically part of a broader attack and provide clues about an incident.

In Microsoft 365 Defender, related alerts are aggregated together to form [incidents](/microsoft-365/security/defender/incidents-overview?azure-portal=true). Incidents will always provide the broader context of an attack. However, analyzing alerts can be valuable when deeper analysis is required.

The Alerts queue shows the current set of alerts. You get to the alerts queue from **Incidents &amp; alerts &gt; Alerts** on the navigation pane in the Microsoft 365 Defender portal.

:::image type="content" source="../media/alerts-page-in-microsoft-365-defender-fcf6f72e.png" alt-text="Screenshot of the Alerts page in the Microsoft 365 Defender portal.":::


> [!IMPORTANT]
> Alerts can be created in different Microsoft security solutions. For example, Microsoft 365 Defender, Microsoft Defender for Endpoint, and Microsoft Defender for Office 365. The alerts that originate from all these solutions are displayed together on the **Alerts** page in the **Microsoft 365 Defender** portal.

By default, the **Alerts** page in the Microsoft 365 Defender portal displays the new and in progress alerts from the last 30 days. The most recent alert is at the top of the list so you can see it first.

From the **Alerts** page, you can select **Filter** to see a **Filter** pane. From the **Filter** pane, you can specify a subset of the alerts. Here's an example.

:::image type="content" source="../media/alerts-filter-pane-6c5e26c2.png" alt-text="Screenshot of the Alerts Filters pane in the Microsoft 365 Defender portal.":::


You can filter alerts according to these criteria:

 -  Severity
 -  Status
 -  Service sources
 -  Entities (the impacted assets)
 -  Automated investigation state

### Analyze an alert

To see the main alert page, select the name of the alert. An alert page is composed of these sections:

 -  Alert story. This section describes the chain of events and alerts related to this alert in chronological order.
 -  Summary details

Throughout an alert page, you can select the ellipses (...) beside any entity to see available actions. For example, linking the alert to another incident. The list of available actions depends on the type of alert.

#### Alert sources

Microsoft 365 Defender alerts may come from solutions like:

 -  Microsoft Defender for Identity
 -  Microsoft Defender for Endpoint
 -  Microsoft Defender for Office 365
 -  Microsoft Defender for Cloud Apps
 -  The app governance add-on for Microsoft Defender for Cloud Apps

You may notice alerts with prepended characters in the alert. The following table provides guidance to help you understand the mapping of alert sources based on the prepended character on the alert.

 -  The prepended GUIDs are specific only to unified experiences such as unified alerts queue, unified alerts page, unified investigation, and unified incident.
 -  The prepended character doesn't change the GUID of the alert. The only change to the GUID is the prepended component.

:::row:::
  :::column:::
    **Alert source**
  :::column-end:::
  :::column:::
    **Prepended character**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Defender for Office 365
  :::column-end:::
  :::column:::
    `fa{GUID}`
Example: `fa123a456b-c789-1d2e-12f1g33h445h6i`
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Defender for Endpoint
  :::column-end:::
  :::column:::
    `da` or `ed` for custom detection alerts

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Defender for Identity
  :::column-end:::
  :::column:::
    `aa{GUID}`
Example: `aa123a456b-c789-1d2e-12f1g33h445h6i`
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Defender for Cloud Apps
  :::column-end:::
  :::column:::
    `ca{GUID}`
Example: `ca123a456b-c789-1d2e-12f1g33h445h6i`
  :::column-end:::
:::row-end:::


#### Analyze affected assets

The **Actions taken** section has a list of impacted assets, such as mailboxes, devices, and users affected by this alert. You can also select **View in action center** to view the **History** tab of the **Action center** in the Microsoft 365 Defender portal.

#### Trace an alert's role in the alert story

The alert story displays all assets or entities related to the alert in a process tree view. The alert in the title is the one in focus when you first land on your selected alert's page. Assets in the alert story are expandable and selectable. They provide additional information and expedite your response by allowing you to take action right in the context of the alert page.

> [!NOTE]
> The **alert story** section may contain more than one alert. Other alerts related to the same execution tree may appear before or after the alert you've selected.

#### View more alert information on the details page

The details page shows the details and actions related to the selected alert. If you select any of the affected assets or entities in the alert story, the details page changes to provide contextual information and actions for the selected object.

Once you've selected an entity of interest, the details page changes to display:

 -  information about the selected entity type.
 -  historic information when it's available.
 -  options to take action on this entity directly from the alert page.

### Manage alerts

To manage an alert, select **Manage alert** in the summary details section of the alert page. For a single alert, here's an example of the **Manage alert** pane.

:::image type="content" source="../media/manage-alert-pane-bd9adade.png" alt-text="Screenshot of the Manage Alert pane in the Microsoft 365 Defender portal.":::


The Manage alert pane allows you to view or specify:

 -  The alert status (New, Resolved, In progress).
 -  The user account that has been assigned the alert.
 -  The alert's classification:
    
     -  **Not set**. This option is the default setting.
     -  **True positive**. Use this classification for alerts that accurately indicate a real threat. Specifying the threat type helps your security team see threat patterns and act to defend your organization from them.
     -  **Informational, expected activity**. Use the options in this category to classify alerts. For example, for security tests, red team activity, and expected unusual behavior from trusted apps and users.
     -  **False positive**. Use this classification for types of alerts that were created even when there's no malicious activity. Classifying alerts as false positive helps Microsoft 365 Defender improve its detection quality.
 -  A comment on the alert.

To manage a set of alerts similar to a specific alert, select **View similar alerts** in the **INSIGHT** box in the summary details section of the alert page.

From the **Manage alerts** pane, you can then classify all of the related alerts at the same time. Here's an example.

:::image type="content" source="../media/manage-alert-pane-bd9adade.png" alt-text="Screenshot of the Manage Alert pane in the Microsoft 365 Defender portal.":::


If similar alerts were already classified in the past, you can save time by using Microsoft 365 Defender recommendations to learn how the other alerts were resolved. From the summary details section, select **Recommendations**.

:::image type="content" source="../media/alert-detail-pane-with-recommendations-option-e2f33e7c.png" alt-text="Screenshot of the alerts detail pane with the Recommendations option highlighted.":::


The **Recommendations** tab provides next-step actions and advice for investigation, remediation, and prevention. Here's an example.

:::image type="content" source="../media/alert-recommendations-tab-a48b0eb6.png" alt-text="Screenshot of the Recommendations tab.":::


### Resolve an alert

Once you're done analyzing an alert and it can be resolved, go to the **Manage alert** pane for the alert or similar alerts and mark the status as **Resolved**. Then classify the resolution as one of the following types:

 -  **True positive**. Also enter a type of threat.
 -  **Informational, expected activity**. Also enter a type of activity.
 -  **False positive**.

Classifying alerts helps Microsoft 365 Defender improve its detection quality.
