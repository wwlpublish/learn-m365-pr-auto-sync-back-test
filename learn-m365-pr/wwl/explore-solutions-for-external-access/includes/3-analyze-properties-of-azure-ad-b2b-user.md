B2B collaboration is a capability of Azure AD External Identities. It lets an organization's users collaborate with users and partners outside of their organization. With B2B collaboration, an external user is invited to sign in to your Azure AD organization using their own credentials. This B2B collaboration user can then access the apps and resources you want to share with them.

A user object is created for the B2B collaboration user in the same directory as your employees. B2B collaboration user objects have limited privileges in your directory by default. They can be managed like employees, added to groups, and so on. This unit discusses the properties of this user object and ways to manage it.

The following table describes B2B collaboration users based on how they authenticate (internally or externally) and their relationship to your organization (guest or member).

:::image type="content" source="../media/table-with-B2B-user-properties-9cb35dc8.png" alt-text="Graphic that describes B2B collaboration users based on how they authenticate and their relationship to an organization.":::


The four user types described in this graphic include:

 -  **External guest**. Most users who are commonly considered external users or guests fall into this category. This B2B collaboration user has an account in an external Azure AD organization or an external identity provider (such as a social identity). They also have guest-level permissions in the resource organization. The user object created in the resource Azure AD directory has a UserType of **Guest**.
 -  **External member**. This B2B collaboration user has either:
    
     -  An account in an external Azure AD organization.
     -  An external identity provider (such as a social identity) and member-level access to resources in your organization. This scenario is common in organizations consisting of multiple tenants. In this situation, users are considered part of the larger organization and need member-level access to resources in the organization’s other tenants.

    The user object created in the resource Azure AD directory has a UserType of **Member**.

 -  **Internal guest**. Before Azure AD B2B collaboration was available, it was common to collaborate with distributors, suppliers, vendors, and others by setting up internal credentials for them and designating them as guests by setting the user object UserType to **Guest**. If you have internal guest users like these, you can invite them to use B2B collaboration instead. By doing so, they can use their own credentials. This design allows their external identity provider to manage authentication and their account lifecycle.
 -  **Internal member**. These users are considered employees of your organization. The user authenticates internally through Azure AD. The user object that's created in the resource Azure AD directory has a UserType of **Member**.

### Invitation redemption

The following sections describe what an Azure AD B2B collaboration user looks like in Azure AD.

#### Before invitation redemption

B2B collaboration user accounts are the result of inviting guest users to collaborate by using the guest users' own credentials. When the invitation is initially sent to the guest user, an account is created in your tenant. This account doesn’t have any credentials associated with it because authentication is performed by the guest user's identity provider.

The Issuer property for the guest user account in your directory is set to the host's organization domain. It remains this value until the guest redeems their invitation. In the portal, the Invitation accepted property in the invited user’s Azure AD portal profile will be set to No. When you query for externalUserState using the Microsoft Graph API, it will return **Pending Acceptance**.

#### After invitation redemption

After the B2B collaboration user accepts the invitation, the Issuer property is updated based on the user’s identity provider.

 -  If the B2B collaboration user is using credentials from another Azure AD organization, the Issuer is External Azure AD.
 -  If the B2B collaboration user is using a Microsoft account or credentials from another external identity provider, the Issuer reflects the identity provider. For example, Microsoft Account, google.com, or facebook.com.

For external users who are using internal credentials, the Issuer property is set to the host’s organization domain. The Directory synced property is:

 -  **Yes,** if the account is homed in the organization’s on-premises Active Directory and synced with Azure AD.
 -  **No**, if the account is a cloud-only Azure AD account.

The directory sync information is also available through the **onPremisesSyncEnable****d** property in Microsoft Graph API.

### Key properties of the Azure AD B2B collaboration user

#### User Principal Name

The user principal name for a B2B collaboration user object contains an **\#EXT\#** identifier.

#### User type

This property indicates the relationship of the user to the host tenancy. This property can have two values:

 -  **Member**. This value indicates an employee of the host organization and a user in the organization's payroll. For example, this user expects to have access to internal-only sites. This user isn't considered an external collaborator.
 -  **Guest**. This value indicates a user who isn't considered internal to the company. These users are typically external collaborators, partners, or customers. For example, such a user isn't expected to receive a CEO's internal memo or receive company benefits.

