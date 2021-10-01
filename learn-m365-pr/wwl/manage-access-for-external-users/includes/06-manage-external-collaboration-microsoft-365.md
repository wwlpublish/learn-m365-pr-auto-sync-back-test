The Microsoft 365 admin center has organization-level settings for sharing and for Microsoft 365 Groups.

## External sharing settings in Microsoft 365

**Navigation**: [Microsoft 365 admin center](https://admin.microsoft.com?azure-portal=true)> **Settings** > **Org settings** > **Security & privacy** tab > **Sharing**

:::image type="content" source="../media/sharepoint-security-privacy-sharing-setting.png" alt-text="Screenshot of the security and privacy guest sharing setting in the  Microsoft 365 admin center":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Let users add new guests to the organization|On|When set to **Yes**, Azure AD members can invite guests via Azure AD; when set to **No**, they cannot. When set to **Yes**, Microsoft 365 Group members can invite guests with owner approval; when set to **No**, Microsoft 365 Group members can invite guests with owner approval but owners must be global administrators to approve. <br><br>Note that **Members can invite** refers to members in Azure AD (as opposed to guests) and not to site or group members in  Microsoft 365. <br><br>This is identical to the **Members can invite** setting in Azure Active Directory Organizational relationships settings.|

## Microsoft 365 Groups settings

**Navigation**: [Microsoft 365 admin center](https://admin.microsoft.com?azure-portal=true)> **Settings** > **Org settings** > **Microsoft 365 Groups**

:::image type="content" source="../media/office-365-groups-guest-settings.png" alt-text="Screenshot of Microsoft 365 Groups guest settings in Microsoft 365 admin center":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Let group members outside your organization access group content|On|When set to **On**, guests can access groups content; when set to **Off**, they can't. This setting should be **On** for any scenario where guests are interacting with Microsoft 365 Groups or Teams.|
|Let group owners add people outside your organization to groups|On|When **On**, Owners of Microsoft 365 Groups or Teams can invite new guests to the group. When **Off**, owners can only invite guests who are already in the directory.|

These settings are at the organization level. See [Create settings for a specific group](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) for information about how to change these settings at the group level by using PowerShell.
