Microsoft Secure Score is a measurement of an organization's security posture. The higher the score, the more improvement actions have been taken. Organizations that implement the Security Score recommendations can protect themselves from threats. From a centralized dashboard in the Microsoft 365 Defender portal, organizations can monitor and work on the security of their Microsoft 365 identities, data, apps, devices, and infrastructure.

Microsoft Secure Score helps organizations:

 *  report on the current state of their security posture.
 *  improve their security posture by providing discoverability, visibility, guidance, and control.
 *  compare with benchmarks and establish key performance indicators (KPIs).

By implementing Microsoft Secure Score, organizations gain access to robust visualizations of metrics and trends, integration with other Microsoft products, score comparison with similar organizations, and much more. The score can also reflect when third-party solutions have addressed recommended actions.

> [!IMPORTANT]
> Microsoft Secure Score is a numerical summary of your security posture based on system configurations, user behavior, and other security-related measurements. It's not an absolute measurement of how likely your system or data will be breached. Rather, it represents the extent to which you have adopted security controls in your Microsoft 365 environment that can help offset the risk of being breached. No online service is immune from security breaches. Secure Score shouldn't be interpreted as a guarantee against security breach in any manner.

Microsoft Secure Score is available directly from the [Microsoft 365 security console](https://security.microsoft.com?azure-portal=true), as seen in the following image.

:::image type="content" source="../media/secure-score-e22dd9fa.png" alt-text="screenshot of the Microsoft Secure Score home page in the Microsoft 365 Security console":::


### How Secure Score works

An organization receives points for configuring recommended security features, completing security-related tasks (such as viewing reports), or addressing the improvement action with a third-party application or software. Some improvement actions only give points when fully completed, and some give partial points if they're completed for certain devices or users.

Microsoft Secure Score displays the full set of possible improvements, regardless of license, so you can understand security best practices and improve your score. Your absolute security posture is represented by Secure Score, which stays the same no matter what product licenses your organization owns. Keep in mind that security should be balanced with usability, and not every recommendation can work for your environment.

Your score is updated in real time to reflect the information presented in the visualizations and improvement action pages. Secure Score also syncs daily to receive system data about your achieved points for each action.

#### How improvement actions are scored.

Most improvements are scored in a binary fashion. If you implement the improvement action, such as creating a new policy or turning on a specific setting, you get 100% of the points. For other improvement actions, points are given as a percentage of the total configuration. For example, if the improvement action states you get 30 points by protecting all your users with multi-factor authentication and you only have 5 of 100 total users protected, you would be given a partial score of around 2 points (5 protected / 100 total \* 30 max pts = 2-pts partial score).

#### Products included in Secure Score.

Secure Score currently includes recommendations for Microsoft 365 (including SharePoint Online, Exchange Online, OneDrive for Business, Microsoft Information Protection, and more), Azure AD, and Defender for Cloud Apps. Recommendations for other security products, such as Microsoft Defender for Identity (formerly Azure ATP) and Microsoft Defender for Endpoint (formerly Microsoft Defender ATP), are coming soon. The recommendations won't cover all the attack surfaces associated with each product, but they're a good baseline. You can also mark the improvement actions as covered by a third party.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”
