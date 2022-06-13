Microsoft Purview Compliance Manager is a feature in the Microsoft Purview compliance portal. It's designed to help organizations manage their compliance requirements with greater ease and convenience. Compliance Manager can help an organization complete the following steps in its compliance journey:

1.  Take inventory of its data protection risks.
2.  Manage the complexities of implementing controls.
3.  Stay current with regulations and certifications.
4.  Report to auditors.

Compliance Manager helps simplify compliance and reduce risk by providing:

 -  Pre-built assessments for common industry and regional standards and regulations.
 -  Custom assessments to meet your unique compliance needs (available assessments depend on your licensing agreement; [learn more](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true)).
 -  Workflow capabilities to help you efficiently complete your risk assessments through a single tool.
 -  Detailed step-by-step guidance on suggested improvement actions to help you comply with the standards and regulations that are most relevant for your organization. For actions that are managed by Microsoft, you’ll see implementation details and audit results.
 -  A risk-based compliance score to help you understand your compliance posture by measuring your progress in completing improvement actions.

These features are maintained in the Compliance Manager dashboard, which is examined in the next unit. The dashboard:

 -  Shows an organization its current compliance score.
 -  Helps it see what needs attention.
 -  Guides it to key improvement actions.

### Understanding your compliance score

Compliance Manager awards points to an organization for completing improvement actions taken to comply with a regulation, standard, or policy. It then combines those points into an overall compliance score. Each action has a different effect on the total score, depending on the potential risks involved. The compliance score can help an organization prioritize which action to focus on to improve its overall compliance posture.

Compliance Manager determines an organization's initial score based on the Microsoft 365 data protection baseline. This baseline is a set of controls that includes key regulations and standards for data protection and general data governance.

### Key elements of Compliance Manager

Compliance Manager uses several data elements to help an organization manage its compliance activities. Because Compliance Manager assigns, tests, and monitors compliance activities, it’s helpful to have a basic understanding of the key elements used in these tasks. These elements are introduced in the following sections.

#### Controls

A control is a requirement of a regulation, standard, or policy. It defines how an organization assesses and manages:

 -  system configuration.
 -  organizational process.
 -  people responsible for meeting a specific requirement of a regulation, standard, or policy.

Compliance Manager tracks the following types of controls:

 -  **Microsoft managed controls**. Controls for Microsoft cloud services, which Microsoft is responsible for implementing.
 -  **Your controls**. These controls are sometimes referred to as customer managed controls. They're implemented and managed by your organization.
 -  **Shared controls**. These controls are managed by both the organization and Microsoft. They each share responsibility for their implementation.

**Additional reading**. For more information, see:

 -  [Monitor progress of your controls](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true).
 -  [Learn how Compliance Manager continuously assesses controls](/microsoft-365/compliance/compliance-score-calculation?azure-portal=true).

#### Assessments

An assessment is grouping of controls from a specific regulation, standard, or policy. Completing the actions within an assessment help organizations meet the requirements of a standard, regulation, or law. For example, an organization may complete all the actions in an assessment that will help to bring its Microsoft 365 settings in line with ISO 27001 requirements.

Assessments have several components:

 -  **In-scope services**. The specific set of Microsoft services applicable to the assessment.
 -  **Microsoft managed controls**. Controls for Microsoft cloud services, which Microsoft implements on your behalf.
 -  **Your controls**. These controls are sometimes referred to as customer managed controls. They're implemented and managed by your organization.
 -  **Shared controls**. These controls are managed by both the organization and Microsoft. They each share responsibility for their implementation.
 -  **Assessment score**. Shows your progress in achieving total possible points from actions within the assessment that are managed by your organization and by Microsoft.

When an organization creates assessments, it must assign them to a group. An organization can configure groups in whatever way is most logical for its business. For example, an organization may group assessments by audit year, region, solution, and teams, or some other way. Once an organization creates groups, it can filter its Compliance Manager dashboard to view its score by one or more groups.

