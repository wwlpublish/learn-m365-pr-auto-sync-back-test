The following tasks must be completed to configure in-place records management in SharePoint.

> [!NOTE]
> You must be a list contributor or an administrator to manually declare items as records.

### Task 1: Activate in-place records management at the site collection level

The first step in configuring an in-place records management system is to activate the feature at the site collection level. Activating the feature enables the **Declare/Undeclared Record** command on the ribbon.

> [!NOTE]
> Only Global administrators and Site Collection administrators can complete this task.

Complete the following steps to activate the in-place records management system at the site collection level:

1.  Sign in to Microsoft 365 using your administrator account credentials and navigate to the top level of the site that you want to configure (for example, https://\[tenant\_domain\]sharepoint.com/sites/\[sitename\]/").
2.  Go to **Site contents** and select **Site Settings**.
3.  Under **Site Collection Administration**, select **Site collection features**.
4.  Next to **In Place Records Management**, select **Activate**.

### Task 2: Configure record declaration settings at the site collection level

Complete the following steps to configure record declaration settings at the site collection level:

1.  At the top-most site level, select **Site contents**, and then select **Site settings**.
2.  Under **Site Collection Administration**, select **Record declaration settings**.
3.  On the **Record declaration settings** page, in the **Record Restrictions** section, select the option that specifies the kind of restrictions that will be placed on an item when it's declared a record. This setting doesn't affect items already declared as records.
    
     -  **No Additional Restrictions**. This restriction is useful if you want records to have a retention policy that's separate from active documents, but you don’t want to block the records from being deleted or edited.
     -  **No Additional Restrictions**. This restriction allows records to be edited but not deleted.
     -  **Block Edit and Delete**. This restriction is useful if you want to completely lock a document so that it can't be edited or deleted. A “padlock” icon is associated with the document to visually show that the item is locked. This option is the default setting.
4.  In the **Record Declaration Availability** section, select the option that specifies whether items can be manually declared as records in lists and libraries by default. If the "**Not available in all locations by default"** option is selected, items can be declared as records only through a policy or workflow.<br><br>This section also includes an option that lets you undeclare a record. To do so, in **Compliance Details**, next to **Record Status**, select **Undeclare Record**. You'll be prompted to confirm that you want to undeclare the item as a record.**<br>**
5.  In the **Declaration Roles** section, specify the types of users that can manually declare and undeclare records.
    
     -  **All list contributors and administrators.** Any user with the “edit items” permissions to a list can declare and undeclare items as records.
     -  **Only list administrators.** Only users with “manage list” permissions to a list can declare and undeclare items as records.
     -  **Only policy actions.** Only policy actions or custom code running as the System Account can declare and undeclare items as records.
6.  Select **OK**.

### Task 3: Configure record declaration settings at the list or library level

You can have more control over where items can be declared as records by configuring record declarations for a list or library. When configuring a list or library for record declaration, items can be automatically declared as records when they're added to the list or library.

Complete the following steps to configure record declaration settings at the list or library level:

1.  Go to the list or library that you want to configure for records management.
2.  For libraries, under **Library Tools**, select the **Library.** For lists, under **List Tools**, select the **List** tab.
3.  For libraries, select **Library Settings**; for lists, select **List Settings**.
4.  In the **Document Library/List Settings** page, under **Permissions and Management**, select **Record declaration settings**.
5.  In the **Manual Record Declaration Availability** section, complete one of the following options:
    
     -  Select whether you want to use the site collection default setting.
     -  Allow for the manual declaration of records for this list or library.
     -  Never allow for the manual declaration of records for this list or library.
6.  In the **Automatic Declaration** section, select the checkbox if you want all items that are added to the list or library to be automatically declared as records.
7.  Select **OK**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”