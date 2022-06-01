SharePoint Online uses two recycle bins:

 -  **Site recycle bin**. In SharePoint Online, items are retained for 93 days from the time you delete them from their original location. They stay in the Site recycle bin the entire time, unless someone deletes them from there or empties that recycle bin.
 -  **Site Collection recycle bin**. If an item is deleted from the Site recycle bin or someone empties that bin, the items go to the Site Collection recycle bin. The items then stay in the Site Collection recycle bin for the remainder of the 93 days.

> [!NOTE]
> The recycle bin retention time isn't configurable in SharePoint Online.

When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them. This content can include:

 -  Documents and document libraries.
 -  Lists and list data.
 -  Site configuration settings.
 -  Role and security information that's related to the site or its subsites.
 -  Subsites of the top-level website, their contents, and user information.

If you accidentally delete a site collection, it can be restored by a global admin or SharePoint admin using the SharePoint admin center.

Deleted site collections are retained for 93 days. After 93 days, sites and all their content and settings are permanently deleted. The content includes lists, libraries, pages, and any subsites.

Hard deletion occurs when:

 -  A user purges deleted items from the Site Collection recycle bin.
 -  The retention and backup periods expire.
 -  An administrator permanently deletes a site collection using the **Remove-SPODeletedSite** cmdlet.

### Restore deleted items from the Site recycle bin

When you delete items from a document library or list in Microsoft Teams or SharePoint Online, they aren't immediately removed. Deleted items go into the Site recycle bin for a period of time or until they're emptied from the recycle bin. The Site recycle bin isn't the same as the Windows recycle bin that you see on your desktop.

While deleted items are in the Site recycle bin, you can restore them to their original location. If you're using SharePoint Online in Microsoft 365, you can even view and restore items that were deleted by someone else, as long as you have edit permissions.

You can restore items that you delete and items other people delete (as long as you have edit permissions). Complete the following steps to restore deleted items from the Site recycle bin:

1.  Go to the SharePoint site where the items were deleted from. (In Microsoft Teams, from the **Files** tab at the top of your channel, select **More &gt; Open in SharePoint**.)
2.  In the **Quick Launch** navigation bar on the bottom left of the screen, select **Recycle bin**.
    
    If you don't see the **Recycle bin** on the **Quick Launch** bar, follow these steps:
    
    
     -  Select **Settings** (the gear icon in the upper right corner of the screen), and then select **Site contents**.
     -  The recycle bin is in the top right portion of the **Site Contents** page.
        
        :::image type="content" source="../media/recycle-bin-on-site-contents-page-1c5bfb3f.png" alt-text="Screenshot of the SharePoint Online Site Contents page showing the Recycle button.":::
        
3.  On the **Recycle bin** page, select the box to the left of the items or files you want to restore, and then select **Restore** on the menu bar.
    
    :::image type="content" source="../media/recycle-bin-page-with-selected-items-and-restore-51fc8e86.png" alt-text="Screenshot of the Recycle bin page with items selected and the Restore button on the menu bar.":::
    

> [!TIP]
> If you don’t see the item you’re looking for, check to see if it was deleted recently. If so, a site collection administrator may be able to restore it from the Site Collection recycle bin. If you're the site collection administrator, see [Restore deleted items from the site collection recycle bin](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b?azure-portal=true).

When an item is restored, it's restored to the same location that it was deleted from.

Deleted items are retained in recycle bins for a certain period of time. For SharePoint, the retention time is 93 days. It begins when you delete the item from its original location. When you delete the item from the site recycle bin, it goes into the site collection recycle bin. It stays there for the remainder of the 93 days, and then it's permanently deleted.

You can restore a list, list item, library, file, or a version of a file to its original location, as long as you haven't already deleted its parent. For example, you can't restore a version of a file if the file itself has been deleted. The reason for this restriction is that when you delete a file, you delete all versions of the file. Similarly, you can't restore a file if the library to which it belonged has been deleted. You must first restore the library and then restore the file to the library.

When you restore a library, all the files the library contained are also restored. Also, when you restore an item that was originally located in a deleted folder:

 -  The folder is recreated in its original location.
 -  The item is then restored in the recreated folder.

> [!CAUTION]
> When you restore an item that was originally located in a deleted folder, the entire contents of the folder isn't restored. If a file or folder already exists at the original path, the item will be restored with a number appended at the end of the file name.

### Restore deleted items from the Site Collection recycle bin

When you delete items (including OneDrive files) from a SharePoint site, they're sent to the Site recycle bin (also called the first-stage recycle bin). From this Site recycle bin, you can restore them if needed. When you delete items from a Site recycle bin, they're sent to the Site Collection recycle bin (also called the second-stage recycle bin).

