When you believe legal action is possible, it's important to be able to locate all emails and documents that may relate to the case. Exchange administrators can use eDiscovery to identify relevant items.

In your newspaper office, legal action is a regular occurrence. You're using the Microsoft 365 compliance center to search for emails from throughout your organization that are relevant to each case. However, you've recently noticed that some items aren't included in eDiscovery search results even though they're important to that case. You want to know if the user has made a mistake in the search conditions, or if there's some other cause.

Here, you'll learn how to troubleshoot eDiscovery searches and ensure that they return all relevant items.

## What is eDiscovery?

When there's a threat of legal action, it's essential to locate all relevant emails and other items quickly. This search stage of the compliance process is referred to as eDiscovery. When you've located the items that relate to a case, you might want to export them to a single location or place a hold on them, to ensure that they can't be tampered with.

Microsoft 365 includes the following eDiscovery solutions, which can all locate emails from Exchange Online as part of their searches:

- **Content search.** Use this tool to search for emails, documents, and other content across your Microsoft 365 data, and to export the results.
- **Core eDiscovery.** Use this tool to associate your search results with a case, and to place holds on relevant content locations.
- **Advanced eDiscovery.** Use this tool for the highest level of functionality. Advanced features such as hold notifications, tagging, and analysis are included.

> [!NOTE] 
> Until recently, Exchange Online included its own eDiscovery tools, which you could access through Exchange Admin Center or PowerShell. These have been retired and are no longer supported. Instead, use the Microsoft 365 eDiscovery tools described in this module including the Microsoft 365 compliance center and the corresponding PowerShell cmdlets, such as `New-ComplianceCase` and `New-ComplianceSearch`.

## Troubleshoot roles for eDiscovery

eDiscovery involves access to emails from outside your own mailbox and documents from throughout your Microsoft 365 organization. Only trusted security personnel should be able to search, export, and hold items. You assign eDiscovery rights by adding users to the following two role groups:

- **eDiscovery Manager.** Members of this role group can perform common eDiscovery tasks such as creating cases, searching for content, and creating holds. They can only access and manage their own cases and their searches, not those created by other eDiscovery Managers.
- **eDiscovery Administrator.** Members of this role group perform all tasks that eDiscovery Managers can complete. In addition, they can access and manage other managers' cases. For example, they can add themselves and other users as members of the case.

If a user is denied access to eDiscovery tools, first check that their job requires them to run eDiscovery searches. If they should have eDiscovery access, you can correct their role membership in the Microsoft 365 compliance center:

1.  In the Microsoft 365 compliance center, select **Permissions** and then, under **Compliance center**, select **Roles**.

    - :::image type="content" source="../media/02-access-roles.png" alt-text="Screen shot showing how to access the role assignment tool in Microsoft 365 compliance center.":::

1.  In the list of role groups, select **eDiscovery Manager**.
1.  To the right of **eDiscovery Manager** or **eDiscovery Administrator**, select **Edit**.
1.  In the **Editing Choose eDiscovery Manager** windows, under the list of users, select **Edit**.

    - :::image type="content" source="../media/02-edit-role.png" alt-text="Screen shot showing how to edit the membership of a role group in Microsoft 365 compliance center.":::

1.  Select **Add**, search for and select the correct user account, and then select **Add** again.
1.  To save the new membership, select **Done,** and then select **Save**.
1.  Select **Close**.

Alternatively, you can add a member to the eDiscovery Manager role group by using this command in PowerShell:

``` powershell
Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
```

## Troubleshoot eDiscovery

Let's examine some common troubleshooting techniques that you can use for eDiscovery in Microsoft 365 compliance center.

### Investigate statistics for eDiscovery searches

It's a good idea to have in mind some approximate values for the size of your search results. If the actual number of results is very different from what you expected, that may indicate an incorrect set of search terms. To investigate statistics for a search, take these steps:

1.  In the Microsoft 365 compliance center, locate the search. For example, if you used the **Content search** tool, under **Solutions** select **Content search,** and then select the case from the list.
1.  In the search window, select **Search statistics**. The data is displayed under three headings:

    - **Search content.** Displays data about the search including the estimated number of items in each location, the number of locations with hits, and the total volume of data for items returned.
    - **Condition report.** Displays data about the number of items that matched each condition in the search. You can use this information to improve the conditions.
    - **Top locations.** Displays the location with the most hits from the search.

### Resolve content location errors

Sometimes, you may receive errors like this when you perform a content search:

```
Error
The search on the following locations failed:
User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)
User2@contoso.com: Application error occurred.Please try again later. (CS012-002)
```

Such errors have error numbers in the form **CS0xx-0xx,** and they tend to arise when you've searched a large number of mailboxes. They are caused by specific servers at the datacenter being unavailable during the search – for example, because of a planned reboot. If you restart the search, similar errors might appear on other inboxes, so instead click the **Retry** button on the Content search page. This button retries only the inboxes where failures occurred on the previous attempt.

### Collect diagnostic information about eDiscovery searches

When a problem arises with an eDiscovery search, the more information you have about the problem, the easier it'll be to diagnose the fault. Also, Microsoft support personnel may require detailed data about the search when you open a support case. You can use PowerShell cmdlets to collect this low-level information and store it in text files.

> [!NOTE] 
> The information you collect in eDiscovery searches often includes security-sensitive material that relates to legal actions. If you are going to send the results of the following commands to Microsoft engineers, make sure you redact any sensitive data.

Use the following command to gather information about a Core eDiscovery search:

``` powershell
Get-ComplianceSearch "ContosoCaseSearch" | FL > "CoreSearchDetails.txt"
```

If you want further information about the actions associated with a search, such as previews, exports, or purges, use this command:

``` powershell
Get-ComplianceSearchAction "ContosoCaseSearch" | FL > "CoreSearchActions.txt"
```

In these commands, replace `ContosoCaseSearch` with the name of your eDiscovery search. You can also use different text file names. When the commands are complete, those text files will contain full data about the search and its actions.

## Learn more

- [eDiscovery solutions in Microsoft 365](/microsoft-365/compliance/ediscovery)
- [Retirement of legacy eDiscovery tools](/microsoft-365/compliance/legacy-ediscovery-retirement)
- [Assign eDiscovery permissions in the Microsoft 365 compliance center](/microsoft-365/compliance/assign-ediscovery-permissions)
- [Retry a Content Search to resolve a content location error](/microsoft-365/compliance/retry-failed-content-search)
- [View statistics for eDiscovery search results](/microsoft-365/compliance/view-keyword-statistics-for-content-search)
