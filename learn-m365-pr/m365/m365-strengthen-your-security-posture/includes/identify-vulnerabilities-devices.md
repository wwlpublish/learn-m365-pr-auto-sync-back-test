You're a security analyst, so you understand that vulnerabilities can manifest at any point. To effectively address vulnerabilities, you need to identify vulnerabilities across your environment.

Here, you'll learn about the software inventory, how to find common vulnerabilities, and the event timeline.

## The software inventory

The software inventory page in Microsoft Defender for Endpoint lists important details about the software installed across your organization. Use the software inventory to review information such as:

- Threats to your software
- The number of threats and weaknesses identified for your software
- The number of exposed devices
- How each software impacts your exposure score

Software inventory also allows you to filter software based any of these criteria, and more. You access the software inventory by selecting **Software inventory** under **Threat and vulnerability management** from the navigation pane.

:::image type="content" source="../media/4-software-inventory-list-inline.png" lightbox="../media/4-software-inventory-list-expanded.png" alt-text="Screenshot showing where to find the software inventory list.":::

> [!NOTE]
> Software without the official [Common Platform Enumerations (CPE)](https://nvd.nist.gov/products/cpe), won't have their vulnerabilities published.

When you select an individual application from the inventory list, you can access its **Software page** for more insights on that particular application.

:::image type="content" source="../media/4-software-page-inline.png" lightbox="../media/4-software-page-expanded.png" alt-text="Screenshot showing the software page for Windows 10.":::

Use the software page to get more information such as:

- Security recommendations that you can implement
- Details about discovered vulnerabilities
- Misconfigurations
- Which versions of the software are installed on different devices

## Find common vulnerabilities and exposures

Use the **Weaknesses** pane to find the common vulnerabilities and exposures across your organization's devices.

:::image type="content" source="../media/4-weaknesses-inline.png" lightbox="../media/4-weaknesses-expanded.png" alt-text="A screenshot showing how to get to the Weaknesses pane.":::

The **Weaknesses** pane provides you with a list of Common Vulnerabilities and Exposures (CVE) with details such as:

- Corresponding breaches for each CVE
- How prevalent a CVE is across your organization
- The severity of each CVE
- Affected devices
- Whether there are any known exploits for each CVE

With this information, you can begin to address your common vulnerabilities and exposures. You can find more detailed insights about a particular CVE by selecting it from the list.

:::image type="content" source="../media/4-remediate-vulnerabilities-inline.png" lightbox="../media/4-remediate-vulnerabilities-expanded.png" alt-text="Screenshot showing the Review vulnerability pane.":::

Use it to review the information, then you can select **Go to related security recommendation** to begin to remediate the issue.

## The event timeline

The event timeline is a risk news feed used to understand how risk has made its way into your organization through exploits and vulnerabilities. Events include things like configuration changes, new vulnerabilities that have been identified for software, and more. Different events can impact your devices, and how your devices are scored. The event timeline lists these events as they occurred.

:::image type="content" source="../media/4-event-timeline-list-inline.png" lightbox="../media/4-event-timeline-list-expanded.png" alt-text="Screenshot showing an Event timeline and how access the security recommendations.":::

Selecting an event from the timeline shows a pane with detailed information on how it has impacted your endpoints.

:::image type="content" source="../media/4-event-details-inline.png" lightbox="../media/4-event-details-expanded.png" alt-text="Screenshot showing the contents of the event details pane.":::

This information includes:

- The type of event
- The number of devices initially impacted, and those that are currently impacted
- Which component the event originated from
- Related common vulnerabilities and exploits for this event

After reviewing the information, you can select **Go to related security recommendation** to begin to remediate the issue.
