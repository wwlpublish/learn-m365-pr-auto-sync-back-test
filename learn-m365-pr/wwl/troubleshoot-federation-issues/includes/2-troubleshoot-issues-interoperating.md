Teams and Skype for Business can coexist within the same organization. Interoperability is the term used for communication between Teams and Skype for Business when both systems are installed.

When the two systems coexist, a user can be assigned a coexistence mode (sometimes called an upgrade mode), either by default or by an administrator:

- **Islands** Each client application, either Skype for Business or Teams, operates as a separate island. Skype for Business clients communicate with other Skype for Business clients. Teams clients talk to other Teams clients. This is the default mode, and requires users to have both clients open at all times. Federated users (people outside your organization) have their messages delivered to Skype for Business. Islands mode does not provide interoperability – each system communicates only with clients of the same system.
- **Teams Only** Users upgrade to Teams and use Teams for most of their communication. They use Skype for Business to only to communicate with users who have not yet upgraded. Teams Only mode makes Teams the default app for the SIP/Tel protocol. Links in a user's contact card in Outlook for calling or chat are handled by Teams.
- **Skype for Business Only** Users only use Skype for Business for chat, meetings and calling, and do not use Teams. You can use this mode while planning your deployment of Teams. 
- **Skype for Business With Teams Collaboration** This mode introduces users to Teams in a controlled way. This mode leaves Skype for Business unchanged for chat, calling, and meeting capabilities, and adds Teams collaboration capabilities:

    - Teams and channels.
    - Access to files in Microsoft 365 or Office 365.
    - Applications. This includes Teams communications capabilities, such as private chat, calling, and scheduling meetings.
   
    You should note that Teams private chat, calling, and scheduling meetings are off by default in this mode.

- **Skype for Business With Teams Collaboration and Meetings** This mode is also known as **Meetings First** because it accelerates the adoption of Teams meeting capability. This coexistence mode is especially useful for organizations with Skype for Business on-premises deployments with Enterprise Voice. These organizations are likely to take some time to upgrade to Teams and want to benefit from the superior Teams meetings as soon as possible.

To assign the upgrade mode for users, go to the **Microsoft Teams Admin center**. In the left navigation, select **Org-wide settings > Teams upgrade** and set the **Coexistence mode**.

## Investigate chat issues with Skype for Business

Depending on which client people are using, and whether they are communicating in-tenant or cross-tenant, chat will either be plain text or have rich formatting options available.

> [!NOTE] 
> Skype for Business Online should upgrade to Teams, or for specific cases migrate to Skype for Business on-premises.

From|To|In-tenant, pure online, or hybrid |Cross-tenant federation configured in both tenant
---|---|---|---
Teams |Teams|Native chat with rich formatting | Plain text chat
Teams |Skype for Business on-prem|Plain text chat|Plain text chat
Skype for Business on-prem|Skype for Business on-prem|Plain text chat|Plain text chat
Skype for Business on-prem|Teams|Plain text chat|Plain text chat

## SIP federated providers in Skype for Business Server

You can configure Skype for Business Server to allow users to chat with people using public providers. You must enter the provider’s Edge server fully qualified domain name, and the default verification level **Allow users to communicate only with people on their Contacts list who use this provider**. By default, no public providers are enabled.

## Troubleshoot Federation issues between Teams and Skype or Skype for Business

Microsoft Teams users can federate with Skype for Business on-premises users using External Access. External access uses the SIP Interoperability Gateway of Skype for Business Online. This allows Teams users to chat and join audio or video meetings with external Skype for Business users.

If someone cannot reach a Skype for Business user in another tenant, check the **Teams Admin center > External access**. Both toggle options should be set to **On**.  

### Setting up federation for Skype for Business Online users

Skype for Business online is being retired. You can either deploy Skype for Business server in your organization or upgrade users to Microsoft Teams, which is the preferred route. Remember that users will be automatically scheduled for an assisted upgrade if you haven’t already upgraded them by the end of July 2021.

To deploy and configure an on-premises Skype for Business Server in your organization you must:

- Have at least one Standard Edition server or one Enterprise Edition Front End pool deployed in your organization.
- Enable internal user accounts for Skype for Business Server.
- Deploy at least one Edge Server and the other components required to support external user access.
- Enable federation support and configure access control by federated domains.
- Enable external user access for users in your organization.

For links to help you with these steps, see the **Learn More** section.

## Native interop and interop escalation

Native and interop escalation are used depending on the coexistence modes assigned to users.
A **native interop** experience occurs within the client when one user is in Skype for Business, and the other is in Teams. Native interop does require users to start another client, but lets them chat in the client they're currently using.

Native interop allows Skype for Business users to chat one-on-one with Teams users, and vice versa. An interop chat goes through an interop gateway, which is part of Teams cloud service. Interop chats are plain text - rich text and emoticons are not supported. Users are notified when their conversation is an interop conversation.

An **interop escalation** experience occurs when a user performs an advanced action, such as sharing their desktop. The client facilitates the creation of a meeting which users can join to continue the experience. The meeting is created on the platform of the initiator of the action and those not on that platform receive a meeting join link. When they select the link, they are joined to the meeting in a compatible client such as a browser, web app, or full client, depending on the configuration.

Both Skype for Business and Teams clients are supported in interoperability experiences in-tenant, and for cross-tenant (federated) communication.

## Troubleshooting InterOp chat scenarios

### You are working in Microsoft Teams and messages from an external contact are not being delivered

Check whether you are in **Islands** or **Teams Only** mode. If you are in **Islands** mode, and the external contact is using Skype for Business, messages will be delivered to Skype for Business and not Microsoft Teams. To solve this problem, upgrade to **Teams Only** mode so that all messages and calls from outside your organization are delivered to Teams.

### You are unable to start a chat conversation using Skype for Business

Check the users upgrade mode. **Teams Only** modes does not allow a user to initiate a Skype for Business chat, call, or meeting.

> [!TIP] 
> Coexistence modes will continue to exist after the retirement of Skype for Business Online on July 31, 2021. Upgrade users to Microsoft Teams before that date, otherwise they will be automatically scheduled for an assisted upgrade. It is recommended that you plan and implement the upgrade yourself, using Microsoft’s upgrade guidance. See the **Learn More** section for more information.