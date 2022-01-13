You can use the PST Import tool in the Microsoft 365 compliance center to bulk-import PST files to Exchange Online mailboxes in your Microsoft 365 organization. You can also use the Import tool to bulk-import documents and other data from your on-premises SharePoint Server organization to SharePoint Online and OneDrive for Business sites.

To import the data to Microsoft 365, the Import tool provides the following transfer options:

 -  **Network upload**. You can upload your PST files to the Import service using your existing Internet connection.
 -  **Drive shipping**. You can store your PST files on an encrypted hard drive and physically ship the drive to Microsoft. This option saves you from having to transfer the data over the Internet using the Network Upload option. This option is especially useful if you have many PST files, or the files are large in size, either of which could cause a network upload to take many days or weeks to complete.

You should consider the following requirements when exporting your PST files and uploading them to Microsoft 365:

 -  To access the **Microsoft 365 import** page and view import jobs in the Microsoft 365 compliance center, you must either be a member of the Global Administrators role in your Microsoft 365 tenant, or a member of the Mail Recipients role in Exchange Online.
 -  To create import jobs for a mailbox, your account must be assigned to the Mailbox Import Export role in Exchange Online.

    > [!WARNING]
    > By default, this role isn't assigned to any role group in Exchange Online.

 -  Your exported PST files must be located on a file server or shared folder within your on-premises environment.
 -  In Exchange hybrid deployments, you can outsource PST file data to Exchange Online archive mailboxes that have already been migrated or were newly created. On-premises mailboxes can access the imported data within the Exchange Online archive mailbox.
 -  You can also import PST files to inactive mailboxes in Exchange Online. The only requirement is that you must identify the GUID of the inactive mailbox to which the data will be imported.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.