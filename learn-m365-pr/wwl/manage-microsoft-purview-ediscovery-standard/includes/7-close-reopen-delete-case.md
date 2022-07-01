This unit examines how to close, reopen, and delete Microsoft Purview eDiscovery (Standard) cases in Microsoft 365.

### Close a case

When the legal case or investigation supported by an eDiscovery (Standard) case is completed, you can close the case. Here's what happens when you close a case:

 -  **If the case contains any eDiscovery holds, they'll be turned off**. After the hold is turned off, a 30-day grace period (called a **delay hold**) is applied to content locations that were on hold. This delay helps prevent content from being immediately deleted. It also provides administrators the opportunity to search for and restore content before it may be permanently deleted after the delay hold period expires. For more information, see [Removing content locations from an eDiscovery hold](/microsoft-365/compliance/create-ediscovery-holds?azure-portal=true).
 -  **Closing a case only turns off the holds that are associated with that case**. Other holds placed on a content location will still be maintained. For example, a Litigation Hold, a retention policy, or a hold from a different eDiscovery (Standard) case.
 -  **The case is still listed on the eDiscovery (Standard) page in the Microsoft Purview compliance portal**. The details, holds, searches, and members of a closed case are retained.
 -  **You can edit a case after it's closed**. Once a case is closed, you can still add or remove members, create searches, and export search results. The primary difference between active and closed cases is that eDiscovery holds are turned off when a case is closed.

An organization should perform the following steps to close a case:

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane to expand the group. Under the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to close.
3.  On the case's detail page, on the **Home** tab, select **Close case**, which appears under the **Status** section.
    
    > [!NOTE]
    > A warning is displayed indicating the holds associated with the case will be turned off.
    
    :::image type="content" source="../media/ediscovery-case-home-page-ae8f18fd.png" alt-text="Screenshot of case's Home tab showing the Close case option highlighted.":::
    
4.  Select **Yes** to close the case. The status of the case on its **Home** tab is changed from **Active** to **Closing**.
5.  On the **eDiscovery (Standard)** page, select **Refresh** to update the status of the closed case.
    
    > [!NOTE]
    > It may take up to 60 minutes for the closing process to complete. When the process is complete, the status of the case is changed to **Closed** on the **eDiscovery (Standard)** page.

### Reopen a closed case

An organization should perform the following steps to reopen a closed a case:

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane to expand the group. Under the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to reopen.
3.  On the case's detail page, on the **Home** tab, select **Reopen case**, which appears under the **Status** section.
    
    > [!NOTE]
    > A warning is displayed indicating the holds that were associated with the case when it was closed won't be turned on automatically.
    
    :::image type="content" source="../media/ediscovery-case-home-page-reopen-8a096adb.png" alt-text="Screenshot of case's Home tab showing the Reopen case option highlighted.":::
    
4.  Select **Yes** to reopen the case. The status of the case on its **Home** tab is changed from **Closed** to **Active**.
5.  On the **eDiscovery (Standard)** page, select **Refresh** to update the status of the reopened case.
    
        > [!NOTE]
        > It may take up to 60 minutes for the reopening process to complete. When the process is complete, the status of the case is changed to **Active** on the **eDiscovery (Standard)** page.
6.  (Optional) To turn on any holds associated with the reopened case, go to **Holds** tab, select a hold, and then select the check box under **Status** on the hold detail pane.

#### Turn on previous eDiscovery holds

When an organization reopens a closed case, any eDiscovery holds that were in place when the case was closed aren't automatically reinstated. If an organization wants to reinstate any of these holds, it must manually turn them back on after reopening the case. To turn an eDiscovery hold back on for a reopened case, you must perform the following steps:

1.  Go to the **Holds** tab in the case that you reopened.
2.  Select the hold that you want to turn back on.
3.  On the hold's detail pane that appears, set the **Status** toggle to **On.**

### Delete a case

An organization can also delete active and closed eDiscovery (Standard) cases. When an organization deletes a case, all searches and exports in the case are deleted. The case is also removed from the list of cases on the **eDiscovery (Standard)** page in the Microsoft Purview compliance portal.

> [!WARNING]
> You can't reopen a deleted case.

Before you can delete a case (whether it's active or closed), you must first delete all eDiscovery holds associated with the case. That includes deleting holds with a status of **Off**.

An organization should perform the following steps to delete an eDiscovery hold:

1.  Go to the **Holds** tab in the case that you want to delete.
2.  Select the hold that you want to delete.
3.  On the detail pane that appears, select **Delete.**

Perform the following steps to delete a case:

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane to expand the group. Under the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to delete.
3.  On the case's detail page, on the **Home** tab, select **Delete case**, which appears under the **Status** section.
    
    :::image type="content" source="../media/ediscovery-case-home-page-delete-eb1f5552.png" alt-text="Screenshot of case's Home tab showing the Delete case option highlighted.":::
    

> [!IMPORTANT]
> If the case you're trying to delete still contains eDiscovery holds, you'll receive an error message. You'll have to delete all holds associated with the case and then try again to delete the case.
