If there's a possibility of legal action involving your company, you must be able to locate all materials that relate the case and protect them from tampering so that you can use them as evidence.

In your firm of legal advisors, you have occasionally had conflicts with customers or other interested parties and have had to submit materials as evidence in legal actions. You want to make sure that, when such problems arise, you can locate and hold data from Teams such as files and chat items.

Here, you'll learn how to use eDiscovery features in Microsoft 365 to capture information from Teams communications.

## What is eDiscovery?

eDiscovery is the process of identifying, collecting, and producing electronically stored information (ESI) when needed. eDiscovery allows you to respond to a legal case involving people in your organization. This might involve finding and retaining specific information in email, documents, instant messaging conversations, and other locations. Within Teams, eDiscovery includes chat, messaging, files, meeting, and call summaries.

Access eDiscovery from the Microsoft 365 compliance center.

## Permissions

To create searches, you must be a member of the eDiscovery Manager role group. Within the eDiscovery Manager group, there are two subgroups: **eDiscovery Managers** and **eDiscovery Administrators**.

An **eDiscovery Manager** can:

- Access and manage the cases they create, but not cases created by other eDiscovery managers.
- Use the Content Search tool to search content locations, preview, and export search results.
- Create and manage Core eDiscovery cases and Advanced eDiscovery cases.
- Add to a case and remove members.
- Create case holds.
- Run searches associated with a case.

**eDiscovery Administrators** can do everything that an eDiscovery Manager can do, plus:

- Access all cases that are listed on the eDiscovery and Advanced eDiscovery pages.
- Access case data in Advanced eDiscovery for any case in the organization.
- Manage any eDiscovery case after they add themselves as a member of the case.

## Licenses

Users, the custodians of the data, must be assigned a Microsoft 365 E5 or Office 365 E5 license. Alternatively, you can purchase an add-on Microsoft 365 E5 Compliance or Microsoft 365 eDiscovery and Audit license for users with an Office 365 E1 or a Microsoft 365 E3 license.

Administrators, compliance officers, or legal personnel who are assigned to cases as members, and use Advanced eDiscovery to collect, view, and analyze data don't need an E5 license.

## Create a Core eDiscovery case

To create a core eDiscovery case:

1. Sign into the [Microsoft 365 compliance center](https://compliance.microsoft.com) with a user account with the appropriate eDiscovery permissions, or who is part of the Organization Management role group.
1. From the left navigation pane, select **Show all** > **eDiscovery** > **Core**.
1. Select **Create a case**.
1. On the **New case** page, give the case a **name** that is unique within your organization. Optionally add a case number and description.
1. Select **Save** to create the case.

## Create a hold

Once you have created a Core eDiscovery case, you can add one or more holds. When you place content locations on hold, content is preserved until you either remove or delete the hold. It may take up to 24 hours for a hold to take effect. A hold may be:

- **Infinite** - where all content in the specified locations is placed on hold.
- **Query based** - where only the content that matches a search query is placed on hold.
- **Date ranged** - where content that was sent, received, or created within that date range is placed on hold.

To create an eDiscovery hold:

1. Sign into the [Microsoft 365 compliance center](https://compliance.microsoft.com), in left navigation pane select **Show all** > **eDiscovery** > **Core**.
1. Select a case, and then select **Open case**.
1. On the **Home page**, select the **Holds** tab.
1. On the **Holds** page, select **Create**.
1. On the **Name your hold** page, give the hold a **name** that is unique in your organization. Optionally add a description.
1. Select **Next**.
1. On the **Content locations** page, select the content locations. You can place mailboxes, sites, and public folders on hold.

## Content Search

To search for content relevant to the case:

1. Sign into the [Microsoft 365 compliance center](https://compliance.microsoft.com), in left navigation pane select **Show all** > **eDiscovery** > **Core**.
1. Select a case, and then select **Open case**.
1. On the **Home** page for the case, select the **Searches** tab.
1. On the **Search** page, select **New search**.
1. On the **New search** page, add keywords and conditions to create a search query.
1. A **Searches** page is added to the case, which can be accessed only by case members.

## Export search results

You can download data from a search, by exporting the results.

1. Sign into the [Microsoft 365 compliance center](https://compliance.microsoft.com), in the left navigation pane select **Show all** > **eDiscovery** > **Core**.
1. Select **Open case** > **Searches** tab.
1. From the **Searches** page, select **Export results**.
1. From the **Exports results** page, select how you want the data output, and then select **Export**.
1. The search results are uploaded to an Azure Storage location in the Microsoft cloud.
1. Select the **Export** tab to display the list of export jobs for the case.

You can also export the results of multiple searches - see the documentation online.

## Learn more

- [eDiscovery in Microsoft 365](/microsoft-365/compliance/ediscovery)
- [Content Search](/microsoft-365/compliance/content-search)
- [Assign eDiscovery permissions in the Microsoft 365 Defender portal](/microsoft-365/compliance/assign-ediscovery-permissions)
- [Create an eDiscovery hold](/microsoft-365/compliance/create-ediscovery-holds)
- [Export content from a Core eDiscovery case](/microsoft-365/compliance/export-content-in-core-ediscovery)
