Organizations that separate the management of Exchange Server objects and Active Directory objects use what's called a split permissions model. Split permissions enable organizations to assign specific permissions and related tasks to specific groups responsible for identity and messaging within the organization. This separation of work not only helps to maintain standards and workflows, but it also helps to control change in the organization.

The highest level of split permissions is the separation of Exchange management and Active Directory management. Many organizations have two groups of administrators:

 -  Administrators that manage the organization's Exchange infrastructure, including servers and recipients.
 -  Administrators that manage the Active Directory infrastructure.

This separation is important for many organizations because the Active Directory infrastructure often spans many locations, domains, services, applications, and even Active Directory forests. Active Directory administrators must ensure that changes made to Active Directory don't negatively impact any other services. As a result, only a small group of administrators is typically allowed to manage that infrastructure.

At the same time, the infrastructure for an Exchange Server environment, including servers and recipients, can also be complex and require specialized knowledge. Exchange Server stores confidential information about the business of the organization. Exchange administrators can potentially access this information. By limiting the number of Exchange administrators, the organization limits who can make changes to Exchange configuration and who can access sensitive information.

Split permissions typically make a distinction between the creation of security principals in Active Directory and the configuration of those objects. Security principals in AD include users and security groups. This distinction between creating and configuring the security principals helps reduce the chance of unauthorized access to the network. It does so by controlling who can create objects and who can maintain them.

Active Directory administrators are typically the only users who can create security principals. Other administrators, such as Exchange or Messaging administrators, can manage specific attributes on existing Active Directory objects.

Exchange supports the varying needs to separate the management of Exchange Server and Active Directory. It does so by letting you choose whether you want a shared permissions model or a split permissions model. A split permissions model is also separated into two types: RBAC permissions and Active Directory permissions.

By default, if you don’t configure anything else, Exchange uses a shared permissions model.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.