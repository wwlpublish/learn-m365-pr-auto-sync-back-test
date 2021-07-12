Enterprise administrators should consider the following requirements and prerequisites for Azure AD Connect before they install and configure it in their environments:

 -  Microsoft 365 Tenant requirements
 -  Domain and forest requirements
 -  Operating system and supporting software requirements
 -  Permissions and accounts
 -  Database requirements

These considerations are examined in the following sections.

### Microsoft 365 tenant requirements

Before an organization deploys Azure AD Connect, it should consider the following Azure AD requirements:

 -  **Azure AD subscription or Microsoft 365 tenant.** If an organization is using Microsoft 365, it doesn't need an Azure subscription to use Azure AD Connect because the Azure AD tenant is provisioned with Microsoft 365.
 -  **Add and verify the domains it plans to use in Azure AD.** Before running Azure AD Connect, the organization should add the domain that it wants to use as the UPN to its Microsoft 365 tenant. For example, if you plan to use adatum.com as your UPN, you must ensure the domain name has been verified in your Microsoft 365 tenant.
 -  **By default, an Azure AD directory allows 50,000 objects.** If an organization doesn’t have a verified domain, its default directory service quota is 50,000 objects. If an organization has at least one verified domain, this limit increases automatically to 300,000 objects. If an organization has more than 300,000 objects, it must open a support case with Microsoft.

### Domain and forest requirements

Azure AD Connect requires that the AD schema version and forest functional level must be Windows Server 2008 or newer. Azure AD Connect supports a single Active Directory forest with express settings, and it supports multiple Active Directory forest scenarios and multiple Exchange organizations with customized settings.

To integrate on-premises Active Directory with Azure AD Connect, domain controllers must run one of the following operating systems:

 -  Windows Server 2008 or later.
 -  If an organization plans to use the password writeback feature, all domain controllers must be on Windows Server 2008 or later.

### Operating system and supporting software requirements

When Azure AD Connect is installed with express settings, the directory synchronization computer must be a member of a domain. For single forest scenarios, this computer must be joined to a domain within the same forest that will be synchronized.

Customized settings can be configured to install Azure AD Connect on a computer that isn't joined to a domain. Azure AD Connect also supports installation on domain controllers. In most cases, it's recommended that a member server should be used for Azure AD Connect.

Azure AD Connect requires the following Windows Server versions (64-bit edition only):

 -  Windows Server 2008 or 2008 R2
 -  Windows Server 2012, 2012 R2
 -  Windows Server 2016
 -  When using password hash synchronization or password writeback, the server must be on Windows Server 2008 R2 or later.

### Permissions and accounts

The account used to install and configure Azure AD Connect must have the following permissions:

 -  A Global Administrator account that's a member of the Global Admin role in the Microsoft 365 tenant.
 -  An Enterprise Administrator account for the on-premises Active Directory. This account is required to create the directory synchronization service account in Active Directory.
 -  Local administrator permission on the Azure AD Connect computer. This permission is required to install the Azure AD Connect tool.

If a dedicated service account is created in Microsoft 365 for directory synchronization in place of the default sync account, the default 90-day password expiration must be disabled. If the default 90-day password expiration isn't disabled, the synchronization service will stop working when the password expires for the account. In this scenario, Azure AD Connect must be reconfigured to update the password. To disable password expiration for the service account in Microsoft 365 by using the Azure Active Directory Module for Windows PowerShell, type the following command, and then press Enter:

```
Set-MsolUser -UserPrincipalName &lt;service account&gt;@&lt;domain&gt;.onmicrosoft.com -PasswordNeverExpires $true
```

The Enterprise Administrator account is only required when installing and configuring Azure AD Connect, and the Enterprise Administrator credential isn't stored or saved by the configuration wizard. The Enterprise Administrator account is required to:

 -  Create the MSOL\_ domain service account in the CN=Users container of the root domain.
 -  Delegate the following permissions to MSOL\_ on each domain partition in the forest:
    
     -  Replicating Directory Changes
     -  Replicating Directory Changes all
     -  Replication Synchronization

During an Azure AD Connect configuration, the Exchange hybrid deployment feature can be enabled. Previously known as rich coexistence, this feature allows for the coexistence of Exchange mailboxes both on-premises and in Azure. It does so by synchronizing a specific set of attributes from Azure AD back into the on-premises Active Directory. During deployment, the Enterprise Administrator account will automatically create an **MSOL\_Active Directory\_Sync\_RichCoexistence** group in the **CN=Users** container of the root domain. The Enterprise Admin must also delegate write permissions for the Active Directory attributes that write back from Azure AD to the on-premises Active Directory.

The following accounts are created in the on-premises Active Directory during Azure AD Connect configuration:

 -  **MSOL\_\[id\].** This account is created during installation of Azure AD Connect. It’s configured to synchronize objects to Azure AD. The account has directory replication permissions in the on-premises Active Directory and write permission on certain attributes to enable the Exchange Hybrid Deployment.
 -  **AAD\_\[id\].** This account is the service account for the synchronization engine. It’s created with a randomly generated complex password automatically configured to never expire. When the directory synchronization service runs, it uses the service account credentials to read from the on-premises Active Directory. It then writes the contents of the synchronization database to Azure AD by using the Microsoft 365 global administrator credentials specified during configuration of Azure AD Connect.

> [!WARNING]
> Don't change the service account after installing Azure AD Connect. If you do, directory synchronization will try to use the service account created during synchronization. If the account is changed, directory synchronization will stop running and scheduled directory synchronizations will no longer occur.

### Database requirements

Azure AD Connect requires a SQL Server database to store identity data. By default, a SQL Server 2012 Express LocalDB (a light version of SQL Server Express) is installed and the service account for the service is created on the local machine. SQL Server Express has a 10-GB database limit, which allows an organization to manage approximately 100,000 objects. A higher volume of objects may need to be managed in large deployments. In this scenario, Azure AD Connect should be configured to a full version of SQL Server. Azure AD Connect supports all SQL Server 2008 or later versions.

When deploying to a different version of SQL Server, SQL Server rights are required to create the database used by Azure AD Connect. They're also required to enable the SQL service account with the role of db\_owner. To configure these SQL Server rights, the account used to install Azure AD Connect must have sysadmin permission to the SQL database. The service account used to run Azure AD Connect must also have public permission to the database used by Azure AD Connect.

The following graphic shows that Azure AD Connect requires a SQL Server database to store identity data, and that it uses different accounts for the different tasks completed by the Azure AD Connect server.

:::image type="content" source="../media/accounts-used-by-aad-connect-server-02bc6933.jpg" alt-text="graphic shows how different accounts are used for the different tasks of an Azure AD Connect server":::
