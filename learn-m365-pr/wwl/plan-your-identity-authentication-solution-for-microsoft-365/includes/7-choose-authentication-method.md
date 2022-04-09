For organizations with an existing on-premises directory footprint that want to move their apps to the cloud, choosing the correct authentication method shouldn't be taken lightly, for the following reasons:

 -  It's one of the first decisions (along with choosing their directory synchronization tool) for an organization that wants to move to the cloud.
 -  The authentication method is a critical component of an organization’s presence in the cloud. It controls access to all cloud data and resources.
 -  It's the foundation of all the other advanced security and user experience features in Azure AD.

Identity is the new control plane of IT security, so authentication is an organization’s access guard to the new cloud world. Organizations need an identity control plane that strengthens their security and keeps their cloud apps safe from intruders.

> [!NOTE]
> Changing your authentication method requires planning, testing, and potentially downtime. [Staged rollout](/azure/active-directory/hybrid/how-to-connect-staged-rollout) is a great way to test users migration from federation to cloud authentication.

Organizations that don't have an existing on-premises directory footprint aren't the focus of this unit. Typically, those businesses create identities only in the cloud, which doesn’t require a hybrid identity solution. Cloud-only identities exist solely in the cloud and aren't associated with corresponding on-premises identities.

### Authentication methods

When the Azure AD hybrid identity solution is your new control plane, authentication is the foundation of cloud access. Choosing the correct authentication method is a crucial first decision in setting up an Azure AD hybrid identity solution. The selected authentication method is configured by using your selected directory synchronization tool - either Azure AD Connect sync or Azure AD Connect Cloud Sync, both of which provision users in the cloud.

To choose an authentication method, you must consider the time, existing infrastructure, complexity, and cost of implementing your choice. These factors are different for every organization and may change over time.

Azure AD supports the following authentication methods for hybrid identity solutions:

 -  **Cloud authentication**. With this authentication method, Azure AD handles the user sign-in process. When this method is coupled with seamless single sign-on (SSO), users can sign in to cloud apps without having to reenter their credentials. With cloud authentication, you can choose from two options:
    
     -  **Azure AD password hash synchronization**. This method is the simplest way to enable authentication for on-premises directory objects in Azure AD. Users can use the same username and password that they use on-premises without having to deploy any extra infrastructure. Some premium features of Azure AD, like Identity Protection and Azure AD Domain Services, require password hash synchronization, no matter which authentication method you choose. Passwords are never stored in clear text or encrypted with a reversible algorithm in Azure AD.
     -  **Azure AD Pass-through Authentication**. This method provides a simple password validation for Azure AD authentication services by using a software agent that runs on one or more on-premises servers. The servers validate the users directly with your on-premises Active Directory, which ensures that the password validation doesn't happen in the cloud. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and sign in hours might use this authentication method.
 -  **Federated authentication**. With this authentication method, Azure AD hands off the authentication process to a separate trusted authentication system, such as on-premises Active Directory Federation Services (AD FS), to validate the user’s password. The authentication system can provide other advanced authentication requirements, such as smartcard-based authentication and third-party multi-factor authentication.

> [!NOTE]
> Each of these authentication methods is examined in greater detail in the following units.

### Decision tree

The following flowchart provides a decision tree that can be used to help organizations decide which authentication method is right for them.

:::image type="content" source="../media/authentication-method-decision-tree-8596a051.png" alt-text="diagram displays a decision tree flowchart to help organizations determine which authentication method is right for them":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”