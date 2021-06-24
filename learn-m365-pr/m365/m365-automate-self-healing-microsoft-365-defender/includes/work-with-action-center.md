## What is Action center

Action center brings together remediation actions across Defender for Endpoint and Defender for Office 365. It defines a common language for all remediation actions and provides a unified investigation experience. The Action center provides a "single pane of glass" experience for incident and alert tasks such as:

- Approving pending remediation actions.
- Viewing an audit log of already approved remediation actions.
- Reviewing completed remediation actions.

:::image type="content" source="../media/4-action-center.png" alt-text="Screenshot showing the Action center":::

Because the Action center provides a comprehensive view of Microsoft 365 Defender at work, your security operations team can operate more effectively and efficiently.

## Action center permissions

To perform tasks, such as approving or rejecting pending actions in the Action center, you must have permissions to access the services where those actions were raised.  

- To manage actions in **Microsoft Defender for Endpoint** you'll need a Security Administrator role assigned in one of these: Azure Active Directory, Microsoft 365 admin center, or the active remediation actions role assigned in Microsoft Defender for Endpoint.
- To manage actions in **Microsoft Defender for Office 365** you'll need the Security Administrator role assigned in either Azure Active Directory, or Microsoft 365 admin center, or the Search and Purge role assigned in the Security and Compliance Center.
- All users who have a Global Administrator role assigned in their Azure AD can approve or reject any pending actions in the Action center.

## Using the Action center

When you open the Action center page, you'll initially see all of the currently active Pending actions. You can also switch the view to the review all historical actions.

:::image type="content" source="../media/4-action-center-pending-history.png" alt-text="Screenschot showing fragment of the action center with pending and history tabs,.":::

### Pending tab

Displays a list of actions that require attention. You can approve or reject actions one at a time, or select multiple actions if they have the same type of action (such as Quarantine file).

> [!NOTE]
> Make sure to review and approve (or reject) pending actions as soon as possible so that your automated investigations can complete in a timely manner.

### History tab

Serves as an audit log for actions that were taken, such as:

- Remediation actions that were taken as a result of automated investigations
- Remediation actions that were taken on suspicious or malicious email messages, files, or URLs
- Remediation actions that were approved by your security operations team
- Commands that were run and remediation actions that were applied during Live Response sessions
- Remediation actions that were taken by your antivirus protection

### Customizing your Action center experience

Regardless of which tab you use, you can adapt and vary the data presented in your view by changing the columns, number of items per page and advanced filtering.

:::image type="content" source="../media/4-action-center-filters.png" alt-text="Screenshot fragment, showing the options to vary and filter the action center pending view. ":::

Through the advanced filtering capabilities of Action center you can:

- Select a column heading to sort items in ascending or descending order.
- Use the time period filter to view data for the past day, week, 30 days, or 6 months.
- Choose the columns that you want to view.
- Specify how many items to include on each page of data.
- Use filters to view just the items you want to see.
- Select Export to export results to a .csv file.

### Review pending actions in Action center

It's good practice to have your SOC and security teams approve or reject pending actions as soon as possible so that your automated investigations can proceed and complete in a timely manner.

To review and manage pending actions, you'll use Action center and select a pending action item. This will open a new pane where you can see information on the action and where you can take the appropriate steps to process it.

:::image type="content" source="../media/4-action-center-details-pane.png" alt-text="Action Center pending action item details pane.":::

From here, you can open the investigation page.

:::image type="content" source="../media/4-open-investigation-page.png" alt-text="An example of the investigation page":::

And if the investigation has been completed, you can approve or reject the action.  Approving the action applies it immediately.

From this pane, you can also open the advanced hunting query tools to hunt for similar incidents.

:::image type="content" source="../media/4-advanced-hunting.png" alt-text="Screenshot showing the advanced hunting.":::

Lastly, you can open the action in explorer: a powerful, real-time tool that lets your security operations teams investigate and respond to threats in the Security and Compliance Center.

:::image type="content" source="../media/4-explorer-screen.png" alt-text="Screenshot showing the explorer real-time tool in security and compliance center":::

### Undo completed actions

If you’ve determined that a device or a file isn't a threat, you can undo remediation actions that were taken, whether those actions were taken automatically or manually. In the Action center, on the History tab, you can undo any of the following actions:

- **Action Source**

  - Automated investigation
  - Microsoft Defender Antivirus
  - Manual response actions

- **Supported Actions**

  - Isolate device
  - Restrict code execution
  - Quarantine a file
  - Remove a registry key
  - Stop a service
  - Disable a driver
  - Remove a scheduled task
