When implementing external access solutions, it's important to understand the properties and states of the Business-to-Business (B2B) guest user object in Azure AD. An Azure AD B2B collaboration user is assigned a Guest user type property. This guest user typically is from a partner organization and, by default, has limited privileges in the inviting directory.

Depending on the inviting organization's needs, an Azure AD B2B collaboration user can be in one of the following account states:

 -  **State 1.** Homed in an external instance of Azure AD and represented as a guest user in the inviting organization. In this case, the B2B user signs in by using an Azure AD account that belongs to the invited tenant. If the partner organization doesn't use Azure AD, the guest user in Azure AD is still created. The user must redeem their invitation, at which time Azure AD verifies their email address. This arrangement is called a just-in-time (JIT) tenancy or a "viral" tenancy.
 -  **State 2.** Homed in a Microsoft or other account and represented as a guest user in the host organization. In this case, the guest user signs in with a Microsoft account or a social account (google.com or similar). The invited user's identity is created as a Microsoft account in the inviting organization’s directory during offer redemption.
 -  **State 3.** Homed in the host organization's on-premises Active Directory and synced with the host organization's Azure AD. Azure AD Connect can sync the partner accounts to the cloud as Azure AD B2B users with UserType = Guest. To do this see [Grant locally managed partner accounts access to cloud resources using Azure AD B2B collaboration](/azure/active-directory/b2b/hybrid-on-premises-to-cloud).
 -  **State 4.** Homed in the host organization's Azure AD with UserType = Guest and credentials that the host organization manages.

### Key properties of the Azure AD B2B collaboration user

There are two key properties of an Azure AD B2B collaboration user:

 -  **UserType.** This property describes the relationship of the user to the host tenancy. The available options include:
    
     -  **Member.** This value indicates a user who is an employee of the host organization and in the organization's payroll. For example, this user expects to have access to internal-only sites and isn't considered an external collaborator.
     -  **Guest.** This value indicates a user who isn't considered internal to the company, such as an external collaborator, partner, or customer. For example, such a user isn't expected to receive a CEO's internal memo or receive company benefits.
 -  **Source.** This property indicates how the user signs in. The available options include:
    
     -  **Invited user.** This user has been invited but hasn't redeemed an invitation.
     -  **External Azure Active Directory.** This user is homed in an external organization and authenticates by using an Azure AD account that belongs to the other organization. This type of sign-in corresponds to State 1.
     -  **Microsoft account.** This user is homed in a Microsoft account and authenticates by using a Microsoft account. This type of sign-in corresponds to State 2.
     -  **Windows Server Active Directory.** This user is signed in from on-premises Active Directory that belongs to this organization. This type of sign-in corresponds to State 3.
     -  **Azure Active Directory.** This user authenticates by using an Azure AD account that belongs to this organization. This type of sign-in corresponds to State 4.

:::image type="content" source="../media/guest-users-in-azure-ad-9ee174cd.jpg" alt-text="Diagram showing the guest users in Azure AD":::


**Additional reading:** To learn more about members versus guests, see [Can Azure AD B2B users be added as members instead of guests?](/azure/active-directory/b2b/user-properties)

## Guided demonstration (optional)

This guided demonstration is a recorded click-through simulation. Select the link at the end of this section to begin the demonstration. A tag will appear in the demonstration showing the next place you must select to advance the demonstration.

#### **Scenario:**

Contoso's internal security user group is dedicated to cross-platform testing and quality assurance. Contoso has started a large project where the testing must be performed in collaboration with a partner organization.

During this project, Contoso's users and its partner must access the same assets online. As Contoso's Enterprise Administrator, you must ensure this partner's access is properly configured.

In this guided demonstration, you'll complete the following steps:

1.  Invite partner users to your directory.
2.  Restrict the partner users to just the resources they need.

Time required: 15 minutes

[Launch the Guided Demonstration](https://aka.ms/AA6y80m)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”