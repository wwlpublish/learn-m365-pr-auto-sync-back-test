When organizations implement SharePoint Online and OneDrive, they usually have existing file shares and on-premises SharePoint sites they want to migrate to their new Microsoft 365 cloud solution. This unit provides a guide to help you plan your migration strategy to SharePoint Online and OneDrive.

The following tools are available in Microsoft 365 for migrating files shares and on-premises SharePoint sites:

 -  **Migration Manager**. Used for migrating your on-premises file share content to Microsoft 365. With the ability to set up multiple computers as "agents", Migration Manager lets you scale your migration project as much as you need. Migration Manager can be accessed in the modern SharePoint admin center. It guides you through the setup of your agents and the creation of your tasks. You can specify global or task level settings, view all-up task progress, and download aggregated summary and task-level reports. For more information, see [Migrate file shares to Microsoft 365 with Migration Manager](/sharepointmigration/mm-get-started?azure-portal=true).
 -  **SharePoint Migration Tool (SPMT)**. SPMT is a free migration solution to help organizations migrate content from on-premises SharePoint sites to Microsoft 365. SPMT supports migration to SharePoint, OneDrive, and Teams from:
    
     -  SharePoint Server 2010, 2013, and 2016
     -  SharePoint Foundation 2010 and 2013

    For more information, see [Overview of the SharePoint Migration Tool](/sharepointmigration/introducing-the-sharepoint-migration-tool?azure-portal=true).

### The stages in a typical migration

The following diagram displays the phases that most file share migrations fall into.

:::image type="content" source="../media/migration-process-fileshare-133b634d.png" alt-text="graphic shows the five stages in a typical file share migration to SharePoint Online and OneDrive. Stages include migration planning, assess and remediate, prepare your OneDrive and SharePoint Online environment, Migrate, and user onboarding.":::


The tasks and considerations for each of these migration stages are outlined in the following chart.<br>

:::row:::
  :::column:::
    **Migration planning**
  :::column-end:::
  :::column:::
    **Assess and remediate**
  :::column-end:::
  :::column:::
    **Prepare your OneDrive and SharePoint environment**
  :::column-end:::
  :::column:::
    **Migrate**
  :::column-end:::
  :::column:::
    **User onboarding**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What content goes where

Understanding permissions vs sharing

What to expect before and after

Migration and network performance considerations

Change management and communications
  :::column-end:::
  :::column:::
    Assess key areas

Remediate issues
  :::column-end:::
  :::column:::
    Pre-provision Microsoft 365 and users
  :::column-end:::
  :::column:::
    Review migration offerings

Microsoft FastTrack services

Migration service providers
  :::column-end:::
  :::column:::
    Send regular emails to users

Provide training

Let users know how they're affected
  :::column-end:::
:::row-end:::


Before you start your migration, it's important that you plan your outcome. To do so, you should complete an assessment of your current source environment. What you discover will influence your overall strategy and timing, including:

 -  The design of the target environment and the mapping between source and target systems.
 -  The amount of content you migrate. Determine if content is redundant, out of date, or still relevant.
 -  Build your user onboarding into your upfront planning. Communicate early and often with your users about the migration and how it affects them. Don't wait until the very end to start preparing them for the change.

### What's migrated

File shares that can be migrated using **Microsoft Manager** include:<br>

 -  Centralized file hosting on a network server or a network drive.
 -  Shared files or disks on a local computer. Often referred to as a "Z drive" on networked computers, it's a shared drive somewhere on the network.

The following chart shows what can and can't be migrated using the **SharePoint Migration Tool**.

:::row:::
  :::column:::
    **Migrated**
  :::column-end:::
  :::column:::
    **Not migrated**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Documents
  :::column-end:::
  :::column:::
    Conversion of embedded URLs in content
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    File and folder structure
  :::column-end:::
  :::column:::
    Windows hidden attributes on file and folder
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User level file and folder permissions
  :::column-end:::
  :::column:::
    Explicit deny permissions
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Files under 15 GB
  :::column-end:::
  :::column:::
    Inaccessible or corrupted documents
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Site, document, and folder metadata
  :::column-end:::
  :::column:::
    Files or folders exceeding current SharePoint restrictions and limitations
  :::column-end:::
:::row-end:::


### What content goes where<br>

