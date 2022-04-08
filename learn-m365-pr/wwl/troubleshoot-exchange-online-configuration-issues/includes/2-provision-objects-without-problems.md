One of the fundamental administrative responsibilities of any messaging administrator is creating objects; these include contacts, groups, mailboxes, and other objects. It's important that you know how to avoid problems when provisioning objects, and how to troubleshoot provisioning problems when they occur.

## Interpret and troubleshoot validation errors encountered during object provisioning

When you attempt to provision objects, you might receive errors. Any error messages can help indicate the nature of the problem.

For example, when working in the Microsoft 365 Admin Center, you experience one or more of the following issues:

- A user object is highlighted with a red circle containing an X.
- You receive the following error message: `There's an error on one or more user accounts. To see which users are affected and the detailed error message, filter the list of users by Users with errors, select a user, and then click Edit.`
- When you view user properties, you receive the error: `Exchange: The name "<Name>" is already being used. Please try another name`.
- In the Azure Active Directory Module for Windows PowerShell, you get a validation error message when you run a cmdlet. For example: `Get-MsolUser -UserPrincipalName User1@contoso.com | Select Errors, ValidationStatus` returns:

    - `Errors : {Microsoft.Online.Administration.ValidationError,Microsoft.Online.Administration.ValidationError,Microsoft.Online.Administration.ValidationError}ValidationStatus : Error`

The cause of the problem can vary, so you'll need to investigate further, but the validation error can be a helpful starting point.

To retrieve errors for an object, use the following PowerShell command: 

``` powershell
$errors = (Get-<object_type> –ObjectID <Object_ID>).Errors`.
```

The following are supported object types:

- Contact - `MsolContact`
- Group - `MsolGroup`
- User - `MsolUser`

For example, the following commands retrieve errors for users' objects and then iterate through the users looking for detailed error information.

Run the following command to retrieve any errors for your users in Azure AD:

``` powershell
Get-MsolUser -HasErrorsOnly -All | ft DisplayName,UserPrincipalName,@{Name="Error";Expression={($_.errors[0].ErrorDetail.objecterrors.errorrecord.ErrorDescription)}} -AutoSize -wrap
```

To export the errors to a CSV file, run the following command:

``` powershell
Get-MsolUser -HasErrorsOnly | select DisplayName,UserPrincipalName,@{Name="Error";Expression={($_.errors[0].ErrorDetail.objecterrors.errorrecord.ErrorDescription)}} | Export-csv c:\temp\validationerrors.csv
```

To retrieve the service information and error message for each user, run the following command:

``` powershell
$errors | foreach-object {"`nService: " + $_.ErrorDetail.Name.split("/")[0]; "Error Message: " + $_.ErrorDetail.ObjectErrors.ErrorRecord.ErrorDescription}
```

The output resembles the following:

``` powershell
Service: MicrosoftCommunicationsOnline

Error Message: The value of the msRTCSIP-LineURI field in your local Active Directory is not unique, or the WorkPhone filed for the user conflicts with other users. Correct the value in your local Active Directory or in the tenant admin UI. After you correct it, the value will be updated in your Microsoft Online Services directory during the next Active Directory synchronization.
```

Having identified the problematic objects, you can attempt a resolution. The following table provides guidance on common error messages, causes, and how to resolve them.

| Error message| Cause| Resolution|
| :--- | :--- | :--- |
| `Exchange: The name <ObjectID> is already being used. Please try another name.`| Can vary| Run the following command: `Set-MsolUser –UserPrincipalName <UserPrincipalName of the User>`|
| `Exchange: Couldn't find object "<ObjectID>". Please make sure that it was spelled correctly or specify a different object.`| There is another object that is referenced from this object (such as permissions), and that object can't be found.| Check the permissions such as Full Access, Send As, Send on Behalf permissions. Make sure those users exist, or remove the permissions.|
| `Exchange: Group "<name>" can't be converted to a room list. Room lists can only have room mailboxes or room lists as members. "<name>" is not a room mailbox or a room list.`| This room list contains members that aren't room mailboxes or other room lists.| Make sure that the group contains only room mailboxes or room lists.|
| `Exchange: No mailbox plan with SKU 'BPOS_L_Standard' was found. User has no access to email`| The company previously had an Office 365 for professionals or small businesses plan or an Office 365 Small Business plan.| Nothing. User has access to email messages.|

## Determine when to restore or recover an inactive mailbox

If an employee has left your organization, their mailbox will no longer be used. If the mailbox contains items that might be useful even after the employee leaves, you might decide to retain the mailbox, at least for a period of time. As a security measure, you might make the mailbox inactive immediately following the employee's departure.

> [!NOTE]
> Mailboxes are retained in a soft-deleted state for 30 days by default. 

If you want to extend this 30-day soft-deleted period, you can apply a hold to the mailbox prior to deletion. This hold converts the mailbox into an inactive mailbox until you decide to either remove the hold, restore the inactive mailbox or recover the inactive mailbox.

