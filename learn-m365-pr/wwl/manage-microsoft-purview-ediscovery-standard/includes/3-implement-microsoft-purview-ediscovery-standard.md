Microsoft Purview eDiscovery (Standard) provides a basic eDiscovery tool that organizations can use to search and export content in Microsoft 365. Organizations can also use eDiscovery (Standard) to place an eDiscovery hold on content locations, such as:

 -  Exchange mailboxes
 -  SharePoint sites
 -  OneDrive accounts
 -  Microsoft Teams

Nothing is needed to deploy eDiscovery (Standard). However, there are some prerequisite tasks that an IT admin and eDiscovery manager must complete before an organization can start using eDiscovery (Standard) to search, export, and preserve content.

This unit examines the steps necessary to set up eDiscovery (Standard) and create an eDiscovery (Standard) case. These steps include:

 -  Ensure the proper licensing required to access eDiscovery (Standard) and place an eDiscovery hold on content locations.
 -  Assign permissions to an organization's IT, legal, and investigation teams so they can access and manage cases.
 -  Create cases to search for and export content.

### Step 1: Verify and assign appropriate licenses

Licensing for eDiscovery (Standard) requires the appropriate organization subscription and per-user licensing.

 -  **Organization subscription**. To access eDiscovery (Standard) in the Microsoft Purview compliance portal and use the hold and export features, an organization must have:
     -  Exchange online Plan 2, OR
     -  Microsoft 365 E3 or Office 365 E3 subscription or higher, OR
     -  Microsoft 365 Frontline organizations must have an F5 subscription.
 -  **Per-user licensing**. To place an eDiscovery hold on mailboxes and sites, users must be assigned one of the following licenses, depending on your organization subscription:
     -  Exchange online Plan 2 license, OR
     -  A Microsoft 365 E3 or Office 365 E3 license or higher, OR
     -  Office 365 E1 license with an Exchange Online Plan 2 or Exchange Online Archiving add-on license, OR
     -  Microsoft 365 Frontline F5 Compliance or F5 Security &amp; Compliance add-on license AND Office 365 E1 license with a SharePoint Online Plan 2 or OneDrive for Business Plan 2 add-on license
    
    For information about how to assign licenses, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users?azure-portal=true).

