Installing Azure AD Connect is accomplished by running an installation wizard. Because Microsoft is continuously improving Azure AD Connect, it's important to [download the latest version](https://aka.ms/edx-cld243x-aad?azure-portal=true) when you're ready to install it.

During installation of Azure AD Connect, you can choose to install it using either Express Setup or Custom Setup. Each setup procedure is examined in detail in the following sections.

### Azure AD Connect express setup

Express Settings is the default setup option when installing Azure AD Connect because it supports the most common installation scenario. When running express setup, Azure AD Connect deploys synchronization with the password hash synchronization option. This synchronization option is for a single forest only. It enables users to sign in to Microsoft 365 using their on-premises password.

During installation of Azure AD Connect with Express Settings, the installer will:<br>

 *  install the synchronization engine.
 *  configure Azure AD Connect.
 *  configure the on-premises Active Directory connector.
 *  enable password hash synchronization.
 *  configure synchronization services.
 *  configure sync services for Exchange hybrid deployment (optional).
 *  enable automatic upgrade of Azure AD Connect.

When installing Azure AD Connect using the Express Settings option, you can optionally choose to start the synchronization process once the installation is complete.

The following graphic shows the three primary operations that are completed in any Azure AD Connect server installation: Configuring Active Directory, Azure AD, and the local machine for identity synchronization.

:::image type="content" source="../media/installing-aad-connect-operations-930b112c.jpg":::


### Azure AD Connect custom setup

When installing Azure AD Connect, the Customized Settings option is designed for organizations with advanced configurations. This option enables organizations to customize their setup when they require optional features that aren't covered in the Express Setup. The Customized Settings option is typically used when organizations have:

 *  multiple forests.
 *  customized their sign-in option, such as AD FS for federation.
 *  a non-Microsoft identity provider.
 *  customized synchronization features, such as filtering and writeback.

Besides the required components that are installed as part of Express Settings, you can select the following optional components during installation:

 *  **Specify a custom installation location.** Enables you to specify a different installation path to install Azure AD Connect.
 *  **Use an existing server running SQL Server.** Enables you to select an existing SQL database server.
 *  **Use an existing service account.** Enables you to specify an existing service account. By default, Azure AD Connect creates a local service account for the synchronization services to use. The password is generated automatically and remains unknown to the person installing Azure AD Connect. If you specify a remote server running SQL Server, then you'll need a service account for which you know the password.
 *  **Specify custom sync groups.** Enables you to specify existing management groups for Azure AD Connect. By default, Azure AD Connect will create the following groups on the server when the synchronization services install: Administrators group, Operators group, Browse group, and Password Reset group. Use this option if you prefer to specify your own groups. The groups must be local on the server and can't be in the domain.

During a customized Azure AD Connect setup, the installer allows you to enable the following features:

