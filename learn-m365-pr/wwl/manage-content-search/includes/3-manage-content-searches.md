Content searches can be created within the Microsoft 365 Compliance center or through PowerShell by using the **New-ComplianceSearch** cmdlet. This cmdlet enables you to run organization-wide searches of all mailboxes and other destinations by using Windows PowerShell.

By using the Compliance Search cmdlets, you can create scripts to integrate Content Searches into your eDiscovery workflow. For example, you could regularly run a Content Search to search all mailboxes in your organization to identify those mailboxes that contain specific search results.

### Clone a Content Search

Although enhanced by scalability and performance improvements, searching a large number of mailboxes or SharePoint sites when using Content Search may still take a while to complete. Cloning a Content Search can be used to break up a large, single search into multiple, smaller searches that run more quickly.

When you clone a search, a new search is created with a different name that contains the same properties as the original search. You can then edit the new search by changing various properties, such as the keyword query or the date range, before running the search.

Cloning a Content Search may also be advantageous when you need to:

 -  Compare the results of different keyword search queries run on the same content locations.
 -  Reenter many previously used content locations when creating a new search, which saves time and effort.
 -  Reduce the size of the search results. For example, if you have a search that returns too many results to export, you can clone the search and then add a search condition based on a date range to reduce the number of search results.

Cloning a Content Search is accomplished by copying and running the script that appears in the [Clone a Content Search page in the Microsoft 365 Compliance Center](/microsoft-365/compliance/clone-a-content-search?azure-portal=true). This page includes a list of prerequisites to running the script, a copy of the script itself, and instruction on editing and running the script.

Once you run the script to create the clone, you can edit and run the new search in the Security &amp; Compliance Center.

### Search for and delete email messages

Occasionally, you may need to find and remove potentially harmful or high-risk email such as:

 -  Messages that contain a dangerous attachment or virus.
 -  Phishing messages.
 -  Messages that contain sensitive data.

You can use Content Search to search for and delete email messages from all the mailboxes in your organization.

The first step is to create and run a Content Search to find the messages that you want to remove from mailboxes in your organization. You can create the search by using the Content Search feature in the Microsoft 365 Compliance center or by running the **New-ComplianceSearch** and **Start-ComplianceSearch** cmdlets. The messages that match the query for this search are deleted by running the **New-ComplianceSearchAction** cmdlet.

> [!IMPORTANT]
> When you run the **New-ComplianceSearchAction** cmdlet, the content locations that are searched in the Content Search must include only mailboxes and public folders. You can't include other locations in a search that deletes emails.

After you've created and refined a Content Search to return the message that you want to remove, the final step is to connect to the Microsoft 365 Security &amp; Compliance Center PowerShell and then run the **New-ComplianceSearchAction** cmdlet to delete the message. Deleted messages are moved to a user's Recoverable Items folder.

**Additional reading**. For more information, see [Search for and delete email messages in your Microsoft 365 organization - Admin Help](/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization?azure-portal=true).
