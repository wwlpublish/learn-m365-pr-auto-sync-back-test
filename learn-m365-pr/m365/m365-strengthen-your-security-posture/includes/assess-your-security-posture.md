As the security analyst of your team, you want to understand your environment's present state of protection and learn where improvements are needed. Here, you'll learn how to use dashboard insights in Microsoft Defender for Endpoint to help you do this.

## Use dashboard insights

You can access the dashboard by selecting **Dashboard** under **Threat and vulnerability management** in the navigation pane of the Microsoft 365 Defender portal:

:::image type="content" source="../media/3-dashboard-inline.png" lightbox="../media/3-dashboard-expanded.png" alt-text="A screenshot showing how to access the dashboard.":::

The dashboard provides a status overview  and access to different kinds of information. The information in the dashboard is displayed as individual cards. Each card represents key information, such as top vulnerable software, top exposed devices, and top security recommendations. This page also includes information such as:

- Exposure score
- Microsoft Secure Score for devices

### Exposure score

Multiple things can affect your exposure score including:

- Weaknesses identified across your devices
- The probability of your devices being breached

To improve your exposure score, you can implement the security recommendations provided by the threat and vulnerability management component of Microsoft Defender for Endpoint. The lower your exposure score, the better.

Here's an example exposure score from the dashboard:

:::image type="content" source="../media/3-exposure-score-inline.png" lightbox="../media/3-exposure-score-expanded.png" alt-text="A screenshot showing the exposure score card.":::

From the dashboard, you can select **Improve score** to learn how to improve your exposure score. Here's an example of the kind of security recommendations you might see to improve your score:

:::image type="content" source="../media/3-exposure-score-recommended-actions-inline.png" lightbox="../media/3-exposure-score-recommended-actions-expanded.png" alt-text="A screenshot showing recommended actions to improve exposure score.":::

#### Use device value tagging

Attackers consider some of your organization's assets more valuable than others. Devices such as domain controllers, executive users' devices, and machines that host production services are valuable targets to attackers. These devices could be used to access sensitive data or move up into the organization's systems for greater control. As a result, assets like these need more attention and higher prioritization, to reduce the overall risk for your organization.

Use device value tagging to indicate how assets should be prioritized and achieve a more accurate assessment of the overall risk for your organization.
You can tag any of your devices with one of the following values:

- **High value**
- **Normal value** (Default)
- **Low value**

The value you assign is taken into account for each individual device when calculating the exposure score. Devices marked as **High value** will be weighted more during the calculation of your exposure score.

You can assign a device value tag from the device details pane of your devices:

:::image type="content" source="../media/3-device-value-tag-inline.png" lightbox="../media/3-device-value-tag-expanded.png" alt-text="A screenshot showing device value tagging.":::

### Microsoft Secure Score for devices

 Your Microsoft Secure Score for devices is based on an ongoing vulnerability discovery process at the following levels:

- Application
- Operating system
- Network
- User and principal accounts
- Security controls

The higher the Microsoft Secure Score, the more resilient your endpoints are to threats.

:::image type="content" source="../media/3-secure-score-inline.png" lightbox="../media/3-secure-score-expanded.png" alt-text=" A screenshot showing the Microsoft Secure Score for devices card on the dashboard.":::

As with exposure score, you select **Improve score** to learn how to improve your score. Here's an example showing the kind of security recommendations that you might get:

:::image type="content" source="../media/3-secure-score-recommendations-inline.png" lightbox="../media/3-secure-score-recommendations-expanded.png" alt-text="A screenshot showing the Microsoft Secure Score recommended actions.":::