Suppose that you then replace the employee, and the new employee needs access to the contents of the former employee's mailbox. In this situation, you have two choices:

- **Restore an inactive mailbox**. If you replace the former employee, or another user requires access to the mailbox, you can restore the mailbox contents to an existing mailbox.

> [!TIP]
> You can also restore the archive from an inactive mailbox.

> [!NOTE]
> After restoration, the inactive mailbox is retained as an inactive mailbox.

- **Recover an inactive mailbox**. If the former employee returns, or if a new employee replaces them in their role, you can recover the inactive mailbox. This process converts the inactive mailbox to a new mailbox that contains the contents of the inactive mailbox.

> [!WARNING]
> After you perform recovery, the inactive mailbox is removed. 

### Restore inactive mailboxes

To restore inactive mailboxes, you'll need to install and use Exchange Online PowerShell. Use the following procedure to install this module and to connect to your Exchange Online environment:

1. Open an elevated Windows PowerShell window and change the execution policy for scripts to remote signed by running: `set-executionpolicy remotesigned`.
1. If the **PowerShellGet** and **ExchangeOnlineManagement** modules are not installed, install them by running and confirming the following commands:

    ``` powershell
    install-module powershellget -force
    install-module -name ExchangeOnlineManagement
    ```

1. Connect to your Exchange Online environment: 

    ``` powershell
    connect-exchangeonline -userprincipalname name
    ```

    Where *name* is your administrative account, for example: `Admin@Contoso.com`.

> [!IMPORTANT]
> You can't use the Exchange admin center.

Start by identifying the inactive mailboxes by running: 

