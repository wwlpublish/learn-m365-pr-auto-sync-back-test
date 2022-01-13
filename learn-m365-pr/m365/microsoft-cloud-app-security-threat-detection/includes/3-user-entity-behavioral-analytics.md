## What is User and Entity Behavioral Analytics (UEBA)?

UEBA uses machine learning to look at patterns of human behavior and statistical analysis to identify malicious or risky behavior. This technique can identify the riskiest users in your organization and their potential impact on your organization.

### Microsoft Defender for Cloud Apps UEBA functionality

Defender for Cloud Apps reports the results of UEBA with an investigation priority score, which aggregates activity and alerts from Azure Advanced Threat Protection, Microsoft Defender for Cloud Apps, and Azure AD Identity Protection over the last seven days.

Defender for Cloud Apps uses alert scoring, activity scoring, and user impact to determine the investigation priority score.

- **Alert scoring** increases the priority score if the alert is more severe, is more frequent, or affects more users.
- **Activity scoring** increases the priority score if a specific user has a high probability of performing the specific action based on behavioral analytics.
- **User impact** increases the priority score if the users could cause a significant amount of damage. For example, a user with high privileges who can access high-value assets would have high user impact.

By combining these three types of score, the investigation priority score not only looks at the risk of the activity, but how likely it is to happen, and the damage that it can cause.

### Detecting UEBA threats in Defender for Cloud Apps

The Defender for Cloud Apps dashboard list the top users to investigate based on their investigation priority score. You can also select **View all users to investigate** to view all users.

:::image type="content" source="../media/3-microsoft-cloud-app-security-dashboard.png" alt-text="Microsoft Cloud App Security dashboard" lightbox="../media/3-microsoft-cloud-app-security-dashboard.png":::

If you select a user, you can see the details of their investigation priority score.

:::image type="content" source="../media/3-user-risk.png" alt-text="Investigation priority score" lightbox="../media/3-user-risk.png":::

In this example, we can see that the user is an accountant, has 41 devices, and has activities including logons from risky IP addresses and suspicious inbox forwarding. The high level of access, high exposure, and number of suspicious activities are the reason for this user's high investigation priority score.

The items in the dashboard can be selected to provide further detail. Furthermore, if you select **User actions** from the dashboard, you can perform actions to attempt to resolve the threat including requiring the user to sign in again, revoking admin privileges, or suspending the user.

:::image type="content" source="../media/3-user-actions.png" alt-text="User actions" lightbox="../media/3-user-actions.png":::

The following video discusses UEBA and how UEBA is implemented in Microsoft Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MxJn]
