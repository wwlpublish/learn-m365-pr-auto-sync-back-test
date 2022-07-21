The purpose of this unit is to help administrators understand and troubleshoot problems when their organizations apply app protection policies in Microsoft Intune. Since app protection policies can cover a wide range of issues, the act of training admins on how to troubleshoot app-related problems would be a complex chore. As such, the training in this unit is designed to cover basic, high-level steps that administrators should be familiar to properly troubleshoot policy deployment issues. Along with this training, it's recommended that organizations also review the following links for more app protection policy troubleshooting guidance:

 -  [Troubleshooting app protection policy user issues](/troubleshoot/mem/intune/troubleshoot-mam?azure-portal=true).
 -  [Troubleshoot data transfer between apps](/troubleshoot/mem/intune/troubleshoot-data-transfer?azure-portal=true).

### Before you begin troubleshooting

Before an organization starts troubleshooting an app protection policy issue, it should collect some basic information to help it better understand the problem, and reduce the time to find a resolution.

Organizations should ask the following questions to collect basic background information:

 -  Which policy setting is or isn't applied? Is any policy applied?
 -  What's the user experience? Have users installed and started the targeted app?
 -  When did the problem start? Has app protection ever worked?
 -  Which platform (Windows, Android, iOS, or other) has the problem?
 -  How many users are affected? Are all users or only some users affected?
 -  How many devices are affected? Are all devices or only some devices affected?
 -  Even though Intune app protection policies don't require a mobile device management (MDM) service, are affected users using Intune or a third-party MDM solution?
 -  Are all managed apps affected, or only specific apps? For example, are line-of-business (LOB) apps built with the [Intune App SDK](/mem/intune/developer/app-sdk-get-started?azure-portal=true) affected but store apps aren't?
 -  Is any management service other than Intune being used on the device?

With the above information in place, an organization can start troubleshooting.

### Recommended investigation flow

Successful app protection policy deployment relies on proper configuration of settings and other dependencies. The recommended flow for investigating common issues with Intune app protection policies is as follows:

1.  Verify you've met the prerequisites for deploying app protection policies.
2.  Check app protection policy status and check targeting.
3.  Verify the user is targeted.
4.  Verify the managed app is targeted.
5.  Verify the user signed in to the affected application using their targeted corporate account.
6.  Collect device data.

Each of these steps is examined in greater detail in the following sections.

#### Step 1: Verify app protection policy prerequisites

The first step in troubleshooting an app protection policy is to check whether all prerequisites are met. Although organizations can use Intune app protection policies independent of any MDM solution, the following prerequisites must still be met:

 -  The user must have an Intune license assigned.
 -  The user must belong to a security group that's targeted by an app protection policy. The same app protection policy must target the specific app that's used.
 -  For Android devices, the **Company Portal** app is required to receive app protection policies.
 -  If an organization uses Word, Excel, or PowerPoint apps, the following requirements must be met:
     -  The user must have a license for [Microsoft 365 Apps for Business or Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans?azure-portal=true) linked to the user's Azure Active Directory (Azure AD) account. The subscription must include the Office apps on mobile devices and can include a cloud storage account with OneDrive for Business.
     -  The user must have a managed location that's configured by using the granular **Save as** functionality. This command is located under the **Save Copies of Org Data** application protection policy setting. For example, if the managed location is OneDrive, the OneDrive app should be configured in the user's Word, Excel, or PowerPoint app.
     -  If the managed location is OneDrive, the app must be targeted by the app protection policy that's deployed to the user.
    
    > [!NOTE]
    > The Office mobile apps currently support only SharePoint Online and not SharePoint on-premises.
 -  If an organization uses Intune app protection policies together with on-premises resources (Microsoft Skype for Business and Microsoft Exchange Server), it must enable [Hybrid Modern Authentication for Skype for Business and Exchange](/microsoft-365/enterprise/hybrid-modern-auth-overview?azure-portal=true).

#### Step 2: Check app protection policy status

Organizations should review the following details to understand the status of their app protection policies:

 -  Has there been a user check-in from the affected device?
 -  Are the applications for the problem scenario managed through the targeted policy?
 -  Verify the timing of policy delivery is within expected behavior. For more information, see [Understand app protection policy delivery timing](/mem/intune/apps/app-protection-policy-delivery?azure-portal=true).

Perform the following steps to get detailed information:

1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
2.  On the **Apps \| Overview** page, select **Monitor** in the middle navigation pane.
3.  On the **Monitor \| App licenses** page, select **App protection status** on the middle navigation pane.
4.  On the **Monitor \| App protection status** page, select the **Assigned users** tile.
5.  On the **App reporting** page, select the **Select user** option on the menu bar.
6.  In the **Select user** pane that appears, search for and select one of the affected users from the list. Then select the **Select** button at the bottom of the pane.
7.  At the top of the **App reporting** page, you can see whether the user is licensed for app protection and has a license for Microsoft 365. You can also see the app status for all the user's devices.
8.  Document important information such as:
     -  the targeted apps
     -  device types
     -  policies
     -  device check-in status
     -  last sync time

