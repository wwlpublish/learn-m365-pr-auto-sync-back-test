Automated investigation and response (AIR) capabilities enable organizations to run automated investigation processes in response to well-known threats that exist today. AIR can help an organization's security operations team operate more efficiently and effectively.

If your organization is using Microsoft 365 Defender, your security operations team receives an alert within the Microsoft 365 Defender portal whenever a malicious or suspicious activity or artifact is detected. Given the never-ending flow of threats that can come in, security teams often face the challenge of addressing the high volume of alerts. Fortunately, Microsoft 365 Defender includes automated investigation and response (AIR) capabilities that can help your security operations team address threats more efficiently and effectively.

When an automated investigation completes, a verdict is reached for every piece of evidence of an incident. Depending on the verdict, remediation actions are identified. In some cases, remediation actions are taken automatically; in other cases, remediation actions await approval through the Microsoft 365 Defender Action center.

### How automated investigation and self-healing works

As security alerts are triggered, it's up to your security operations team to look into those alerts and take steps to protect your organization. Prioritizing and investigating alerts can be very time consuming, especially when new alerts keep coming in while an investigation is going on. Security operations teams can feel overwhelmed by the sheer volume of threats they must monitor and protect against. Automated investigation and response capabilities, with self-healing, in Microsoft 365 Defender can help.

