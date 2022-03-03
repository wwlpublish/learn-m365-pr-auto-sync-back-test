File storage is part of so many applications. It's a much better experience for users if they can access the files directly where they're working. For Microsoft 365 users, those files are in OneDrive for Business and SharePoint. Now you've built an app that can enumerate, download, and upload these files.

You also learned about the Microsoft Authentication Library and how to implement the dynamic consent pattern in your application. You could have chosen to request all the permissions at the beginning. That's up to you as the application developer to decide.

You also saw the power of the Microsoft Graph SDK, which made it easy to set up a session for uploading large files in only a few lines of code.

Check out the other modules in this series to learn how to do even more with Microsoft Graph.

## Graph calls used in this module

- [Microsoft Graph API reference](/graph/api/overview?WT.mc_id=m365-0000016105-cxa)
- [List children of a drive item](/graph/api/driveitem-list-children?WT.mc_id=m365-0000016105-cxa)
- [Get a drive item](/graph/api/driveitem-get?WT.mc_id=m365-0000016105-cxa)
- [Upload a file <4 MB (single request)](/graph/api/driveitem-put-content?WT.mc_id=m365-0000016105-cxa)
- [Upload a file >4 MB (upload session)](/graph/api/driveitem-createuploadsession?WT.mc_id=m365-0000016105-cxa)
- [Upload a file >4 MB (with Microsoft Graph SDK)](/graph/sdks/large-file-upload?WT.mc_id=m365-0000016105-cxa)