> [!NOTE]
> App protection policies are applied only when apps are used in the work context. For example, when the user is accessing apps by using a work account.

**Additional reading**. For more information, see [How to validate your app protection policy setup in Microsoft Intune](/mem/intune/apps/app-protection-policies-validate?azure-portal=true).

#### Step 3: Verify the user is targeted

Intune app protection policies must be targeted to users. If an organization doesn't assign an app protection policy to a user or user group, the policy isn't applied.

To verify the policy is applied to the targeted user, perform the following steps:

1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
2.  On the **Apps \| Overview** page, select **Monitor** in the middle navigation pane.
3.  On the **Monitor \| App licenses** page, select **App protection status** on the middle navigation pane.
4.  On the **Monitor \| App protection status** page, select the **User status** tile (based on device OS platform).
5.  On the **App reporting** page, select the **Select user** option on the menu bar.
6.  In the **Select user** pane that appears, select the user from the list, and then select the **Select** button at the bottom of the pane.

    > [!NOTE]
    > Note it can take up to 24 hours for a newly targeted user to show up in reports.

When an organization assigns the policy to a user group, perform the following steps to ensure the user is in the user group:

1.  In the **Microsoft Endpoint Manager admin center**, select **Groups** in the navigation pane.
2.  On the **Groups** page, select **All groups.**
3.  Search for and select the group that's used for your app protection policy assignment.
4.  Under the **Manage** section, select **Members**.
5.  If the affected user isn't listed, review [Manage app and resource access using Azure Active Directory groups](/azure/active-directory/fundamentals/active-directory-manage-groups?azure-portal=true) and your group membership rules. Verify the affected user is included in the group.
6.  Verify the affected user isn't in any of the excluded groups for the policy.

Organizations should verify the following conditions when assigning a policy to a user group:

 -  The Intune app protection policy must be assigned to user groups and not device groups.
 -  If the affected device uses Android Enterprise, only personally owned work profiles will support app protection policies.
 -  If the affected device uses Apple's Automated Device Enrollment (ADE), verify that **User Affinity** is enabled. **User Affinity** is required for any app that requires user authentication under ADE. For more information on iOS/iPadOS ADE enrollment, see [Automatically enroll iOS/iPadOS devices](/mem/intune/enrollment/device-enrollment-program-enroll-ios?azure-portal=true).

#### Step 4: Verify the managed app is targeted

> [!WARNING]
> When an organization configures Intune app protection policies, the targeted apps must use Intune App SDK. Otherwise, app protection policies may not work correctly.

Organizations should verify the targeted app is included in the list of [Microsoft Intune protected apps](/mem/intune/apps/apps-supported-intune-apps?azure-portal=true). For LOB or custom apps, verify the apps use the latest version of Intune App SDK.

For iOS, this practice is important because each version contains fixes that affect how these policies are applied and how they function. For more information, see [Intune App SDK iOS releases](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/releases?azure-portal=true).

Android users should have the latest version of the **Company Portal** app installed because the app works as the policy broker agent.

#### Step 5: Verify the user signed in to the affected application using their targeted corporate account

Some apps can be used without user sign-in. However, to successfully manage an app using Intune app protection policies, an organization's users must sign in to the app using their corporate credentials. Intune app protection policies require the user's identity be consistent between the app and Intune App SDK. Organizations must verify the affected user has successfully signed in to the app with their corporate account.

In most scenarios, users sign in to their accounts with their user principal name (UPN). However, in some environments (such as on-premises scenarios), users may use some other form of sign-in credentials. In these cases, an organization may find the UPN that's used in the app doesn't match the UPN object in Azure AD. When this situation issue occurs, app protection policies aren't applied as expected.

> [!IMPORTANT]
> The recommended best practice is to match the UPN to the primary SMTP address. Doing so enables users to sign-in to managed apps, Intune app protection, and other Azure AD resources by having a consistent identity. For more information, see [Azure AD UserPrincipalName population](/azure/active-directory/hybrid/plan-connect-userprincipalname?azure-portal=true).

The only way to guarantee this consistency is through [modern authentication](/microsoft-365/enterprise/hybrid-modern-auth-overview?azure-portal=true). There are scenarios in which apps may work in an on-premises configuration without modern authentication. However, the outcomes aren't consistent or guaranteed.

