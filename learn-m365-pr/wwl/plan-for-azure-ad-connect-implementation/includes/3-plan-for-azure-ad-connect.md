Azure AD Connect is easy to implement. That being said, if an organization has a complex Active Directory implementation or special requirements (such as partial attribute synchronization), it must thoroughly plan the Azure AD Connect tool implementation. To start planning, an organization should collect answers to the following questions:

 -  On what server do you want to install Azure AD Connect?
 -  Do you require an Azure AD Connect failover scenario?
 -  Do you want to synchronize one or more Active Directories (or multiple Forests)?
 -  Do you want to synchronize all or only part of your Active Directory?
 -  Do you want to synchronize all object attributes, or use specific filters?
 -  Do you want to use advanced configuration features such as password hash synchronization, password writeback, or device writeback?

An organization's decision whether to implement password hash synchronization will affect its next steps. Be mindful of the following considerations:

 -  **Implementing password hash synchronization.** Password hash synchronization enables users to authenticate using the same username and password as on-premises. Azure AD Connect synchronizes a user's password hash (a cryptographic hash of the password hash) and stores it in the respective user object in Azure AD. Since the password can't be reverse-engineered, it can be considered as securely stored.
 -  **Not implementing password hash synchronization.** If a company doesn't want its Active Directory password hashes stored outside the company, it must implement either Active Directory Federation Services (AD FS) or Azure AD pass-through authentication to provide single-sign on. Alternatively, each user can be provided with a separate password for their Azure AD account.

When planning for Azure AD Connect, an organization should include the following items in its planning preparation:

 -  Planning the Azure AD Connect Server
 -  Planning the Azure AD Connect Staging Server
 -  Planning Active Directory Federation Services for Azure AD Connect
 -  Planning the source anchor attribute

### Planning the Azure AD Connect server

Before installing Azure AD Connect, an organization must consider the following items when determining which server the tool should be installed on:

 -  Azure AD Connect can be installed on a domain controller, member server, or non-domain joined server.
 -  Azure AD Connect supports Windows Server 2008 or later.
 -  If an organization's Active Directory has less than 100,000 objects, it can use the light version of SQL Server Express that will be installed on the Azure AD Connect server.
 -  If an organization's Active Directory has more than 100,000 objects, it must plan for another SQL Server to manage the database and load.

An organization can't have more than one Azure AD Connect server connected to a single Azure AD or Microsoft 365 tenant. There's a 1:1 ratio between an Azure AD tenant and a server that runs Azure AD Connect. If an organization wants more than one Azure AD Connect server, it must deploy more than one Azure AD tenant.

The following table displays the minimum hardware requirements for the Azure AD Connect sync computer.

:::row:::
  :::column:::
    

**Number of objects in AD**


  :::column-end:::
  :::column:::
    

**CPU**


  :::column-end:::
  :::column:::
    

**RAM**


  :::column-end:::
  :::column:::
    

**Hard drive size**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**&lt; 10,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

4 GB


  :::column-end:::
  :::column:::
    

70 GB


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**10,000-50,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

4 GB


  :::column-end:::
  :::column:::
    

70 GB


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**50,000-100,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

16 GB


  :::column-end:::
  :::column:::
    

100 GB


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**100,000-300,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

32 GB


  :::column-end:::
  :::column:::
    

300 GB


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**300,000-600,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

32 GB


  :::column-end:::
  :::column:::
    

450 GB


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**&gt; 600,000**


  :::column-end:::
  :::column:::
    

1.6 GHz


  :::column-end:::
  :::column:::
    

32 GB


  :::column-end:::
  :::column:::
    

500 GB


  :::column-end:::
:::row-end:::


### Planning the Azure AD Connect staging server

Azure AD Connect supports installing extra server(s) in staging mode. A server in this mode reads data from all connected directories, but it doesn't write anything to connected directories. It uses the normal synchronization cycle, so it has an updated copy of the identity data.

If a disaster occurs and the primary server fails, an organization can fail over to the staging server in the Azure AD Connect wizard. This second server can be in a different datacenter where no infrastructure is shared with the primary server. Any configuration changes made on the primary server must be manually copied to the second server.

It's possible to have more than one staging server when an organization wants to have multiple backups in different datacenters. The following graphic shows that a staging server is an inactive server that takes over synchronization when the primary server fails.

:::image type="content" source="../media/sync-using-staging-server-during-failover-c7785b4a.jpg" alt-text="graphic shows that a staging server is an inactive server that takes over synchronization when the primary server fails":::


### Planning Active Directory Federation Services for Azure AD Connect

Azure AD Connect can also be used to set up and configure an Active Directory Federation Services (AD FS) infrastructure. The following prerequisites are required when an organization plans to implement AD FS:

 -  A Windows Server 2012 R2 or later server for the federation server with remote management enabled.
 -  A Windows Server 2012 R2 or later server for the Web Application Proxy server with remote management enabled.
 -  An SSL certificate for the federation service name the organization intends to use (for example, sts.adatum.com).
 -  Add a domain an organization plans to use in Microsoft 365 with single sign-on. For example, if you plan to use adatum.com for your users, then make sure this domain has been added to your Microsoft 365 tenant.

**Additional reading.** For more information on planning ADFS for Azure AD Connect, see [Prerequisites for Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect-prerequisites).

### Planning the source anchor attribute

Another crucial planning aspect for Azure AD Connect is deciding which object to use as the **sourceAnchor**. The sourceAnchor attribute matches both the source and the target object, thereby linking both objects together. For this reason, sourceAnchor uniquely identifies an object as being the same object both in the local Active Directory and in Azure AD. The sourceAnchor should be an object that never changes.

When deciding which object to use as the sourceAnchor, consider the following scenarios:

 -  **You have a single forest on-premises.** In this scenario, it's recommended that you use the msDs-ConsistencyGuid attribute. This attribute is used when you run with express settings in Azure AD Connect.
 -  **You have multiple forests but you don't move users between forests and between domains in the same forest.** In this scenario, objectGUID is a good attribute to use.
 -  **You have multiple forests and you move users between forests and domains.** In this scenario, you must find an attribute that won't change or that can be moved along with the users. One recommended approach is to introduce a synthetic attribute. Synthetic attributes can hold something that looks like a GUID. During object creation, a new GUID is created and stamped on the user. A custom rule can be created in the sync engine server to create this value based on the objectGUID and update the selected attribute in Active Directory. When you move the object, you must also copy the content of this value.
 -  **Select an existing attribute that won't change.** A commonly used attribute is employeeID. If you consider an attribute that contains letters, you must ensure there's no way the case (upper case vs. lower case) can change for the attribute's value. Attributes that shouldn't be used include the user’s name, which can change if a person marries or divorces, or the user’s position, which could change if the user changes assignments. This reason is also why attributes such as userPrincipalName, mail, and targetAddress can't be selected in the Azure AD Connect installation wizard. Those attributes also contain the @-character, which isn't allowed in the sourceAnchor. Other attributes that can't be used include attributes with an @-sign, such as email and userPrincipalName (UPN).
