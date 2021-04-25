SharePoint Online has several options to maintain and recover content that's either been deleted or misplaced in the intranet. One common way to recover deleted content is through the Recycle Bin. There are two types of Recycle Bins:

 *  **Local recycle bin.** This bin is located on the left-hand side of the site on the Quick Launch bar. This bin is used to recover recently deleted items that are local to this site.
 *  **Site collection recycle bin.** Items in this bin have been removed from the local recycle bin. This bin is a repository of all deleted items from the child and parent site that belongs to the site collection.

:::image type="content" source="../media/deleted-data-in-recycle-bins-9b90632c.jpg" alt-text="graphic showing how deleted data flows from the local recycle bin to the site collection recycle bin and is then permanently deleted":::


Versioning is another way to manage sites, libraries, folders, and files. When versioning is enabled in your SharePoint list or library, you can store, track, and restore items in a list and files in a library whenever they change. Versioning, combined with other settings, such as checkout, gives you significant control of the content that is posted on your site and can provide real value if you ever have a need to look at or restore an old version of an item or file.

You can use versioning to:

 *  **Track history of a version.** When versioning is enabled, you can see when an item or file was changed and who changed it. You can also see when properties (information about the file) were changed. For example, if someone changes the due date of a list item, that information appears in the version history. You can also see the comments people make when they check files into libraries.
 *  **Restore a previous version.** You can replace the current version of an item or file with a previous one if you made a mistake in the current version, if the current version is corrupt, or if you simply like a previous version better. When restoring a previous version, the restored version becomes the new current version.
 *  **View a previous version.** You can view a previous version without overwriting your current version. If you are viewing version history within a Microsoft Office document, such as a Word or Excel file, you can compare the two versions to identify the differences.

**Additional reading.** For more information, see [how versioning works in a SharePoint list or library](https://support.office.com/article/How-does-versioning-work-in-a-SharePoint-list-or-library-0F6CD105-974F-44A4-AADB-43AC5BDFD247?azure-portal=true).

### Point-in-time recovery

Point-in-time recovery is a last resort when trying to restore an item. This option requires that you submit a request to Microsoft Technical Support to have Microsoft recover the item.

The request must include the following information:

 *  Date and time at which you want the site collection restored to.
 *  The full URL that you want restored.
 *  An email or letter in which you request a Point-in-time Recovery and accept the Terms regarding this request.

The submission must not exceed 14 days after the time you want recovered. For example, if a user deletes a site on the 10th and you submit the Point-in-time Recovery on the 25th, then the request will be rejected because it has been more than 14 days since the item was deleted.

Once the request has been submitted, it can take up to 72 hours to complete. It's highly recommended that you back up any documents that are currently being worked on. Because of the restore process, items may not be there since the site collection was restored back to a previous date. All versions in the site collection will also be removed.
