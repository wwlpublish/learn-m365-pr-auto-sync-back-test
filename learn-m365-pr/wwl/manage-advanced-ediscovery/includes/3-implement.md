Advanced eDiscovery in Microsoft 365 provides a beginning-to-end workflow to preserve, collect, review, analyze, and export data that's responsive to your organization's internal and external investigations. Nothing is needed to deploy Advanced eDiscovery. Organizations just need to configure licenses, permissions, and an optional global setting to set it up. Once Advanced eDiscovery is set up, you're ready to create and manage cases.

:::image type="content" source="../media/get-started-advanced-ediscovery-831676ec.png" alt-text="diagram showing the two steps to get started with advanced eDiscovery including setting it up and creating cases":::


The tasks required to set up licenses, permissions, and an optional global setting are outlined in the following sections.

### Step 1: Verify and assign appropriate licenses

To access Advanced eDiscovery in the Microsoft 365 compliance center, an organization must have the correct licensing. Licensing for Advanced eDiscovery requires the appropriate organization subscription and per-user licensing. Licensing for Advanced eDiscovery requires the appropriate organization subscription and per-user licensing.

 -  **Organization subscription.** To access Advanced eDiscovery in the Microsoft 365 compliance center, your organization must have one of the following subscriptions:
    
     -  Microsoft 365 E5 or Office 365 E5 subscription
     -  Microsoft 365 E3 subscription with E5 Compliance add-on
     -  Microsoft 365 E3 subscription with E5 eDiscovery and Audit add-on
     -  Microsoft 365 Education A5 or Office 365 Education A5 subscription
    
    If you don't have an existing Microsoft 365 E5 plan and want to try Advanced eDiscovery, you can add Microsoft 365 to your existing subscription or sign up for a trial of Microsoft 365 E5.
 -  **Per-user licensing.** To add a user as a custodian in an Advance eDiscovery case, that user must be assigned one of the following licenses, depending on your organization subscription:
    
     -  **Microsoft 365.** Users must be assigned a Microsoft 365 E5 license, an E5 Compliance add-on license, or an E5 eDiscovery and Audit add-on license. Microsoft 365 Education users must be assigned an A5 license.
     -  **Office 365.** Users must be assigned an Office 365 E5 or Office 365 Education A5 license.

> [!NOTE]
> Users only need an E5 or A5 license (or the appropriate add-on license) to be added as custodians to an Advanced eDiscovery case. IT admins, eDiscovery managers, lawyers, paralegals, or investigators who use Advanced eDiscovery to manage cases and review case data don't need an E5, A5, or add-on license.<br>

### Step 2: Assign eDiscovery permissions

To access Advanced eDiscovery or added as a member of an Advanced eDiscovery case, a user must be assigned the appropriate permissions. Specifically, a user must be added as a member of the **eDiscovery Manager** role group in the Microsoft 365 compliance center. Members of this role group have permissions to complete the following tasks:

 -  Create and manage Advanced eDiscovery cases.
 -  Add and remove members.
 -  Place custodians and content locations on hold.
 -  Manage legal hold notifications.
 -  Create and edit searches associated in a case.
 -  Add search results to a review set.
 -  Analyze data in a review set.
 -  Export and download from an Advanced eDiscovery case.

There are two subgroups in the eDiscovery Manager role group. The difference between these subgroups is based on scope.

 -  **eDiscovery Manager.** Members of this role group can view and manage the Advanced eDiscovery cases they create or are a member of. If another eDiscovery Manager creates a case but doesn't add a second eDiscovery Manager as a member of that case, the second eDiscovery Manager can't view or open the case on the Advanced eDiscovery page in the Microsoft 365 compliance center. In general, most people in your organization can be added to the eDiscovery Manager subgroup.
 -  **eDiscovery Administrator.** Members of this role group can complete all case management tasks that an eDiscovery Manager can do. Additionally, an eDiscovery Administrator can:
    
     -  View all cases that are listed on the Advanced eDiscovery page.
     -  Manage any case in the organization after they add themselves as a member of the case.
     -  Access and export case data for any case in the organization.

> [!CAUTION]
> Because of the broad scope of access, an organization should have only a few admins who are members of the eDiscovery Administrators subgroup.

### Step 3: Configure global settings for Advanced eDiscovery

The last step to complete before people in your organization start to create and use cases is to configure global settings that apply to all cases in your organization. At this time, the only global setting that's available is attorney-client privilege detection. This setting enables the attorney-client privilege model to run when you analyze data in a review set.

**Additional reading.** For more information about setting up and using the attorney-client privilege detection model view, see [Set up attorney-client privilege detection in Advanced eDiscovery](/microsoft-365/compliance/attorney-privilege-detection).
