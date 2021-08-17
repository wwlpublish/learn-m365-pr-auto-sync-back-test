If your organization uses Skype for Business today and you're starting to use Teams alongside Skype for Business—or you're starting to upgrade to Teams—it's important to understand how the two applications coexist, when and how they interoperate, and how to manage users' migration all the way to their eventual upgrade from Skype for Business to Teams.

The purpose of the Skype for Business coexistence modes is to provide a predictable experience for end users as organizations transition from Skype for Business to Teams. Depending on how you deploy Teams, the chat, calling, and meeting capabilities in Teams may overlap with the same capabilities delivered by Skype for Business for a given user.

For an organization moving to Teams, the TeamsOnly mode is the final destination for each user, though not all users need to be assigned TeamsOnly (or any other mode) at the same time. Prior to users reaching TeamsOnly mode, you can use any of the coexistence modes to ensure predictable communication between users who are TeamsOnly and users who aren't yet.

When a user is in any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings), all incoming chats and calls are routed to the user's Skype for Business client. To avoid end-user confusion and ensure proper routing, calling and chat functionality in the Teams client are disabled in the Skype for Business modes. Similarly, meeting scheduling in Teams is explicitly disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and explicitly enabled when a user is in the SfBWithTeamsCollabAndMeetings mode.

Because presence indicates when a user is reachable through chat and calling, when chat and calling are disabled, self-presence in Teams (that is, showing whether a user is available in the user's picture) is also hidden.

You can learn more about coexistence and interoperability in the module, **Understand coexistence and interoperability.**

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Teams client experience and conformance to coexistence modes](/MicrosoftTeams/teams-client-experience-and-conformance-to-coexistence-modes)
- [Understand Microsoft Teams and Skype for Business coexistence and interoperability](/MicrosoftTeams/teams-and-skypeforbusiness-coexistence-and-interoperability)
