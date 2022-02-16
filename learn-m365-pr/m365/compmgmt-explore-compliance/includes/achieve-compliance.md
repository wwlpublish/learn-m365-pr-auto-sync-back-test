## Improvement actions summary

The Compliance Manager **Improvement actions** page lists the actions you can take to improve your compliance score. It shows all the improvement actions managed by your organization. Improvement actions managed by Microsoft are not shown here. Rather, they can be viewed within each assessment. You can filter, group, sort, and search items on the improvement actions page to customize your view. You can also conduct a search based on the improvement action title and filter them in a variety of ways. Clicking on an individual improvement action provides detailed information about that action and guidance on how to implement it.

  :::image type="content" source="../media/improvement-actions.png" alt-text="Compliance Manager Improvement actions summary." lightbox="../media/improvement-actions.png":::

## Improvement action details

Some improvement actions can be assigned to users in your organization to implement and test. You can also store documentation, notes, and record status updates in the improvement action. Improvement action achievement points updates can take up to 24 hours to be reflected in your compliance score. Some improvement actions are automatically monitored, while others depend on you to update status. The image below shows the **Apply Sensitivity Labels to Protect Sensitive or Critical Data** improvement action. The **Edit status** button on the improvement action details page indicates the improvement action status is updated manually.

  :::image type="content" source="../media/sensitivity-labels.png" alt-text="Apply Sensitivity Labels to Protect Sensitive or Critical Data view." lightbox="../media/sensitivity-labels.png":::

For improvement actions not monitored automatically, Microsoft Compliance Manager includes workflow functionality to help manage the improvement action to completion. Generally speaking, the workflow can be broken down into an implementation phase and a test phase, both of which are managed by clicking **Edit status** on the improvement action's details page. Each user assigned to the improvement action must have the permissions required to view and edit their assignment, and only one user can be assigned to an improvement action at a time. Anyone with editing permissions can edit the action, not just the user assigned. Here are the tasks broken down by phases.

### Implementation phase

- **Assign:** You can do the work to complete the improvement action yourself or assign it to another user like a business owner, data admin, or IT professional. Email is sent to the user that informs them of their assignment and includes a link to additional details.
- **Implement:** The user completing the improvement action can use the guidance under **Implementation** to complete the task. All actions include implementation recommendations. Technical actions also include a link to where the action can be performed and where to learn more.
- **Document:** Documentation includes the evidence the organization satisfies the regulations or standards associated with the action. The formal documentation should be produced during the implementation phase so it can be verified during the test phase. Upload proof you completed the action by clicking on **Manage documents.** Additional notes can also be added using the links provided.
- **Update status:** Implementation status can be updated at any time during the process but should be done at least once after the implementation is complete. An **Implementation date** can only be added when **Implementation status** is set to **Implemented** or **Alternative Implementation.** The test status fields are locked until **Implementation date** is provided.

### Test phase

- **Assign:** The intent of the test phase is to allow someone acting in an oversight capacity, like an auditor or assessor, to confirm the evidence provided during the implementation proves successful completion of the action. The assignee in the implement phase is replaced with the individual responsible for this phase. Email is sent to the assigned user just like it is in the implement phase.
- **Test:** The tester evaluates the evidence to determine if it is satisfactory.
- **Document:** Additional evidence can be uploaded to the improvement action at any time, but documentation in this step should consist mainly of adding information to the Test notes.
- **Update status:** Status must be set to Passed for the action to achieve points that contribute to your compliance score. If set to Failed, the assessor can assign the action back to someone else to do additional work.