If your environment requires alternative sign-in methods, see [Configuring Alternate Sign-in ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id?azure-portal=true), specifically [Hybrid Modern Authentication with Alternate-ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id#hybrid-modern-authentication-with-alternate-id?azure-portal=true).

#### Step 6: Collect device data with Microsoft Edge

An organization should work with its users to collect details about what they're trying to do and the steps they're taking to do it. Users should be asked to collect screenshots or a video recording of their behavior. Doing so will help clarify the explicit device actions being performed. The organizations should then collect managed app logs through Microsoft Edge on the device.

Users with Microsoft Edge installed on their iOS or Android devices can view the management status of all Microsoft published apps. They can use the following steps to send logs to help with troubleshooting.

1.  Open Microsoft Edge for iOS and Android on your device.
2.  In the address bar, type **about:intunehelp**.
3.  Microsoft Edge for iOS and Android launches in troubleshooting mode.

From this screen, the user will be presented with data about the device and two options, **Get Started** and **View Intune App Status**. These options are examined in the following sections.

:::image type="content" source="../media/intune-diagnostics-start-2e310fa0.png" alt-text="Screenshot of the Intune Diagnostics start page with the View Intune App Status option highlighted.":::


#### Get started option

The **Get Started** option enables organizations to collect logs about the app protection policy-enabled applications. If an organization opens a support ticket with Microsoft for app protection policies, it should always provide these logs from an affected device, if possible. For Android-specific instructions, see [Upload and email logs](/mem/intune/user-help/send-logs-to-your-it-admin-by-email-android?azure-portal=true).

:::image type="content" source="../media/intune-logs-5ac62678.png" alt-text="Screenshot of the Collect Intune Diagnostics page showing the options to Share logs and to Send logs to Microsoft.":::


For a list of the settings stored in the Intune Diagnostics (APP) logs, see [Review client app protection logs](/mem/intune/apps/app-protection-policy-settings-log).

#### View Intune App Status option

The **View Intune App Status** option displays a list of apps. If you select a specific app, the app's protection policy settings that are currently active on the device will be displayed. The following screenshot shows some of the settings for the **com.microsoft.msedge** app.

:::image type="content" source="../media/intune-diagnostics-app-status-e214553a.png" alt-text="Screenshot of the Intune App Status page showing the settings associated with a selected app.":::


If the information displayed for a specific app is limited to the app version and bundled with the policy check-in timestamp, it means that no policy is currently applied to that app on the device.

### Additional troubleshooting scenarios

Organizations should review the following common scenarios when troubleshooting an app protection policy issue. they can also review the scenarios in [Common data transfer issues](/troubleshoot/mem/intune/data-transfer-scenarios?azure-portal=true).

#### Scenario: Policy changes aren't applying

The Intune App SDK checks regularly for policy changes. However, this process may be delayed for any of the following reasons:

 -  The app hasn't checked in with the service.
 -  The **Company Portal** app has been removed from the device.

Intune app protection policy relies on user identity. As such, a valid sign-in that uses a work or school account to the app and a consistent connection to the service are required. If the user hasn't signed in to the app, or the **Company Portal** app has been removed from the device, policies updates won't apply.

> [!TIP]
> Every 30 minutes the Intune App SDK checks for selective wipe. However, changes to existing policy for users who are already signed in may not appear for up to 8 hours. To speed up this process, have the user sign out of the app, and then sign back in or restart their device.

To check app protection status, organizations should perform the following steps:

1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
2.  On the **Apps \| Overview** page, select **Monitor** in the middle navigation pane.
3.  On the **Monitor \| App licenses** page, select **App protection status** on the middle navigation pane.
4.  On the **Monitor \| App protection status** page, select the **Assigned users** tile.
5.  On the **App reporting** page, select the **Select user** option on the menu bar.
6.  In the **Select user** pane that appears, select the user from the list, and then select the **Select** button at the bottom of the pane.
7.  On the **App reporting** page, review the policies that are currently applied, including the status and last sync time.
8.  If a policy's status is **Not checked in**, or if the display indicates there hasn't been a recent sync, check whether the user has a consistent network connection. For Android users, verify they have the latest version of the app installed.

Intune app protection policies include multi-identity support. Intune can apply app protection policies to only the work or school account that's signed in to the app. However, only one work or school account per device is supported.

#### Scenario: Intune-enrolled iOS devices require extra configuration

When an organization creates an app protection policy, it can target it to the following app types:

 -  All app types
 -  Apps on unmanaged devices
 -  Apps on Intune-managed devices
 -  Apps in the Android personally owned work profile

> [!NOTE]
> To specify the app types, set the **Target to all app types** option to **No**. Then select from the **App types** list.

If an organization is targeting only iOS Intune-managed devices, it must configure the following app configuration settings alongside its app protection policy:

 -  **IntuneMAMUPN** must be configured for all MDM (Intune or a third-party EMM)-managed applications.
 -  **IntuneMAMDeviceID** must be configured for all third-party and LOB MDM-managed applications.
 -  **IntuneMAMDeviceID** must be configured as the device ID token. For example, key=IntuneMAMDeviceID, value=\{\{deviceID\}\}. For more information, see [Add app configuration policies for managed iOS devices](/mem/intune/apps/app-configuration-policies-use-ios?azure-portal=true).

> [!WARNING]
> If only the **IntuneMAMDeviceID** value is configured, Intune app protection policies will consider the device as unmanaged.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”