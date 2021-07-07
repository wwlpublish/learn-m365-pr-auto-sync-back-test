## PST file import

Some customers have a significant amount of email stored in PST files that needs to be governed. You can use the import service to bulk-import PST files to Exchange Online mailboxes in your Office 365 organization. You can then use retention policies to control how long mailbox content is retained and delete content after the retention period expires.

There are two ways you can import PST files to Office 365: network upload and drive shipping.

### Network upload

You upload the PST files over the network to a temporary Azure Storage location in the Microsoft cloud. Then you use the Office 365 Import service to import the PST data to Exchange Online mailboxes.

### Drive shipping

You copy the PST files to a BitLocker-encrypted hard drive and send the drive to Microsoft. When Microsoft receives the hard drive, and data center personnel upload the data to a temporary Azure Storage location in the Microsoft cloud. Then you use the Office 365 Import service to import the data to Exchange Online mailboxes.

## Import third party data

Administrators can import and archive third-party data from social media platforms, instant messaging platforms, and document collaboration platforms, to Exchange Online mailboxes. After it is imported, you can apply Microsoft 365 compliance features, including retention policies to the data. Examples of third-party data sources that you can import to Microsoft 365 include the following:

- **Social**. Facebook business pages (preview), LinkedIn company pages, Twitter (preview)
- **Instant messaging**. Yahoo Messenger and GoogleTalk
- **Document collaboration**. Box and DropBox
- **Vertical industries**. Customer Relationship Management (such as Salesforce Chatter) and Financial Services (such as Bloomberg and Thomson Reuters)
- **SMS/text messaging**. BlackBerry

Microsoft provides several data connectors in the Microsoft 365 compliance center for Facebook, Twitter, LinkedIn, Instant Bloomberg and HR data. You can also work with a Microsoft partner if you have a requirement to import data from these, or other sources.

## Learn more

- [Overview of importing your organizations PST files to Office 365](/microsoft-365/compliance/importing-pst-files-to-office-365?azure-portal=true)
- [Overview of archiving third-party data](/microsoft-365/compliance/archiving-third-party-data?azure-portal=true)
