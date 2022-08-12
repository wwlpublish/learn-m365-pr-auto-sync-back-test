Azure Active Directory (Azure AD) enables organizations to bulk create new users, bulk delete existing users, and bulk restore deleted users. Bulk user operations require that you fill out a comma-separated values (CSV) template to download the selected users from the Azure AD portal.

> [!NOTE]
> To perform any of the bulk operations in the Azure AD admin center, you must be signed in as a Global administrator or User administrator.

### Create users in bulk

Bulk user operations require the use of a bulk user CSV template. The CSV template for bulk user creations is slightly different from the template used to bulk delete users, which is slightly different from the template used to bulk restore deleted users. Organizations should download and fill in the CSV template for the corresponding bulk operation.

The CSV template used to bulk create users should look like this example (older versions may vary):

:::image type="content" source="../media/create-template-example-a7c1d059.png" alt-text="Screenshot of a clipped version of the C S V template for bulk creating user accounts, with text boxes explaining the purpose of each row.":::


> [!WARNING]
> If you're adding only one entry using the CSV template, you must preserve row 3 and add your new entry to row 4. Ensure that you add the ".csv" file extension and remove any leading spaces before userPrincipalName, passwordProfile, and accountEnabled.

The rows in the downloaded CSV template to bulk create new users are as follows:

 -  **Version number**. The first row containing the version number must be included in the upload CSV.
 -  **Column headings**. The format of the column headings is **&lt;*Item name*&gt; \[PropertyName\] &lt;*Required or blank*&gt;**. For example, `Name [displayName] Required`. Some older versions of the template may have slight variations.
 -  **Examples row**. The template includes a row of examples of acceptable values for each column. You must remove the examples row and replace it with your own entries.

