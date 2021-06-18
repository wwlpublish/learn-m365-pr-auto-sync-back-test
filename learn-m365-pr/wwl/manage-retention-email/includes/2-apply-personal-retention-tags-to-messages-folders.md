Data governance in Exchange Server and Exchange Online is accomplished by using retention tags and retention policies. Managing retention in email is based on the following strategy:

 -  Assigning retention policy tags (RPT) to default folders, such as the Inbox and Deleted Items.<br>
 -  Applying default policy tags (DPT) to mailboxes to manage the retention of all untagged items.<br>
 -  Allowing the user to assign personal tags to custom folders and individual items.<br>
 -  Separating email retention functionality from users' Inbox management and filing habits. Users aren't required to file messages in managed folders based on retention requirements. Individual messages can have a different retention tag than the one applied to the folder in which they're located.<br>

The following figure illustrates the tasks involved in managing retention in email using personal tags and various policy tags.

:::image type="content" source="../media/email-retention-strategy-f6b8491b.gif" alt-text="diagram showing the tasks involved in email retention strategy":::


As the prior diagram indicates, retention tags are used to apply retention settings to folders and individual items such as e-mail messages and voice mail. These settings specify how long a message remains in a mailbox and the action to be taken when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted.

Retention tags enable users to tag their own mailbox folders and individual items for retention. Users no longer have to file items in managed folders provisioned by an administrator based on message retention requirements.

### Types of retention tags

Retention tags are classified into the following three types based on who can apply them and where in a mailbox they can be applied. Since this unit focuses on applying personal retention tags to messages and folders, pay special attention to how personal tags differ from DPTs and RPTs.

:::row:::
  :::column:::
    **Type of retention tag**
  :::column-end:::
  :::column:::
    **Applied...**
  :::column-end:::
  :::column:::
    **Applied by...**
  :::column-end:::
  :::column:::
    **Available actions...**
  :::column-end:::
  :::column:::
    **Details**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Default policy tag (DPT)
  :::column-end:::
  :::column:::
    Automatically to entire mailbox.

A DPT applies to untagged items, which are mailbox items that don't have a retention tag applied directly or by inheritance from the folder.
  :::column-end:::
  :::column:::
    Administrator
  :::column-end:::
  :::column:::
    Move to archive.
Delete and allow recovery.
Permanently delete.
  :::column-end:::
  :::column:::
    Users can't change DPTs applied to a mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Retention policy tag (RPT)
  :::column-end:::
  :::column:::
    Automatically to a default folder.

Default folders are folders created automatically in all mailboxes, for example: Inbox, Deleted Items, and Sent Items. See the list of supported default folders in [Default folders that support Retention Policy Tags](https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/default-folders?azure-portal=true).
  :::column-end:::
  :::column:::
    Administrator
  :::column-end:::
  :::column:::
    Delete and allow recovery.
Permanently delete.
  :::column-end:::
  :::column:::
    Users can't change the RPT applied to a default folder.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Personal tag
  :::column-end:::
  :::column:::
    Manually to items and folders.

Users can automate tagging by using Inbox rules to either move a message to a folder that has a particular tag or to apply a personal tag to the message.
  :::column-end:::
  :::column:::
    Users
  :::column-end:::
  :::column:::
    Move to archive.
Delete and allow recovery.
Permanently delete.
  :::column-end:::
  :::column:::
    Personal tags allow your users to determine how long an item should be retained. For example, the mailbox can have a DPT to delete items in seven years, but a user can create an exception for items such as newsletters and automated notifications by applying a personal tag to delete them in three days.
  :::column-end:::
:::row-end:::


### Applying personal retention tags<br>

Users can apply personal tags to folders they create or to individual items. Messages that have a personal tag applied are always processed based on the personal tag's settings. For example, a user can apply a personal tag to a message so that it's moved or deleted sooner or later than the settings specified in the default policy tags or retention policy tags applied to that user's mailbox. You can also create personal tags with retention disabled. This design enables users to tag items so they're never moved to an archive or they never expire.

Users can create personal tags that override both archive and retention policies.

 -  Users can apply archive policies to default folders, user-created folders or subfolders, and individual items.
 -  Users can apply a retention policy to user-created folders or subfolders and individual items (including subfolders and items in a default folder), but not to default folders.

Personal tags are available to Outlook and Outlook on the web users as part of their retention policy. In Outlook and Outlook on the web, personal tags with the **Move to Archive** action appear as Archive Policy, and personal tags with the **Delete and Allow Recovery** or **Permanently Delete** actions appear as Retention Policy, as shown in the following figure.

:::image type="content" source="../media/user-account-with-personal-tags-5269193e.png" alt-text="screenshot showing a user account with personal tags":::


:::image type="content" source="../media/outlook-with-assign-policy-menu-750c04f0.png" alt-text="screenshot of Outlook menus with Assign Policy option and retention policy drop-down menu":::


Users can also use Outlook on the web (under **Settings** &gt; **Your app settings** &gt; **Mail** &gt; **Retention policies**) to select other personal tags that aren't linked to their retention policy. The selected tags then become available in Outlook and Outlook on the web. To enable users to select other tags by using Outlook on the web, the **MyRetentionPolicies** role must be added to the user's role assignment policy. If users have permission to select other personal tags, all personal tags in an Exchange organization become available to them.

:::image type="content" source="../media/retention-policies-in-outlook-0116d4ff.png" alt-text="screenshot of retention policies in Outlook on the Web":::


**Additional reading.** For more information on retention policies, see [MyRetentionPolicies role](https://docs.microsoft.com/exchange/myretentionpolicies-role-exchange-2013-help?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”