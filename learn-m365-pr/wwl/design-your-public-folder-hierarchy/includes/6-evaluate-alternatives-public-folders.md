Public folders have always been an essential feature of Exchange Server, and Microsoft will continue to support public folders as long as it supports Exchange Server. However, over the years Microsoft has developed new technology that has built on the foundation of public folders, and in several cases, offers significant advantages over public folders.

> [!TIP]
> Moving forward, Messaging administrators should explore alternatives to public folders before they consider creating new ones.

This unit examines the Microsoft 365 alternatives to public folders:

 -  Microsoft 365 Groups (only if you run a Hybrid or Exchange Online environment)
 -  SharePoint Server
 -  Shared mailboxes

### Microsoft 365 Groups as a public folder replacement

Microsoft 365 Groups is the latest collaboration offering from Microsoft. As such, it takes advantage of the latest collaboration technology. This fact alone makes it a preferable collaboration solution over public folders, which is a much older technology. For example, Groups can replace mail-enabled public folders altogether in Microsoft Outlook. Compiling a list of every scenario in which Microsoft 365 Groups works better than public folders is impossible, but several scenarios stand out, including:

 -  **Collaboration over email**. In Outlook, there's a dedicated **Conversations** space in Groups that stores all the emails and lets users collaborate over them. The group can even be set up to receive messages from people outside the group or from outside the organization. For example, if you're currently using mail-enabled public folders to store project-related discussions, or purchase orders that must be viewed by a team of people, using groups would be an improvement. Groups are also better for situations when you simply want to broadcast information to a set of users.
 -  **Collaboration over documents**. In Outlook, there's a dedicated **Files** tab in Groups that displays all files from the group's SharePoint team site and from mail attachments. You get one view of all the files, so you don't have to go searching for them like you would in public folders. Co-authoring also becomes easier. Organizations should consider migrating to Groups if they're using public folders for storing files meant to be consumed by multiple people.
 -  **Shared calendar**. At the time it's created, every group is assigned a shared calendar. Any member of the group can create events on that calendar. When you mark a group as a favorite, that group's calendar can be displayed alongside your personal calendar. You can also subscribe to a group's events, in which case events created in that group appear in your personal calendar. If you're using public folders to host calendars for your team, such as a schedule or a timetable, Groups would be an improved experience.
 -  **Simplified permissions**. When you assign users to a group, they're automatically assigned the permissions they need. In comparison, you must manually assign users the proper permissions when using public folders. With Groups, members can be added as "owners" or "members." Owners have full rights in the group, including the ability to complete group management tasks. Members can also create content and edit files like owners, but members can't delete content that they haven't created. If you find the public folders' permissions model too overwhelming and you instead prefer something simple and quick, Microsoft 365 Groups is the way to go.
 -  **Mobile and Web presence**. Public folders can't be accessed through mobile devices. They also provide limited functionality on the Web. In comparison, Microsoft 365 Groups is accessible through Outlook mobile apps and has a richer set of features on the Web. If your team is on the move and requires mobile access, then you should be using Microsoft 365 Groups.
 -  **Access to a wide range of Microsoft 365 apps**. When you create a group, you unlock access to a wide range of apps from the Microsoft 365 suite. You get a SharePoint team site for storing files and a plan on Planner to track your tasks. Microsoft 365 Groups is the membership service that combines elements of the entire Microsoft 365 suite.

You should be aware of a few major differences that you'll notice after leaving the public folders experience. The two primary differences include:

 -  **Folder hierarchy.** While public folders are often used to organize content in deep-rooted hierarchy, Microsoft 365 Groups has a flat structure. All emails in the group are in the Conversations space and all the documents go into the **Files** tab. Also, you can't create subfolders in Microsoft 365 groups.
 -  **Granular permission roles.** While public folders have various permission roles, Microsoft 365 Groups only provides two: owner and member.

If you decide to switch to Microsoft 365 Groups, you can use a batch migration process to move your email and calendar content from your existing public folders to Groups. The specific steps for running a batch migration depend on which version of Exchange currently hosts your public folder hierarchy.

### SharePoint Server as a public folder replacement

Another alternative to public folders is SharePoint Server. SharePoint Server has advanced features and a web-based platform for collaboration.

Some of the commonly used features in SharePoint Server include:

 -  **Document libraries.** Document libraries store documents that users can check in and check out, and the documents are tracked with version control.
 -  **Discussion groups.** Users can use the discussion-groups feature as a forum for communication, similar to using postings in a public folder.
 -  **Shared calendars.** Users can use the shared calendars feature instead of shared calendars in a public folder.
 -  **Contacts.** Users can link the Contacts feature with Office Outlook to provide a shared location for creating contacts.

You also can integrate SharePoint Server with Exchange Server to provide meeting workspaces. Meeting workspaces are created as a site to support a meeting and are created automatically as part of the meeting request. You can use the meeting workspace to store documents related to the meeting and to conduct project discussions.

### Shared mailboxes as a public folder replacement

A shared mailbox is a mailbox that selected users can access to read and send email messages and to share a common calendar. Shared mailboxes can provide a generic email address (such as info@contoso.com or sales@contoso.com) that customers can use to ask about your company. It serves best as a common contact mailbox, such as a support team email or a general address for all sales representatives.

Shared mailboxes are often found in company departments that require a mailbox that's shared with a small group of users. When comparing shared mailboxes and public folders, both can store Outlook type items such as messages and calendar events, and both can receive emails (if public folders are mail enabled). However, public folders are considered a company-wide collaboration tool that can be accessed by anyone in an organization. In comparison, a shared mailbox is designed to serve small- to medium-sized groups.

**Additional reading.** For more information, see [Collaboration in Exchange Online](/exchange/collaboration-exo/collaboration-exo?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.