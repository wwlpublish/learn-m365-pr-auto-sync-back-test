One of the key skills for managing incidents is triaging the incident queue. This is similar to managing your email inbox to focus on the important messages first. However, triaging a busy incident queue can be daunting. Most incidents in your queue will be genuine attacks and can be thought of as true positives. Which is used as an early indicator that the attack is real. Some of the incidents in your queue will be benign or were raised by mistake. These are thought of as false positives.

When triaging your incident queue, you want to remove the false positives as soon as possible so you can focus on investigating, containing, and remediating the true positives.

## Classifying incidents and alerts

It's important to make sure that you correctly identify and classify active or resolved issues as either true or false positives. Doing this helps tune the detection system so that it can correctly flag genuine attacks. Classifying incidents helps:

- Share knowledge based on history of similar items.
- Microsoft 365 Defender tune detection classifications using data from all their customers.
- Track trends to improve incident quality.

Classifying an incident should be done as soon as you've determined if the activity is malicious in nature. You can classify an incident even if it hasn't been resolved.

This short five-minute video explains why classification of incidents is essential to maintaining a healthy incident queue.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LHJq]

### How to classify an incident

To classify an incident, you'll need to be in the incident queue. From there, select the incident that you'd like to manage. This will open a new pane, which will show you further details on the incident.

:::image type="content" source="../media/3-classification-pane.png" alt-text="Section of the Microsoft security center incidents page showing the classification section.":::

From here, you'll select **Manage incident**, which will let you assign the classification.

:::image type="content" source="../media/3-Incident-classification.png" alt-text="Screenshot showing the edit classification pane.":::

There are three possible options. By default, the classification is: **Not set**.

You should choose from the other two options:

- False alert
- True alert

Depending on the assessment of the alert.

:::image type="content" source="../media/3-classification-types.png" alt-text="Screenshot showing the different classification types":::

From the classification options, if you select **true alert**, you’ll be prompted with to provide a determination.

:::image type="content" source="../media/3-true-positivie-determination.png" alt-text="Screenshot showing the available determination options.":::

The determination is used to further qualify a true incident. You can select:

- APT
- Malware
- Security personnel
- Security testing
- Unwanted software
- Other

Lastly, you should always add a comment to document the reason for the classification change. This additional information can be used later by other analysts in your security team who are working on the same incident, or when they're investigating similar incidents.

Once you've assigned the correct classification, save your change to apply it.

:::image type="content" source="../media/3-alerts-page.png" alt-text="Screenshot showing a typical alerts page.":::

Classifying an alert is similar to classifying an incident. From the Alert page, you'll select an alert to open the alert details pane.

:::image type="content" source="../media/3-alert-classification.png" alt-text="Screenshot showing the alert classification options.":::

From there, you can manage the alerts classification by selecting True alert or False alert.

## Improving incident and alert queue quality

Classifying incidents and alerts can help you to improve their quality, which is important if certain apps or scripts used by your organization generate *false positives*. However, just classifying items that are unique to your organization as a *false positive* doesn't automatically prevent it from occurring again. Microsoft 365 Defender won't tune the detection algorithm until you do something to stop them.

### Fine-tuning detections to reduce *false positives*

In order to reduce the number of *false positives* in your incident queue, you may need to make changes in your environment. These could include:

- Changing any applications or scripts used within your organization.
- Setup and configure a custom indicator allowlist.
- The creation of suppression rules.
- Define policies that prevent *false positives*.

Try to understand what organizational activities or characteristics look malicious and try to rework them to eliminate them as a data source.
