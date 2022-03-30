To plan user identities, you first need to understand the different user identities, namely: Cloud identities, Synchronized identities, and Federated identities. An organization can choose to maintain identities only in Microsoft 365, or it can integrate identities with its on-premises Active Directory.

:::image type="content" source="../media/m365-identity-models-cd023cf8.png" alt-text="graphic that identifies the differences between the three identity models used by Microsoft 365":::


### Cloud identities

A cloud identity is a user account that only exists in Azure AD. While an organization can create a cloud identity with the same name as an on-premises Active Directory Domain Services (AD DS) user account, there won't be any link between the two accounts. They would be considered two different, unique identities, each with their own password. Cloud identities are created in the Microsoft 365 admin center. Most often, only small organizations use cloud identities because they don't need to maintain a local Active Directory implementation.

### Synchronized identities

A synchronized identity is a user that exists in an on-premises AD DS and in Microsoft 365. The AD DS user and the Microsoft 365 user are synchronized and linked together. Any changes that you make to the on-premises user account are synchronized to the Microsoft 365 user account.

Azure Active Directory Connect (Azure AD Connect) does the synchronization once an organization downloads and installs it in its on-premises environment. Azure AD Connect filters the accounts that are synchronized and determines whether to synchronize passwords.

When an organization implements synchronized identities, its on-premises AD DS is the authoritative source for most information. As such, most of the administrative tasks that are done must be completed on-premises. These changes are then synchronized to Azure AD. Only a small set of attributes is synchronized from Microsoft 365 back to AD DS on-premises.

Authentication for synchronized identities occurs in Microsoft 365. The username and password are evaluated in Microsoft 365 without any reliance on the on-premises infrastructure.

### Federated identities

A federated identity is a synchronized user account that is authenticated by Lightweight Directory Access Protocol (LDAP) on the AD DS. This authentication process creates a local claims provider trust with the Active Directory Federation Services (AD FS).

AD FS is deployed on-premises and communicates with AD DS on-premises. As such, Azure AD authorizes federated user accounts to access resources in Microsoft 365 based on the LDAP policy located on AD DS (through AD FS). Because the on-premises user account is used for authentication, the same password is used for signing in to Microsoft 365 and on-premises AD DS.

Implementing federated identities used to be more complex than implementing synchronized identities because of the requirement to implement AD FS. However, that complexity has been removed with the adoption of Azure AD Connect, which now deploys most of the AD FS infrastructure.

Because authentication to Microsoft 365 is dependent on the availability of AD FS, service interruptions to the on-premises infrastructure can affect Microsoft 365 authentication. For example, an on-premises Internet outage will cause Microsoft 365 authentication to fail. However, this issue can be mitigated by placing a copy of AD DS and AD FS in Microsoft Azure.

The main benefit of using federated identities is Single Sign-On (SSO). Users authenticate at a domain-joined workstation by using their credentials. SSO uses these cached credentials to automatically authenticate to Microsoft 365 services. Synchronized identities typically need to enter their credentials manually when accessing Microsoft 365 services.

Federated identities also take advantage of password policies and account lockout policies in an on-premises AD DS. This design provides more flexibility when managing password policies for Microsoft 365.

### Determining the best model for your organization

Each identify model has different advantages and disadvantages. To determine the best option for your company, you must first understand what scenario is best suited for each model, along with the greatest benefit for each model as outlined in the following table.

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **Cloud Identity**
  :::column-end:::
  :::column:::
    **Synchronized Identity**
  :::column-end:::
  :::column:::
    **Federated Identity**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Definition**
  :::column-end:::
  :::column:::
    User account only exists in Microsoft 365.
  :::column-end:::
  :::column:::
    User account exists in local Active Directory and an identical user in exists in Microsoft 365.
  :::column-end:::
  :::column:::
    Synchronized user account authenticated by using AD FS.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Best for…**
  :::column-end:::
  :::column:::
    Small to medium-sized organizations or organizations that don't need a local Active Directory Domain Service (AD DS) anymore.
  :::column-end:::
  :::column:::
    Organizations running Active Directory already and are planning to move to the cloud.
  :::column-end:::
  :::column:::
    Organizations that want to centralize their authentication and authorization processes.
This model is also used by organizations already running a federated authentication system, or that require a special type of sign-in, such as with ID card.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Greatest benefit**
  :::column-end:::
  :::column:::
    Simple to use; no extra tools required.
  :::column-end:::
  :::column:::
    Same Sign-In, and where management of identities is only required in one place.
  :::column-end:::
  :::column:::
    Single Sign-On (SSO), and where management of identities is only required in one place.
  :::column-end:::
:::row-end:::
