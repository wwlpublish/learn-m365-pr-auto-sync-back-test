For most organizations, the volume and complexity of their data is increasing daily—email, documents, instant messages, and more. Effectively managing or governing this information is important because organizations need to:

 -  Comply proactively with industry and government regulations and internal policies that require them to store content for a minimum period of time. For example, some government regulations require organizations to store certain types of content for seven years.<br>
 -  Reduce their risk if there's litigation or a security breach by permanently deleting old content that they're no longer required to keep.<br>
 -  Share knowledge effectively and be more agile by ensuring that their users work only with content that's current and relevant to them.<br>

Retention settings that organizations configure can help them achieve these goals. Managing content commonly requires two actions:

 -  **Retain content.** Prevent permanent deletion and remain available for eDiscovery.
 -  **Delete content.** Permanently delete content from the organization.

With these two retention actions, organizations can configure retention settings for the following outcomes:<br>

 -  **Retain-only.** Keep content forever or for a specified period of time.
 -  **Delete-only.** Permanently delete content after a specified period of time.
 -  **Retain and then delete.** Keep content for a specified period of time and then permanently delete it.

These retention settings work with content in place that saves organizations the extra overhead of creating and configuring extra storage when they need to retain content for compliance reasons. They also don't need to implement customized processes to copy and synchronize this data.

### Using retention policies to manage data

Organizations use retention policies to implement retention settings. Retention policies enable organizations to proactively decide whether to retain content, delete content, or retain and then delete the content. A retention policy enables organizations to efficiently manage their data by assigning the same retention settings at the container level to be automatically inherited by content in that container.

When content has retention settings assigned to it, users can continue to edit and work with the content as if nothing’s changed. They're able to do so because the content is retained in place, in its original location. But if they edit or delete content that’s included in the retention policy, a copy of the content as it existed when the policy was applied is saved to a secure location where it’s kept while the policy is in effect.

For sites, a copy of the original content is kept in the Preservation Hold library when users edit or delete it. For email and public folders, the copy is retained in the Recoverable Items folder. These secure locations and the retained content aren't visible to most users. With a retention policy, uses don't even need to know that their content is subject to the policy.<br>

The following sections examine how retention policies work throughout Microsoft 365.

### Content in OneDrive accounts and SharePoint sites

A retention policy is applied at the site level. When you include a SharePoint site or OneDrive account in a retention policy, a Preservation Hold library is created if one doesn’t already exist. Most users can’t view the Preservation Hold library because it’s visible only to site collection administrators.

When a user attempts to change or delete content in a site that’s subject to a retention policy, the policy first checks whether the content’s been changed since the policy was applied. If the change is the first one made since the policy was applied, the retention policy copies the content to the Preservation Hold library and then enables the person to change or delete the original content.

> [!NOTE]
> Any content in the site can be copied to the Preservation Hold library, even if the content doesn't match the query used by the retention policy.

At this point, a timer job cleans up the Preservation Hold library. The timer job runs periodically and compares all content in the Preservation Hold library to all the queries used by the retention policies on the site. Unless content matches at least one of the queries, the timer job permanently deletes the content from the Preservation Hold library.

Processing within the timer job applies to content that exists when the retention policy is applied. Any new content that’s created or added to the site after it was included in the policy will be retained after deletion. However, new content isn’t copied to the Preservation Hold library the first time it’s edited, only when it’s deleted.

> [!NOTE]
> A user will receive an error if they try to delete a library, list, folder, or site that's subject to a retention policy. A user can delete a folder if they first move or delete any files in the folder that are subject to the policy.

After a retention policy is assigned to a OneDrive account or SharePoint site, content can follow one of two paths:

1.  **Content is modified or deleted during the retention period.** A copy of the original content as it existed when the retention policy was assigned is created in the Preservation Hold library. There, a timer job runs periodically and identifies items whose retention period has expired, and these items are permanently deleted within seven days of the end of the retention period.
2.  **Content isn't modified or deleted during the retention period.** The content is moved to the first-stage Recycle Bin at the end of the retention period. If a user deletes the content from there or empties this Recycle Bin (also known as purging), the document is moved to the second-stage Recycle Bin. A 93-day retention period spans both the first- and second-stage recycle bins. At the end of 93 days, the document is permanently deleted from wherever it is, in either the first- or second-stage Recycle Bin.

:::image type="content" source="../media/content-flow-with-retention-policy-8d14e8eb.png" alt-text="graphic showing the previous two options of how content flows after a retention policy is assigned to a OneDrive account or SharePoint site.":::


### How a retention policy works with document versions in a site

