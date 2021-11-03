You can use Defender for Cloud Apps app connectors to enable better control and visibility of your organization's cloud apps. Defender for Cloud Apps uses APIs provided by your cloud app provider to enable and manage connections to that provider's apps. You can even connect to multiple instances of the same cloud app. For example, you might use Salesforce in two parts of your organization. Each instance is treated and managed separately by Defender for Cloud Apps.

> [!IMPORTANT]
> This multi-instance app support does not include Microsoft Azure or Office 365.

## Overview

The following process describes how Defender for Cloud Apps uses app connectors. Defender for Cloud Apps:

1. Retrieves and save authentication permissions.
2. Requests the user list.
3. Periodically scans users, groups, activities, and files.

> [!TIP]
> For each app you want to connect to, we recommend that you create an admin service account for that purpose alone.

The following table describes the items you can enable through your app connector.

| Items                      | Description                                                  |
| -------------------------- | ------------------------------------------------------------ |
| Account  information       | Visibility  into users, accounts, profile information, status (suspended, active,  disabled) groups, and privileges |
| Audit trail                | Visibility  into user activities, admin activities, sign-in activities |
| Data scan                  | Scanning of  unstructured data using two processes -periodically (every 12 hours) and in  real-time scan (triggered each time a change is detected). |
| App  permissions           | Visibility  into issued tokens and their permissions         |
| Account  governance        | Ability to  suspend users, revoke passwords                  |
| Data  governance           | Ability to  quarantine files, including files in trash, and overwrite files |
| App  permission governance | Ability to  remove tokens                                    |

> [!IMPORTANT]
> Not all apps that are connected will have all the governance actions.

## How to connect apps

To add an app connector, for example, a connector to GitHub, use the following procedure:

1. Navigate to the [Defender for Cloud Apps portal](https://portal.cloudappsecurity.com?azure-portal=true).
2. Sign in as a Global Admin.
3. In Defender for Cloud Apps, select **Settings** (the cog icon), and then select **App connectors**.
4. On the **Connected apps** page, displayed in the following screenshot, select the **App connectors** tab.
5. Then select the **+** symbol.
6. Choose from the list of supported app connectors. In this case, select **GitHub**.
7. In the **GitHub** dialog box, enter an **Instance name**, and then select **Connect GitHub**.
8. Enter the required details:

    - Client ID
    - Client Secret
    - Organization Login Name

9. Select **Connect in GitHub** and complete the connection process.

> [!IMPORTANT]
> Some vendors require that you add their apps' IP addresses to allow lists to enable access from Defender for Cloud Apps.

### What apps can you connect with?

You can use Defender for Cloud Apps app connectors to connect to the following apps:

> [!NOTE]
> This list is subject to change as Defender for Cloud Apps adds more apps for API connections.

- Microsoft Azure
- Amazon Web Services
- Box
- Cisco Webex
- Dropbox
- GitHub
- Google Cloud Platform
- Google Workspace
- Microsoft Office 365
- Okta
- Salesforce
- ServiceNow
- Workday

> [!TIP]
> You can select **Suggest more apps** from the drop down list to request additional app connectors.

> [!IMPORTANT]
> To connect Defender for Cloud Apps to Azure, you must be a Global or Security administrator in Azure AD.

### Connect Office 365

Defender for Cloud Apps supports the following Office 365 apps:

- Dynamics 365 CRM
- Exchange
- Office
- OneDrive
- Power Automate
- Power BI
- SharePoint
- Skype for Business
- Teams
- Yammer

When you connect to Office 365 using the procedure outlined earlier, you are prompted to select Office 365 components. These are described in the following table.

| Component                   | Description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| Azure AD User  and groups   | Enables Cloud  App Security to monitor users and groups in Azure AD. This is a prerequisite  for all other components. |
| Azure AD  Management events | Enables Cloud  App Security to monitor admin activities in Azure AD |
| Azure AD  Sign-in events    | Enables Cloud  App Security to audit all sign in and sign out activities. |
| Azure AD Apps               | Enables Cloud  App Security to monitor all OAuth apps registered in Azure AD. |
| Office 365  activities      | Enables Cloud  App Security to audit all user activities across your Office 365 apps. |
| Office 365  files           | Enables Cloud  App Security to audit all file activities across your Office 365 apps. |

The following screenshot displays these components.

:::image type="content" source="../media/office365-components.png" alt-text="A screenshot of the Connect Office 365 dialog box. The options discussed in the preceding table are displayed.":::
