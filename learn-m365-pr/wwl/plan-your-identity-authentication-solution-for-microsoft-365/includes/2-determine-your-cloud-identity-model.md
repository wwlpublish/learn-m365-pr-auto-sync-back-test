Microsoft 365 uses Azure Active Directory (Azure AD) to manage identities and authentication for Microsoft 365. Azure AD is a cloud-based user identity and authentication service that's included with your Microsoft 365 subscription. Getting your identity infrastructure configured correctly is vital to managing Microsoft 365 user access and permissions for your organization.

To plan for user accounts, you must first understand the two identity models used in Microsoft 365:

 -  **Cloud-only identity**. An organization maintains its identities in the Azure AD tenant for your Microsoft 365 subscription. No identities are maintained on-premises.
 -  **Hybrid identity**. An organization maintains its identities in its on-premises Active Directory Domain Services (AD DS) and uses them for authentication when users access Microsoft 365 cloud services.

The following table outlines the two types of identity and their best fit and benefits.

:::row:::
  :::column:::
    **Attribute**
  :::column-end:::
  :::column:::
    **Cloud-only identity**
  :::column-end:::
  :::column:::
    **Hybrid identity**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Definition
  :::column-end:::
  :::column:::
    User account only exists in the Azure AD tenant for your Microsoft 365 subscription.
  :::column-end:::
  :::column:::
    User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription. The user account in Azure AD may also include a hashed version of the already hashed AD DS user account password.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    How Microsoft 365 authenticates user credentials
  :::column-end:::
  :::column:::
    The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.
  :::column-end:::
  :::column:::
    The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Best for
  :::column-end:::
  :::column:::
    Organizations that don't have or need an on-premises AD DS.
  :::column-end:::
  :::column:::
    Organizations using AD DS or another identity provider.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Greatest benefit
  :::column-end:::
  :::column:::
    Simple to use. No extra directory tools or servers required.
  :::column-end:::
  :::column:::
    Users can use the same credentials when accessing on-premises or cloud-based resources.
  :::column-end:::
:::row-end:::


The following sections examine each identity model in greater detail.

### Cloud-only identity

A cloud-only identity uses user accounts that exist only in Azure AD. Cloud-only identity is typically used by small organizations that don't have on-premises servers or don't use AD DS to manage local identities.

In the cloud-only model, both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Microsoft 365 cloud services. Azure AD authenticates user credentials based on its stored user accounts and passwords.

Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the Microsoft 365 admin center and Windows PowerShell.

### Hybrid identity

Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription. Most changes, except for [specific account attributes](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized?azure-portal=true), only flow one way. Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.

Microsoft 365's directory synchronization tools, Azure AD Connect sync and Azure AD Connect Cloud Sync (which are covered in a later unit), provide ongoing account synchronization. You must select the tool that best fits your business requirements. They check for changes in the AD DS and forward those changes to Azure AD. They can also filter which accounts are synchronized and determine whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).

When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information. This design means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD. The Azure AD tenant has a copy of the AD DS accounts. In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.

> [!NOTE]
> In the hybrid model, you must choose one of the two directory synchronization tools to synchronize user accounts for hybrid identity (these tools are examined in greater detail in a later unit in this module). You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.

Depending on your business needs and technical requirements, the hybrid identity model is the most common choice for enterprise customers who are adopting Microsoft 365. Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS), and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”