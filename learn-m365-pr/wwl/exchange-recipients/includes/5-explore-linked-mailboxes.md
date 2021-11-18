Linked mailboxes in Exchange Server provide mailboxes for users whose primary accounts are in a separate, trusted forest. Users with linked mailboxes sign into their local AD DS domain by using the local credentials. Those credentials are then used to access a mailbox in an Exchange organization in a different forest.

Linked mailboxes can be useful in the following two scenarios:

 -  **Organizations deploy Exchange Server in a resource forest.** In this scenario, an organization centralizes Exchange Server in a single forest, while allowing access to the Exchange organization with user accounts that are located in one or more trusted forests (called *account forests*). The user account that accesses the linked mailbox doesn't exist in the forest where Exchange is deployed. As such, a disabled user account that exists in the same forest as Exchange is created and associated with the corresponding linked mailbox.
 -  **Organizations use linked mailboxes in a merger or acquisition scenario.** In this scenario, both organizations may have deployed Exchange Server before the merger or acquisition. Linked mailboxes provide the opportunity to remove the Exchange Server deployment from one of the organizations. The users from one of the organizations can be configured with linked mailboxes in the other organization. This design ensures that users from both organizations are listed in a single Global Access List (GAL), making availability information accessible to all users.

When deploying linked mailboxes, messaging administrators must carefully plan security permissions. The following approaches to managing the messaging environment are available:

 -  Organizations can decide which administrator’s team will manage user accounts in the account forest and which administrator’s team will manage recipients in the resource forest. Both teams should work together in administering the messaging environment. However, administrators should have enough administration permissions to complete their tasks so that unauthorized access to each forest isn't allowed.
 -  Another approach is that one of the administration teams manages both forests.
 -  You may also consider the trust relationship’s selective authentication. In this scenario, sign in’s from the resource forest are restricted to specific hosts in the production forest.

The following diagram illustrates the relationship between the linked user account used to access the linked mailbox (located in the account forest) and the disabled user account in the Exchange resource forest that's associated with the linked mailbox.

:::image type="content" source="../media/linked-mailboxes-architecture-b9236a70.png":::


> [!NOTE]
> A trust between the Exchange forest and at least one account forest must be set up before you can create linked mailboxes. At a minimum, you must set up a one-way, outgoing trust so that the Exchange forest trusts the account forest. For more information, see [Learn more about setting up a forest trust to support linked mailboxes](/previous-versions/exchange-server/exchange-150/jj156983%28v=exchg.150%29?azure-portal=true).

When configuring a linked mailbox, the user account that accesses the linked mailbox doesn't exist in the forest where Exchange is deployed. When you create the linked mailbox, a disabled user account is created in the domain where Exchange is deployed and associated with the linked mailbox. The user account from the account forest is granted full control of the mailbox.

To implement linked mailboxes, you must complete the following steps:

1.  Configure a one-way trust in which the domain where Exchange is deployed trusts the domain where the user account exists. This trust can be an external or forest trust. A one-way trust is required.
2.  Verify that the user account exists in the account forest before you create a linked mailbox. You can't create the user account when you create the linked mailbox.
3.  Besides configuring the one-way trust, you should also consider creating a two-way trust between the domains. The two-way trust isn't required, but the account that creates the linked mailbox must have permissions to modify the user object in the account forest. If you don't implement a two-way trust, you must provide account forest administrator credentials when you create the linked mailbox.
