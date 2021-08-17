With Microsoft Secure Score in the Microsoft 365 Defender portal, you can have increased visibility and control over your organization's security posture. From a centralized dashboard you can monitor and improve the security for your Microsoft 365 identities, data, apps, devices, and infrastructure. The alerts include recommendations from Azure AD, Intune, Cloud App Security, Azure Security Center, and Microsoft Defender for Endpoint.

The overview page is the place to get an all-up view of the total score. This can be subdivided into the historical trend of your secure score with benchmark comparisons and prioritized recommended actions that can be taken to improve your score.

![Microsoft Secure Score](../media/secure-score.png)

You can increase your score by configuring recommended security features, performing security-related tasks (such as viewing reports), or addressing the improvement action with a third-party application or software. Some actions are scored for partial completion, like enabling multifactor authentication (MFA) for your users.

As you go deeper into the secure score, you'll find a list of recommended improvement actions ranked by Microsoft according to their security value. You can adjust these parameters to ensure that you only make the changes to your security environment that works for your organization.

![Actions you can take to improve your Secure Score](../media/secure-score-actions.png)

When you select an improvement action, a pane on the right gives you even more information about that action. You'll see:

- **Description**
- **Category** – This is the security category of the threat and can be one of many categories
  - Identity
  - Data
  - Device
  - Apps
  - Infrastructure
- **Protects against** – This is what the improvement can protect against
- **Complexity** – Tells you how complex and costly the implementation would be
- **Steps to complete the action**
- **How it will affect your users**
- **Compliance Controls** – Which set of compliance instructions this action is listed under
- **Notes** – Custom note taking field to help you track the status

Here's an example of Require MFA for Azure AD privileged roles:

![Require MFA for Azure AD privileged roles - sample action](../media/require-mfa.png)
