The Office Add-ins platform provides add-in commands so users can activate an add-in that opens a task pane or runs code behind the scenes (UI-less command). You can configure your add-in so the Office application renders a custom ribbon or menu command button&mdash;or even a group of buttons&mdash;depending on the tasks your add-in is making available to users.

## Excel, Word, PowerPoint, and OneNote

You can set up an add-in that a user can run by pressing a button in the:

- Office ribbon or command overflow menu&mdash;"PrimaryCommandSurface" extension point.
- Context menu&mdash;"ContextMenu" extension point.

An add-in command can also open a submenu with additional commands.

![Add-in commands in Excel](../media/add-in-commands.png)

*Add-in commands in Excel on Windows*

## Outlook

You can set up an add-in that a user can run by pressing a button in the Office ribbon or command overflow menu. You can configure your add-in to be available when the user is:

- Reading a message in the reading pane or in a pop-out window&mdash;"MessageReadCommandSurface" extension point.
- Composing a message&mdash;"MessageComposeCommandSurface" extension point.
- Creating or viewing an appointment or meeting as the organizer&mdash;"AppointmentOrganizerCommandSurface" extension point.
- Viewing a meeting as an attendee&mdash;"AppointmentAttendeeCommandSurface" extension point.

An add-in command can also open a submenu with additional commands.

![Add-in commands in Outlook](../media/commands-normal-collapsed.png)

*Add-in commands in Outlook on Windows*

## Where can you use add-in commands?

Add-in commands are available in Excel, Outlook, OneNote, PowerPoint, and Word as follows.

|Platform|Major Office version|Subscription or one-time purchase?|Notes|
|---|---|---|---|
|Windows|*Not applicable*|connected to Office 365 subscription|*Excluding OneNote*|
||2019|one-time purchase|*Excluding OneNote*|
||2016|one-time purchase|*Outlook only on Exchange 2016 (requires post-release update) or later.*|
||2013|one-time purchase|*Outlook only on Exchange 2016 or later. Requires post-release updates for Outlook and Exchange 2016.*|
|Mac|*Not applicable*|connected to Office 365 subscription|*Excluding OneNote*|
||2019|one-time purchase|*Excluding OneNote*|
||2016|one-time purchase|*Excluding OneNote*|
|iOS|*Not applicable*|connected to Office 365 subscription|*Outlook only*|
|Android|*Not applicable*|connected to Office 365 subscription|*Outlook only*|
|web browser|*Not applicable*|*Not applicable*||
