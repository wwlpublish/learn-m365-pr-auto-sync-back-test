Commonly, during mergers or divestitures, an organization must move its users' Exchange Online mailboxes into a new tenant. This migration process is known as a cross-tenant migration. Cross-tenant mailbox migration allows tenant administrators to use well-known interfaces like Remote PowerShell and Microsoft Exchange Mailbox Replication Service (MRS) to transition users to their new organization.

Cross-tenant mailbox moves are done using Windows PowerShell. The feature doesn’t have a UI through the Exchange admin center (EAC) portal. Administrators can use the New-MigrationBatch cmdlet, available through the Move Mailboxes management role, to execute cross-tenant moves.

Cross-tenant Exchange mailbox migrations are started from the target tenant as migration batches. This process is similar to how on-boarding migration batches work when migrating from Exchange on-premises to Microsoft 365.

Migrated users must be present in the target tenant's Exchange Online system as MailUsers, marked with specific attributes to enable the cross-tenant moves. The system will fail moves for users who aren't properly set up in the target tenant.

When the moves are complete:

 -  The source user mailbox is converted to a MailUser.
 -  The targetAddress (shown as ExternalEmailAddress in Exchange) is stamped with the routing address to the destination tenant.

This process leaves the legacy MailUser in the source tenant and provides a period of coexistence and mail routing. When business processes allow, the source tenant may remove the source MailUser or convert them to a mail contact.

Cross-tenant Exchange mailbox migrations are supported for tenants in hybrid or cloud only, or any combination of the two.

> [!WARNING]
> Microsoft has recently updated its setup steps to enable cross-tenant mailbox migration to no longer require Azure Key Vault (AKV)! Organizations that have started configuring their tenants using the previous AKV method are recommended to stop or remove that configuration and begin using this new method. If you have mailbox migrations in progress with the previous AKV method, then wait until your existing migrations are complete and follow the steps described in this unit to enable the new simplified method. Azure Key Vault required setup steps are archived but can be found [here](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview), for reference.

### Cross-tenant mailbox migration requirements

Before starting, be sure you have the necessary permissions to configure the Move Mailbox application in Azure, EXO Migration Endpoint, and the EXO Organization Relationship.

Additionally, at least one mail-enabled security group in the source tenant is required. These groups are used to scope the list of mailboxes that can move from source (or sometimes referred to as resource) tenant to the target tenant. This design enables the source tenant admin to restrict or scope the specific set of mailboxes that must be moved, preventing unintended users from being migrated. Nested groups aren't supported.

You must also communicate with your trusted partner company, which is the company to which you'll be moving mailboxes. You must obtain their Microsoft 365 tenant ID, which is used in the Organization Relationship DomainName field.

Complete the following steps to obtain the tenant ID of a subscription:

1.  Sign in to the Microsoft 365 admin center.
2.  Navigate to [https://aad.portal.azure.com/\#blade/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties?azure-portal=true).
3.  Select the copy icon for the Tenant ID property to copy it to the clipboard.

> [!WARNING]
> You must configure the target (destination) first. To complete these steps, you aren't required to have or know the tenant admin credentials for both source and target tenant. Steps can be performed individually for each tenant by different administrators.

### Prepare the target (destination) tenant by creating the migration application and secret

Complete the following high-level steps to prepare the target (destination) tenant for a cross-tenant migration:<br>

1.  Log into your Azure AD portal with your target tenant admin credentials.
2.  Under Azure's services, select **Azure Active Directory**.
3.  On the left navigation bar, select **Enterprise Applications**.
4.  Select **New application**.
5.  Select **Create your own application**.
6.  Enter a name for your application, select the **Register an application** to integrate with Azure AD, and then select **Create**.
7.  On the **Register an application** page, under **Supported account types**, select the option titled **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**. Then under **Redirect URI (optional),** select **Web** and enter **https://office.com**. Then select **Register**.
8.  On the top-right corner of the page, you'll see a notification pop-up window that states the app was successfully created.
9.  Go back to **Home &gt; Azure Active Directory** and select **App registrations**.
10. Under **Owned applications**, find the app you created and select it.
11. Under Essentials, you must copy down the **Application (client) ID** as you'll need it later to create a URL for the target tenant.
12. On the left navigation bar, select **API permissions** to view the permissions assigned to your app.
13. By default, **User.Read** permissions are assigned to the app you created in the previous steps. Because this permission isn't required for mailbox migrations, you can remove that permission.
14. To add permission for mailbox migration, select **Add a permission**.
15. In the **Request API permissions** windows, select **APIs my organization uses**, search for **Office 365 Exchange Online**, and then select it.
16. Select **Application permissions**.
17. Under **Select permissions**, expand **Mailbox**, check **Mailbox.Migration**, and select **Add permissions** at the bottom on the screen.
18. Select **Certificates &amp; secrets** on the left navigation bar for your application.
19. Under **Client secrets**, select **new client secre**t.
20. In the **Add a client secret** window, enter a description, and configure your planned expiration settings.

> [!IMPORTANT]
> This password will be used when creating your migration endpoint. It's important that you copy this password to your clipboard or copy this password to a secure/secret password safe location. This moment is the only time you can see this password! If you do somehow lose it or need to reset it, you can sign back into our Azure portal, go to **App registrations**, find your migration app, select **Secrets &amp; certificates**, and create a new secret for your app.

21. Now that you've successfully created the migration application and secret, you'll need to consent to the application. To consent to the application, go back to the **Azure Active Directory** landing page, select **Enterprise applications** in the left navigation, find the migration app you created, select it, and select **Permissions** on the left navigation.
22. Select the **Grant admin consent for \[your tenant\]** button.
23. A new browser window will open. Select **Accept**.
24. You can go back to your portal window and select **Refresh** to confirm your acceptance.

```powershell
https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com

```

To complete the URL in the final step, you'll need the following information:

 -  The application ID of the mailbox migration app you created.
 -  Replace sourcetenant.onmicrosoft.com in the example with your source tenant's correct onmicrosoft.com name.
 -  Replace \[application\_id\_of\_the\_app\_you\_just\_created\] with the application ID of the mailbox migration app you created.

### Prepare the target tenant by creating the Exchange Online migration endpoint and organization relationship

To prepare the target tenant by creating the Exchange Online migration endpoint and organization relationship, you'll need:

 -  The application ID of the mailbox migration app you created.
 -  The password (the secret) you configured during this process.
 -  Depending on the Microsoft 365 Cloud Instance you use, your endpoint may be different.

> [!NOTE]
> Refer to the [Microsoft 365 endpoints](/microsoft-365/enterprise/microsoft-365-endpoints?azure-portal=true) page and select the correct instance for your tenant. Then review the Exchange Online Optimize Required address and replace as appropriate in the following steps.<br>

Complete the following steps to prepare the target tenant by creating the Exchange Online migration endpoint and organization relationship:

1.  Create a Remote PowerShell connection to the target Exchange Online tenant.
2.  Create a new migration endpoint for cross-tenant mailbox moves.

```powershell
$AppId = "[guid copied from the migrations app]"

$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this password is the secret password you saved in the previous steps]" -AsPlainText -Force)

New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
```

3.  Create a new relationship or edit your existing organization relationship object to your source tenant.

```powershell
$sourceTenantId="[tenant id of your trusted partner, where the source mailboxes are]"
$orgrels=Get-OrganizationRelationship
$existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId}
If ($null -ne $existingOrgRel)
{
    Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound
}
If ($null -eq $existingOrgRel)
{
    New-OrganizationRelationship "[name of the new organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound -DomainNames $sourceTenantId$orgrels=Get-OrganizationRelationship
$existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId
}
```

### Prepare the source tenant by accepting the migration application and configuring the organization relationship

Complete the following high-level steps to prepare the source (current mailbox location) tenant by accepting the migration application and configuring the organization relationship:

1.  From a browser, go to the URL link provided by your trusted partner to consent to the mailbox migration application. The URL will look like this:
    
    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```
    
    To configure the URL, you'll need:
    
     -  The application ID of the mailbox migration app you created.
     -  To replace sourcetenant.onmicrosoft.com in the example with your source tenants correct onmicrosoft.com name.
     -  To replace \[application\_id\_of\_the\_app\_you\_just\_created\] with the application ID of the mailbox migration app you created.
2.  Accept the application when the pop-up window appears. You can also log into your Azure Active Directory portal and find the application under Enterprise applications.<br>
3.  Create new or edit your existing organization relationship object to your target (destination) tenant from an Exchange Online Remote PowerShell window.

```powershell
$targetTenantId="[tenant id of your trusted partner, where the mailboxes are being moved to]"
$appId="[application id of the mailbox migration app you consented to]"
$scope="[name of the mail enabled security group that contains the list of users who are allowed to migrate]"
$orgrels=Get-OrganizationRelationship
$existingOrgRel = $orgrels | ?{$_.DomainNames -like $targetTenantId}
If ($null -ne $existingOrgRel)
{
    Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
}
If ($null -eq $existingOrgRel)
{
    New-OrganizationRelationship "[name of your organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -DomainNames $targetTenantId -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
}
```

> [!NOTE]
> The tenant ID that you enter as the $sourceTenantId and $targetTenantId is the GUID and not the tenant domain name. For an example of a tenant ID and information about finding your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id?azure-portal=true).

### Verify whether the cross-tenant migration worked

You can verify cross-tenant mailbox migration configuration by running the **Test-MigrationServerAvailability** cmdlet against the cross-tenant migration endpoint that you created on your target tenant. For example:

```powershell
Test-MigrationServerAvailability -Endpoint "[the name of your cross-tenant migration endpoint]" -TestMailbox "[email address of a source mailbox that is part of your migration scope]"
```