``` powershell
Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress`.
```

After you've identified the inactive mailboxes, you can restore the mailboxes needed. Use the following procedure:

1. Create a variable that contains the properties of the inactive mailbox: 

    ``` powershell
    $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>.
    ```

1. Display the **LegacyExchangeDN** of the inactive mailbox so that you can add it as a proxy address to the target mailbox in the next step: 

    ``` powershell
    $inactiveMailbox.LegacyExchangeDN
    ```

1. Add the **LegacyExchangeDN** of the inactive mailbox as an X500 proxy address to the target mailbox: 

    ``` powershell
    Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
    ```

1. Restore the contents of the inactive mailbox to an existing mailbox. The contents of the inactive mailbox (source mailbox) are merged into the corresponding folders in the existing mailbox (target mailbox):

    ``` powershell
    New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox>
    ```

### Recover inactive mailboxes

To recover inactive mailboxes, you'll also need to install and use Exchange Online PowerShell.

> [!IMPORTANT]
> You can't use the Exchange admin center.

As before, start by identifying the inactive mailboxes by running: 

``` powershell
Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
```

Then, use the following procedure:

1. Create a variable that contains the properties of the inactive mailbox:

    ```powershell
    $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
    ```

1. Create a new mailbox using the properties obtained in the previous command. Recover the inactive mailbox to an active mailbox for the user Adele Vance:

    ``` powershell
    New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name adeleV -FirstName Adele -LastName Vance -DisplayName "Adele Vance" -MicrosoftOnlineServicesID AdeleV@contoso.com -Password (ConvertTo-SecureString -String 'Pa55w.rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
    ```

    > [!IMPORTANT]
    > Ensure that the values specified for `Name` and `MicrosoftOnlineServicesID` parameters are unique within your organization.

1. After you recover an inactive mailbox, a new user account is also created. You need to activate this user account by assigning a license.

> [!NOTE]
> The primary SMTP address for the recovered inactive mailbox will have the same value as the one specified by the `MicrosoftOnlineServicesID` parameter.

## Troubleshoot issues managing resource mailboxes

Resource mailboxes are those mailboxes associated with **rooms** and **equipment** rather than specific individuals. The following table describes these two types of resource mailbox.

| Type| Description|
| :--- | :--- |
| Room| Assigned to a physical location, such as a conference room, an auditorium, or a training room. After you create room mailboxes, users can reserve rooms by including room mailboxes in meeting requests.|
| Equipment| Assigned to a resource that's not location specific, such as a laptop, projector, camera, or a company car. After you create an equipment mailbox, users can reserve the equipment by including the corresponding equipment mailbox in a meeting request.|

> [!TIP]
> You can use the Exchange Admin Center or Exchange Online PowerShell to create an equipment mailbox or change equipment mailbox properties.

It's important you familiarize yourself with the procedures for creating and managing resource mailboxes, in addition to the properties of these mailboxes. In this way, you can help to avoid problems with resource mailboxes. Consider the following:

- To create a room mailbox, you must be an administrator that's a member of either of the following role groups:

    - Organization Management
    - Recipient Management

- You should never set a Room mailbox as the organizer of a meeting. Users should only add Rooms to meetings by including them in the Attendee or Location fields.
- Don't assign Full Access permissions to directly manage resource calendars' response to a meeting invite.
- Sharing a room calendar to a user doesn't prevent you from enabling the Auto-accept setting for the room. If the room calendar is shared and Auto-accept is enabled, requests are accepted by default.

> [!TIP]
> However, the response can always be changed by any user with Editor or Delegate permissions to the room calendar.

There are a couple of common problems that your users might encounter when working with resource mailboxes, for example when making a booking. These issues are described in the following table, along with suggested solutions.

| Issue| Description| Solution|
| :--- | :--- | :--- |
| Room Finder in Outlook doesn't display any conference rooms when a user creates a meeting| Might occur if the user doesn't select a room list. A room list must be selected before available rooms are displayed in the Room Finder.| Create a room list. Run the following command in Exchange Online PowerShell: `New-DistributionGroup <RoomListName> -RoomList -Members $Members`. Then add the required rooms to the room list: `Add-DistributionGroupMember <RoomListName> -Member <RoomMailbox>`|
| Users can reserve a meeting room even though it's already reserved for another meeting| When a user attempts to schedule a meeting in a room that's already reserved for another meeting, the Calendar Attendant doesn't automatically decline the conflicting meeting request. This issue occurs if the `AllRequestOutOfPolicy` property of the room mailbox is set to `True` and causes the room mailbox to ignore conflicting meeting requests.| Using Exchange Online PowerShell, change the `AllRequestOutOfPolicy` property of the room mailbox to `False`. Run the following command: `Set-CalendarProcessing -Identity "Meeting Room" -AllRequestOutOfPolicy $False`|

## Troubleshoot issues purging deleted users

There are multiple considerations related to user mailbox deletion. For example, there are different kinds of mailbox deletions, soft-deleted or hard-deleted. The following table describes these deletion types.

| Deletion type| Description|
| :--- | :--- |
| Soft-deleted user mailboxes| A mailbox that's been deleted but has still been in the Azure Active Directory (Azure AD) recycle bin for fewer than 30 days.|
| Hard-deleted user mailboxes| A mailbox that's been soft deleted for more than 30 days, and all mailbox content is permanently deleted.|

When you delete a user account, the following occurs:

- The corresponding Exchange Online mailbox is also deleted and removed from the list of mailboxes.
- The user account is listed on the Deleted Users page in the Microsoft 365 admin center.
- After 30 days, the user account and mailbox are permanently deleted and not recoverable.

> [!TIP]
> Before 30 days have passed, you can recover the user and associated mailbox.

If you use the `Remove-MsolUser` cmdlet to delete a user and want to immediately remove it from the Azure AD recycle bin, you can use the `RemoveFromRecycleBin` parameter. The user is now unrecoverable, but you should be aware that the corresponding mailbox is not purged; it is soft-deleted. To remove a mailbox and make it unrecoverable (purge), use the `Remove-Mailbox` cmdlet with the `PermanentlyDelete` parameter in Exchange Online PowerShell.

> [!WARNING]
> You can only use the `PermanentlyDelete` parameter if the mailbox is soft-deleted. This command will fail to run against an active mailbox.

Occasionally, the permanent deletion can fail. This problem might arise for several reasons:

- The operation couldn't be performed because 'Soft Deleted Objects\Mailbox1' matches multiple entries

    - Solution: Retrieve a list of mailboxes and then purge the appropriate mailbox based on its GUID.

- The operation couldn't be performed because there is a soft deleted user; please remove the soft deleted user and then try again

    - Solution: Hard delete the user and then purge the mailbox.

- The operation couldn't be performed because it is outside the writing scope of this server

    - Caused because the user account is synced from on-premises using Azure AD Connect. Solution: delete the on-premises user and sync to Azure AD, then purge the mailbox.

- The "Disconnect" parameter can't be used on the "Remove-Mailbox" cmdlet because it isn't present in the role definition for the current user

    - Occurs if you attempt to purge multiple mailboxes in one go. Solution: purge the mailboxes one at a time.

- Mailbox is placed on Litigation Hold or In-Place Hold and cannot be deleted - Litigation Hold

    - Solution: Remove litigation hold and then purge the mailbox

- Mailbox is placed on Litigation Hold or In-Place Hold and cannot be deleted - In-Place Hold

    - Solution: Remove the in-place hold and purge the mailbox.

To review the steps to perform the required solutions, review the material at the Community pages at Microsoft: [How to purge mailboxes in Exchange Online](https://answers.microsoft.com/msoffice/forum/all/how-to-purge-mailboxes-in-exchange-online/3a94a5c5-c173-4259-995a-9de1699bb401)

## Learn more

- [Restore an inactive mailbox](/microsoft-365/compliance/restore-an-inactive-mailbox)
- [Recover an inactive mailbox](/microsoft-365/compliance/recover-an-inactive-mailbox)
- [Create and manage resource mailboxes in Microsoft 365](/exchange/troubleshoot/user-and-shared-mailboxes/create-and-manage-resource-mailboxes)
- [Manage resource mailboxes in Exchange Online](/exchange/recipients-in-exchange-online/manage-resource-mailboxes)

