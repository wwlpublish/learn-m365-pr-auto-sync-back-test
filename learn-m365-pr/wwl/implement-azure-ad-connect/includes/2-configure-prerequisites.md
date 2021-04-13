Enterprise administrators should consider the following requirements and prerequisites for Azure AD Connect before they install and configure it in their environments:

 *  Microsoft 365 Tenant requirements
 *  Domain and forest requirements
 *  Operating system and supporting software requirements
 *  Permissions and accounts
 *  Database requirements

These considerations are examined in the following sections.

### Microsoft 365 tenant requirements

Before deploying Azure AD Connect in your environment, there are a few requirements for Azure AD that you must consider:

 *  **Azure AD subscription or Microsoft 365 tenant.** If you're using Microsoft 365, you don't need an Azure subscription to use Azure AD Connect because the Azure AD tenant is provisioned with Microsoft 365.
 *  **Add and verify your domains you plan to use in Azure AD.** Before you run Azure AD Connect, make sure you add the domain that you want to use as the UPN to your Microsoft 365 tenant. For example, if you plan to use Adatum.com as your UPN, you need to ensure the domain name has been verified in your Microsoft 365 tenant.
 *  **An Azure AD directory will by default allow 50,000 objects.** If you don’t have a verified domain, your default directory service quota is 50,000 objects. If you have at least one verified domain, this limit increases automatically to 300,000 objects. If you have more than 300,000 objects, you must open a support case with Microsoft.

### Domain and forest requirements

Azure AD Connect requires that the AD schema version and forest functional level must be Windows Server 2008 or newer. Azure AD Connect supports a single Active Directory forest with express settings, and it supports multiple Active Directory forest scenarios and multiple Exchange organizations with customized settings.

To integrate your on-premises Active Directory with Azure AD Connect, domain controllers must run one of the following operating systems:

 *  Windows Server 2008 or later.
 *  If you plan to use the password writeback feature, all domain controllers must be on Windows Server 2008 or later.

### Operating system and supporting software requirements

When you install Azure AD Connect with express settings, the directory synchronization computer must be a member of a domain. For single forest scenarios, this computer must be joined to a domain within the same forest that will be synchronized.

You can configure customized settings to install Azure AD Connect on a computer that isn't joined to a domain. Azure AD Connect also supports installation on domain controllers. In most cases it's recommended that you use a member server for Azure AD Connect.

Azure AD Connect requires the following Windows Server versions (64-bit edition only):

 *  Windows Server 2008 or 2008 R2
 *  Windows Server 2012, 2012 R2
 *  Windows Server 2016
 *  If you plan to use the password hash synchronization or password writeback feature, the server must be on Windows Server 2008 R2 or later.

### Permissions and accounts

The account used to install and configure Azure AD Connect must have the following permissions:

 *  A Global Administrator account that is member of the Global Admin role in your Microsoft 365 tenant.
 *  An Enterprise Administrator account for your on-premises Active Directory. This account is required to create the directory synchronization service account in Active Directory.
 *  Local administrator permission on the Azure AD Connect computer. This permission is required to install the Azure AD Connect tool.

If you create a dedicated service account in Microsoft 365 for directory synchronization in place of the default sync account, you must disable the default 90-day password expiration. If the default 90-day password expiration isn't disabled, the synchronization service will stop working when the password expires for the account. In this scenario, you must reconfigure Azure AD Connect to update the password. To disable password expiration for the service account in Microsoft 365 by using the Azure Active Directory Module for Windows PowerShell, type the following command, and then press Enter:

```
Set-MsolUser -UserPrincipalName <service account>@<domain>.onmicrosoft.com -PasswordNeverExpires $true
```

The Enterprise Administrator account is only required when installing and configuring Azure AD Connect, and the Enterprise Administrator credential is not stored or saved by the configuration wizard. The Enterprise Administrator account is required to:

 *  Create the MSOL\_ domain service account in the CN=Users container of the root domain.
 *  Delegate the following permissions to MSOL\_ on each domain partition in the forest:
    
     *  Replicating Directory Changes
     *  Replicating Directory Changes all
     *  Replication Synchronization

During an Azure AD Connect configuration, you can enable the Exchange hybrid deployment feature. Previously known as rich coexistence, this feature allows for the coexistence of Exchange mailboxes both on-premises and in Azure by synchronizing a specific set of attributes from Azure AD back into your on-premises Active Directory. During deployment, the Enterprise Administrator account will automatically create an **MSOL\_Active Directory\_Sync\_RichCoexistence** group in the **CN=Users** container of the root domain. The Enterprise Admin must also delegate write permissions for the Active Directory attributes that write back from Azure AD to your on-premises Active Directory.

The following accounts are created in your on-premises Active Directory during Azure AD Connect configuration:

 *  **MSOL\_\[id\].** This account is created during installation of Azure AD Connect, and it’s configured to synchronize objects to Azure AD. The account has directory replication permissions in your on-premises Active Directory and write permission on certain attributes to enable the Exchange Hybrid Deployment.
 *  **AAD\_\[id\].** This account is the service account for the synchronization engine, and it’s created with a randomly generated complex password automatically configured to never expire. When the directory synchronization service runs, it uses the service account credentials to read from your on-premises Active Directory and then to write the contents of the synchronization database to Azure AD by using the Microsoft 365 global administrator credentials specified during configuration of Azure AD Connect.

>[!WARNING]
>Don't change the service account after installing Azure AD Connect. If you do, directory synchronization will try to use the service account created during synchronization. If the account is changed, directory synchronization will stop running and scheduled directory synchronizations will no longer occur.

### Database requirements

Azure AD Connect requires a SQL Server database to store identity data. By default, a SQL Server 2012 Express LocalDB (a light version of SQL Server Express) is installed and the service account for the service is created on the local machine. SQL Server Express has a 10-GB database limit, which allows you to manage approximately 100,000 objects. You may need to manage a higher volume of objects in large deployments. In this scenario, you should configure Azure AD Connect to a full version of SQL Server. Azure AD Connect supports all SQL Server 2008 or later versions.

When deploying to a different version of SQL Server, SQL Server rights are required to create the database used by Azure AD Connect. They're also required to enable the SQL service account with the role of db\_owner. To configure these SQL Server rights, the account used to install Azure AD Connect must have sysadmin permission to the SQL database, and the service account used to run Azure AD Connect must have public permission to the database used by Azure AD Connect.

The following graphic shows that Azure AD Connect requires a SQL Server database to store identity data, and that it uses different accounts for the different tasks completed by the Azure AD Connect server.

:::image type="content" source="../media/accounts-used-by-aad-connect-server-02bc6933.jpg" alt-text="graphics shows how different accounts are used for the different tasks of an Azure AD Connect server":::
