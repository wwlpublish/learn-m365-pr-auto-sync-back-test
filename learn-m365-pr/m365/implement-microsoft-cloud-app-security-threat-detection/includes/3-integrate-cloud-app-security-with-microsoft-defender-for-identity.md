Microsoft Defender for Identity integrates with your on-premises Active Directory Domain Services (AD DS) environment. This integration can help you detect, investigate, and identify advanced threats, compromised identities, and other malicious actions targeted at your organization.

By using Defender for Identity, you can:

- Monitor activities, users, and entity behavior
- Help protect AD DS identities and credentials
- Identify and investigate suspicious user activities and advanced attacks
- Provide clear incident information to help triage security threats

## Enable integration

You can integrate Defender for Identity with Microsoft Cloud App Security. By doing so, you can use the Cloud App Security portal to access alerts and insights from:

- Cloud App Security, which monitors cloud apps
- Defender for Identity, which identifies attacks in your on-premises network environment
- Azure Active Directory (Azure AD) Identity Protection, which helps detect and prevent user and sign-in risks for cloud-based identities

> [!NOTE]
> To access user investigation features across your hybrid environment, you'll need a license for both Microsoft Cloud App Security and Microsoft Defender for Identity.

To enable integration, use the following procedure:

1. From within the Cloud App Security portal, open **Settings**.
2. In the **Threat Protection** section, select **Microsoft Defender for Identity**.
3. On the **Microsoft Defender for Identity** page, select **Enable Microsoft Defender for Identity data integration**.

   > [!NOTE]
   > In can take up to 12 hours for Cloud App Security to complete its initial setup and integration.

## Investigate Defender for Identity activities

After you have enabled integration, you can use the Cloud App Security portal to investigate Defender for Identity activities. In the portal, select the **Alerts** in the navigation pane. You can then filter for specific users, devices, or actions. In the following example, the administrator has filtered the alerts for a specific **USER NAME**.

:::image type="content" source="../media/alerts.png" alt-text="A screenshot of the Alerts page. The administrator is reviewing an alert where the Policy equals Activity from an infrequent country.":::

If you need more information, you can select **Advanced** and build a more detailed query. You can also create activity policies in Cloud App Security to take action against suspected threats. As with other policies, you can create a policy from within a query in the **Activity log**, or else use the **Policies** node in the navigation pane.

:::image type="content" source="../media/activity-log.png" alt-text="A screenshot of the Activity log page. The administrator has selected an **App** that equals **Active Directory**. Three activities are displayed.":::

For example, to save a query as an activity policy, use the following procedure:

1. From any Activity log page, apply a filter such as App, User Name, or Activity type. For example, to filter activities from Defender for Identity, select **Active Directory** in the **App** filter.
2. Select **New policy from search**.
3. Enter a **Policy name** and a policy **Description**.
4. Assign the **Severity** of the policy.
5. Select a **Category** for the policy.
6. Choose or modify filters to create and assign for the policy.
7. Refine or add more filters.
8. Save and apply the new policy.
