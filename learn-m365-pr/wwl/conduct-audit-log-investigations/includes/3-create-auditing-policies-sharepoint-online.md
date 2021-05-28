Microsoft 365 auditing policies enable organizations to log events, such as viewing, editing, and deleting content like email messages, documents, task lists, issues lists, discussion groups, and calendars. When auditing is enabled as part of an information management policy in SharePoint Online, you can view reports on audit data and summaries of current usage. You can also use these reports to determine how information is used within the organization, to manage compliance, and investigate areas of concern.

The Auditing policy feature available in SharePoint Online logs events and operations that are completed on documents and list items. Auditing can be configured to log events, such as:

 -  Editing a document or item
 -  Viewing a document or item
 -  Checking a document in or out
 -  Changing the permissions for a document or item
 -  Deleting a document or item

### Create a policy for multiple content types within a site collection

To ensure that an information policy is applied to all documents of a certain type within a site collection, consider creating the policy at the site collection level and then later applying the policy to content types. These types of policies are referred to as site collection policies. To create a policy for multiple content types, you must first activate the **Site Policy** feature for the site collection.

1.  On the site collection home page, select the **gear (Settings)** icon on the top right of the screen.
2.  In the **Settings** drop-down menu that appears, select **Site Contents.**
3.  On the site collection page, the **Site contents** tab is selected from the list of tabs that appear at the top of the page. On the right-side of the menu bar, select **Site settings.** 
4.  On the **Site Settings** page, under the **Site Collection Administration** group, select **Site collection features**.
5.  On the **Site Settings&gt;Site Collection Features** page, scroll down to **Site Policy** and select its **Activate** button.
6.  Scroll back to the top of the **Site Settings&gt;Site Collection Features** page and select **Site Settings** in the heading.
7.  On the **Site Settings** page, under the **Site Collection Administration** group, **Content Type Policy Templates** appears in the list now that you have activated **Site Policy** on the **Site Collection Features** page. Select **Content Type Policy Templates.**
8.  On the **Policies** page, select **Create**.
9.  On the **Policies&gt;Edit Policy** page, enter a **Name** and optional **Administrative Description** for the policy, and then enter a brief **Policy Statement** that explains to users what the policy is for.
10. To enable auditing for the documents and items that are subject to this policy, select the **Enable Auditing** check box and then specify the events you want to audit.
11. Select **OK** to apply the auditing feature to the policy.

### Create a policy for a site content type

Adding an information management policy to a content type makes it easy to associate policy features with multiple lists or libraries. You can:

 -  add an existing information management policy to a content type.
 -  create a unique policy specific to an individual content type.
 -  add an information management policy to a content type that's specific to lists. By doing so, you're basically applying the policy only to items in that list that are using the content type.

Complete the following steps to create a policy for a site content type:

1.  On the site collection home page, select the **gear (Settings)** icon on the top right of the screen.
2.  In the **Settings** drop-down menu that appears, select **Site Contents.**
3.  On the site collection page, the **Site contents** tab is selected from the list of tabs that appear at the top of the page. On the right-side of the menu bar, select **Site settings.** 
4.  On the **Site Settings** page, under the **Web Designer Galleries** group, select **Site content types**.
5.  On the **Site Settings&gt;Site Content Types** page, select the content type that you want to add a policy to.
6.  On the **Site Content Types&gt;Site Content Type** page, under **Settings**, select **Information management policy settings.**
7.  On the **Site Content Types&gt;Edit Policy** page, enter a **Name** and optional **Administrative Description** for the policy, and then enter a brief **Policy Statement** that explains to users what the policy is for.
8.  To enable auditing for the documents and items that are subject to this policy, select the **Enable Auditing** check box and then specify the events you want to audit.
9.  Select **OK** to apply the auditing feature to the policy.
