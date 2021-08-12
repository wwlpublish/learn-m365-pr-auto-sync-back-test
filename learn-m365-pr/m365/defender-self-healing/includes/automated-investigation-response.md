As security alerts are triggered, it's up to you to look into those alerts and take the necessary steps to protect your organization's assets, data, and users. Prioritizing and investigating alerts is time consuming, especially when new alerts keep coming in while an investigation is ongoing.

AIR capabilities enable you and your security team to dramatically increase your organization's capacity to deal with security alerts and incidents. With automated investigation and response, you can reduce the cost of dealing with manual investigation and response activities. AIR capabilities help your security operations team by:

- Determining whether a threat requires action.
- Taking (or recommending) any necessary remediation actions.
- Determining whether and what other investigations should occur.
- Repeating the process as necessary for other alerts.

> [!NOTE]
> To fully utilize AIR, make sure your Microsoft 365 Defender environment meets the licensing and pre-requisites in [this article](/microsoft-365/security/defender/prerequisites).

## The automated investigation process

Depending on how you've configured your automated investigation and response capabilities, remediation actions can either be taken automatically or require manual approval by you and your security team. While an investigation is running, any related alerts that arise are added to the investigation until it's completed. This makes it easier for you and your team to focus on the attack. If an affected entity is seen elsewhere, the automated investigation expands its scope to include that entity, and the investigation process repeats. In Microsoft 365 Defender, each automated investigation correlates signals across all deployed services: Microsoft Defender for Identity, Microsoft Defender for Endpoint, and Microsoft Defender for Office 365.

## Details and results of an automated investigation

When an automated investigation runs, details about that investigation are available both during and after the automated investigation process. This means that you and your security team can obtain an up-to-date status of any active incidents and can review remediated ones.

You can get to the results of an automated investigation through the Action center. In the Action center, you can view actions that are awaiting approval and actions that were already approved or completed.

The first place you'll go to is the **incident details** page. This lets you and your team view detailed information about any incident, and to drill down to find any alerts that were triggered, and information about any affected devices, user accounts, and mailboxes.

:::image type="content" source="../media/3-investigation-page.png" alt-text="Screenshot showing a fragment of the Microsoft 365 Defender portal incident investigation page." lightbox="../media/3-investigation-page.png":::

You can track the current progress of an active or remediated incident from the **Investigations** tab of an incident. This tab shows a breakdown of each automated investigation that has been carried out so far and lets you drill into each to obtain more information such as the investigation graph that shows the relationships between affected entities, the current remediation status, the actions that were taken, and how long the investigation took.

:::image type="content" source="../media/3-investigation-summary-page.png" alt-text="Screenshot showing the investigation summary page." lightbox="../media/3-investigation-summary-page.png":::

You can also drill down into the entities affected by the automated investigation, such as the devices, users, or mailboxes by selecting the appropriate tab.

> [!NOTE]
> The specific tabs you see in an investigation details page depends on your subscription. For example, if your subscription does not include Microsoft Defender for Office 365 Plan 2, you won't see a Mailboxes tab.
