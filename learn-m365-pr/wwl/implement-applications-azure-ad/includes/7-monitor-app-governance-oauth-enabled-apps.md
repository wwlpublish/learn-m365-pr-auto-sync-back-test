Cyberattacks have become increasingly sophisticated in the ways they exploit the apps that organizations have deployed in their on-premises and cloud infrastructures. These attacks establish a starting point for privilege escalation, lateral movement, and exfiltration of an organization's data. For this reason, it's imperative that organizations understand the potential risks and stop these types of attacks. To do so, they must gain clear visibility into their app compliance posture. This visibility will enable them to quickly identify when an app exhibits anomalous behaviors. They can also respond when these behaviors present risks to their environment, data, and users.

The app governance add-on feature to Microsoft Defender for Cloud Apps is a security and policy management capability. App governance:

 -  Is designed for OAuth-enabled apps that access Microsoft 365 data through Microsoft Graph APIs.
 -  Delivers full visibility, remediation, and governance into how these apps and their users access, use, and share an organization's sensitive data stored in Microsoft 365.
 -  Provides these features through actionable insights and automated policy alerts and actions.

App governance provides organizations with comprehensive:

 -  **Insights**. Displays all the third-party apps in an organization's Microsoft 365 tenant on a single dashboard. The view displays the status of all apps and alert activities. This design enables organizations to react or respond to them.
 -  **Governance**. Create proactive or reactive policies for app and user patterns and behaviors. This feature enables an organization to protect its users from using non-compliant or malicious apps. It also limits the access of risky apps to company data.
 -  **Detection**. Organizations are alerted and notified when there are anomalies in app activity. They're also notified when non-compliant, malicious, or risky apps are used.
 -  **Remediation**. Along with automatic remediation capabilities, organizations should use remediation controls in a timely manner to respond to anomalous app activity detections.

App governance is a platform-based solution that's an integral part of the Microsoft 365 app ecosystem. App governance oversees and governs OAuth-enabled apps that:

 -  Are registered with Azure Active Directory (Azure AD).
 -  Access data through the Microsoft Graph API.

App governance provides organizations with application behavior controls to help strengthen the security and compliance posture of their IT infrastructure.

### App governance integration with Azure AD and Defender for Cloud Apps

App governance, Azure AD, and Microsoft Defender for Cloud Apps collect and provide different data sets:

 -  **App governance**. Provides detailed information about an app’s activity at the API level.
 -  **Azure AD**. Provides foundational app metadata and detailed information on sign-ins to apps.
 -  **Microsoft Defender for Cloud Apps**. Provides app risk information.

An organization can share information across app governance, Azure AD, and Microsoft Defender for Cloud Apps. By doing so, the organization can display aggregate information in one portal and easily link to another portal for more information. For example:

 -  **App sign-in information in app governance**. From the app governance portal, you can see the aggregated sign-in activity for each app. You can also link back to the Azure Active Directory admin center for the details of sign-in events.
 -  **API usage information in the Microsoft Defender for Cloud Apps portal**. From the Microsoft Defender for Cloud Apps portal, you can see API usage level and aggregate data transfer and link to the app governance portal for the details.

The following graphic displays a summary of the integration.

:::image type="content" source="../media/app-governance-architecture-3d489fa6.png" alt-text="Graphic shows a summary of the integration between app governance, Azure Active Directory, and Microsoft Defender for Cloud Apps.":::


App governance sends its alerts to Microsoft Defender for Cloud Apps and Microsoft 365 Defender. It then receives alerts from Microsoft Defender for Cloud Apps. These alerts enable more detailed analysis of app-based security incidents.

 -  **Alerts sent from App governance to Microsoft 365 Defender**. These alerts appear in Microsoft 365 Defender with the **Detection source** field set to **App Governance**.
 -  **Alerts sent from App governance to Microsoft 365 Defender for Cloud Apps**. These alerts appear in Microsoft 365 Defender for Cloud Apps with the **Policy** field set to one of the following values:
    
     -  Microsoft 365 OAuth App Governance
     -  Microsoft 365 OAuth Phishing Detection
     -  Microsoft 365 OAuth App Reputation
 -  **Alerts sent from Microsoft 365 Defender for Cloud Apps to Apps governance**. These alerts appear in app governance with the **Source** field set to **Defender for Cloud Apps**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”