The Outlook JavaScript APIs give your add-ins access to the user's mailbox, messages, and appointments in Outlook. An Outlook add-in can get the content and properties of a message or appointment. An add-in can also manage the content, formatting, and structure of a message or appointment that is being composed.

## Object model

To understand the Outlook APIs, you must see how the main components of a mailbox relate to each other.

- The **Mailbox** object enables you to handle authentication, manage a selected item, and view user profile details.
- The **Item** object represents the selected message or appointment that the user is reading or composing.

Most of the APIs are organized around whether the user is reading or composing an item and if they're the item creator or a recipient.

|Item type|Modes|
|---|---|
|Message|Read, Compose|
|Appointment (or meeting)|Attendee (read), Organizer (compose)|

Using the Outlook APIs, you can manage many properties of an email or appointment.

## Key features

### Authentication

### Contextual add-ins

### Module add-ins

## Get started developing Outlook add-ins

Use the Yeoman Generator tool to start developing an Outlook add-in. You can use a template as your base then add your functionality.
