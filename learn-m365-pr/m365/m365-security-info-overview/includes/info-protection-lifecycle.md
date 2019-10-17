Let’s look at the journey of a file and discuss how Microsoft technologies can help protect the data within that file.

![Microsoft technologies protect a file from creation through editing and cloud storage.](../media/story-of-file.png)

**File is created**

- Regardless of where the file is created, the Azure Information Protection (AIP) client can enforce information protection based on the labels attached to the data.

**User edits the file**

- If users open and edit the file in Office, Windows Information Protection helps protect the data according to the labels applied.

**User shares the file with another user in the organization**

- If users share the data through Office 365, Data Loss Prevention (DLP) policies ensure that users handle the labeled data appropriately and according to policy.

**User opens the file on their phone**

- If a user receives and opens the data on a mobile device, Intune enforces protection of the data.

**User uploads the file to another cloud service such as Dropbox**

- If a user uploads the data to other clouds for external sharing, services such as Microsoft Cloud App Security can apply policies based on the data’s labels.
