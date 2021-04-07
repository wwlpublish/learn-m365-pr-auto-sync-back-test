To plan user identities, you first need to understand the different user identities, namely: Cloud identities, Synchronized identities, and Federated identities. You can choose to maintain identities only in Microsoft 365, or you can integrate identities with your on-premises Active Directory.

:::image type="content" source="../media/m365-identity-models-cd023cf8.png" alt-text="graphic that identifies the differences between the three identity models used by Microsoft 365":::


### Cloud identities

A cloud identity is a user account that exists only in Azure AD. You can create a cloud identity with the same name as your on-premises AD DS user account, but there is no link between the two accounts. They would be considered two different, unique identities, each with their own password. You will create cloud identities by using the Microsoft 365 admin center. Most often, only small organizations use cloud identities because they do not need to maintain a local Active Directory implementation.

### Synchronized identities

A synchronized identity is a user that exists in an on-premises AD DS and in Microsoft 365. The AD DS user and the Microsoft 365 user are synchronized and linked together. Any changes that you make to the on-premises user account are synchronized to the Microsoft 365 user account.

Azure Active Directory Connect (Azure AD Connect) performs the synchronization once you have downloaded and installed it in your on-premises environment. Azure AD Connect filter the accounts that are synchronized and determines whether to synchronize passwords.

When you implement synchronized identities, your on-premises AD DS is the authoritative source for most information. As such, you must perform administration tasks mostly on-premises, which are then synchronized to Azure AD. Only a small set of attributes is synchronized from Microsoft 365 back to AD DS on-premises.

Authentication for synchronized identities occurs in Microsoft 365. The username and password are evaluated in Microsoft 365 without any reliance on the on-premises infrastructure.

### Federated identities

A federated identity is a synchronized user account that is authenticated by Lightweight Directory Access Protocol (LDAP) on the AD DS. This authentication process creates a local claims provider trust with the Active Directory Federation Services (AD FS). AD FS is deployed on-premises and communicates with AD DS on-premises. Therefore, Azure AD authorizes federated user accounts to access resources in Microsoft 365 based on the LDAP policy located on AD DS (through AD FS). Because the on-premises user account is used for authentication, the same password is used for signing in to Microsoft 365 and on-premises AD DS.

Implementing federated identities used to be more complex than implementing synchronized identities because of the requirement to implement AD FS. However, that complexity has been removed with the adoption of Azure AD Connect, which now deploys most of the AD FS infrastructure.

Because authentication to Microsoft 365 is dependent on the availability of AD FS, service interruptions to the on-premises infrastructure can affect Microsoft 365 authentication. For example, an on-premises Internet outage will cause Microsoft 365 authentication to fail. However, you can mitigate this issue by placing a copy of AD DS and AD FS in Microsoft Azure.

The main benefit of using federated identities is single sign-on (SSO). Users authenticate at a domain-joined workstation by using their credentials. SSO uses these cached credentials to automatically authenticate to Microsoft 365 services. Synchronized identities typically need to enter their credentials manually when accessing Microsoft 365 services.

Federated identities also take advantage of password policies and account lockout policies in an on-premises AD DS. This design provides more flexibility when managing password policies for Microsoft 365.

### Determining the best model for your organization

Each identify model has different advantages and disadvantages. To determine the best option for your company, you must first understand what scenario is best suited for each model, along with the greatest benefit for each model as outlined in the following table.

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    <p><b>Cloud Identity</b></p>
  :::column-end:::
  :::column:::
    <p><b>Synchronized Identity</b></p>
  :::column-end:::
  :::column:::
    <p><b>Federated Identity</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>Definition</b></p>
  :::column-end:::
  :::column:::
    <p>User account only exists in Microsoft 365.</p>
  :::column-end:::
  :::column:::
    <p>User account exists in local Active Directory and an identical user in exists in Microsoft 365.</p>
  :::column-end:::
  :::column:::
    <p>Synchronized user account authenticated by using AD FS.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>Best for…</b></p>
  :::column-end:::
  :::column:::
    <p>Small to medium-sized organizations or organizations that do not need a local Active Directory Domain Service (AD DS) anymore.</p>
  :::column-end:::
  :::column:::
    <p>Organizations running Active Directory already and are planning to move to the cloud.</p>
  :::column-end:::
  :::column:::
    <p>Organizations that want to centralize their authentication and authorization processes.<br></p>  <p>Also used by organizations already running a federated authentication system, or that require a special type of login, such as with ID card.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>Greatest benefit</b></p>
  :::column-end:::
  :::column:::
    <p>Simple to use; no extra tools required.</p>
  :::column-end:::
  :::column:::
    <p>Same Sign-In, and where management of identities is only required in one place.</p>
  :::column-end:::
  :::column:::
    <p>Single Sign-On (SSO), and where management of identities is only required in one place.</p>
  :::column-end:::
:::row-end:::
