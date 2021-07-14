Mail users are similar to mail contacts. Both have external email addresses and both contain information about people outside your Exchange or Exchange Online organization that can be displayed in the shared address book and other address lists. However, unlike a mail contact, a mail user has credentials in your Exchange or Microsoft 365 organization and can access resources.

To complete any of the actions or procedures mentioned in this unit, you'll need to ensure the account you're using has the Recipient Management permission.  

In Exchange Online, the Exchange admin center has replaced the Exchange Control Panel (ECP) as the GUI-based administrative tool used to manage cloud-based recipients. The Exchange admin center also replaces the Exchange Management Console in Exchange Server.

## Create a mail user

There are two ways to create a mail user. You can use the Exchange admin center or Exchange Online PowerShell commands.  

Suppose you want to create a new mail-enabled account for Jeffery Brown with the following details:

- Name and the display: **Jeffery Brown**.
   >[!NOTE]
   > If you don't set a *DisplayName*, the value from the *Name* parameter is used instead.
- Email alias: **jefferyb**.
- External email address: **jbrown\@tailspintoys.com**.
- First name: **Jeffery**
- Initials: **JB**
- Last name: **Brown**.
- User name: **jefferyb\@fabrikam.com**.
- Assigned password: **Pa$$w0rd1**.

We'll look at both ways to create the account.  

### Create a mail user using the Exchange admin center  

The Exchange admin center provides a graphical interface for the management of mail-enabled user accounts.  

1. In the Exchange admin center, go to **Recipients > Contacts > New > Mail user**.
2. On the **New mail user** page, enter the alias for the mail user in **Alias**.
3. Specify what type of email address you're going to create. You can use SMTP or specify a custom address type, for example, X.500, GroupWise, or LotusNotes.
4. Enter the mail user's external email address in **External email address**.
5. Specify whether you're enabling mail for an existing user or a new user.  
6. If you selected **New User** in Step 5, use the details about the user to complete the information on the **New mail user** page. Otherwise skip to Step 7.  
7. Select **Save** to create a mail user or to save the changes to an existing user.  

### Create a mail user using the Exchange Online PowerShell interface

You can use the Exchange Online PowerShell cmdlets to create a new email user. With the scenario details, you use this PowerShell cmdlet to create Jeffery's email-enabled account in Exchange Online:

```PowerShell
New-MailUser -Name "Jeffrey Brown" -Alias jeffreyb -ExternalEmailAddress jbrown@tailspintoys.com -FirstName Jeffrey -LastName Brown -UserPrincipalName jeffreyb@fabrikam.com -Password (ConvertTo-SecureString -String 'Pa$$w0rd1' -AsPlainText -Force) 
```

## Changing mail user properties

After you create a mail user, you can make changes and set additional properties by using either the Exchange admin center or Exchange Online PowerShell cmdlets.  

### Modify a mail user in the Exchange admin center

1. In the Exchange admin center, go to **Recipients > Contacts**.
2. Select the user that you want to change, and then select **Edit**.
3. Select one of the following sections to view or change the user's properties:
   - **General**: Use this section to view or change basic information about the mail user. This includes name, display name, user name, whether the mail user can appear in an address list, and any custom attributes.
   - **Contact Information**: Use this section to view or change the user's contact information.
   - **Organization**: Use this section to record detailed information about the user's role. This includes title, department, company name, manager, and to whom the user directly reports.
   - **Email Address**: Use this section to view or change the email addresses associated with the mail user. This includes the mail user's primary SMTP address, their external email address, and any associated proxy addresses.
   - **Mail Flow Settings**: Use this section to view or change Message Size Restrictions and Message Delivery Restrictions.
   - **Members Of**: Use this section to view a list of the distribution groups or security groups to which this user belongs. You can't change membership information on this page.
   - **MailTip**: Use this section to add a MailTip to alert users to potential issues before they send a message to this recipient. A MailTip is text that's displayed in the InfoBar when this recipient is added to the To, Cc, or Bcc lines of a new email message.

### Modify a mail user by using the Exchange Online PowerShell cmdlets

Properties for a mail user are stored in both Active Directory and Exchange. In general, use the **Get-User** and **Set-User** cmdlets to view and change organization and contact information properties. Use the **Get-MailUser** and **Set-MailUser** cmdlets to view or change mail-related properties, such as email addresses, the MailTip, custom attributes, and whether the mail user is hidden from address lists.

Here are some examples of using the cmdlets to change mail user properties.  

This example sets the external email address for Pilar Pinilla:

```PowerShell
Set-MailUser "Pilar Pinilla" -ExternalEmailAddress pilarp@tailspintoys.com 
```

This example hides all mail users from the organization's address book:

```PowerShell
Get-MailUser | Set-MailUser -HiddenFromAddressListsEnabled $true 
```

This example sets the *Company* property for all mail users to Fabrikam:

```PowerShell
Get-User -ResultSize unlimited -Filter "RecipientTypeDetails -eq 'mailuser'" | Set-User -Company Fabrikam 
```

This example sets the *CustomAttribute1* property to "FabrikamEmployee" for all Fabrikam mail users:

```PowerShell
Get-User -ResultSize unlimited -Filter "(RecipientTypeDetails -eq 'mailuser') -and (Company -eq 'Fabrikam')" | Set-MailUser -CustomAttribute1 FabrikamEmployee 
```

## Bulk edit mail user properties

If you need to modify multiple mail users, you can use the EAC to change selected properties for multiple mail users. (You can't modify more than one user at a time by using the PowerShell cmdlets.) When you select two or more mail users from the contacts list in the EAC, the properties that can be bulk edited are displayed in the **Details** pane. When you change one of these properties, the change is applied to all selected recipients.

When you bulk edit mail users, you can change the following property areas:

- **Contact Information**: Change shared properties such as street, postal code, and city name.
- **Organization**: Change shared properties such as department name, company name, and the manager to whom the selected mail contacts or mail users report.
 
1. In the EAC, go to **Recipients > Contacts**.
2. In the list of contacts, select two or more mail users. You can't bulk edit a combination of mail contacts and mail users.
3. In the **Details** pane, under **Bulk Edit**, select **Update** under **Contact Information** or **Organization**.
4. Make the changes on the properties page and then save your changes.

## Learn more

- [Recipients in Exchange Online](/Exchange/recipients-in-exchange-online/recipients-in-exchange-online)
- [Create a new mail user using the EAC](/Exchange/recipients-in-exchange-online/manage-mail-users#use-the-eac-to-create-a-mail-user)
- [Use the EAC to bulk edit mail users](/Exchange/recipients-in-exchange-online/manage-mail-users#use-the-eac-to-bulk-edit-mail-users)
- [Use the EAC to change mail user properties](/Exchange/recipients-in-exchange-online/manage-mail-users#use-the-eac-to-change-user-mailbox-properties)
- [Use Exchange Online PowerShell to change mail user properties](/Exchange/recipients-in-exchange-online/manage-mail-users#use-exchange-online-powershell-to-change-mail-user-properties)
- [Bulk edit mail user](/Exchange/recipients-in-exchange-online/manage-mail-users#bulk-edit-mail-users)
- [PowerShell Reference Library](/powershell/windows/get-started?azure-portal=true)
