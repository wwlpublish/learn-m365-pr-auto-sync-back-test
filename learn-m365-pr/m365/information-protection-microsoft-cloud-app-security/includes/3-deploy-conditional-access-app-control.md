Conditional App Access Control is a feature of Microsoft Cloud App Services that allows you to implement policies to monitor and control apps in real time. These policies can implement a number of controls, including:

- Protecting downloads by either labeling and protecting downloaded files with Azure Information Protection or blocking the copying or downloading of sensitive documents to unmanaged devices.
- Blocking the upload of files that are potentially malicious, or that are unlabeled.
- Blocking access or activities based on risk factors.
- Monitoring and logging the activity of risky users.

Any web app that uses Security Assertion Markup Language (SAML) 2.0 or Open ID Connect is supported for Conditional Access App Control. Any Azure AD app that uses Azure AD App Proxy is also supported for Conditional Access App Control.

The process of using a web app protected by Conditional Access App Control is as follows:

1. User browses to web app.
2. User authenticates using web app's identity provider.
3. Identity provider redirects to Microsoft Defender for Cloud Apps and Microsoft Defender for Cloud Apps applies a session policy.
4. The web session is proxied by Microsoft Defender for Cloud Apps.
5. Session activity is audited and governed.

## Steps to add an app to Conditional Access App Control

These are the steps to add a featured app to Conditional Access App Control:

1. Go to the Azure portal, select **Azure Active Directory** in the side menu, select **Security** in the side menu, and select **Conditional Access** in the side menu.

2. Either select an existing policy, or select **New policy** to create a new policy.

    :::image type="content" source="../media/3-new-policy.png" alt-text="New policy.":::

3. Select **Session**, select **Use Conditional App Access Control**, and select **Use custom policy**.

    :::image type="content" source="../media/3-device-compliance-app-policy.png" alt-text="Device compliance policy.":::

4. Save the policy and Conditional App Access Control works instantly for featured apps. Other apps can be onboarded in the Defender for Cloud Apps portal.

The following video walks through the steps to add an app to Conditional Access App Control:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Mnep]
