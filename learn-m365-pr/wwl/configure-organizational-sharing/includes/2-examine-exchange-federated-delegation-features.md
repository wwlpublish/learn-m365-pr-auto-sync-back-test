Users in one organization must often collaborate with users from another organization, such as vendors, partners, or customers. As part of this collaboration, users may need to share their availability information, calendars, and contacts with users in other organizations.

Sharing address lists or availability data with users who are outside an Exchange Server organization isn't possible by default. Instead, organizations that want to enable collaboration between their Exchange 2010 or higher organization and users who are either in another Exchange Server 2010 or higher organization or located in Exchange Online can do so by using federated trusts.

### Federated trusts

Federation refers to the underlying trust infrastructure that supports federated sharing.

 -  When you configure federation, you configure a federated trust with the Microsoft Azure Active Directory (Azure AD) authentication system.
 -  When another organization configures the same federated trust, the Azure AD authentication system provides a security token that contains claims (an assertion of information about the subject that has been authenticated). These claims enable users in one organization to access information in the other organization.

Each Exchange organization must develop federated trusts using the business instance of the Microsoft Azure AD authentication system. The following Exchange organizations use the business instance of the Microsoft Azure AD authentication system:

 -  Exchange Online
 -  Exchange Server 2010 or later organizations that run the Federated Trust Wizard

> [!NOTE]
> Microsoft no longer supports federation trust support for the consumer instance of the Microsoft Federation Gateway, which was used in Exchange 2010 and earlier implementations.

:::image type="content" source="../media/exchange-federation-21ccba3b.png" alt-text="Graphic showing the Azure AD authentication system in the middle and an organization on each side, with federation trust arrows between each organization and the Azure AD authentication system.":::


After you configure the federated trust, you must configure organization relationships or sharing policies. These settings identify the organizations that you want to share information with. When both organizations define these policies, users in the organizations can share their availability information, calendars, and contacts.
