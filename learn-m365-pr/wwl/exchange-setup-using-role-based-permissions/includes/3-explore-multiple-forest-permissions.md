Many organizations deploy multiple Active Directory forests to create security boundaries within their organizations. Using multiple forests helps administrators define security boundaries to better match their requirements, whether that's ensuring the fewest number of people have access to resources, or segmenting divisions within an organization.

Microsoft Exchange Server supports two types of multiple forest topologies:

 -  **Cross-forest.** This topology type can have multiple forests, each with their own installation of Exchange.
 -  **Resource forest.** This topology type has an Exchange forest and one or more accounts forests.

For the purposes of this unit, the forest that contains the universal security groups (USGs) and users outside of the forest where Exchange is installed, whether it's an accounts forest or other resource forest, is called a foreign forest.<br>

Configuration of permissions in a multiple forest topology relies on the correct configuration of forest trusts and global address list (GAL) synchronization for the creation of linked mailboxes. The Exchange forest must trust the foreign forest that contains the USGs associated with linked role groups and users associated with linked mailboxes.

Exchange uses a Role-Based Access Control (RBAC) permissions model. Each end-user and administrator can complete tasks that are based on:

 -  The management role groups that administrators are members of.
 -  The management role assignment policies that end users are assigned.

To understand multiple-forest permissions, you must be familiar with RBAC.<br>

### Permissions in a multiple forest topology

RBAC applies permissions to all Exchange objects within a single forest. The RBAC configuration in each forest is configured independently of all other forests. When you create a role group in one forest:

 -  That role group doesn't exist in any other forest.
 -  The permissions granted by that role group apply only to the forest in which it was created.

For example, a member of a role group that grants permissions to create a mailbox can create a mailbox only in the forest that contains that role group.

If you have multiple Exchange forests and you want to configure permissions identically within each forest, you must apply the same configuration explicitly in each forest.

For example, if you have two Exchange forests and you want to create a Compliance Management role group to manage permissions for your legal department, you must complete the following steps:

1.  In each forest, create a role group named Compliance Management. If your administrators are in a separate foreign forest from either Exchange forest, create both role groups as linked role groups.
2.  In each forest, create role assignments between the new role groups and the roles that you want to use.
3.  As part of the new role assignments, optionally add management scopes that encompass the server and recipient objects within each forest.
4.  If you created the role groups as linked role groups, add members to the associated USG in the foreign forest.

### A multi-forest example

The following diagram shows how the role groups configured within Exchange forests are bound to their respective forests.

 -  The Organization Management role group in Exchange forest A grants permissions only to manage the mailboxes and servers that are within that forest.
 -  The role groups in Exchange forest B grant permissions only to the mailboxes and servers within that forest.

:::image type="content" source="../media/multi-forest-permissions-797e59c7.png" alt-text="Diagram showing how the role groups configured within Exchange forests are bound to their respective forests.":::


The diagram also shows that Custom role group A is created in each forest. Even though the two custom role groups were created with the same name, each is its own separate entity. In fact, as the figure shows, each can be assigned different management roles in their respective forests:

 -  Custom role group A in Exchange forest A is assigned the Mailbox Search and Message Tracking roles.
 -  Custom role group A in Exchange forest B is assigned the Mailbox Search and Retention Management roles.

Finally, management scopes created in each forest are also bound by the forest. Server scopes created in each forest can only contain the servers that are members of that forest. In the diagram:

 -  Server scope A can contain only servers within Exchange forest A.
 -  Server scope B can contain only servers that are within Exchange forest B.
 -  The recipient scope in Exchange forest B can only contain mailboxes that are within Exchange forest B.

**Additional reading**. For more information, see [Cross-boundary permissions](/exchange/understanding-multiple-forest-permissions-exchange-2013-help?azure-portal=true).