A SharePoint site collection administrator can view and restore deleted items from the Site Collection recycle bin to their original locations. An item will be permanently deleted in either of the following scenarios:

 -  The item is deleted from the Site Collection recycle bin.
 -  The item exceeds the retention time in the Site Collection recycle bin.

> [!IMPORTANT]
> The Site Collection recycle bin is different from the recycle bin in Windows. If you delete files or folders that you're syncing, you can restore them from the Windows recycle bin on your PC.

Keep in mind the following considerations when restoring items from the Site Collection recycle bin:

 -  **Securable objects bring all their content back with them.** When you restore any securable object (any object to which access can be controlled), it's restored with all the objects that it contained when it was deleted. For example, if you restore a list, library, folder, or Document Set, the restored version contains all the documents and other items that it contained when it was deleted. If you restore a file or other item that has multiple versions, the restored file or item includes all the versions it contained when it was deleted.
 -  **Most objects can’t be restored if their container objects aren’t present**. If you delete an object and then delete the object that contained it, you must restore the container before you can restore the object. For example, if you delete a file and then delete the library in which it was stored, you must restore the library before you can restore the file. If you delete an earlier version of a file and then delete the current version of the file itself, you must restore the file itself before you can restore the earlier version.
 -  **Exception: An object deleted from a folder can be restored without first restoring the folder**. Let's assume the folder is automatically re-created in its former location. However, it now contains only the object that you restored. Alternatively, you can also restore the folder manually from the recycle bin, in which case it’s restored with all the contents that it had when it was deleted.

Complete the following steps to restore an item from SharePoint Online's Site Collection recycle bin:

1.  On modern team sites and classic sites (subsites), in the navigation pane, select **Recycle bin**.
    
    :::image type="content" source="../media/classic-sharepoint-sites-page-with-recycle-bin-fed1abd6.jpg" alt-text="Screenshot of the navigation pane on the modern teams sites page and the Recycle bin option highlighted.":::
    
2.  On modern communication sites, select **Site contents**, and then select **Recycle bin** in the top navigation bar. If you don't see the Recycle Bin, follow these steps:
    1.  Select **Settings** (the gear icon in the upper right corner of the screen) and then select **Site settings**. If you don't see **Site settings**, select **Site information** and then select **View all site settings**. Some pages may require you to select **Site contents** and then **Site settings**.
    2.  On **Site settings**, under **Site Collection Administration**, select **Recycle bin**.
        
        :::image type="content" source="../media/site-collection-administration-window-with-recycle-bin-be5c0779.png" alt-text="Screenshot of the site settings page with the recycle bin option under the site collection administration section.":::
        
3.  At the bottom of the **Recycle Bin** page, select the **Second-stage recycle bin** link.
    
    :::image type="content" source="../media/recycle-bin-page-with-second-stage-recycle-bin-link-eac17358.png" alt-text="Screenshot of the recycle bin page with the second stage recycle bin link highlighted.":::
    
    
    > [!NOTE]
    > You need administrator or owner permissions to use the Site Collection recycle bin. If you don't see it, it may have been disabled or you don't have permission to access it.
4.  Point to the items you want to restore, select the check icon to the right of each one, and then select **Restore**.
    
    > [!NOTE]
    > If you restore an item that was originally located in a deleted folder, the folder is recreated in its original location. The item is then restored in that folder.

### Restore an entire site collection

If you're a global admin or SharePoint admin in Microsoft 365, you can also restore entire site collections from the Site Collection recycle bin. For info, see [Restore a deleted site collection](/sharepoint/restore-deleted-site-collection?azure-portal=true).

### How long are deleted items kept in the Recycle Bin?

In SharePoint Online, items are retained for 93 days from the time you delete them from their original location. They stay in the Site recycle bin the entire time, unless someone deletes them from there or empties that recycle bin. In that case, the items go to the Site Collection recycle bin, where they stay for the remainder of the 93 days - unless:

 -  The Site Collection recycle bin exceeds its quota and starts purging the oldest items.
 -  The items are manually deleted by the site collection administrator from the Site Collection recycle bin.

The Site recycle bin storage counts against your site collection storage quota and the [List View Threshold](https://support.microsoft.com/office/manage-large-lists-and-libraries-b8588dae-9387-48c2-9248-c24122f07c59?azure-portal=true). The amount of space allocated to the Site Collection recycle bin is 200% of the site collection quota. These values aren't configurable.

SharePoint Online retains backups of all content for 14 more days beyond the actual deletion date. If content can't be restored through ﻿the recycle bin or [Files Restore](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15?azure-portal=true), an administrator ﻿can contact Microsoft Support to request it restore the content anytime inside the 14 day window.
