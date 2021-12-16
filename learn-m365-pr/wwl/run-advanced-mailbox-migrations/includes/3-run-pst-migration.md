The steps involved in importing a PST file using the PST Import tool in the Microsoft 365 compliance center are illustrated in the following diagram. The Messaging administrator should follow the steps defined in the PST import workflow (the center column in the diagram).

> [!NOTE]
> Some portions of the process will vary depending on whether the Network upload or Drive shipping option is selected.

:::image type="content" source="../media/pst-import-workflow-bedfcf72.png" alt-text="Diagram showing the steps involved in importing a PST file using the Import service in the Security and Compliance Center":::


The following list describes the steps defined in the diagram in greater detail:

1.  **Download the PST import tool and key to a private Azure storage location.** The first step is to download the tool and access key used to upload the PST files or copy them to a hard drive. The access key is unique to your organization and provides you (or Microsoft data center personnel if you use drive shipping) with the necessary permissions to upload PST files to a private and secure Azure storage location.
2.  **Upload or copy the PST files.** The appropriate tool must be used to upload or copy the PST files:
    
     -  **Network upload.** The **AzCopy.exe** tool is used to upload and store your PST files in a private Azure storage location in the Microsoft cloud.
     -  **Drive shipping.** The **WAImportExport.exe** tool is used to copy your PST files to the hard drive. This tool encrypts the hard drive with BitLocker and then copies the PST files to the hard drive.
3.  **Create a PST import-mapping file.** A comma-separated value (CSV) file must be created that specifies which user mailboxes the PST files will be imported to.
4.  **Create a PST import job.** You’re now ready to create a PST import job on the **Import** page in the Microsoft 365 compliance center and submit the PST import-mapping file.
    
     -  **Network upload**. Because the PST files have been uploaded to Azure, Microsoft 365 analyzes the data in the PST files and then gives you an opportunity to set filters that control what data gets imported to the mailboxes specified in the PST import-mapping file.
     -  **Drive shipping**. When shipping a physical hard drive to Microsoft, the following steps are involved:
        
        1.  You physically ship the hard drive to a Microsoft data center.
        2.  When Microsoft receives the hard drive, data center personnel will upload the PSTs files on the hard drive to the Azure storage location for your organization. The PST files on the hard drive are uploaded to Azure within 7 to 10 business days after Microsoft receives the hard drive.
        3.  Microsoft ships the hard drive back to you.
5.  **Filter the PST data that will be imported to mailboxes.** After the import job is created, Microsoft 365 analyzes the data in the PST files by identifying the age of the items and the different message types included in the PST files. You can then decide if you want to import all data or just the messages that fall within a specific date range.
6.  **Start the PST import job.** After the import job begins, Microsoft 365 uses the information in the PST import-mapping file to import the PSTs files from the Azure storage location to the user mailboxes.

**Additional reading.** For more information, see [Overview of importing your organization PST files to Microsoft 365](/microsoft-365/compliance/importing-pst-files-to-office-365?azure-portal=true).
