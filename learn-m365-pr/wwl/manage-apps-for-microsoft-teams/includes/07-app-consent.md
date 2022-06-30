Admins can grant org-wide admin consent to apps that request permissions to access data and view resource-specific consent (RSC) permissions for apps. Keep in mind that the process applies only to **custom** and **third-party apps**. You won’t see the link or need to grant admin consent for apps published by Microsoft.

## View resource-specific consent (RSC) permissions for apps

RSC permissions let team owners grant consent for an app to access and modify a team's data. RSC permissions are granular Teams-specific permissions that define what an app can do in a specific team.

From the **Manage apps** page, the **Permissions** column indicates whether an app has permissions that need consent. You'll see a **View details** link for each app registered in Azure AD that has permissions that need consent.

Examples of RSC permissions include the ability to:

-   Create and delete channels,
-   Get the settings for a team.
-   Create and remove channel tabs.

    :::image type="content" source="../media/app-perm-admin-center-rsc-new.png" alt-text=" Screenshot of RSC permissions for an app.":::

## Evaluate security, compliance, and privacy of third-party apps

Microsoft requires all apps to pass a mandatory validation before being listed in the store for end-uses. It applies to all apps (except custom apps) published on the Teams App store.

From the **Manage apps** page, the **Certification** column provides the app validation information. Admins can use the information to better evaluate Teams apps before enabling it for the organization. You can see the following

-   **Publisher Attestation:** The app publishers complete a self-assessment of your app's security, data handling, and compliance practices. Publisher attested apps provide confidence to admins about security and compliance measures of an app.
-   **Microsoft 365 certified:** The Microsoft 365 App Compliance Program checks and audits an app against controls that are derived from leading industry-standard frameworks. The Microsoft 365 Certified apps have strong security and compliance practices are in place to protect their data security, and privacy.
-   **“—”:** The app is either a Microsoft-provided app or no certification information for the app.

You can find information about security, privacy, compliance and behaviors for an attested or certified app in [Microsoft documentation](/microsoft-365-app-certification/teams/teams-apps?azure-portal=true) and Teams admin center.

When evaluating an app for your organization, you can use independent Cloud Access Security Brokers (CASB), such as Microsoft Cloud App Security (MCAS), to find information about security and behaviors of an app. The Teams admin center includes security and compliance information from MCAS for Microsoft 365 Certified apps to check if an app meets your needs.

You can access **Security and Compliance** information for an app:

1.  In the Teams admin center, select **Manage apps** under **Teams apps**.
2.  Select **Certification** column name to sort apps and push all Microsoft 365 Certified apps to the top of the table.
3.  Choose a Microsoft 365 Certified app.
4.  Select the **Security and compliance** tab.

    To get more details on the supported capabilities for the app, select the dropdown list for each category.

    :::image type="content" source="../media/mcas.png" alt-text=" Screenshot of Teams admin center security and compliance tab":::

### Grant org-wide admin consent to an app

If you’re a global admin, you can review and grant consent to apps that request permissions on behalf of all users in your organization. You do the consent in advance so that users don’t have to review and accept the permissions requested by the app when they start the app. Additionally, depending on the user’s consent settings in Azure Active Directory (Azure AD), some users may not be allowed to grant consent to apps that access company data.

To grant org-wide consent to an app, follow these steps:

1.  In the left navigation of the Microsoft Teams admin center, go to **Teams apps** \> **Manage apps**.
2.  Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
3.  Under **Org-wide permissions**, select **Review permissions and consent**.



    :::image type="content" source="../media/app-permission-admin-center-organization-wide.png" alt-text=" Screenshot of org-wide permissions on the Permissions tab for an app":::

    You must be a global admin to do the consent. This option isn't available to Teams service admins.

4. On the **Permissions** tab, review the permissions requested by the app.

    :::image type="content" source="../media/app-permission-admin-center-organization-wide-permissions.png" alt-text=" Screenshot of permissions requested by an app":::

    
5. If you agree with the permissions requested by the app, select **Accept** to grant consent. A banner temporarily appears at the top of the page to let you know that the requested permissions have been granted for the app. The app now has access to the specified resources for all users in your organization and no one else will be prompted to review the permissions.

After you accept the permissions, you'll see a message under **Org-wide permissions** on the app details page to let you know that consent was granted. To view details about the app's permissions, select the **Azure Active Directory** link to go to the app's page in the Azure AD portal.


