When troubleshooting directory synchronization issues, Enterprise Administrators analyze logs for errors and remediate synchronization errors with the tool itself. Typical issues that can lead to synchronization problems include:

 -  Authentication errors, such as using incorrect on-premises or Microsoft 365 credentials.
 -  Inadvertently deactivating directory synchronization in the Microsoft 365 admin center or through Windows PowerShell.
 -  Unexpected changes in Active Directory that affect OU scoping or attribute filtering.
 -  Corrupted Active Directory, requiring directory recovery.
 -  Duplicate attributes that must be unique, such as **UserPrincipalName** and **Proxy Address** for User, Group, or Contact objects.

Microsoft 365 Enterprise Administrators should become familiar with the following tasks and tools to successfully troubleshoot directory synchronization issues:

 -  Deactivate and Reactivate Directory Synchronization
 -  View directory synchronization errors in the Microsoft 365 admin center
 -  Identity synchronization and duplicate attribute resiliency
 -  Unhealthy Identity Synchronization Notification
 -  Directory Synchronization Troubleshooter
 -  Synchronization Service Manager
 -  Troubleshoot password hash synchronization with Azure AD Connect

### Deactivate and reactivate directory synchronization

One key area that can lead to issues unless clearly understood is when directory synchronization is deactivated and then reactivated in the Microsoft 365 admin center. When directory synchronization is deactivated, the source of authority is transferred from the on-premises Active Directory to Microsoft 365. Deactivation is required when on-premises Active Directory is no longer being used to create and manage users, groups, contacts, and mailboxes, such as after a staged Exchange migration to the cloud, where the organization no longer wants to manage objects from on-premises. Problems can occur if directory synchronization is then reactivated, with the source of authority transferred back from Microsoft 365 to the on-premises Active Directory.

For example, assume an organization decided to deploy AD FS and Single Sign-On. To meet this requirement, directory synchronization must be activated and new users created on-premises. These objects were synced to Microsoft 365, and the source of authority is the on-premises Active Directory. Then, later in the year, the organization deactivated directory synchronization, resulting in the transfer of the source of authority to Microsoft 365. From this point on, objects were edited in Microsoft 365. Keep in mind that when directory synchronization is reactivated, any changes made to the Microsoft 365 objects are overwritten.

### View directory synchronization errors in the Microsoft 365 admin center

The Microsoft 365 Admin Center provides an overview of directory synchronization errors. For example, if an organization has 10,000 objects that must be synchronized to Azure AD, there may be errors for some objects, such as attributes that must be unique, like UserPrincipalName and proxy address.

To view any directory synchronization errors in the Microsoft 365 admin center, complete the following steps:

1.  Sign in to the **Office 365 Home** page with an administrative account, such as a global admin account.
2.  In the left-hand navigation pane, select the **Admin** icon to navigate to the **Microsoft 365 admin center**.
3.  On the **Microsoft 365 admin center**, the **Home** tab in the left-hand navigation pane will be displayed by default. On the **Home** page, you'll see the **DirSync Status** tile.
4.  Select the **DirSync Status** to go to the **Directory Sync Status** page.
5.  At the bottom, you can see directory synchronization errors. Choose **We found DirSync object errors** to go to a detailed view of the errors.

The **metaverse search** tab in the Azure AD Connect Synchronization Service Manager can be used to troubleshoot data-related problems. In the top half of the tab, a search query can be created based on a combination of attributes, such as the proxy address conflict in the previous example. The attribute properties of the affected objects will then be displayed.

### Identity synchronization and duplicate attribute resiliency

Duplicate Attribute Resiliency is a feature in Azure AD that eliminates friction caused by UserPrincipalName and ProxyAddress conflicts when running directory synchronization. This feature allows object attributes to be synchronized even if they aren’t unique. Instead of completely failing to provision or update an object with a duplicate attribute, Azure AD quarantines the duplicate attribute. For example, if the UserPrincipalName is already assigned, Azure AD assigns a placeholder value:

**“+\[4DigitNumber\]@.onmicrosoft.com”**

To check if this feature is available and enabled for your tenant, run the following cmdlets in the Azure Active Directory PowerShell module:

```
Get-MsolDirSyncFeatures -Feature DuplicateUPNResiliency
```

```
Get-MsolDirSyncFeatures -Feature DuplicateProxyAddressResiliency
```