Organizations should keep in mind the following issues related to the bulk create CSV template:

 -  The first two rows of the upload template must not be removed or modified, or the upload can't be processed.
 -  The required columns are listed first.
 -  It isn't recommended that you add new columns to the template. Any other columns that are added are ignored and not processed.
 -  It's recommended that you download the latest version of the CSV template as often as possible.
 -  Verify there's no unintended whitespace before or after any field. For User principal name, having such whitespace would cause import failure.
 -  Verify that values in the **Initial password** comply with the currently active [password policy](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

Organizations should complete the following steps to bulk create users in Azure AD:

1. Sign in to your Azure AD admin center with an account that is either a Global administrator or User administrator.
1. In the **Azure AD admin center**, select **Users** &gt; **Bulk create**.
1. On the **Bulk create user** page, select **Download** to receive a valid comma-separated values (CSV) file of user properties, and then add users you want to create.
    
    :::image type="content" source="../media/upload-button-a5156563.png" alt-text="Screenshot of the Bulk create user pane showing the Download button highlighted to download the C S V template.":::
    
1. Open the CSV file and add a line for each user you want to create. The only required values are **Name**, **User principal name**, **Initial password**, and **Block sign in (Yes/No)**. Then save the file.
    
    :::image type="content" source="../media/add-csv-file-731f9ef9.png" alt-text="Screenshot of the C S V template file opened in Excel and displaying the first three rows and the users to bulk create.":::
    
1. On the **Bulk create user** page, under **Upload your CSV file**, browse to the file. When you select the file and then select **Submit**, validation of the CSV file starts.
1. After the file contents are validated, a **File uploaded successfully** message will appear. If there are errors, you must fix them before you can submit the job.
1. When your file passes validation, select **Submit** to start the Azure bulk operation that imports the new users.
1. When the import operation completes, you'll see a notification of the bulk operation job status.

If there are errors, you can download and view the results file on the **Bulk operation results** page. The file contains the reason for each error. The file submission must match the provided template and include the exact column names.

#### Check status of your bulk operations

An organization can check the status of all its pending bulk requests in the **Bulk operation results** page.

:::image type="content" source="../media/bulk-center-0e609961.png" alt-text="Screenshot of the Bulk operations results page that's used to check the status of bulk operations.":::


> [!WARNING]
> Each bulk activity to create users can run for up to one hour. This process enables bulk creation of at least 50,000 users.

#### Verify the users were created

An organization can then verify whether the users it created exist in the Azure AD organization. It can do so either in the Azure portal or by using PowerShell.

##### Verify users in the Azure portal

1. Sign in to the Azure AD admin center with an account that is either a Global administrator or User administrator.
1. In the **Azure AD admin center**, select **Azure Active Directory** in the navigation pane.
1. On the **Azure Active Directory** page, under the **Manage** section in the navigation pane, select **Users**.
1. On the **Users** page, under **Show**, select **All users** and verify the users you submitted to be bulk created are displayed in the list.

##### Verify users with PowerShell

To verify whether the users that were submitted were actually bulk created, run the following command:

```powershell
Get-AzureADUser -Filter "UserType eq 'Member'"
```

### Delete users in bulk

Just as you added users in bulk to Azure AD, so too can you delete users in bulk. And just as you used the CSV file to identify the users you wanted to add, so too will you use a CSV file to identify the users you want to delete.

The template used for bulk deletion is slightly different from the template used for bulk creation. Instead of having two columns, only one column is required, as shown in the following image.

:::image type="content" source="../media/delete-csv-file-ba931c43.png" alt-text="Screenshot of a clipped version of the C S V template for bulk deleting user accounts, with text boxes explaining the purpose of each row.":::


The rows in the downloaded CSV template to bulk deleted existing users are as follows:

 -  **Version number**. The first row containing the version number must be included in the upload CSV.
 -  **Column headings**. `User name [userPrincipalName] Required`. Older versions of the template may vary.
 -  **Examples row**. The template includes an example of an acceptable value. Example: `chris@contoso.com`. You must remove the example row and replace it with your own entries.

Organizations should keep in mind the following issues related to the bulk delete CSV template:

 -  The first two rows of the template must not be removed or modified, or the template can't be processed.
 -  The required columns are listed first.
 -  It isn't recommended that you add new columns to the template. Any other columns that are added are ignored and not processed.
 -  It's recommended that you download the latest version of the CSV template as often as possible.

Organizations should complete the following steps to bulk delete users in Azure AD:

1. Sign in to your Azure AD organization with an account that is either a Global administrator or a User administrator.
1. In the **Azure AD admin center**, select **Users** &gt; **Bulk operations** &gt; **Bulk delete**.
1. On the **Bulk delete user** page, select **Download** to download the latest version of the CSV template.
1. Open the CSV file and add a line for each user you want to delete. The only required value is **User principal name**. Save the file.
1. On the **Bulk delete user** page, under **Upload your csv file**, browse to the file. When you select the file and select **Submit**, validation of the CSV file starts.
1. After the file contents are validated, a **File uploaded successfully** message will appear. If there are errors, you must fix them before you can submit the job.
1. When your file passes validation, select **Submit** to start the Azure bulk operation that deletes the users.
1. When the deletion operation completes, you'll see a notification that the bulk operation succeeded.

If there are errors, you can download and view the results file on the **Bulk operation results** page. The file contains the reason for each error.

You can see the status of all of your pending bulk requests in the **Bulk operation results** page.

### Restore users in bulk

Just as you deleted users in bulk from Azure AD, so too can you restore deleted users in bulk. And just as you used the CSV file to identify the users you wanted to delete, so too will you use a CSV file to identify the users you want to restore.

The template used for bulk restore is slightly different from the template used for bulk deletion. Instead of specifying each user's UPN, you'll instead specify the user's object ID.

:::image type="content" source="../media/restore-template-e0185687.png" alt-text="Screenshot of a clipped version of the C S V template for bulk restoring user accounts, with text boxes explaining the purpose of each row.":::


The rows in the downloaded CSV template to bulk restore deleted users are as follows:

 -  **Version number**. The first row containing the version number must be included in the upload CSV.
 -  **Column headings**. The format of the column headings is **&lt;*Item name*&gt; \[PropertyName\] &lt;*Required or blank*&gt;**. For example, `Object ID [objectId] Required`. Some older versions of the template might have slight variations.
 -  **Examples row**. The template includes an example of an acceptable value. You must remove the example row and replace it with your own entries.

Organizations should keep in mind the following issues related to the bulk delete CSV template:

 -  The first two rows of the upload template must not be removed or modified, or the upload can't be processed.
 -  The required columns are listed first.
 -  It isn't recommended that you add new columns to the template. Any other columns that are added are ignored and not processed.
 -  It's recommended that you download the latest version of the CSV template as often as possible.

Organizations should complete the following steps to bulk restore users in Azure AD:

1. Sign in to your Azure AD organization with an account that is either a Global administrator or a User administrator.
1. In the **Azure AD admin center**, select **Users** &gt; **Deleted**.
1. On the **Deleted user** page, select **Bulk restore** to download the latest version of the CSV template.
1. Open the CSV file and add a line for each user you want to restore. The only required value is **ObjectID**. Save the file.
1. On the **Bulk restore** page, under **Upload your csv file**, browse to the file. When you select the file and select **Submit**, validation of the CSV file starts.
1. After the file contents are validated, a **File uploaded successfully** message will appear. If there are errors, you must fix them before you can submit the job.
1. When your file passes validation, select **Submit** to start the Azure bulk operation that restores the deleted users.
1. When the restore operation completes, you'll see a notification that the bulk operation succeeded.

If there are errors, you can download and view the results file on the **Bulk operation results** page. The file contains the reason for each error.

You can see the status of all of your pending bulk requests in the **Bulk operation results** page.