**Additional reading**. For more information, see [Build and manage assessments in Compliance Manager](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true).

#### Templates

Compliance Manager provides templates to help organizations quickly create assessments. An organization can modify these templates to create an assessment optimized for its business needs. It can also build a custom assessment by creating a template with its own controls and actions. For example, an organization may want a template to cover an internal business process control, or a regional data protection standard that isn’t covered by one of Microsoft's 325+ pre-built assessment templates.

Additional reading. For more information, see:

 -  [View the list of assessment templates provided by Compliance Manager](/microsoft-365/compliance/compliance-manager-templates-list?azure-portal=true).
 -  [Get detailed instructions for creating and modifying templates for assessments](/microsoft-365/compliance/compliance-manager-templates?azure-portal=true).

#### Improvement actions

Improvement actions help centralize an organization's compliance activities. Each improvement action provides recommended guidance that’s intended to help the organization align with data protection regulations and standards. Improvement actions can be assigned to users in the organization to perform implementation and testing work. Documentation, notes, and record status updates can also be stored within the improvement action.

### Start a premium assessments trial

The Compliance Manager premium assessments trial is a great way to quickly set up assessments that are most relevant to your organization. Microsoft's library of over 300 templates correspond to governmental regulations and industry standards around the world. Learn more about the [premium assessments trial](/microsoft-365/compliance/compliance-easy-trials-compliance-manager-assessments?azure-portal=true).

An organization can start its trial directly from Compliance Manager and set up recommended assessments by following these steps:

1.  On the **Compliance Manager dashboard**, the **Overview** tab displays a notification message about the premium assessments trial. Within this notification, select **Start trial**. Doing so initiates a trial activation wizard. This wizard asks questions to help Microsoft recommend assessments for your organization.
2.  On the **Activate trial** page, select **Next** to begin your free 90 day premium assessments trial and continue with creating assessments.
3.  Select one or more industries that identify your organization, and then select **Next**.
4.  Select one or more regions for your organization's location, and then select **Next**.
5.  On the **Choose assessments** page, select the dropdown arrow next to **Recommended templates** to see the list of assessments that Microsoft thinks apply to your organization. Check the boxes next to the templates you want to use for creating assessments, and then select **Next**.
6.  Review your final selections and select **Add Recommended Assessments** to create your new assessments.

Learn more about getting started with assessments by visiting the [Assessments page](/microsoft-365/compliance/compliance-manager-setup?azure-portal=true) section below.

### Settings for automated testing and user history

The Compliance Manager settings in the Microsoft Purview compliance portal allow organizations to enable and disable automatic testing of improvement actions. The settings also allow organizations to manage the data of users assigned to improvement actions, including the ability to reassign improvement actions to a different user. Only people with a global administrator or Compliance Manager Administrator role can access the Compliance Manager settings.

> [!WARNING]
> The automated testing feature isn't available to customers in GCC High and DoD environments because Secure Score isn't available in these environments. GCC High and DoD customers must manually implement and test their improvement actions.

### Set up automated testing

Compliance Manager detects signals from other Microsoft Purview solutions that an organization subscribes to, including:

 -  data lifecycle management
 -  information protection
 -  Microsoft Purview Data Loss Prevention
 -  communication compliance
 -  insider risk management

In each improvement action's details page, the **Testing logic** field on the **Testing** tab will show what's required in the other solution for the action to pass and earn points toward the organization's compliance score.

Compliance Manager also detects signals from complementary improvement actions that are also monitored by [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score?azure-portal=true). Compliance Manager uses these signals to automatically test certain improvement actions for an organization. Doing so helps maximize efficiency in its compliance activities. When an improvement action is successfully tested and implemented, an organization receives the full number of points. In turn, these points get credited to the organization's overall compliance score.

