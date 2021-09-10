With guest access, you can provide access to teams, documents in channels, resources, chats, and applications to people outside your organization, while maintaining control over your corporate data. 

> [!NOTE]
> If you just want to find, call, chat, and set up meetings with people in other organizations, use external access. External access is a way for Teams users from an entire external domain to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business (online and on-premises) and Skype (in preview).

A guest is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants. Anyone who isn't part of your organization can be added as guest in Teams. This means that anyone with a business account (that is, an Azure Active Directory account) or consumer email account (with Outlook.com, Gmail.com or others) can participate as a guest in Teams, with access to teams and channel experiences.

Guests in Teams are covered by the same compliance and auditing protection as the rest of Microsoft 365. Guest access is subject to Azure AD and Microsoft 365 service limits. As a Teams administrator, you have full control over which features and services a guest can or can't have access to.

> [!IMPORTANT]
> Even if you activate Guest access in Teams, you must also ensure that Guest access is enabled in Azure AD.

## Guest access settings

### Guest calling

| Setting | Default | Description |
|:--|:--|:--|
|Make private calls|On|When **On**, guests can make peer-to-peer calls in Teams; when **Off**, they can't.|

### Guest meeting

| Setting | Default | Description |
|:--|:--|:--|
|Allow IP video|On|When **On**, guests can use video in their calls and meetings; when **Off**, they can't.|
|Screen sharing mode|Entire screen|When **Disabled**, guests can't share their screens in Teams. <br/>When set to **Single application**, guests can only share a single application on their screen. <br/>When set to **Entire screen**, guests can choose to share an application or their entire screen.|
|Allow Meet Now|On|When **On**, guests can use the Meet Now feature in Teams; when **Off**, they can't.|

### Guest messaging

| Setting | Default | Description |
|:--|:--|:--|
|Edit sent messages|On|When **On**, guests can edit messages they previously sent; when **Off**, they can't.|
|Delete sent messages|On|When **On**, guests can delete messages they previously sent; when **Off**, they can't.|
|Chat|On|When **On**, guests can use chat in Teams; when **Off**, they can't.|
|Use Giphy in conversations|On|When **On**, guests can use Giphys in conversations; when **Off**, they can't.|
|Giphy content rating|Moderate|When set to **Allow all content**, guests will be able to insert all Giphys in chats, regardless of the content rating. <br/>When set to **Moderate** guests can insert Giphys in chats, but will be moderately restricted from adult content. <br/>When set to **Strict** guests can insert Giphys in chats, but will be restricted from inserting adult content.|
|Use Memes in conversations|On|When **On**, guests can use memes in conversations; when **Off**, they can't.|
|User stickers in conversations|On|When **On**, guests can use stickers in conversations; when **Off**, they can't.|
|Allow immersive reader for viewing messages|On|When **On**, guests can view messages in Immersive Reader; when **Off**, they can't.|

:::image type="content" source="../media/teams-guest-access-setting.png" alt-text="Guest permissions settings in Teams" lightbox="../media/teams-guest-access-setting.png":::

## Configure guest access 

### Use Teams admin center

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/?azure-portal=true).

2. Select **Org-wide settings** > **Guest access**.

3. Set **Allow guest access in Microsoft Teams** to **On**.

4. Under **Calling**, **Meeting**, and **Messaging**, select **On** or **Off** for each capability, depending on what you want to allow for guest users.

5. Select **Save**.

### Use PowerShell

You can also use PowerShell to toggle guest access with ```Set-CsTeamsClientConfiguration``` cmdlet. For example, to allow guest users globally, run the following cmdlet:

```powershell
Set-CsTeamsClientConfiguration -AllowGuestUser $True -Identity Global
```

Then you can use the following cmdlets to customize the guest access settings:

```powershell
Set-CsTeamsGuestCallingConfiguration
Set-CsTeamsGuestMeetingConfiguration
Set-CsTeamsGuestMessagingConfiguration
```

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”