**Additional viewing**. Select the following link to watch a video titled: [Automated self-healing](https://www.microsoft.com/videoplayer/embed/RE4BzwB?postJsllMsg=true?azure-portal=true).

In Microsoft 365 Defender, automated investigation and response with self-healing capabilities works across your devices, email &amp; content, and identities.

Automated investigation and response capabilities enable an organization's security operations team to dramatically increase the company's capacity to deal with security alerts and incidents. With automated investigation and response, you can reduce the cost of dealing with investigation and response activities. You can also get the most out of your threat protection suite. Automated investigation and response capabilities help your security operations team by:

1.  Determining whether a threat requires action.
2.  Taking (or recommending) any necessary remediation actions.
3.  Determining whether and what other investigations should occur.
4.  Repeating the process as necessary for other alerts.

An alert creates an incident, which can start an automated investigation. The automated investigation results in a verdict for each piece of evidence. Verdicts can be:

 -  Malicious
 -  Suspicious
 -  No threats found

Remediation actions for malicious or suspicious entities are identified. Examples of remediation actions include:

 -  Sending a file to quarantine
 -  Stopping a process
 -  Isolating a device
 -  Blocking a URL
 -  Other actions

**Additional reading**. For more information, see See [Remediation actions in Microsoft 365 Defender](/microsoft-365/security/defender/m365d-remediation-actions?azure-portal=true).

Depending on how automated investigation and response capabilities are configured for your organization, remediation actions are taken automatically or only upon approval by your security operations team. All actions, whether pending or completed, are listed in the Action center in the Microsoft 365 Defender portal.

While an investigation is running, any other related alerts that arise are added to the investigation until it completes. If an affected entity is seen elsewhere, the automated investigation expands its scope to include that entity, and the investigation process repeats.

> [!IMPORTANT]
> Not every alert triggers an automated investigation, and not every investigation results in automated remediation actions. It depends on how automated investigation and response is configured for your organization. See [Configure automated investigation and response capabilities](/microsoft-365/security/defender/m365d-configure-auto-investigation-response?azure-portal=true).

### Details and results of an automated investigation

With Microsoft 365 Defender, when an automated investigation runs, details about that investigation are available both during and after the automated investigation process. If you have the proper permissions, you can view those details in an investigation details view that provides you with up-to-date status and the ability to approve any pending actions.

You can open the **Investigation Details** view by using one of the following methods:

 -  Select an item in the Action center
 -  Select an investigation from an incident details page

These methods are outlined in the following sections.

#### Select an item in the Action center

The Action center in the Microsoft 365 Defender portal brings together remediation actions across your devices, email and collaboration content, and identities. Listed actions include remediation actions that were taken automatically or manually. In the Action center, you can view actions that are awaiting approval and actions that were already approved or completed. You can also navigate to more details, such as an investigation page. You must have [proper permissions](/microsoft-365/security/defender/m365d-action-center?view=o365-worldwide#required-permissions-for-action-center-tasks?azure-portal=true) to approve, reject, or undo actions.

Complete the following steps to select an item in the Action center:

1.  Go to the Microsoft 365 Defender portal and sign in.
2.  In the navigation pane, select **Actions &amp; submissions**, and then select **Action center**.
3.  On the **Action center** pane, the **Pending** tab is displayed by default. Select either the **Pending** or **History** tab and then select an item. A detail pane is displayed for the selected item.
4.  Review the information in the details pane, and then take one of the following steps:
    
     -  Select **Open investigation page** to view more details about the investigation.
     -  Select **Approve** to initiate a pending action.
     -  Select **Reject** to prevent a pending action from being taken.
     -  Select **Go hunt** to go into Advanced hunting (advanced threat hunting is covered in a later unit in this module).

#### Select an investigation from an incident details page

The second method of opening an Investigation Details page is by opening an incident in the Microsoft 365 Defender portal. Doing so enables you to view detailed information about an incident, including alerts that were triggered, and information about any affected devices, user accounts, or mailboxes.

1.  Go to Microsoft 365 Defender portal and sign in.
2.  In the navigation pane, select **Incidents &amp; alerts**, and then select **Incidents**.
3.  On the **Incidents** page, select an item in the list, and then select **Open incident page**.
4.  Select the **Investigations** tab, and then select an investigation in the list. A detail pane appears for the investigation..
5.  On the detail pane, select O**pen investigation page.**

#### Investigation details

Use the **investigation details** view to see past, current, and pending activity pertaining to an investigation. In the Investigation details view, you can see information on the Investigation graph, Alerts, Devices, Identities, Key findings, Entities, Log, and Pending actions tabs, described in the following table.

> [!NOTE]
> The specific tabs you see in an investigation details page depends on what your subscription includes. For example, if your subscription doesn't include Microsoft Defender for Office 365 Plan 2, you won't see a Mailboxes tab.

:::row:::
  :::column:::
    **Tab**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Investigation graph
  :::column-end:::
  :::column:::
    Provides a visual representation of the investigation. Depicts entities and lists threats that were found, along with alerts and whether any actions are awaiting approval.

You can select an item on the graph to view more details. For example, selecting the **Evidence** icon takes you to the **Evidence** tab. From here, you can see detected entities and their verdicts.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Alerts
  :::column-end:::
  :::column:::
    Lists all alerts associated with the investigation. Alerts can come from threat protection features on a user's device, in Office apps, Microsoft Defender for Cloud Apps, and other Microsoft 365 Defender features.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Devices
  :::column-end:::
  :::column:::
    Lists all devices included in the investigation, along with their remediation level. Remediation levels correspond to [the automation level for device groups](/microsoft-365/security/defender/m365d-configure-auto-investigation-response?view=o365-worldwide#review-or-change-the-automation-level-for-device-groups?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mailboxes
  :::column-end:::
  :::column:::
    Lists the mailboxes that are affected by the detected threats.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Users
  :::column-end:::
  :::column:::
    Lists the user accounts that are affected by the detected threats.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Evidence
  :::column-end:::
  :::column:::
    Lists the pieces of evidence raised by alerts or investigations. Includes verdicts (*Malicious*, *Suspicious*, *Unknown*, or *No threats found*) and remediation status.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Entities
  :::column-end:::
  :::column:::
    Provides details about each analyzed entity, including a verdict for each entity type (*Malicious*, *Suspicious*, or *No threats found*).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Log
  :::column-end:::
  :::column:::
    Provides a chronological, detailed view of all the investigation actions taken after an alert was triggered.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Pending actions history
  :::column-end:::
  :::column:::
    Lists the items that require approval to proceed. Go to the Action center to approve pending actions.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”