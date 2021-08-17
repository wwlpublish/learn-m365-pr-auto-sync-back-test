Sharing free/busy (calendar availability) information between users located on-premises, and in the Exchange Online organization, is one of the primary benefits of a hybrid deployment. Users in both organizations can view each other's calendars just as if they were located in the same physical organization. This makes scheduling meetings and resources easy and efficient.

To enable the shared free/busy feature between your on-premises Exchange organization and Exchange Online, you need to establish a federation trust and configure organization relationships.

## Federation trust

Both the on-premises and Office 365 service organizations need to have a federation trust established with the Azure AD authentication system. A federation trust is a one-to-one relationship with the Azure AD authentication system that defines parameters for your Exchange organization.

A federation trust with the Azure AD authentication system is automatically configured for your Office 365 service organization when the account is created. The Hybrid Configuration wizard automatically checks to see if there is an existing federation trust with the Azure AD authentication system for the on-premises organization. If present, the existing federation trust is used to support the hybrid deployment. If it isn't present, the wizard creates a federation trust for the on-premises organization with the Azure AD authentication system.

## Organization relationships

Organization relationships are needed for both the on-premises and Exchange Online organization, and are configured automatically by the Hybrid Configuration wizard. An organization relationship defines the level of free/busy information shared for the organization.

## Learn more

- [Shared free/busy in Exchange hybrid deployments](/Exchange/shared-free-busy?azure-portal=true)
