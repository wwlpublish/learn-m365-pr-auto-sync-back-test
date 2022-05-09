Public folders have been a feature of Exchange for as long as Exchange Server has been around. They continue to provide an easy way to access shared content. You should understand how to configure and troubleshoot public folders to best support your users.

If your organization doesn't currently use public folders, you'll need to create the required public folder mailboxes. You should start by creating the primary public folder mailbox by using the following Exchange Online PowerShell command: 

``` powershell
New-Mailbox -PublicFolder -Name MasterHierarchy
```

After that, you can create additional public folders using the `New-PublicFolder` command. For example:

``` powershell
New-PublicFolder -Name Sales -Path \
```

> [!TIP]
> You can verify the presence of the root public folder using the `Get-OrganizationConfig | Format-List RootPublicFolderMailbox` command.

## Troubleshoot mail-enabled public folders

For users to be able to send email to public folders, you must mail-enable those folders. You can use the following PowerShell command to check whether a folder is mail enabled: 

``` powershell
Get-PublicFolder -recurse | ft Name, MailEnabled
```

If you need to mail-enable the folder, use the following procedure within Exchange admin center:

1. Open the **Exchange admin center** and expand **Public folders**.
1. Click **Public folders** and then select the appropriate public folder.
1. In the actions area, beneath the **Mail settings - Disabled** heading, click **Enable**.

    :::image type="content" source="../media/mail-enable-public-folder.png" alt-text="Screenshot showing the list of public folders in the Exchange admin center.":::

1. At the **Warning**, click **Yes**.

To determine the email address, in the admin center:

1. Open the public folder by clicking **Edit**.
1. On the **general mail properties** tab, review and if needed, update the **Alias** and **Display Name** properties. These properties default to the public folder name.

    > [!TIP]
    > You can select **Hide from Exchange address list** if you want.

1. On the **email address** tab, review and optionally edit the email address or addresses.

1. Click **Save**.

> [!TIP]
> If users are unable to send email messages to a public folder, verify the mail flow settings to ensure there are no restrictions. 

You might want to assign delegate access for the public folder so that other users can use **Send As** or **Send on Behalf** actions for the folder. You can configure the delegate access by using the Exchange admin center.

1. Open the Exchange admin center and select **public folders** > **public folders**.
1. Select the public folder that requires permission, and then click **Edit**.
1. Select the **delivery options** tab, and then add the user to **Send As** or **Send on Behalf** permissions, as required.
1. Select **Save**.

You can use the following PowerShell command to assign Send on Behalf permissions: 

``` powershell
Set-MailPublicFolder -Identity <Folder name> -GrantSendOnBehalfTo <User>
```

If you need to assign, Send as Access, use the following command:

``` powershell
Add-RecipientPermission -Identity <Folder name> -Trustee <User> -AccessRights 'SendAs'
```

## Troubleshoot access to public folders

Public folders are available to Outlook desktop clients, Outlook on the web, and Outlook for macOS. So long as your users are using a supported client type, then access problems might be related to permissions. You can check the permissions in the Exchange admin center.

1. Open the Exchange admin center and select **public folders** > **public folders**.
1. Select the appropriate public folder and in the actions pane, click **Manage**.
1. Review the configured permissions. If necessary, click **Add**.
1. In the **public folder permissions** dialog box, shown in the following screenshot, click **Browse** and locate the appropriate user and click **Add**.
1. Configure the desired permissions and click **Save**. Choose between:

    - Reviewer
    - Contributor
    - Non Editing Author
    - Author
    - Editor
    - Publishing Author
    - Publishing Editor
    - Owner
    - Custom

1. Click **Save** again.

    :::image type="content" source="../media/public-folder-permissions.png" alt-text="Screenshot of the public folder permissions dialog box. AdeleV is assigned Publishing Editor permissions.":::

## Troubleshoot load-balancing issues for public folders

Heavily used public folders can impose a load on a public folder mailbox. If you add a new public folder mailbox, use the `IsHierarchyReady` parameter to determine whether the public folder mailbox is ready to serve the public folder hierarchy to users.

Check the IsHierarchyReady parameter by using this PowerShell command:

``` powershell
Get-Mailbox -PublicFolder Identity "Public folder name" | FL Name,IsHierarchyReady
```

> [!NOTE]
> If this command returns True for the IsHierarchyReady property then the entire hierarchy has been synced to the public folder mailbox.

The `IsExcludedFromServingHierarchy` parameter prevents users from accessing the public folder hierarchy on the specified public folder mailbox. For load-balancing purposes, users are equally distributed across public folder mailboxes by default. When this parameter is set to true on a public folder mailbox, that mailbox isn't included in this automatic load balancing and won't be accessed by users to retrieve the public folder hierarchy. Check the `IsExcludedFromHierarchy` parameter by using this PowerShell command:

``` powershell
Get-Mailbox -PublicFolder Identity "Public folder name" | FL Name,IsExcludedFromHierarchy
```

## Learn more

- [Create a public folder mailbox in Exchange Server](/exchange/collaboration/public-folders/create-public-folder-mailboxes)
- [Public folders in Exchange Server](/exchange/collaboration/public-folders/public-folders)