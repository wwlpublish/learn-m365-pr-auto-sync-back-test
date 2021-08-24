
Teams provides a rich set of tools to implement collaboration lifecycle management processes for your organization. Planning for lifecycle management is important, because it means you're building a plan to get your work done effectively. Most projects consist of a beginning, middle, and end. Projects can also be constructed and used in different kinds of ways that it's not always obvious which stage of their lifecycle they're in. Having a plan for lifecycle management will help you track your organization's projects as they go through these stages.
 

## Lifecycle concepts

The following concepts and definitions all affect the decisions you make for lifecycle management.

‎:::image type="content" source="../media/teams-lifecycles-concepts.png" alt-text="Lifecycle concepts":::


* **Teams**. A *team* is a collection of people, content, and tools that facilitate collaboration. A team defines who its members are, and the permissions and policies that apply to those members. Teams are built on Microsoft 365 Groups, and changes to Microsoft 365 group membership sync to the team. Like other Microsoft 365 Groups, Teams come auto-provisioned with an Exchange mailbox, a SharePoint site, a OneNote notebook, and other assets within Microsoft 365 or Office 365. There are tree types of teams:

    * **Org-wide teams** provide an automatic way for everyone in a small to medium-sized organization to be a part of a single team for collaboration.
    * **Public teams** are open and anyone within the organization can join. 
    * **Private teams** consist only of invited users. 

* **Channels**. Channels are the collaboration spaces within a team where the actual work is done. For each channel, a folder is automatically created on the SharePoint site to store all files shared to that channel. Channels can also be extended with apps that are relevant to the particular workstream—for example, you can add a Power BI dashboard to a channel to track the success of one aspect of your project.

    * **Standard channels**. Standard channels are visible to all team members. 

    * **Private channels**. Private channels are similar to standard channels, but they restrict access to conversations, files, and apps to a limited subset of team members. 

    * **Shared channels**. Shared channels enable you to share channels with any user or group with Azure Active Directory identity to your organization. (The feature is in development. For the latest status, check the roadmap with the [feature ID_70766](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=70766&azure-portal=true).)

* **Team user types and admin roles**. Team user types determine how much control a team member has:

    * **Team creator** has permissions to create a group or team in the directory. 
    
    * **Team owner** manages membership and settings for the team. 
    
    * **Team member** is a member of your organization who participates in a team.

    * **Guest** is a user who's external to your organization.

## Teams lifecycle stages

Generally speaking, a team has a purpose that's aligned with a project or accomplishing a goal. Even if a team was formed based on a shared interest, the team membership will probably change over time and the discussion might grow stale—only to surface again in a slightly different way in a different team.

Each team has a beginning, when the team is created and the channels are set up; a middle, when the team is used and collaboration occurs to match the rhythm of the workflow; and—sometimes—an end, when the team has completed its purpose and reached the end of its useful life.

‎:::image type="content" source="../media/teams-lifecycles.png" alt-text="Teams lifecycle sequence":::

### Stage 1: Beginning

The **beginning stage** involves defining the team’s goal and membership, creating the team and its channels, inviting team members, and setting permissions for individual members. Key decision points to consider in the beginning stage include:

- What is the team’s purpose?
- Who belongs on the team?
- Will the team be private or public?
- Can new members add themselves or do team owners add them?
- Who will have permissions to create channels or add tabs, bots, and connectors?
- What initial channels will be added to the team?

### Stage 2: Middle 

In the **middle stage**, collaboration takes place according to an established workflow, with team members interacting toward common goals within team channels. Decision points that should be considered in this stage include:

- Who will monitor usage to identify problems?
- What metrics will be used to determine whether a team is healthy?
- Identify any teams that have reached the end of their useful life.
- Identify unhealthy teams that still serve a purpose but need revitalizing.

### Stage 3: End
 
The **end stage** occurs when a team has concluded its useful lifecycle, normally for a finite project. In this stage, you formally acknowledge the closing of the team and delete teams you no longer need. 

Teams are deleted with a "soft delete" that IT can reverse for up to 30 days. Deleting teams doesn't affect any chats or content that were retained in accordance with compliance policies. Channels also have a "soft delete" and can be reversed for up to 21 days after deletion. 

When a group or team is deleted, most of the information in the connected services is also deleted. Understand the impacts when a team is deleted to avoid any potential data loss.

* **Guests**. When a team is deleted, guests aren't removed from Azure Active Directory. 

* **SharePoint**. All files in team channels are stored in the SharePoint site of the associated group. In some cases, content other than documents may exist in SharePoint, such as lists or pages. Deleting a channel will not delete the folder or its contents from the SharePoint document library. 

* **Planner**. The deletion of the group will also result in the deletion of any associated plans. To keep the data, you can **export the plan to a spreadsheet**, **copy and move tasks to another Plan**, or **Copy entire plan** before deleting the team.

* **Forms**. The deletion of the group will also result in the deletion of any associated forms. When a team is deleted, you can **duplicate the form**, **export results to a spreadsheet**, or just **delete the form**.

* **Power Automate**. Flows created in Power Automate and associated with a group or team don't belong to the group. They are owned by the creator and merely shared with other users and groups. As such they aren't affected if a group or team is deleted.

* **Power BI**. Power BI data and workspaces can operate independently from groups and teams. If you need the report once the group or team is deleted, it can be copied from the existing workspace to another workspace within Power BI.

* **Dataverse for Teams**. If the team is deleted, the Dataverse for Teams environment that was created will also be deleted. The Dataverse for Teams environment itself can be deleted from within the team by the team owner. To keep the data, you can upgrade a Dataverse for Teams environment to a Dataverse database environment. The upgraded environment's lifecycle will no longer be tied to the lifecycle of that team. If the team is deleted, the upgraded environment remains.

Important decision points related to the end stage include:

- Defining what the end of a team’s life looks like.
- Deciding whether to keep a team’s stored content available, and for how long.
- Documenting best practices and lessons learned.
- Archiving data, if necessary.

## Automation throughout the lifecycle

You can configure and manage the Teams lifecycle through the Teams Admin Center, the Microsoft 365 Admin Center, and the Azure AD Admin Center. Should you wish to automate specific management tasks throughout the team lifecycle, you can do so using PowerShell and Graph API automation tools.

For more information, see [End of lifecycle options for groups, teams, and Yammer](/microsoft-365/solutions/end-life-cycle-groups-teams-sites-yammer).
 


 
