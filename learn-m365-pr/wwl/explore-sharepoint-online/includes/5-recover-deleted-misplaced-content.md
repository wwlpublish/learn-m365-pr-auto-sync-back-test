Organizations can use the following options to maintain and recover SharePoint Online content that's either been deleted or misplaced in the intranet:

 -  Recycle bins
 -  Versioning
 -  Point-in-time recovery

### Recycle bins

Recycle bins provide a common way to recover deleted content. There are two types of Recycle bins:

 -  **Local recycle bin.** This bin is located on the left-hand side of the site on the Quick Launch bar. This bin is used to recover recently deleted items that are local to this site.
 -  **Site collection recycle bin.** Items in this bin have been removed from the local recycle bin. This bin is a repository of all deleted items from the child and parent site that belongs to the site collection.

    > [!NOTE]
    > Items are automatically purged from the Site Collection Recycle Bin after 93 days. The time at which 93 days begin is from the time an item is placed in the Local Recycle Bin.

:::image type="content" source="../media/deleted-data-in-recycle-bins-9b90632c.jpg" alt-text="graphic showing how deleted data flows from the local recycle bin to the site collection recycle bin and is then permanently deleted":::


### Versioning

Versioning is another way to manage sites, libraries, folders, and files. When versioning is enabled in a SharePoint list or library, an organization can store, track, and restore items in a list and files in a library whenever they change. Versioning, combined with other settings such as checkout, provides an organization with significant control of the content that's posted on its site. It also provides real value if an organization must view or restore an old version of an item or file.

Versioning can be used to:

 -  **Track history of a version.** When versioning is enabled, an organization can see when an item or file was changed and who changed it. It can also see when properties (information about the file) were changed. For example, if someone changes the due date of a list item, that information appears in the version history. Comments people make when they check files into libraries can also be viewed.
 -  **Restore a previous version.** The current version of an item or file can be replaced with a previous one if a mistake was made in the current version, if the current version is corrupt, or a previous version is preferred over the current version. When restoring a previous version, the restored version becomes the new current version.
 -  **View a previous version.** A previous version can be viewed without overwriting the current version. When viewing version history within a Microsoft Office document, such as a Word or Excel file, a user can compare the two versions to identify the differences.

**Additional reading.** For more information, see [how versioning works in a SharePoint list or library](https://support.office.com/article/How-does-versioning-work-in-a-SharePoint-list-or-library-0F6CD105-974F-44A4-AADB-43AC5BDFD247?azure-portal=true).

### Point-in-time recovery

Point-in-time recovery is a last resort when trying to restore an item. With this option, an organization must submit a request to Microsoft Technical Support to have Microsoft recover the item.

The request must include the following information:

 -  Date and time the organization wants the site collection restored to.
 -  The full URL the organization wants to restore.
 -  An email or letter in which the organization requests a Point-in-time Recovery and accepts the Terms for this request.

The submission must not exceed 14 days after the time that must be recovered. For example, if a user deletes a site on the 10th and the organization submits the Point-in-time Recovery on the 25th, then the request will be rejected because it has been more than 14 days since the item was deleted.

Once the request has been submitted, it can take up to 72 hours to complete. It's highly recommended that organizations should back up any documents that are currently being worked on. Because of the restore process, items may not be there once a site collection is restored back to a previous date. All versions in the site collection will also be removed.