A retention policy doesn’t automatically keep all versions of a document in a OneDrive account or SharePoint site. To do so, you need to turn on versioning for the document libraries in the site. For more information, see [Enable and configure versioning for a list or library](https://support.office.com/article/Enable-and-configure-versioning-for-a-list-or-library-1555D642-23EE-446A-990A-BCAB618C7A37?azure-portal=true).

If a document is deleted from a site that’s being retained and document versioning is turned on for the library, all versions of the deleted document are kept.

If document versioning isn’t turned on and an item is subject to several retention policies, the version that’s kept is the one that’s current when each retention policy takes effect. For example, if version 27 of an item is the most recent when the site is retained the first time, and version 51 is the most recent when the site is retained the second time, versions 27 and 51 are retained.

### Content in mailboxes and public folders

For a user's mail, calendar, and other items, a retention policy is applied at the level of a mailbox. For a public folder, a retention policy is applied at the folder level, not the mailbox level. Both a mailbox and a public folder use the Recoverable Items folder to retain items. Only people who have been assigned eDiscovery permissions can view items in another user's Recoverable Items folder.

When a user deletes a message in a folder other than the Deleted Items folder, the message is moved, by default, to the Deleted Items folder. When a person deletes an item in the Deleted Items folder, the message is moved to the Recoverable Items folder. A person can also soft delete an item (SHIFT+DELETE) in any folder, which bypasses the Deleted Items folder and moves the item directly to the Recoverable Items folder.

A process periodically evaluates items in the Recoverable Items folder. If an item doesn't match the rules of at least one retention policy, the item is permanently deleted (also called hard deleted) from the Recoverable Items folder.

When a person attempts to change certain properties of a mailbox item—such as the subject, body, attachments, senders and recipients, or date sent or received for a message—a copy of the original item is saved to the Recoverable Items folder before the change is committed. This process also happens after any other changes. At the end of the retention period, copies in the Recoverable Items folder are permanently deleted.

If a user leaves your organization, and their mailbox is included in a retention policy, the mailbox becomes an inactive mailbox when the user's Microsoft 365 account is deleted. The contents of an inactive mailbox are still subject to any retention policy that was placed on the mailbox before it was made inactive, and the contents are available to an eDiscovery search. For more information, see [Create and Manage Inactive Mailboxes in Office 365](https://docs.microsoft.com/office365/securitycompliance/create-and-manage-inactive-mailboxes?azure-portal=true).

:::image type="content" source="../media/delete-email-from-public-folder-b9683f59.png" alt-text="graphic showing the two options as to how email or content from a public folder is permanently deleted":::


### Content in Teams

You can use a retention policy to save chats and channel messages in Teams. Teams chats are stored in a hidden folder in the mailbox of each user included in the chat, and Teams channel messages are stored in a similar hidden folder in the group mailbox for the team. However, it’s important to understand that Teams uses an Azure-powered chat service that also stores this data, and by default this service stores the data forever. For this reason, it's recommended that you use the Teams location to save and delete Teams data. Using the Teams location will permanently delete data from both the Exchange mailboxes and the underlying Azure-powered chat service.

**Additional reading.** For more information, see [Overview of security and compliance in Microsoft Teams](https://docs.microsoft.com/microsoftteams/security-compliance-overview?azure-portal=true).

> [!NOTE]
> Teams chats and channel messages are not affected by retention policies applied to user or group mailboxes in the Exchange or Microsoft 365 groups locations. Even though Teams chats and channel messages are stored in Exchange, they’re affected only by a retention policy that’s applied to the Teams location.

There are several limitations to be aware of concerning retention in Microsoft Teams, including:

 -  **Teams requires a separate retention policy.** When you create a retention policy and toggle on the Teams location, all other locations toggle off. A retention policy that includes Teams can include only Teams and no other locations.
 -  **Teams isn't included in an organization-wide policy.** If you create an organization-wide policy, Teams isn't included because it requires a separate retention policy.
 -  **Teams doesn't support advanced retention.** When you create a retention policy, if you choose the **advanced retention** settings, the Teams location isn't available. Retention in Teams currently applies to all the chat and channel message content.
 -  **Teams content must be at least 30 days old to be deleted.** Creating a policy to delete Teams content that's less than 30 days old isn't currently supported. If you want this policy to apply to Teams content, specify a retention period that's equal to or greater than 30 days.
 -  **Teams may take up to 30 days to clean up retained content.** A retention policy applied to Teams will delete the content from all relevant storage locations. However, immediately after launch, it may take up to 30 days for Teams clients to clean up content based on the retention policy. But even though content still appears in the Teams clients, that content won't appear in content search or eDiscovery after the end of the retention period.

In a team, files that are shared in chat are stored in the OneDrive account of the user who shared the file. Files that are uploaded into channels are stored in the SharePoint site for the team. As a result, you must create a retention policy that applies to the SharePoint and OneDrive locations to save or delete files in a team. If you want to apply a policy to the files of just a specific team, you can choose the SharePoint site for the team and the OneDrive accounts of users in the team.

### Content in Skype locations

Unlike Exchange email, you can't toggle the status of the Skype location to **On** to include all users. However, you can turn on that location and then manually choose the users whose conversations you want to keep.

When you choose Skype for Business users, you can quickly include all users by selecting the Name box in the column header. However, each user counts as a specific inclusion in the policy. As a result, if you include over 1,000 users, the limits apply. Selecting all Skype users here isn't the same as if an organization-wide policy included all Skype users by default.

> [!CAUTION]
> Conversation History, which is a folder in Outlook, is a feature that has nothing to do with Skype archiving. **Conversation History** can be turned Off by the end user, but archiving for Skype is done by storing a copy of Skype conversations in a hidden folder that is inaccessible to the user but available to eDiscovery.

### Limitations for creating retention policies

Besides the current limitations of retention policies mentioned previously, there are the following limits that organizations should be aware of:

 -  **Organization-wide and entire-location policies.** There's a limit of 10 organization-wide policies and entire-location policies combined per tenant.
 -  **Retention policies that include or excludes over 1,000 specific users.** Such a retention policy can contain no more than 1,000 mailboxes and 100 sites. A tenant can contain no more than 1,000 such retention policies.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”