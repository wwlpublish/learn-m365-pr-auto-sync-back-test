Microsoft 365 connectors are used with both Microsoft Teams and Microsoft 365 groups, making it easier for all members to stay in sync and receive relevant information quickly.

Any member of a team can connect their team to popular cloud services with the connectors if the team permissions allow, and all team members are notified of activities from that service. Any team member with the permissions to add or remove can modify.

## Enable or disable connectors in Teams

Both Microsoft Teams and Exchange use the same connector model, which allows you to use the same connectors within both platforms.

Admins can use Exchange Online PowerShell to enable or disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox. It isn't possible to disable for few specific users.

To enable or disable a connector, execute the following commands in Exchange Online PowerShell:

* To enable connectors for Teams, execute the following commands:
  * `Set-OrganizationConfig -ConnectorsEnabled:$true`
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

* To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.

* To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.


### Publish connectors for your organization

If you want a custom connector to be available only to the users in your organization, you can upload a custom connector app to your organization's app catalog. 

After you upload the app package, the end-users can install the connector from the organization's app catalog and can configure and use the connector in a team.

To use connectors in a team or a channel:

1.  Open the More Options menu from the upper right corner of a channel.
2.  From the menu select **Connectors**
3.  In the **Connectors page** locate or search for the required connector app. 

    :::image type="content" source="../media/connectors-selection-ui.png" alt-text="Screenshot of connectors page.":::


4.  Click **Add** to use the connector, Configure the selected connector if required.

### Update URL of a connector

The Teams connectors are transitioning to a new URL to enhance security. During transition, you'll receive a notification to update the configured connector. Update your connector at the earliest to prevent any disruption to connector services.

To update your connector:

1.  In the connectors configuration page, check for **Attention Required** message next to the configured connector.
2.  To recreate the connection for incoming webhook connectors, select **Update URL** and use the generated webhook URL.
3.  For other connector types, remove the connector and recreate the connector configuration. A **URL is up-to-date** message appears.
