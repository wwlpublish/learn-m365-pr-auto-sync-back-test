Microsoft Secure Score is a web-based tool that:

 *  analyzes an organization’s Microsoft 365 security based on security settings across the tenant.
 *  assigns a score that can be tracked over time.
 *  creates a roadmap of recommended actions (ranked by priority) to help an organization mitigate security risks.

Like a credit score, the Secure Score framework is based on a score relative to:

 *  what features have been enabled by the organization.
 *  what features are available in the service.
 *  what the risks might look like.

The Microsoft Secure Score console enables you to select various tabs to display Secure Score data. The following sections describe each of these tabs.

### Dashboard tab

Organizations are assigned points for various aspects of their security framework. These points are accumulated into a final total, which is referred to as the organization's Secure Score. Microsoft 365 Global administrators can access Microsoft Secure Score, which initially displays the Dashboard tab. This tab provides a summarized view into an organization’s security posture.

### Overview tab 

The Secure Score tool provides organizations with an action roadmap. This roadmap lists tasks that an organization can complete to reduce security risks. To help you quickly find the information you need, the actions are organized into the following groups in the Overview tab:

 *  **Identity.** Displays Azure AD accounts and roles.
 *  **Data**. Displays Microsoft Information Protection.
 *  **Device.** Doesn't currently display improvement actions.
 *  **App**. Displays email and cloud apps, including Microsoft 365 and Microsoft Defender for Cloud Apps.
 *  **Infrastructure.** Doesn't currently display improvement actions.

In the Microsoft Secure Score Overview tab, you can see how points are split between these groups and what points are available. The Overview tab is also the place to get an all-up view of the organization's total Secure Score. This tab also displays the historical trend of an organization's Secure Score with benchmark comparisons, and improvement actions that can be taken to improve its score. The actions are ranked by priority.

### Improvement actions tab

The Improvement actions tab lists the security recommendations that address possible attack surfaces. It also displays the status of each action (completed, not completed, resolved through third party, and ignored). You can search, filter, and group all the improvement actions.

#### Ranking

The Improvement actions tab ranks each improvement action. The ranking assigned to each action is based on:

 *  the remaining points left to achieve for that action
 *  implementation difficulty
 *  user impact
 *  complexity of the action

The highest ranked improvement actions have a large number of points remaining with low difficulty, user impact, and complexity.

#### Actions

The Improvement actions tab displays the actions recommended by the Secure Score tool. Actions labeled as **Not Scored** aren't tracked by Microsoft Secure Score. You can still complete the suggested action, but completing them won't affect your score. If an action becomes tracked by Microsoft Secure Score in the future and you've already completed it, your secure score will automatically reflect the change.

:::image type="content" source="../media/securescoreactions-2cec22d1.png" alt-text="screenshot showing actions that can be taken in secure score.":::




When you select a specific improvement action, a fly out window appears. You can select one of the following options related to the action:

 *  **View settings.** Select this option when you want to complete the action. This option takes you to the configuration screen, where you can make the recommended change. You then gain the points that the action is worth, which is visible at the top of the fly out. Points may take up to 24 hours to update.
 *  **Resolved through third party.** Select this option when the improvement action has already been addressed by a third-party application or software. You gain the points that the action is worth, so your secure score better reflects your overall security posture. If a third party no longer covers the control, you can mark the improvement action as "Not complete." Keep in mind, Microsoft has no visibility into whether the score requirements have been met if the improvement action is marked as "Resolved through third party."
 *  **Ignore.** Select this option when you've decided to accept the risk and not enact the improvement action. Once you ignore an improvement action, the total number of secure score points you can achieve is reduced. You can view this action in history or undo it at any time.
 *  **Review.** Select this option if the improvement action requires you to regularly review a part of your environment to gain and keep points. For example, mailbox forwarding rules should be reviewed on a weekly basis to ensure data isn't being stolen from your network. You don't need to make any changes, but an action must be performed. If you regularly review the rules, you'll receive the points. If you don't regularly review the rules, the score is reduced.

### History tab

The History tab displays a graph of your organization's Secure Score over time. Below the graph is a list of all the actions taken in the selected time range and their attributes, such as resulting points and category. You can customize a date range and filter by category.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”
