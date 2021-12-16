In a cross-tenant migration scenario, users objects that are migrated must be present in the target tenant and Exchange Online system (as MailUsers). They must also be marked with specific attributes to enable the cross-tenant moves. The system will fail moves for users that aren't properly configured in the target tenant.

For any mailbox moving from a source organization, you must configure a mail user object in the target organization. Each mail user object must have the following attributes:<br>

 -  **ExchangeGUID (direct flow from source to target)**. The mailbox GUID must match. The move process won't continue if this attribute isn't present on the target object.
 -  **ArchiveGUID (direct flow from source to target)**. The archive GUID must match. The move process won't continue if this attribute isn't present on the target object. This attribute is only required if the source mailbox is Archive enabled.
 -  **LegacyExchangeDN (flow as proxyAddress, "x500:&lt;LegacyExchangeDN&gt;")**. The LegacyExchangeDN must be present on target MailUser as x500: proxyAddress. You also must copy all x500 addresses from the source mailbox to the target mail user. The move processes won't continue if these addresses aren't present on the target object.
 -  **UserPrincipalName**. UPN will align to the user's NEW identity or target company (for example, user@northwindtraders.onmicrosoft.com).
 -  **Primary SMTPAddress**. Primary SMTP address will align to the user's NEW company (for example, user@northwind.com).
 -  **TargetAddress/ExternalEmailAddress**. MailUser will reference the user's current mailbox hosted in source tenant (for example user@contoso.onmicrosoft.com). When assigning this value, verify that you're also assigning the PrimarySMTPAddress or this value will set the PrimarySMTPAddress, which will cause move failures.

You can't add legacy smtp proxy addresses from the source mailbox to the target MailUser. For example, you can't maintain contoso.com on the mail end user in fabrikam.onmicrosoft.com tenant objects. Domains are associated with one Azure AD or Exchange Online tenant only.

Users in the target organization must be licensed with appropriate Exchange Online subscriptions applicable for the organization. You may apply a license in advance of a mailbox move, but ONLY once the target MailUser is properly set up with ExchangeGUID and proxy addresses. Applying a license before the ExchangeGUID is applied will result in a new mailbox provisioned in target organization.

> [!NOTE]
> When you apply a license on a Mailbox or MailUser object, all SMTP type proxyAddresses are scrubbed to ensure only verified domains are included in the Exchange EmailAddresses array.

### Example of a target MailUser object

The following table displays an example target MailUser object.

:::row:::
  :::column:::
    **Attribute**
  :::column-end:::
  :::column:::
    **Value**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Alias
  :::column-end:::
  :::column:::
    LaraN
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    RecipientType
  :::column-end:::
  :::column:::
    MailUser
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    RecipientTypeDetails
  :::column-end:::
  :::column:::
    MailUser
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    UserPrincipalName
  :::column-end:::
  :::column:::
    LaraN@northwintraders.onmicrosoft.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PrimarySmtpAddress
  :::column-end:::
  :::column:::
    Lara.Newton@northwind.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    ExternalEmailAddress
  :::column-end:::
  :::column:::
    SMTP:LaraN@contoso.onmicrosoft.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    ExchangeGuid
  :::column-end:::
  :::column:::
    1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    LegacyExchangeDN
  :::column-end:::
  :::column:::
    /o=First Organization/ou=Exchange Administrative Group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    EmailAddresses
  :::column-end:::
  :::column:::
    x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    7273f1f9-Lara
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    smtp:LaraN@northwindtraders.onmicrosoft.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    SMTP:Lara.Newton@northwind.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
:::row-end:::


### Example of a source MailUser object

The following table displays an example source MailUser object.

:::row:::
  :::column:::
    **Attribute**
  :::column-end:::
  :::column:::
    **Value**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Alias
  :::column-end:::
  :::column:::
    LaraN
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    RecipientType
  :::column-end:::
  :::column:::
    UserMailbox
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    RecipientTypeDetails
  :::column-end:::
  :::column:::
    UserMailbox
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    UserPrincipalName
  :::column-end:::
  :::column:::
    LaraN@contoso.onmicrosoft.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PrimarySmtpAddress
  :::column-end:::
  :::column:::
    Lara.Newton@contoso.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    ExchangeGuid
  :::column-end:::
  :::column:::
    1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    LegacyExchangeDN
  :::column-end:::
  :::column:::
    /o=First Organization/ou=Exchange Administrative Group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    EmailAddresses
  :::column-end:::
  :::column:::
    smtp:LaraN@contoso.onmicrosoft.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    SMTP:Lara.Newton@contoso.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::


The following attributes may be included in Exchange hybrid write-back already. If not, they should be included.

 -  **msExchBlockedSendersHash**. Writes back online safe and blocked sender data from clients to on-premises Active Directory.<br>
 -  **msExchSafeRecipientsHash**. Writes back online safe and blocked sender data from clients to on-premises Active Directory.
 -  **msExchSafeSendersHash**. Writes back online safe and blocked sender data from clients to on-premises Active Directory.<br>

### Target quota size

If the source mailbox is on LitigationHold and the source mailbox Recoverable Items size is greater than the database default (30 GB), moves won't continue. The reason the moves will fail is that the target quota is less than the source mailbox size.

You can update the target MailUser object to transition the ELC mailbox flags from the source environment to the target. This action triggers the target system to expand the quota of the MailUser to 100 GB. This expansion allows the move to the target.

**Additional reading**. For a sample script that completes this update, see [Cross-tenant mailbox migration (preview)](/microsoft-365/enterprise/cross-tenant-mailbox-migration?azure-portal=true).

Non-hybrid target tenants can modify the quota on the Recoverable Items folder for the MailUsers before migration by running the following command to enable Litigation Hold on the MailUser object and increasing the quota to 100 GB (this command won't work for hybrid tenants):

```powershell
Set-MailUser -EnableLitigationHoldForMigration
```

### ExchangeGUID conflicts

You must ensure the target MailUser has no previous ExchangeGuid that doesn't match the Source ExchangeGuid. This situation can occur if the target mail end user was previously licensed for Exchange Online and provisioned a mailbox. If the target MailUser was previously licensed for or had an ExchangeGuid that doesn't match the Source ExchangeGuid, you must complete a cleanup of the cloud mail end user.

For these cloud mail end users, you can run the following command:

```powershell
Set-User <identity> -PermanentlyClearPreviousMailboxInfo
```

> [!CAUTION]
> This process is irreversible. If the object has a softDeleted mailbox, it can't be restored after this point. Once cleared, however, you can synchronize the correct ExchangeGuid to the target object and MRS will connect the source mailbox to the newly created target mailbox.

You can find objects that were previously mailboxes by using this command:

```powershell
Get-User <identity> | select Name, *recipient* | Format-Table -AutoSize
```

Here's an example.

```powershell
Get-User John@northwindtraders.com |select name, *recipient*| Format-Table -AutoSize

Name      PreviousRecipientTypeDetails    RecipientType RecipientTypeDetails
----      ---------------------------- ------------- --------------------
John      UserMailbox                  MailUser      MailUser
```

Clear the soft-deleted mailbox using this command.

```powershell
Set-User <identity> -PermanentlyClearPreviousMailboxInfo
```

Here's an example.

```powershell
Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo -Confirm

Are you sure you want to perform this action?
Delete all existing information about user "John@northwindtraders.com". This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.

Do you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.