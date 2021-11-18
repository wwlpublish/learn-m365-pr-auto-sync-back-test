When creating a resource mailbox, you can also configure settings that determine how the resource mailbox will respond to meeting requests. For example, you can:

 -  Configure resource mailboxes to automatically process incoming meeting requests for all users.
 -  Restrict who can book the meeting room.
 -  Configure delegates who must approve all meeting requests.
 -  Configure the resource mailbox to accept only certain types of meetings. For example, you can configure a conference room to automatically accept incoming meeting requests but not accept recurring meeting requests.

You can create and manage resource mailboxes in the Exchange admin center (EAC) or with Exchange PowerShell using the **New-Mailbox** cmdlet with the **-Room** parameter for a room mailbox or the **-Equipment** parameter for an equipment mailbox.

For example, to create a new room mailbox with the name ConfRoom1 and the display name “Conference Room 1”, you would run the following command:

```powershell
New-Mailbox -Name ConfRoom1 -DisplayName "Conference Room 1" -Room
```

To create a new equipment mailbox with the name “Projector1” and display name “Projector 1”, you would run the following command:

```powershell
New-Mailbox -Name Projector1 -DisplayName "Projector 1" -Equipment
```

### Manage resource mailboxes

When managing a resource mailbox through the EAC, you can configure the following settings that define how the mailbox will accept meeting requests.

:::row:::
  :::column:::
    **Settings**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    General
  :::column-end:::
  :::column:::
    Specify Name, capacity, hide from address lists, department, company, address book policy, and custom attributes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Booking delegates
  :::column-end:::
  :::column:::
    Accept booking requests automatically, select delegates, or customize an acceptance policy for this mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Booking options
  :::column-end:::
  :::column:::
    Allow repeated meetings, only schedule during working hours, maximum booking lead time, maximum meeting duration, and a customized reply to the meeting organizer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Contact information
  :::column-end:::
  :::column:::
    Add street, Zip/post code, city and so on if required.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Email address
  :::column-end:::
  :::column:::
    Add further email addresses if required.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MailTip
  :::column-end:::
  :::column:::
    Create a MailTip to provide additional information that users can see when they select this address in an email.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mailbox delegation
  :::column-end:::
  :::column:::
    Configure Send As, Send on Behalf Of, and Full Access permission for this mailbox, as with shared mailboxes.
  :::column-end:::
:::row-end:::


You can also configure several additional settings that control how the resource mailbox will respond to meeting requests. These settings can be configured in Exchange PowerShell by using the **Set-CalendarProcessing** cmdlet. Some of the available options include:

:::row:::
  :::column:::
    **Configuration option**
  :::column-end:::
  :::column:::
    **Sample command**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow conflicting meetings.
  :::column-end:::
  :::column:::
    Set-CalendarProcessing –id MeetingRoom1 –AllowConflicts $true
  :::column-end:::
  :::column:::
    If an organization wants to allow room bookings even when there's a conflict in the booking calendar so that conflicts will be manually resolved by a booking delegate.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow certain users to request meetings that don't follow the policies involving maximum lead time or maximum meeting limits.
  :::column-end:::
  :::column:::
    Set-CalendarProcessing –id MeetingRoom1 –RequestOutOfPolicy pattif
  :::column-end:::
  :::column:::
    If an organization needs specific users to have permission to book a room, despite any booking policies.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevent the meeting room from accepting meeting requests automatically.
  :::column-end:::
  :::column:::
    Set-CalendarProcessing -Identity MeetingRoom1 -AutomateProcessing:None
  :::column-end:::
  :::column:::
    If an organization needs to assign a delegate who will be responsible for room booking.
  :::column-end:::
:::row-end:::


Messaging administrators should consider the following factors when designing how meeting requests will be accepted:

 -  **Restricting who can schedule a resource mailbox**. You might accept the default settings for most resources in the organization but consider restricting who can book heavily used or important resources. For example, if you use a resource room mailbox to manage the schedule for a large conference room, you may want to restrict who can book meetings in the conference room.
 -  **Restricting resource mailbox scheduling and usage**. You may want to set restrictions on the time of day when meetings can be booked with a resource, or restrict the meeting length or meeting recurrence.
 -  **How to configure the automatic acceptance policy for the resource mailbox**. By default, all resource mailboxes are configured to accept all new appointment requests and to block conflicting requests. You can change this so that all meeting requests are accepted as tentative, or to allow users to book the meeting resource for the same time.
