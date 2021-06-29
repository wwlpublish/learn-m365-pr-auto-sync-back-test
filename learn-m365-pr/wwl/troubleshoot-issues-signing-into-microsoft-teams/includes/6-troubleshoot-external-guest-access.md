The ability to communicate with users outside your own organization is an essential part of Teams. Guest access in Teams allows people outside your organization to access teams and channels inside your organization. A guest is someone who isn't an employee, student, or member of your organization, and don't have a school or work account with your organization. For example, guests might include partners, vendors, suppliers, or consultants.

Anyone can be added as guest in Teams. This means that anyone with a business (with an Azure AD account) or consumer email account can participate as a guest in Teams, and have full access to team chats, meetings, and files. 

Organizations using Teams can provide this external access while maintaining complete control over their own corporate data. All guests in Teams are covered by the same compliance and auditing protection as the rest of Office 365, and can be managed securely within Azure AD.

> [!TIP]
> Guest access is a tenant-level setting in Teams and is turned off by default.

Before you get involved in fine tuning and troubleshooting guest access within specific services, it’s a good idea to make sure Guest access and External access is enabled at an organizational level. 

> [!TIP]
> The key principle to remember when comparing Guest access and External access is that Guest access grants access permission to an individual, while External access grants access permission to an entire domain.

## Ensure Microsoft Teams is enabled for Guest access

If you’re experiencing problems with Guest access, or adding guests to Teams, check the global settings for Microsoft 365. In the Microsoft 365 admin center:

1. Select **Settings** and then select **Org settings**.
2. In the details pane, select **Microsoft Teams**.
3. On the **Microsoft Teams** blade, ensure that the **Allow guest access in Teams** setting is enabled. 
4. If needed, select **Save**.

:::image type="content" source="../media/global-access.png" alt-text="A screenshot displays the Microsoft Teams blade in the Org settings section of the Microsoft 365 admin center. Both settings are enabled.":::

## Verify org-wide External access and Guest access settings

To verify org-wide guest and external access settings, open the **Microsoft Teams admin center**. Select **Org-wide settings**. You can then select the following settings:

- **External access**. Configures external access for your Teams and Skype for Business users, allowing or blocking communication with users that are outside of your organization. You can also choose to allow or block communications on a per-domain basis. 

   :::image type="content" source="../media/external-access.png" alt-text="A screenshot displays the External access page on the Org-wide settings. All settings are enabled. The administrator has blocked access with Adatum.com domain.":::

- **Guest access**. Allows or blocks guest access to teams and channels from people outside your organization. From the Guest access page, you can configure the following settings for your guest users at an Org-wide level:

   - **Allow guest access in Teams**
   - **Make private calls**
   - **Allow IP video**
   - **Screen sharing mode**
   - **Allow Meet Now**
   - **Enable guest users to edit or delete sent message**
   - **Enable Chat and the use of chat features, such as Giphy, memes, and stickers**

   :::image type="content" source="../media/guest-access.png" alt-text="A screenshot of the Guest access page in Org-wide settings. The default values are displayed.":::

> [!TIP]
> You can also enable or disable guest access from the Microsoft 365 admin center, or by using the `Set-CsTeamsClientConfiguration` PowerShell cmdlet.

### Troubleshoot External access

With Microsoft Teams External access, Teams users from other domains can participate in your chats and calls. Specifically, external access allows external users to find, call, and send you instant messages, as well as set up meetings with you.

Use External access when:

- You have users in different domains in your business: for example, Rob@contoso.com and Ann@northwindtraders.com. 
- You want the people in your organization to use Teams to contact people in specific businesses outside of your organization. 
- You want anyone else in the world who uses Teams to be able to find and contact you using your email address. 

If users from outside your organization are unable to collaborate with users within your organization, you must:

- Verify whether you have enabled and configured external access in your organization. 
- Determine whether the type of collaboration sought is supported by External access. 
- Verify that you have allowed the external domain, and that the external administrator has also allowed your domain.

> [!IMPORTANT]
> External access enables you to communicate with users from other domains that are already using Teams. Therefore, they must provide their own licenses to use Teams.

### Troubleshoot Guest access

If you want users from outside your organization to have access to teams and channels, Guest access is the only mechanism. 

A team owner in Microsoft Teams can add and manage guests in their teams via the web, mobile or desktop client. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams, with full access to team chats, meetings, and files. People outside your organization, such as partners or consultants, can be added as guests and people from within your organization, can join as regular team members.

If guests from outside your organization are unable to collaborate with users within your organization, you must:

- Verify whether you have enabled guest access for Teams.
- Determine whether the type of collaboration sought is supported by Guest access. 
- Verify that the appropriate meeting, messaging, and call policies are configured correctly for guest access.
- Verify that the guest users have available licenses in your organization.  

> [!IMPORTANT]
> Guest access utilizes your existing licenses when using certain features. Teams doesn't restrict the number of guests you can add. However, the total number of guests that can be added to your tenant is based on what your Azure AD licensing allows - usually 5 guests per licensed user. 

## Verify guest meeting configuration policies

If you’ve enabled and configured guest access at an organizational level, you might also need to verify the settings for specific policies for meetings. If guest users experience issues when creating meetings, review the meeting policy settings for **Participants & guests**. 

:::image type="content" source="../media/guest-settings.png" alt-text="A screenshot that displays the Participants & guests section of a meeting policy. Default settings are displayed.":::

The following table describes general policy settings. 

| Setting                                  | Description                                                  |
| ---------------------------------------- | ------------------------------------------------------------ |
| **Let anonymous people start a meeting** | Enables an unauthenticated user to start a  meeting. A user might connect anonymously when they connect to a meeting  using their phone. |
| **Allow Meet  now in private meetings**  | Determines if  a user can start an unplanned private meeting. |
| **Automatically  admit people**          | Determines  who can automatically enter a meeting. For guests, you can select Everyone,  People in my organization and guests, or People in my organization, trusted  organizations and guests. |