> [!WARNING]
> Keep in mind that once duplicate attribute resiliency is enabled, it can't be disabled.

To see a general list of attribute provisioning errors in the tenant, run the following cmdlet in the Azure Active Directory PowerShell module:

```
Get-MsolDirSyncProvisioningError -ErrorCategory PropertyConflict
```

**Additional reading.** For more information, see [Identity synchronization and duplicate attribute resiliency](/azure/active-directory/connect/active-directory-aadconnectsyncservice-duplicate-attribute-resiliency).

### Unhealthy identity synchronization notification

Azure AD Connect informs the Enterprise Administrator by default through email about directory synchronization errors. The subject of this email report is "Directory Synchronization Error Report: Date + Time." It will only be sent to the technical contact email address that's configured in the organization's Microsoft 365 tenant. The technical contact email address can be modified in the Microsoft 365 admin center.

### Directory synchronization troubleshooter

Azure AD Connect includes a [troubleshooting task](/azure/active-directory/hybrid/tshoot-connect-objectsync) that identifies possible issues. It also provides guidance on changes that can be made to fix any synchronization issues.

One of the following options can be chosen when running this task:

 -  **Quick Scan.** This option scans your event logs and Microsoft 365 settings.
 -  **Full Scan.** This option runs the quick scan and also scans your Active Directory objects.

After choosing the type of scan to run, the Microsoft 365 Support Assistant tool must be downloaded to run and evaluate these checks. The tool should be downloaded to a desktop or a member server, depending on the environment. The user must have at least Read permissions in the on-premises Active Directory and Microsoft 365 tenant to run the tool.

### Synchronization Service Manager

To check synchronization issues, the Synchronization Service Manager must be opened in the Azure AD Connect group on the Start menu. Within the application, the **Operations** tab can be viewed to confirm whether the following operations have been completed successfully:

 -  Import on the AD Connector
 -  Import on the Azure AD Connector
 -  Export on the AD Connector
 -  Export on the Azure AD Connector
 -  Full Sync on the AD Connector
 -  Full Sync on the Azure AD Connector

Review the result from these operations to validate the directory synchronization status and to identify any errors.

By default, directory synchronization will run every 30 minutes. If you don't want to wait 30 minutes to troubleshoot an issue, complete the following procedure to force a manual synchronization:

1.  In the **Synchronization Service Manager**, on the **Connectors** page, select **Actions** in menu bar and then select **Run**.
2.  In the **Run Connector** window, in the **Connector** drop-down list, select the source directory. For example, to synchronize changes from the on-premises Active Directory to Azure AD, select the organization's domain name, such as adatum.com.
3.  In the **Run profiles** section, select whether to run a **Full**, **Delta**, or **Export** synchronization.
4.  Select **Run** to start the directory synchronization.

Windows PowerShell can also be used to start a manual directory synchronization on the organization's Azure AD Connect server. The following table displays the necessary cmdlets.

:::row:::
  :::column:::
    

**Cmdlet**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Start-ADSyncSyncCycle -PolicyType Initial


  :::column-end:::
  :::column:::
    

Start a full synchronization


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Start-ADSyncSyncCycle -PolicyType Delta


  :::column-end:::
  :::column:::
    

Start a delta synchronization


  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [Troubleshooting Errors during synchronization](/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-sync-errors).

### Troubleshoot password hash synchronization with Azure AD Connect

Passwords are synchronized in near real time, specifically every two minutes. The directory synchronization scheduler isn't responsible for password hash synchronization. To complete a full sync of all passwords, it must be manually requested through PowerShell.

An organization can get an overview of its password hash synchronization configuration by running a PowerShell script provided by Microsoft.

If you're experiencing issues with one object, ensure the **User must change password at next logon** option isn't selected for the user in Active Directory Users and Computers. This option shouldn't be selected because temporary passwords aren't synchronized to Azure AD. The **In from AD – User AccountEnabled** rule in the Azure AD Connect Synchronization Service Manager can also be checked if there's an inbound rule with PasswordSync set to True. The same must be configured for the **Out to Azure AD – User Join sync** outbound rule.

**Additional reading.** For more information, see [Troubleshooting password hash synchronization with Azure AD Connect sync](/azure/active-directory/connect/active-directory-aadconnectsync-troubleshoot-password-hash-synchronization).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”