In your planning, include how this transition to Microsoft 365 will make for a more collaborative experience for your users. Review how you use the content stored in your file shares today. Does the file belong to a single user, even though they might share it with others? If so, save it in your OneDrive. Your OneDrive is private by default, but you can share files with others. This design is useful if you aren't working as a team yet.

If you're working on a file or folder intended for team consumption and collaboration, move it to a shared library where team members can access it by default. OneDrive gives you access to all your shared libraries in Microsoft Teams, SharePoint, or Outlook. When you need a new shared library for team files, you can create one right from OneDrive, add members, and start working together.

:::image type="content" source="../media/sharepoint-migration-what-goes-where-b4d2fca9.png" alt-text="graphic shows where files and site information are migrated to in a migration to SharePoint Online and OneDrive":::


### Assess and remediate your content using the SharePoint Migration Tool

Before your migration starts, it's important to perform an analysis of your current environment. Only you know your data and how and who uses it.

The SharePoint Migration Tool can scan your files and provide assessment reports. To find any issues with your file before migration, turn on the setting titled "**Only perform scanning**." If you have multiple sources that you want to assess, consider using the bulk process by creating a .json or .csv file.

The following chart outlines some of the more common issues that arise when preparing for migration.

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **Assess**
  :::column-end:::
  :::column:::
    **Remediate**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **File extensions**
  :::column-end:::
  :::column:::
    Find all files in the Folders and Files report whose path ends in one of the extensions defined here: [Types of files that can't be added to a list or library](https://support.office.com/article/30BE234D-E551-4C2A-8DE8-F8546FFBF5B3?azure-portal=true).
  :::column-end:::
  :::column:::
    If the blocked file types are scripting files, they're blocked because scripting capabilities are turned off by default in OneDrive.

If you want to allow these file types, turn on scripting capabilities as described here: [Allow or prevent custom script](/sharepoint/allow-or-prevent-custom-script?azure-portal=true).

Make sure you understand why these files are blocked by default as described here: [Security considerations of allowing custom script](/sharepoint/security-considerations-of-allowing-custom-script?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **File and folder name characters**
  :::column-end:::
  :::column:::
    Find all items in the Folders and Files report whose name contains any of the characters detailed here: [Invalid file names and file types in OneDrive and SharePoint](https://support.office.com/article/64883a5d-228e-48f5-b3d2-eb39e07630fa?azure-portal=true).
  :::column-end:::
  :::column:::
    Work with your migration vendor to substitute these characters in all file and folder names.

The \# and % characters are supported but not enabled by default. Follow these steps to enable them: [New support for \# and % in SharePoint and OneDrive](https://techcommunity.microsoft.com/t5/Microsoft-SharePoint-Blog/New-support-for-and-in-SharePoint-Online-and-OneDrive-for/ba-p/60357?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **File and folder path length**
  :::column-end:::
  :::column:::
    Find all items in the *Folders and Files* report whose Path exceeds the file path length described here: [SharePoint limits](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits?azure-portal=true).
  :::column-end:::
  :::column:::
    Work with your migration vendor to reorganize your file and folder structure such that it doesn't exceed this limit. Splitting large drives that serve several scenarios into multiple smaller, more focused drives may help here.
  :::column-end:::
:::row-end:::


### Migrating to OneDrive

A typical migration to OneDrive that follows Microsoft's best practices guidance includes the following steps:

1.  **Select a small set of users for a pilot migration**. The goal of the pilot is to validate the process, including performance, user communication, and to get a sample of user feedback. Before you migrate your file share content, you must pre-provision your users in Microsoft 365.
2.  **Complete the pilot migration**. The migration process should use an incremental migration method. In this process:
    
     -  Migration happens in the background to eliminate any effect on users.
     -  Migration is followed by a cut-over event to reduce the effect on users. During this event:
        
         -  Network file shares and local file shares are disabled.
         -  The disabled file shares are then directed to use the SharePoint or OneDrive environment.
3.  **Analyze your data**. Analyze the data from the pilot migration to determine the remainder of your migration schedule and make any changes. For example, you may update your user communication template to address a question you received from a pilot user.
4.  **Complete the remainder of the migration**. This process should also follow an incremental migration method, just like the pilot. It's recommended that you use a single cut-over event for all users to switch to using their OneDrive accounts and SharePoint sites. This design helps eliminate users from updating duplicate copies of content.

> [!IMPORTANT]
> Make sure that the account used to migrate content has permissions on the destination OneDrive.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”