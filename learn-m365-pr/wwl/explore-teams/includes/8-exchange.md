Another core service of Microsoft Teams is Exchange Online. When you create a team, a corresponding Microsoft 365 Group and a mailbox for the Group are automatically created behind the scene. This group mailbox provides messaging capabilities and a mail-based storage location for data processed and produced in Teams. 

## Exchange Mailbox for Teams

Every Microsoft 365 Group that is associated with a team has a corresponding group mailbox in Exchange Online that provides resources to use messaging and a calendar for planning meetings. Data created in Teams is stored in different Exchange locations:

- **Emails sent to the team.** When an email is sent to the Microsoft 365 Group email address, the email is stored in the Microsoft 365 Group mailbox. A copy is distributed to the user mailboxes of all subscribers.

- **Chat messages.** Chat messages and users’ chat history are stored in their user mailboxes. 

- **Channel messages.** Messages posted into channel conversations are stored in a hidden folder in the Microsoft 365 Group mailbox.

- **Meeting information.** When planning meetings for a team, the meetings are stored as meeting elements in the Microsoft 365 Group mailbox.

- **User profile picture.** When a user changes his or her profile picture in Teams, the picture is also stored in the user’s mailbox.

- **Call History and Voicemail.** Call history and voice mail messages are delivered to the associated user’s mailbox.

- **Connector configuration.** The configuration data for connectors is stored in the Microsoft 365 Group mailbox. An example would be the connector data required to subscribe to RSS feeds.
 
These Exchange locations support the security and compliance tools provided by Microsoft 365, such as retention policies, eDiscovery, legal holds, and data loss prevention.
 
## Teams in a Hybrid Exchange Deployment

Teams can be deployed with Exchange Hybrid, where either some or all mailboxes are hosted on an on-premises Server(s). In a hybrid deployment, Exchange must be deployed so that it’s ready to use the supported Teams feature for storing and discovering data from on-premises Exchange locations.

For more information, see [Configure an Exchange hybrid organization for use with Microsoft Teams](/microsoftteams/exchange-hybrid-organization).
