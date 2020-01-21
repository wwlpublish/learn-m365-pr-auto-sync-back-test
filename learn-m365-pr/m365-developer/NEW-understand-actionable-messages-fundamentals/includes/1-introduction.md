Actionable Messages in Outlook enables you to extend the functionality of an email message to increase engagement and improve productivity.

## What are Actionable Messages in Outlook?

An Actionable Message in Outlook replaces or enhances an HTML email body with an adaptive card. This adaptive card can provide the user with succinct information, and allow the user to take action on that information without leaving Outlook. For example, Actionable Messages in Outlook could be used to:

- Send a survey to a group, allowing them to quickly respond in the email message itself, without having to browse to or login to a website.
- Quickly approve a code check-in or expense report.
- Add actions to automated email that a service desk ticketing system sends to the employees responsible for handling service requests. These actions could allow employees to assign, redirect, or add notes to the ticket.

An Actionable Messages in Outlook solution has two main components as follows.

- An application or service that sends HTML-formatted email with Adaptive Card markup.
- A web API that is called when the user activates the actions in the Actionable Message.

The mail sender application sends the Actionable Message to recipients. The recipient opens the mail, and activates one of the actions in the Adaptive Card. For example, the user may want to assign a service ticket to herself. When the user activates the action, the Office 365 servers call the web API specified in the Adaptive Card markup and processes the response. Finally, the card is updated in the user's mailbox to indicate the response.

## Why use Actionable Messages in Outlook?

Key benefits of Actionable Messages in Outlook include:

- Quickly build UX using Adaptive Card technology: A regular email with a link to an application means having to build an application UX for the user that works on all form factors. With Adaptive Cards, you design the card once, and the clients present it in the way that makes sense for the client.
- Stream-line business processes: Users are more likely to promptly take a requested action if it is immediately available to them in the request. If they have to open a separate application or web page, they are more likely to postpone (and possibly forget) taking action.
- Up-to-date information: A standard email can only have the latest data available at the time it was sent. If the user reads the mail the following morning, the data contained may no longer be accurate. With Actionable Messages, you have the ability to query for the latest data when the user opens the message.

## Where are Actionable Messages in Outlook supported?

Actionable Messages are supported in all Office 365 versions of Outlook, including mobile and web versions.

- Outlook on the web for Office 365
- Office 365 ProPlus
- Outlook on iOS
- Outlook on Android