:::row:::
  :::column:::
    <p><b>Feature</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
  :::column:::
    <p><b>When to use it?</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Select the Single Sign-On (SSO) method</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to specify the SSO method for users. The SSO methods include password hash synchronization, pass-through authentication, federation with AD FS, and Don't configure SSO. You can also select the option to enable single sign-on.</p>
  :::column-end:::
  :::column:::
    <p>You want to enable your users for SSO.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Connect multiple on-premises directories or forests</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to connect to one or more Active Directory domains or forests.</p>
  :::column-end:::
  :::column:::
    <p>You have multiple forests to connect to one Azure AD tenant.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Matching across forests</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to define how Azure AD represents users from your Active Directory forests. A user might either be represented only once across all forests or have a combination of enabled and disabled accounts.</p>
  :::column-end:::
  :::column:::
    <p>You have multiple forests to connect to one Azure AD tenant.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Sync filtering based on organizational units</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to run a small pilot where only a small subset of objects should be created in Azure AD and Microsoft 365. To use this feature, create an organizational unit in your Active Directory and add the users and groups that should synchronize from the OU to Azure AD. You can later add and remove users to this group to maintain the list of objects that should be present in Azure AD.</p>
  :::column-end:::
  :::column:::
    <p>You only want to sync specific OUs or items to Azure AD.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Select the source anchor</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to choose the primary key (that is, the ImmutableID) that will link the on-premises user with the user in Azure AD.</p>
  :::column-end:::
  :::column:::
    <p>You must change the source anchor, such as when you have multi-forests.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Select the login attribute</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to choose the attribute users will use when they log in to Azure AD and Microsoft 365. Typically, this attribute should be the userPrincipalName attribute. But if this attribute is non-routable and can't be verified, then it's possible to select another attribute, for example email, as the attribute holding the login ID, known as Alternate ID.</p>
  :::column-end:::
  :::column:::
    <p>You want to use UPNs for user login.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Exchange hybrid deployment</p>
  :::column-end:::
  :::column:::
    <p>This optional feature enables coexistence of Exchange mailboxes both on-premises and in Microsoft 365 by synchronizing a specific set of attributes from Azure AD back to your on-premises Active Directory.</p>
  :::column-end:::
  :::column:::
    <p>You currently have Exchange on-premises installed and you plan to move mailboxes to Exchange Online.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Exchange mail public folders</p>
  :::column-end:::
  :::column:::
    <p>This feature allows you to synchronize mail-enabled public folders from your on-premises Active Directory to Azure AD to support EOP’s directory-based edge blocking (DBEB).</p>
  :::column-end:::
  :::column:::
    <p>You currently use mail-enabled Public Folders on-premises.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Azure AD app and attribute filtering</p>
  :::column-end:::
  :::column:::
    <p>This optional feature enables you to tailor the set of synchronized attributes to a specific set, based on Azure AD apps.</p>
  :::column-end:::
  :::column:::
    <p>You're using Azure AD apps.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Password hash synchronization</p>
  :::column-end:::
  :::column:::
    <p>This feature allows synchronization of passwords from your Active Directory to Azure AD. Also, you can then use password hash synchronization as a backup option if you configured AD FS.</p>
  :::column-end:::
  :::column:::
    <p>You plan to support password hash synchronization.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Password writeback</p>
  :::column-end:::
  :::column:::
    <p>This feature enables password changes that originate in Azure AD are written back to your on-premises Active Directory. You typically deploy this feature when you want to enable users for self-service password reset of their Azure AD passwords.</p>
  :::column-end:::
  :::column:::
    <p>You want to allow users to change their password in the Microsoft 365 portal or other areas.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Group writeback</p>
  :::column-end:::
  :::column:::
    <p>With this feature, if you use the Microsoft 365 Groups feature, then you can have these groups in your on-premises Active Directory as a distribution group. This option is only available if you have deployed Exchange Server on-premises.</p>
  :::column-end:::
  :::column:::
    <p>You're using an Exchange hybrid deployment and Microsoft 365 groups.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Device writeback</p>
  :::column-end:::
  :::column:::
    <p>With this feature, device objects in Azure AD are written back to your on-premises Active Directory for conditional access scenarios.</p>
  :::column-end:::
  :::column:::
    <p>You plan to implement conditional access for your mobile devices.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Directory extension attribute sync</p>
  :::column-end:::
  :::column:::
    <p>This feature enables you to extend the schema in Azure AD with custom attributes added by your organization or other attributes in your on-premises Active Directory.</p>
  :::column-end:::
  :::column:::
    <p>You extended your on-premises Active Directory schema with custom attributes.</p>
  :::column-end:::
:::row-end:::


After you select the optional features required by your organization, the Azure AD Connect installer provides the option to deploy a new Windows Server 2016 AD FS farm or to select an existing AD FS farm.

When installing Azure AD Connect using the Custom Settings option, you can optionally choose to start the synchronization process once the installation is complete.

You can also choose to enable staging mode. This process allows you to set up a new directory synchronization server in parallel with an existing server. While Microsoft 365 only supports one directory synchronization server connected to one Azure AD directory in the cloud, if you want an extra backup server for your directory synchronization setup, you can enable Azure AD Connect in staging mode. When enabled, the sync engine imports and synchronizes data as normal, but it doesn't export anything to Azure AD, and it turns off password hash sync and password writeback.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”