Two of the most common types of Exchange recipients are user mailboxes and resource mailboxes.

### User mailboxes

A user mailbox is the most common type of recipient because one is created for every user in an Exchange organization.

 -  In Exchange Online, each user mailbox is associated with a user account that's created in Microsoft 365.
 -  In Exchange Server, each user mailbox is associated with an Active Directory user account.

A user can use their mailbox to:

 -  Send and receive messages
 -  Store messages
 -  Schedule meetings and appointments
 -  Maintain task lists
 -  Write notes
 -  Store documents
 -  Manage contacts

User mailboxes can be accessed from different types of clients, such as Outlook, Outlook on the Web, Outlook Mobile, and third-party clients.

#### Archive mailboxes

Each user mailbox can be associated with an archive mailbox. An archive mailbox is a specialized mailbox that appears alongside a user's primary mailbox in Outlook and Outlook on the Web. It provides extra storage, and can be used for storing older messages.

> [!NOTE]
> An archive mailbox is available only if the user is connected to Exchange. As such, an archive mailbox can't be accessed in Outlook cached mode if the user isn't connected to Exchange.

An archive mailbox can be accessed and searched in the same way as the primary mailbox. Users can also move or copy messages between their primary mailbox and their archive mailbox.

Messaging administrators can also create retention policies that will automatically move messages to an archive mailbox. For example, a retention policy may move all messages that are older than two years from the users' primary mailbox to their archive mailbox.

### Resource mailboxes<br>

Resource mailboxes are specific types of mailboxes that can represent meeting rooms or shared equipment. Users can include them as resources in meeting requests.

Two different types of resource mailboxes can be created in Exchange:

 -  **Room mailboxes.** These mailboxes can be assigned to meeting locations, such as conference rooms, auditoriums, and training rooms. You to configure room mailbox settings such as booking delegates and booking options.
 -  **Equipment mailboxes.** These mailboxes can be assigned to resources that aren't location-specific, such as portable computer projectors, microphones, or company cars. On an equipment mailbox, you can configure settings that are similar to those on room mailboxes.

Both types of resource mailboxes can be included as resources in meeting requests. This design provides a simple and efficient way for users to book these resources. For example, to book a room or a piece of equipment, open Outlook from your computer and schedule a new meeting where you must add the room or equipment to the meeting, similar to how you would invite other users:

1.  Open **Outlook** on your computer.
2.  On the **Home** tab, choose **New Items** &gt; **Meeting**.
3.  In the **To** field, type the name of the conference room or equipment you want to reserve, along with any attendees you'd like to invite. You may optionally use the **Rooms** button if you want to search for all room mailboxes. You can also use the **Address Book** button to search for all room and equipment mailboxes.

Resource mailboxes have properties such as location and size that help you to search for meeting rooms that meet their requirements. You can also use the **Scheduling Assistant** option to see a calendar view of the room and the equipment's availability.
