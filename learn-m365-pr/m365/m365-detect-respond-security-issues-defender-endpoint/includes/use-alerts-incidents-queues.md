As a member of the security team for your organization, you understand that threats can emerge on any device, at any time. Your organization has many devices, which could potentially result in a lot of devices being affected by the same threat, or multiple threats. To help you address these issues, you'll learn about the alerts queue, the incident queue, and how to investigate incidents.

## What is the alerts queue?

An alert is a notification about a potential threat that has been detected on your endpoints. Alerts in Microsoft Defender for Endpoint contain detailed information about the threat and how it affects your environment.

Use the alerts queue to get a list of all of the alerts that have been raised from across your organization's devices. To access the alerts queue, select **Alerts** under **Incidents & alerts** in the navigation pane in the Microsoft 365 Defender portal.

:::image type="content" source="../media/2-alerts-queue-inline.png" lightbox="../media/2-alerts-queue-expanded.png" alt-text="A screenshot showing the Alerts queue.":::

You can select any alert in the list to get more detailed information. The alert details pane gives you information such as:

- Alert category
- Alert classification
- A detailed description
- The users and devices impacted
- The incident to which the alert relates

Here's what the alert details pane looks like:

:::image type="content" source="../media/2-alert-details-pane-inline.png" lightbox="../media/2-alert-details-pane-expanded.png" alt-text="A screenshot showing the Alert details pane.":::

## What is the incidents queue?

An incident is a collection of correlated alerts and associated data that make up the story of an attack. You use the incident queue to view a list of all the incidents that have been flagged from the devices across your organization. You use it to prioritize your incidents and make better informed decisions on how to respond to them. To access the incidents queue, select **Incidents** under **Incidents & alerts** in the navigation pane.

:::image type="content" source="../media/2-incident-queue-inline.png" lightbox="../media/2-incident-queue-expanded.png" alt-text="A screenshot showing the Incident queue":::

When you select an incident, a details pane appears for the incident. Use this pane to get more information about the incident and related alerts.

:::image type="content" source="../media/2-incident-details-inline.png" lightbox="../media/2-incident-details-expanded.png" alt-text="A screenshot showing the incident details pane.":::

You're able to view information about the incident including:

- The incident classification
- The incident status
- The alerts contained in the incident
- Users impacted by the incident

## Manage incidents and alerts

When you select **Manage incident** in the incident details pane, the **Manage incident** pane appears:

:::image type="content" source="../media/2-manage-incident-inline.png" lightbox="../media/2-manage-incident-expanded.png" alt-text="The manage incidents pane.":::

In the **Manage incident** pane, you can:

- Change details such as the name of the incident
- Tag the incident
- Assign the incident to yourself if it hasn't been assigned to anyone
- Mark the incident as resolved if it has been remediated
- Classify the incident as a true incident or a false incident
- Provide useful comments specific to this incident

Once you've made your changes, select **Save** to save your changes.

To manage an alert, select **Manage alert** in the alert's detail pane, and the **Manage alert** pane appears:

:::image type="content" source="../media/2-manage-alert-inline.png" lightbox="../media/2-manage-alert-expanded.png" alt-text="Manage alert.":::

Just as with an incident, you can set the status of the alert, update its classification to a false or true alert, and leave comments. When you're done, select **Save** to save your changes.

## Investigate incidents

To begin your investigation, open the **Incident** page for the incident. You'll see important information about the incident at-a-glance.

:::image type="content" source="../media/2-incident-page-summary-inline.png" lightbox="../media/2-incident-page-summary-expanded.png" alt-text="The incident summary page.":::

Use the incident page to understand the full scope of the incident by looking at useful information on:

- Alerts
- Devices
- Users
- Investigations
- Evidence and response

### Alerts

You can use the alerts tab to gather information for your investigation by looking into the incident's alerts and find out how they are linked.

:::image type="content" source="../media/2-alerts-tab-inline.png" lightbox="../media/2-alerts-tab-expanded.png" alt-text="A screenshot showing the Alerts tab.":::

### Investigate alerts

Once you've reviewed the scope of the incident, you'll need to investigate its alerts. To do this, select an alert from the alerts tab.

:::image type="content" source="../media/2-select-alert-inline.png" lightbox="../media/2-select-alert-expanded.png" alt-text="A screenshot showing how to select an alert.":::

You're forwarded to the alert page. You use the **alert story** section in the alert page to understand why an alert was triggered, which events have led up to it, and information on any related entities (including any other alerts).

:::image type="content" source="../media/2-alert-story-inline.png" lightbox="../media/2-alert-story-expanded.png" alt-text="A screenshot showing an alert story.":::
