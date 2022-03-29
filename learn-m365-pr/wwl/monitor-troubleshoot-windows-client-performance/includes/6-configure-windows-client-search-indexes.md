Indexing is a technology used by Windows search. As the name implies, it is an index, a local database. Windows uses this index to keep track of files, folders, file types, data properties, and other details about files so that you can search by those details to locate data more easily. Generally when you search for a file, Windows accesses this index first. It is important to personalize the settings for indexing to meet your needs. You want to make sure the service is indexing all of the areas of your computer that you use and it does not index unnecessary areas.

:::image type="content" source="../media/configure-index-855e09c1.jpg" alt-text="Screenshot of the Indexing Options screen":::


### Contents of the Windows Search Index

One index is maintained per computer so shared data stored on local drives is indexed only once. In addition, each user’s data is distinguishable by a unique user security identifier \{SID\}, so users have access only to their own content. System administrators can use Group Policy to prevent specific paths or file types from being indexed.

Windows Search indexes information as follows:

 -  By default, Windows Search indexes each user’s e-mail and Documents and Settings folders (users can add custom locations like network shares). Indexing of shared folders can be turned off with Group Policy.
 -  Windows Search does not index password-protected Office files.
 -  Windows Search indexes e-mail and attachments in a secure environment. Indexing of attachments can be turned off with Group Policy.
 -  The Windows Search index is updated automatically in the background when data is added, deleted, and modified.

### Index Encrypted Files

Windows Search 4.0 and higher fully supports indexing encrypted files on local file systems, enabling users to index and search the properties and contents of encrypted files. Users can manually configure Windows Search to include encrypted files, or administrators can configure this with Group Policy. Windows Search ensures that only users with the correct permissions can search the content of encrypted files by honoring ACLs and by restricting access to users with decryption permissions for the files. Additionally, Windows Search restricts access to encrypted files to local searches only; Windows Search does not return encrypted files in search results when the query is initiated remotely.

> [!NOTE]
> The indexing of encrypted files should not be enabled unless the search index itself is protected with full volume encryption. While encrypting the index file with EFS is possible, it is not recommended.