**Additional reading**. For information and guidance on security and compliance:

 -  Download and see the eDiscovery and auditing section in the [Microsoft 365 Comparison table](https://aka.ms/M365EnterprisePlans?azure-portal=true).
 -  See the [Microsoft 365 guidance for security &amp; compliance - Service Descriptions \| Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true).

### Step 2: Assign eDiscovery permissions

A user must be assigned the appropriate permissions to access Microsoft Purview eDiscovery (Standard) or to be added as a member of an eDiscovery (Standard) case. Specifically, a user must be added as a member of the **eDiscovery Manager** role group in the Microsoft Purview compliance portal. Members of this role group can:

 -  Create and manage eDiscovery (Standard) cases.
 -  Add and remove members to an eDiscovery (Standard) case.
 -  Place an eDiscovery hold on users.
 -  Create and edit searches.
 -  Export content from an eDiscovery (Standard) case.

Complete the following steps to add users to the eDiscovery Manager role group:

1.  On the **Microsoft Purview compliance** portal, select **Permissions** on the navigation pane.
2.  On the **Permissions** page, under the **Microsoft Purview solutions** group, select **Roles**.
3.  On the **Role groups for Microsoft Purview solutions** page, select the **eDiscovery Manager** role group.
4.  On the **eDiscovery Manager** detail pane that appears, select **Edit** next to the **eDiscovery Manager** section.
5.  On the **Choose eDiscovery Manager** page in the edit role group wizard, select **Choose Discovery Manager**.
6.  On the **Choose eDiscovery Manager** page, select the **+Add** button. Doing so displays the list of users.
7.  Select the checkbox for all users you want to add to the role group, and then select the **Add** button at the bottom of the pane.
8.  You can select the **Add** or **Remove** button to modify the selected users, if necessary. Once the list is correct, select **Done**.
9.  Select **Save** to add the users to the role group, and then select **Close** to complete the process.

#### More information about the eDiscovery Manager role group

There are two subgroups in the eDiscovery Manager role group. The difference between these subgroups is based on scope.

 -  **eDiscovery Manager**. Users who are assigned this role can view and manage the eDiscovery (Standard) cases they create or are a member of. If another eDiscovery Manager creates a case but doesn't add a second eDiscovery Manager as a member of that case, the second eDiscovery Manager won't be able to view or open the case on the **eDiscovery (Standard)** page in the Microsoft Purview compliance portal. In general, most people in an organization can be added to the eDiscovery Manager subgroup.
 -  **eDiscovery Administrator**. Users who are assigned this role can perform the same case management tasks as an eDiscovery Manager. However, an eDiscovery Administrator can also:
     -  View all cases that are listed on the **eDiscovery (Standard)** page.
     -  Manage any case in the organization after they add themselves as a member of the case.
     -  Access and export case data for any case in the organization.
     -  Remove members from an eDiscovery case. Only an eDiscovery Administrator can remove members from a case. Users who are members of the eDiscovery Manager subgroup can't remove members from a case, even if the user created the case.
    
    > [!IMPORTANT]
    > Because of the broad scope of access, an organization should only have a few administrators who are members of the eDiscovery Administrators subgroup.

### Step 3: Create an eDiscovery (Standard) case

The next step is to create a case and start using eDiscovery (Standard). The user who creates the case is automatically added as a member.

> [!TIP]
> Members of the Organization Management role group can also create eDiscovery (Standard) cases.

Complete the following steps to create a case:

1.  On the **Microsoft Purview compliance** portal, select **eDiscovery** on the navigation pane. In the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page,
3.  On the **eDiscovery (Standard)** page, select the **+Create a case** option on the menu bar.
4.  On the **New case** pane that appears, enter a **Name** for the case, optionally enter a **Description**, and then select **Save**. The case name must be unique in your organization.
5.  The new case is created and displayed on the **eDiscovery (Standard)** page. You may have to select the **Refresh** option on the menu bar to display the new case.

### Step 4 (optional): Add members to an eDiscovery (Standard) case

If you create a case in Step 3 and you're the only person who will use the case, then you don't have to perform this step. You can start using the case to create eDiscovery holds, search for content, and export search results. Perform this step if you want to give other users (or roles group) access to the case.

1.  On the **Microsoft Purview compliance** portal, select **eDiscovery** on the navigation pane. In the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to add members to.
3.  On the case detail page that appears, select the **Settings** tab.
4.  On the **Settings** tab, two tiles are displayed: **Case Information** and **Access and permissions**. Select the **Select** button in the **Access and permissions** tile.
5.  On the **Access &amp; permissions** pane that appears, under the **Manage members** section, select **+Add** to add members to the case.
    
        > [!NOTE]
        > You can also choose to add role groups as members of a case. Under the **Manage role groups** section, select **+Add**. You can only assign the role groups that you're a member of to a case. This restriction is in place because role groups control who can assign members to an eDiscovery case.
6.  On the **Add members** pane, in the list of users or role groups that can be added as members of the case, select to the left of the name of the people or role groups that you want to add. Doing so displays a check box for the user or role group. If you have a large list of people or role groups who can be added as members, use the **Search** box to search for a specific person or role group in the list.
7.  On the **Access &amp; permissions** pane, select the **Exit** button at the bottom of the pane, which returns you to the case detail page.

 -  If a role is added or removed from a role group that you've added as a member of a case, then the role group will automatically be removed as a member of the case (or any case the role group is a member of). The reason for this action is to protect the organization from inadvertently providing extra permissions to members of a case. Similarly, if a role group is deleted, it will be removed from all cases it was a member of.
 -  As previously mentioned, only an eDiscovery Administrator can remove members from a case. Users who are members of the eDiscovery Manager subgroup can't remove members from a case, even if the user created the case.

### Explore the eDiscovery (Standard) workflow

The following diagram is designed to help organizations get started using eDiscovery (Standard) once they've created a case. A brief summary of each step included in this diagram is provided below. Each summary highlights some extended eDiscovery (Standard) functionality that organizations can explore.

:::image type="content" source="../media/core-ediscovery-workflow-c44de18f.png" alt-text="Diagram showing the Microsoft Purview eDiscovery Standard workflow, which consists of three steps.":::


1.  **Create an eDiscovery hold**. The first step after creating a case is placing a hold (also called an **eDiscovery hold**) on the content locations of the people of interest in the investigation. Content locations include:
     -  Exchange mailboxes
     -  SharePoint sites
     -  OneDrive accounts
     -  the mailboxes and sites associated with Microsoft Teams and Microsoft 365 Groups
    
    While this step is optional, creating an eDiscovery hold preserves content that may be relevant to the case during the investigation. When an organization creates an eDiscovery hold, it can preserve all content in specific content locations. It can also create a query-based hold to preserve only the content that matches a hold query. Besides preserving content, eDiscovery holds enable organizations to quickly search the content locations on hold (instead of having to select each location to search) when they create and run searches in the next step. After an organization completes its investigation, it can release any hold that it created.
2.  **Search for content**. After an organization creates eDiscovery holds, it can use the built-in search tool to search the content locations on hold. It can also search other content locations for data that may be relevant to the case. An organization can create and run different searches that are associated with the case. You can use keywords, properties, and conditions to build search queries. Queries will return search results with the data that's most likely relevant to the case. An organization can also:
     -  View search statistics that may help refine a search query to narrow the results.
     -  Preview the search results to quickly verify whether the relevant data is being found.
     -  Revise a query and rerun the search.
3.  **Export and download search results**. After an organization searches for and finds data that's relevant to its investigation, it can export the search results out of Microsoft 365. Doing so enables people outside of the investigation team to review the results. Exporting data is a two-step process.
    1.  **Export the search results out of Microsoft 365**. This step is accomplished by copying the search results to a Microsoft-provided Azure Storage location.
    2.  **Download the export package to a local computer**. Use the eDiscovery Export tool to download the content to a local computer. In addition to the exported data files, the export package contains an export report, a summary report, and an error report.
