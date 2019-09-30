Add-in commands are UI elements that extend the Office UI and start actions in your add-in. You can use add-in commands to add a button on the ribbon or an item to a context menu. When users select an add-in command, they initiate actions such as running JavaScript code, or showing a page of the add-in in a task pane. Add-in commands help users find and use your add-in, which can help increase your add-in's adoption and reuse, and improve customer retention.

## Add-in commands in Excel, Word, PowerPoint, and OneNote

You can configure an add-in so that a user can run it by selecting:

- Office application's ribbon or command overflow menu button
  - Key manifest setting: `<ExtensionPoint xsi:type="PrimaryCommandSurface">`.
- Context menu item
  - Key manifest setting: `<ExtensionPoint xsi:type="ContextMenu">`.

An add-in command can also open a submenu with additional commands.

**Note**: Content add-ins do not currently support add-in commands.

The following image shows three add-in commands (custom buttons) added to the **Data** tab of the Excel ribbon.

![Add-in commands in Excel](../media/add-in-commands.png)

*Add-in commands in Excel on Windows*

## Add-in commands in Outlook

You can configure an add-in so that a user can run it by selecting a button in the Office ribbon or command overflow menu when the user is:

- Reading a message in the reading pane or in a pop-out window.
  - Key manifest setting: `<ExtensionPoint xsi:type="MessageReadCommandSurface">`.
- Composing a message.
  - Key manifest setting: `<ExtensionPoint xsi:type="MessageComposeCommandSurface">`.
- Creating or viewing an appointment or meeting as the organizer.
  - Key manifest setting: `<ExtensionPoint xsi:type="AppointmentOrganizerCommandSurface">`.
- Viewing a meeting as an attendee.
  - Key manifest setting: `<ExtensionPoint xsi:type="AppointmentAttendeeCommandSurface">`.

An add-in command can also open a submenu with additional commands.

The following images show three add-in commands (custom buttons) added to the ribbon in Outlook. In the first image, the buttons are rendered in a regular state; in the second image, the buttons are rendered in a collapsed state.

![Add-in commands in Outlook](../media/commands-normal-collapsed.png)

*Add-in commands in Outlook on Windows*

## Where can you use add-in commands?

Add-in commands are available in Excel, Outlook, OneNote, PowerPoint, and Word as follows.

|Platform|Major Office version|Subscription or one-time purchase?|Notes|
|---|---|---|---|
|Windows|*Not applicable*|connected to Office 365 subscription|*Not available in OneNote*|
||2019|one-time purchase|*Not available in OneNote*|
||2016|one-time purchase|*Only available in Outlook on Exchange 2016 (requires post-release update) or later. Not available in Office other applications.*|
||2013|one-time purchase|*Only available in Outlook on Exchange 2016 or later. Requires post-release updates for Outlook and Exchange 2016. Not available in other Office applications.*|
|Mac|*Not applicable*|connected to Office 365 subscription|*Not available in OneNote*|
||2019|one-time purchase|*Not available in OneNote*|
||2016|one-time purchase|*Not available in OneNote*|
|iOS|*Not applicable*|connected to Office 365 subscription|*Only available in Outlook*|
|Android|*Not applicable*|connected to Office 365 subscription|*Only available in Outlook*|
|web browser|*Not applicable*|*Not applicable*|*Available in all supported Office applications*|
