These next two units examine the steps required to create a DLP policy that protects documents:

 -  Step 1 - Upload a document with the needed property to Microsoft 365.
 -  Step 2 - Create a managed property.
 -  Step 3 - Create the DLP Policy.

This unit examines the first two steps in this process.

### Step 1 - Upload a document with the needed property to Microsoft 365

The first step requires that you upload a document with the property that you want to reference in your DLP policy. Microsoft 365 will detect the property and automatically create a crawled property from it.

In the next step, you'll create a managed property and then map the managed property to this crawled property.

### Step 2 - Create a managed property in SharePoint Online

You're now ready to create a managed property in SharePoint Online. Once the property is created, you must then map it to the crawled property that was created in the previous step.

1.  Sign in to the Microsoft 365 admin center.
2.  In the left-hand navigation pane, select **Show all** and then under **Admin centers**, select **SharePoint**.
3.  In the **SharePoint admin center**, in the left-hand navigation, select **More features**.
4.  On the **More features** page, in the **Search** section, select **Open**.
5.  On the **Search** window, select **Manage Search Schema**. This option displays three tabs across the top of the **Search** page. The **Managed Properties** tab is displayed by default.
6.  On the **Managed Properties** page, select **New Managed Property**, which appears above the list of managed properties.
7.  Enter a name and description for the new property. This name will appear in your DLP policies.
8.  For **Type**, select **Text**.
9.  Under the **Main characteristics** section, select the **Queryable** and **Retrievable** checkboxes.
10. Scroll down to the bottom of the window and under the **Mappings to crawled properties** section, select **Add a mapping**.
11. In the **crawled property selection** window that appears, select the crawled property that corresponds to the Windows Server FCI property or other property that you plan to use in your DLP policy. Select **OK**.
12. At the bottom of the page, select **OK**.

The following graphic shows a file with a managed property being uploaded to SharePoint Online.

:::image type="content" source="../media/managed-property-uploaded-to-sharepoint-e81a4f49.jpg" alt-text="graphic shows a file with a managed property being uploaded to SharePoint Online.":::
