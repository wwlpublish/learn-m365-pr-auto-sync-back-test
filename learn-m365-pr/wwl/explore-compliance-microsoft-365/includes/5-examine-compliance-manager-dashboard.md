The Compliance Manager dashboard:

 -  shows an organization's current compliance score.
 -  provides visibility into what needs attention.
 -  provides guidance to key improvement actions.

The following screenshot displays the top portion of the Compliance Manager dashboard. This portion of the dashboard shows the company's overall compliance score and key improvement actions that are suggested for improving the company's state of compliance.

:::image type="content" source="../media/compliance-manager-dashboard-top-half-1b420828.png" alt-text="Screenshot of the top half of the Compliance Manager dashboard showing Contoso's overall compliance score." lightbox="../media/compliance-manager-dashboard-top-half-1b420828.png":::


The following screenshot displays the bottom portion of the Compliance Manager dashboard. This portion of the dashboard shows the breakdown of the company's compliance score by each compliance category. This design provides visibility into those areas of compliance that a company is doing well at, and those areas that could use improvement.

:::image type="content" source="../media/compliance-manager-dashboard-bottom-half-b962abb3.png" alt-text="Screenshot of the bottom half of the Compliance Manager dashboard showing Contoso's compliance score breakdown by compliance component." lightbox="../media/compliance-manager-dashboard-bottom-half-b962abb3.png":::


