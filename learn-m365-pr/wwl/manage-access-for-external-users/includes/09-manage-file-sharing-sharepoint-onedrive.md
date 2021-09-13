Teams content such as files, folders, and lists are all stored in SharePoint. In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.

The organization-level settings determine what settings are available for individual sites, including sites associated with teams. Site settings can't be more permissive than the organization-level settings.

If you want to allow file and folder sharing with unauthenticated people, choose **Anyone**. If you want to ensure that all guests have to authenticate, choose **New and existing guests**. Choose the most permissive setting that will be needed by any site in your organization.

You can go to **SharePoint admin center** > **Sharing** to configure the file sharing experience.

:::image type="content" source="../media/manage-sharing-sharepoint.png" alt-text="Screenshot of external sharing setting in SharePoint admin center" :::

## External sharing settings

Because OneDrive is a hierarchy of sites within SharePoint, the organization-level sharing settings directly affect OneDrive just as they do other SharePoint sites.

| Setting | Default | Description |
|:-----|:-----|:-----|
|SharePoint|Anyone|Specifies the most permissive sharing permissions allowed for SharePoint sites.|
|OneDrive|Anyone|Specifies the most permissive sharing permissions allowed for OneDrive sites. This setting cannot be more permissive than the SharePoint setting.|

The options for sharing permissions include:

* **Anyone**: Allows users to share files and folders by using links that let anyone who has the link access the files or folders without authenticating. This setting also allows users to share sites with new and existing guests who authenticate. If you select this setting, you can restrict the Anyone links so that they must expire within a specific number of days, or so that they can give only View permission.

* **New and existing guests**: Requires people who have received invitations to sign in with their work or school account (if their organization uses Microsoft 365) or a Microsoft account, or to provide a code to verify their identity. Users can share with guests already in your organization's directory, and they can send invitations to people who will be added to the directory if they sign in.

* **Existing guests**: Allows sharing only with guests who are already in your directory. These guests may exist in your directory because they previously accepted sharing invitations or because they were manually added, such as through Azure B2B collaboration.

* **Only people in your organization**: Turns off external sharing.  

## Advanced sharing settings

| Setting | Default | Description |
|:-----|:-----|:-----|
|Limit external sharing by domain|Off|This setting allows you to specify a list of allowed or blocked domains for sharing. When allowed domains are specified, then sharing invitations can only be sent to those domains. When denied domains are specified, then sharing invitations cannot be sent to those domains.<br><br> This setting affects all SharePoint and OneDrive sites in the organization.|
|Allow only users in specific security groups to share externally|Off|If you want to limit who can share with guests in SharePoint and OneDrive, you can do so by limiting sharing to people in specified security groups. These settings do not affect sharing via Microsoft 365 Groups or Teams. Guests invited via a group or team would also have access to the associated site, though document and folder sharing could only be done by people in the specified security groups.<br><br>For each specified group, you can choose if those users can share with Anyone links.|
|Guests must sign in using the same account to which sharing invitations are sent|Off|Prevents guests from redeeming site sharing invitations using a different email address than the invitation was sent to.<br><br>[SharePoint and OneDrive integration with Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration?azure-portal=true) does not use this setting because all guests are added to the directory based on the email address that the invitation was sent to. Alternate email addresses cannot be used to access the site.|
|Allow guests to share items they don't own|On|When **On**, guests can share items that they don't own with other users or guests; when **Off** they cannot. Guests can always share items for which they have full control.|
|Guest access to a site or OneDrive will expire automatically after this many days| off | This setting allows you to create a policy that revokes guest access to documents and files after a set number of days.
|People who use a verification code must reauthenticate after this many days|Off|This setting allows you to require that users authenticating with a one-time passcode need to reauthenticate after a certain number of days.|