> [!NOTE]
> The UserType has no relation to how the user signs in, the directory role of the user, and so on. This property simply indicates the user's relationship to the host organization. It allows the organization to enforce policies that depend on this property.

#### Issuer

This property indicates the user’s primary identity provider. A user can have several identity providers. They can be viewed by selecting **issuer** in the user’s profile or by querying the **onPremisesSyncEnabled** property through the Microsoft Graph API.

> [!NOTE]
> Issuer and UserType are independent properties. A value of issuer doesn't imply a particular value for UserType.

:::row:::
  :::column:::
    **Issuer property value**
  :::column-end:::
  :::column:::
    **Sign-in state**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    External Azure AD
  :::column-end:::
  :::column:::
    This user is homed in an external organization. It authenticates by using an Azure AD account that belongs to the other organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft account
  :::column-end:::
  :::column:::
    This user is homed in a Microsoft account. It authenticates by using a Microsoft account.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    \{host’s domain\}
  :::column-end:::
  :::column:::
    This user authenticates by using an Azure AD account that belongs to this organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    google.com
  :::column-end:::
  :::column:::
    This user has a Gmail account. It has also signed up by using self-service to the other organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    facebook.com
  :::column-end:::
  :::column:::
    This user has a Facebook account. It has also signed up by using self-service to the other organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    mail
  :::column-end:::
  :::column:::
    This user has an email address that doesn't match with verified Azure AD or SAML/WS-Fed domains. It also isn't a Gmail address or a Microsoft account.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    phone
  :::column-end:::
  :::column:::
    This user has an email address that doesn't match a verified Azure AD domain or a SAML/WS-Fed domain. It also isn't a Gmail address or Microsoft account.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    \{issuer URI\}
  :::column-end:::
  :::column:::
    This user is homed in an external organization that doesn't use Azure Active Directory as their identity provider. Instead, it uses a SAML/WS-Fed-based identity provider. The issuer URI is shown when the issuer field is selected.
  :::column-end:::
:::row-end:::


#### Directory synced

The Directory synced property indicates whether the user is being synced with on-premises Active Directory and is authenticated on-premises. This property is set to:

 -  **Yes,** if the account is homed in the organization’s on-premises Active Directory and synced with Azure AD.
 -  **No**, if the account is a cloud-only Azure AD account.

In Microsoft Graph API, the Directory synced property corresponds to **onPremisesSyncEnabled**.

### Add Azure AD B2B users as members instead of guests

Typically, an Azure AD B2B user and guest user are synonymous. Therefore, an Azure AD B2B collaboration user is added as a user with UserType set to **Guest** by default.

However, in some cases, the partner organization is a member of a larger organization to which the host organization also belongs. If so, the host organization may want to treat users in the partner organization as members instead of guests. In this situation, use the Azure AD B2B Invitation Manager APIs to add or invite a user from the partner organization to the host organization as a member.

### Convert UserType

It's possible to convert UserType from Member to Guest and vice-versa. You can make this change by editing the user's profile in the Azure portal or by using PowerShell.

The thing to keep in mind is that the UserType property represents the user's relationship to the organization. Therefore, you should change this property only if the relationship of the user to the organization changes. In this scenario, you should consider the following questions:

 -  If the relationship of the user changes, should the user principal name (UPN) change?
 -  Should the user continue to have access to the same resources?
 -  Should a mailbox be assigned?

### Remove guest user limitations

There may be cases where you want to give your guest users higher privileges. You can add a guest user to any role. You can also remove the default guest user restrictions in the directory to give a user the same privileges as members.

It's possible to turn off the default limitations so that a guest user in the company directory has the same permissions as a member user.

### Make guest users visible in the Exchange Global Address List

By default, guest objects aren't visible in your organization's global address list. However, you can use Azure Active Directory PowerShell to make them visible. For details, see "Add guests to the global address list" in the article titled [Microsoft 365 per-group guest access](/microsoft-365/solutions/per-group-guest-access?azure-portal=true).

### Update a guest user's email address

A guest user may sometimes accept your invitation and then later change their email address. When this situation occurs, the new email address doesn't automatically sync to the guest user object in your directory.

You can correct this situation by updating the mail property in the Azure AD guest user object. The mail property is created through Microsoft Graph API. You can update the mail property through the Microsoft Graph API, the Exchange admin center, or Exchange Online PowerShell. The change will be reflected in the Azure AD guest user object.