**Additional viewing**. Select the following link to watch a short video on how [Compliance Manager can help simplify how an organization manages compliance](https://www.microsoft.com/videoplayer/embed/RE4VdoO?postJsllMsg=true?azure-portal=true).

The remainder of this unit examines the sections that make up the Compliance Manager dashboard.

#### Overall compliance score

An organization's compliance score is featured prominently at the top. It shows a percentage based on points achievable for completing improvement actions that address key data protection standards and regulations. Points from [Microsoft actions](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true), which are managed my Microsoft, also count toward an organization's compliance score.

When an organization comes to Compliance Manager for the first time, its initial score is based on the [Microsoft 365 data protection baseline](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true). This baseline assessment, which is available to all organizations, is a set of controls that includes common industry regulations and standards. Compliance Manager scans an organization's existing Microsoft 365 solutions. It then provides an initial assessment based on the company's current privacy and security settings. As the company adds assessments that are relevant to its business, its score becomes more meaningful.

**Additional reading**. For more information, see [Understand how your compliance score is calculated](/microsoft-365/compliance/compliance-score-calculation?azure-portal=true).

#### Key improvement actions

This section lists the top improvement actions an organization can take right now to make the largest positive effect on its overall compliance score.

#### Solutions that affect your score

This section highlights solutions containing improvement actions that can positively affect an organization's score. It also displays the number of outstanding improvement actions in those solutions.

#### Compliance score breakdown

This section gives an organization a more detailed view of its score in two different ways:

 -  **Categories**. Shows the percentage of an organization's overall score within data protection categories, such as "protect information" or "manage devices."
 -  **Assessments**. Shows the percentage of an organization's progress in managing assessments for particular compliance and data protection standards, regulations, or laws.

#### Filtering the Compliance Manager dashboard view

An organization can filter its dashboard view to see only the items related to particular:

 -  regulations and standards
 -  solutions
 -  type of action
 -  assessment groups
 -  data protection categories

Filtering the view in this way will also filter the score on an organization's dashboard. It will show how many points the organization has achieved out of total possible points based on its filter criteria.

> [!NOTE]
> After an organization applies a filter, it will see its score adjusted in real time. At that point, the compliance score percentage and breakdown information, and the improvement actions and solutions, will only pertain to data covered by the filter criteria. If a user signs out of Compliance Manager, the filtered view remains when they sign back in.

### Improvement actions tab

The Improvement actions tab shows all the improvement actions that are managed by an organization. Actions that are managed by Microsoft can be viewed within each assessment (learn more about [Microsoft actions](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true)).

Working with improvement actions helps to centralize an organization's compliance activities and align it with data protection regulations and standards. Each improvement action gives detailed implementation guidance and a link to launch the user into the appropriate solution. Improvement actions can be assigned to an organization's users to perform implementation and testing work. Documentation, notes, and record status updates can also be stored within the improvement action.

If you have a long list of actions on your Improvement actions tab, it may be helpful to filter your view.

The default view for the Improvement actions tab doesn't show improvement actions with a test status of **Passed**. To view actions that have passed testing, check the **Passed** box in the **Filters** flyout pane.

> [!NOTE]
> Only actions with a test status of **Passed** count toward your score.

Some actions may show a **Pending update** label. Learn more about [updates to improvement actions](/microsoft-365/compliance/compliance-manager-improvement-actions?azure-portal=true).

The Improvement actions tab shows the following data points for each improvement action:

 -  **Products**. The product being evaluated.
 -  **Points achieved**. The number of points achieved out of the total available by completing the action.
 -  **Regulations**. The regulations or standards pertaining to the action.
 -  **Group**. The group to which you assigned the action.
 -  **Solutions**. The solution where you can go to perform the action.
 -  **Assessments**. The assessments that contain the action.
 -  **Categories**. The related data protection category (such as, protect information, manage devices, and so on).
 -  **Test status**:
     -  **None**. no status update recorded.
     -  **Not assessed**. Testing hasn't started.
     -  **Passed**. Implementation successfully tested.
     -  **Failed low risk**. Testing failed, low risk.
     -  **Failed medium risk**. Testing failed, medium risk.
     -  **Failed high risk**. Testing failed, high risk.
     -  **Out of scope**. The action isn't in scope for the assessment. As such, it doesn't affect your score.
     -  **To be detected**. For manual test, indicates an action has been implemented but not tested; for automated test, indicates an action is waitin**g** for automation result.
     -  **Could not be detected**. Automated status can't be determined.
     -  **Partially tested**. Automated scoring that awards partial points.
 -  **Action type**. Indicates whether the improvement action is technical or non-technical.
     -  **Technical**. A technical status means the action can be implemented within a solution or product.
     -  **Non-technical**. A non-technical means the action would be implemented outside of a technical solution.
 -  **Assigned to**. The person this action has been assigned to, if applicable.
 -  **Testing source**. Indicates whether the testing source for the action is manual, automatic, or inherited from a parent.

**Additional reading**. For more information, see [See how to assign and perform work on improvement actions](/microsoft-365/compliance/compliance-manager-improvement-actions?azure-portal=true).

### Solutions tab

The Solutions tab shows the share of earned and potential points as organized by solution. Viewing the remaining points and improvement actions from this view helps an organization understand which solutions need more immediate attention.

The Solutions tab displays an organization’s solutions that are connected to improvement actions. it lists:

 -  Each solution’s contribution to the organization's overall compliance score.
 -  The points achieved within that solution.
 -  The total points possible within that solution.
 -  The remaining number of improvement actions grouped in that solution that can increase the organization's score.

There are two ways you can take action from this screen:

 -  On the row of your intended solution, under the **Remaining actions** column, select the hyperlinked number. You’ll see a filtered view of the improvement actions screen showing untested improvement actions for that solution.
 -  On the row of your intended solution, under the **Open solution** column, select **Open**. You’ll see the solution or location in the Microsoft Purview compliance portal where you can take the recommended action.

### Assessments tab

The Assessments tab lists all the assessments that an organization has set up. An organization's compliance score denominator is determined by all its tracked assessments. As more assessments are added:

 -  More improvement actions will be listed in the Improvement actions tab.
 -  The organization's compliance score denominator increases.

The activated templates counter near the top of the page shows the number of active assessment templates currently in use out of the total number of templates available for the organization to use. For more information, see [Template availability and licensing](/microsoft-365/compliance/compliance-manager-templates?azure-portal=true).

The Assessments tab summarizes the following key information about each assessment:

 -  **Assessment**. Name of the assessment.
 -  **Status**:
     -  **Complete**. All controls have a status of “passed,” or at least one is passed and the rest are “out of scope”.
     -  **Incomplete**. At least one control has a status of “failed".
     -  **None**. All controls haven't been tested.
     -  **In progress**. Improvement actions have any other status, including “in progress,” “partial credit,” or “undetected.
 -  **Assessment progress**. The percentage of the work done toward completion, as measured by the number of controls successfully tested.
 -  **Your improvement actions**. The number of completed actions to satisfy implementation of the organization's controls.
 -  **Microsoft actions**. The number of completed actions to satisfy implementation of Microsoft controls.
 -  **Group**. Name of the group the assessment belongs to.
 -  **Product**. Associated product, such as Microsoft 365 or another product defined for assessment.
 -  **Regulation**. The regulatory standard, policy, or law that applies to the assessment.

By default, the [Data Protection Baseline](/microsoft-365/compliance/compliance-manager-assessments?azure-portal=true) assessment is displayed on the Assessments tab. Compliance Manager also provides several pre-built [templates](/microsoft-365/compliance/compliance-manager-templates-list?azure-portal=true) for building assessments.

### Assessment templates tab

A template is a framework for creating an assessment in Compliance Manager. The Assessment templates tab displays a list of templates and key details. The list includes templates provided by Compliance Manager and any templates an organization has modified or created. You can apply filters to find a template based on certification, product scope, country, industry, and who created it.

The activated templates counter near the top of the page shows the number of active assessment templates currently in use out of the total number of templates available for your organization to use. For more information, see [Template availability and licensing](/microsoft-365/compliance/compliance-manager-templates?azure-portal=true).

Select a template from its row to bring up its details page. The details page contains a description of the template and further information about certification, scope, and controls details. From this page you can select the appropriate buttons to create an assessment, export the template data to Excel, or modify the template.

### Alerts tab

Select the Alerts tab in Compliance Manager to view and manage your alerts. The Alerts tab contains a table that lists each alert generated by an alert policy. It also displays the severity of each alert, the triggering event (for example, an action's score change), and date of the alert.

To view an individual alert, select its row in the table. A flyout pane will appear that shows all details on the **Overview** tab of the pane. The **Events log** tab displays actions taken by users that triggered the alert.

The **Action** button at the bottom of the pane provides options to:

 -  Assign the alert to a user for follow-up.
 -  Email the user whose actions generated the alert.
 -  View the details of the policy that generate the alert.

You can also take the same actions by selecting the round button that appears to the left of the alert name when you hover over its row. Then select one of the buttons near the top of the table, above the filters.

### Alert policies tab

Select the Alert policies tab in Compliance Manger to view and manage your alert policies. The Alert policies tab contains a table that lists all the policies created by the organization. From this tab, you can create new policies, edit existing policies, and change activation status, and delete policies.

The **Status** column will display one of the following values:

 -  **Active**. Means the policy is in effect and triggering alerts when conditions are met.
 -  **Inactive**. Means the policy exists but is't generating alerts.

The policies table also displays the severity of the policy and the date the policy was last modified.

To view an individual policy's details, select its row in the table. A flyout pane will appear that shows all details. Select the **Action** button at the bottom of the pane. Then select from options to edit the policy, view its alerts, or delete it. The commands to add, edit, delete, activate, and disable are also available near the top of the table, above the filters.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”