Automatic testing is turned On by default for organizations new to Compliance Manager. When an organization first deploys Microsoft 365, it takes approximately seven days to fully collect data and factor it into the organization's compliance score. When automated testing is turned on, the action’s test date won’t be updated, but its test status will update. When new assessments are created, scores automatically include Microsoft control scores and Secure Score integration.

#### Manage automated testing settings

The global administrator for an organization can change the settings for automated testing at any time. They can turn off automated testing for common improvement actions. Or, they can turn it on for individual actions. Follow the instructions below to change your automated testing settings.

1.  Select **Settings** in the **Microsoft Purview compliance** portal.
2.  On the **Settings** page, select **Compliance Manager**.
3.  Select **Testing source** from the navigation pane.
4.  Select the applicable button to either:
     -  Turn on automatic testing for all improvement actions.
     -  Turn off automatic testing for all improvement actions.
     -  Turn on automatic testing by individual improvement action.
5.  If you select **Turn on per improvement action**, a list will show all the available improvement actions to choose from. Check the box next to any action you want automatically tested.
6.  Select **Save** to save your settings. You’ll receive a confirmation message at the top of your screen that your selection was saved. If you receive a failure notice, try again.

> [!CAUTION]
> Only the global administrator can turn on or off automatic updates for all actions. The Compliance Manager Administrator can turn on automatic updates for individual actions, but not for all actions globally.

**Additional reading**. For more information, see:

 -  [Learn more about how continuous monitoring contributes to your compliance score](/microsoft-365/compliance/compliance-score-calculation?azure-portal=true).
 -  [Learn more about designating a testing source for an improvement action](/microsoft-365/compliance/compliance-manager-improvement-actions?azure-portal=true).

### Manage user history

The Manage user history settings help you quickly identify which users have worked with improvement actions in Compliance Manager. The identifiable user data associated with improvement actions includes:

 -  Any implementation and testing work done.
 -  Documents they uploaded.
 -  Any notes they entered.

Understanding and retrieving this type of data may be necessary for your organization’s own compliance needs.

The user history settings also allow you to reassign all improvement actions from one user to another. Complete the following steps to find the user history settings:

1.  Select **Settings** in the **Microsoft Purview compliance** portal.
2.  On the **Settings** page, select **Compliance Manager**.
3.  Select **Manage user history** on the navigation pane.

The **Manage user history** page displays a list of all users by email address who are assigned to an improvement action. Use the **Search** button to quickly find a specific user by typing in their email address.

To the right of each user’s email address, the **Select** drop-down menu provides options to:

 -  **Export a report**. You can export an Excel file containing a list of improvement actions currently assigned to a user. The report also lists any evidence files uploaded by that user. This information can help you reassign open improvement actions. The report reflects the improvement action’s status as of its creation date. It isn't a historical report of all previous changes to its status or assignment (learn how to [export a report from your improvement actions page](/microsoft-365/compliance/compliance-manager-improvement-actions?azure-portal=true)).
 -  **Reassign improvement actions**. You can reassign improvement actions from one user to another. When you reassign an action, the document upload history doesn't change. However, the name of the user who originally uploaded the documentation no longer appears within the improvement action. The new assignee receives an email that they've been assigned to an improvement action. The email contains a direct link into the improvement action's details page.
    
        > [!WARNING]
        > If you reassign an action that has a pending update, the direct link to the action in the reassignment email will break if the update is accepted after reassignment. You can fix this situation by reassigning the action to the user after the update is accepted. Learn more about [updates to improvement actions](/microsoft-365/compliance/compliance-manager-improvement-actions?azure-portal=true).
 -  **Delete history**. Deleting a user’s history will remove the user as an owner of improvement actions. It will also remove the user's name from all other fields in Compliance Manager. When you delete a user’s history, the improvement actions they owned won't display an **Assigned to** value until a new user is assigned. Any documents uploaded to the improvement action will show **User removed** in place of the deleted user’s name. Deleting user history is permanent.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”