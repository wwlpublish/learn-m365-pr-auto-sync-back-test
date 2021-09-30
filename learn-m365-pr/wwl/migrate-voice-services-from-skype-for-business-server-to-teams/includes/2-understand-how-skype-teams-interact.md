If your organization uses Skype for Business Server today, and you implement Microsoft Teams, the two systems do not enter a coexistence state by default.

To coexist and allow the migration of users to Microsoft Teams, you must create a relationship between the two environments so they can share an address space, allow users to communicate with each other, external partners, and so that you can migrate users.

The diagram below illustrates how Microsoft Teams and Skype for Business interact.

[!div class="mx-imgBorder"]
![A diagram showing Office 365 and an On-Premises environment, linked by Azure Active Directory and Azure AD Connect, with an on-premises Skype for Business Server and Microsoft Teams. Two users (A and B) are homes in Microsoft Teams and two users (C and D) are homed on-premises.](../media/teams-skype-business-interaction.png)


In addition to configuring a Hybrid relationship between Skype for Business and Microsoft Teams, you must also enable Voice Services in Microsoft Teams.

Depending on how you choose to deploy Microsoft Teams, certain capabilities may overlap with the capabilities delivered by Skype for Business for a given user.

Initially, when you implement Teams with your on-premises Skype for Business Server environment, you will run Teams alongside Skype for Business, with the capabilities overlapping; however, a user can be assigned one of several coexistence modes (also known as upgrade modes) that were designed to ensure that these capabilities don't overlap for that user (in which case interoperability between Teams and Skype for Business is available).

For example, if you have significant Skype for Business Server on-premises assets with a complex Enterprise Voice deployment but want your users to enjoy modern meetings as quickly as possible, you might want to evaluate Meetings First as an alternative path.

Based on the coexistence mode you have configured, users will have the following capabilities enabled in Teams in Hybrid, prior to migration from Skype for Business Server:<br>

| **User's effective mode**| **Experience in Teams client**|
| :--- | :--- |
| Any Skype for Business mode| Calling, Chat, and self-presence are disabled.|
| SfBWithTeamsCollabAndMeetings| Meeting scheduling is available.|
| SfBWithTeamsCollab or SfBOnly| Meeting scheduling is not available.|

As you migrate users from Skype for Business Server to Microsoft Teams, users will enter Teams only mode. This allows calling, chat, and presence coexistence between users remaining on-premises. Additionally, configuration that restricted Meeting Scheduling in Teams is removed, and Skype for Business can no longer be used for new meetings a user creates.

