Calendars provide essential time management and collaboration functionality for users. It's therefore important that you know how to identify and troubleshoot calendaring problems in Exchange Online.

Certain problems with calendars might be related to sign-in problems, which we've already explored. In addition, Client Access Rules might impinge on calendaring function by controlling access from configured protocols, such as Outlook on the web.

It's always worth reviewing the necessary Client Access Rules, Conditional Access policies, and mailbox policies that might restrict calendar access. After you've reviewed these fundamentals, then use the following guidance to attempt to resolve specific calendaring issues.

## Use the Calendar Checking Tool for Outlook

A general troubleshooting tool for calendar-related problems is the Calendar Checking Tool for Outlook. After installation, the tool opens an Outlook profile, opens the Outlook Calendar, and then checks several things such as:

- Permissions
- Free/busy publishing
- Auto booking

Then, the tool checks each item in the calendar folder for problems that cause items to seem to be missing or that might otherwise cause problems in the Calendar.

> [!TIP]
> You can download the tool here: [CalCheck](https://github.com/rtopken/CalCheck/). 

To use this tool, open an elevated Command Prompt, and run the `CalCheck.exe` tool. The tool generates a report that you can use to help diagnose problem items or identify trends.

The tool runs the following calendar-specific tests which are then logged in a report:

- Permissions on the calendar.
- The total number of items in the calendar folder.
- Delegates on the calendar.
- Free/busy publishing information.
- Direct Booking settings for the mailbox or calendar.

Additional guidance on using this tool is located in this knowledge base article: [Information about the Calendar Checking Tool for Outlook (CalCheck)](https://support.microsoft.com/topic/information-about-the-calendar-checking-tool-for-outlook-calcheck-0d2ccac8-f8dd-9289-82cc-943650e36a76)

## Troubleshoot calendar sharing permissions issues

Sharing calendar information is very common. It's a useful way for users to determine their respective availability. If, after sharing a calendar, users don't have the expected permissions, then use Outlook to verify the permissions:

1. Open **Outlook** and navigate to the appropriate calendar.
1. Right-click the calendar, point to **Share** and then click **Calendar Permissions**.
1. Click **OK** when you've made any required changes.

:::image type="content" source="../media/calendar-permissions.png" alt-text="A screenshot that displays the Calendar Properties dialog box. ":::

> [!TIP]
> You can also use the CalCheck.exe tool to verify permissions. 

Your users will quite likely want to share their calendars with users from other organizations. From time to time, users might experience problems when sharing calendars, or accessing shared calendars. A common reason for problems relating to sharing calendars with external users is Sharing policies. Sharing policies control how your users share their calendars with people outside your organization.

You define the rules that make up a sharing policy. These rules include:

- The domains that users can share with
- The levels of access to calendars:

    - Free/busy information with time only
    - Free/busy information with time, subject, and location
    - Free/busy information, including time, subject, location, and title

To create Sharing polices, you can use both the Exchange Admin Center and Exchange Online PowerShell.

1. In the **Exchange Admin Center**, select **Organization**, and then select **Sharing**.
1. In the details pane, you can review or create policies.

You can use the `New-SharingPolicy` cmdlet to create policies with PowerShell.

> [!TIP]
> This document provides more guidance on creating policies: [Create a sharing policy in Exchange Online](/exchange/sharing/sharing-policies/create-a-sharing-policy).

You can create two basic types of policy:

- **Organization Sharing**. Enables free/busy and other calendar information sharing between federated Exchange organizations.
- **Individual Sharing**. Allow users to share calendar information and contacts with external organizations.

The Default Sharing Policy (DEFAULT) enables sharing with all domains (anonymous) and  enables sharing of All calendar information including time, subject, location, and title. It's an Individual Sharing policy.

You'll need to check which sharing policy is assigned to a user. You can use the following command to check:

``` powershell
Get-Mailbox username | fl *sharing*
```

Now, open the Exchange Admin Center and determine the settings in the applied policy. If there's a restriction in the assigned policy, consider reviewing and, if necessary, updating the settings to enable the desired level of access. Either that, or assign another sharing policy to the user.

## Troubleshoot broken manager/delegation issues

Your users experience a problem when Outlook can't correctly retrieve the delegate information from the local free/busy object in the mailbox. This problem might occur after the manager's or delegate's mailbox is moved.

To resolve this issue, set a new temporary delegate in the manager's mailbox by using Outlook on the web to force updating of the local free/busy object. Use these steps:

1. Sign in to the manager's mailbox through Outlook on the web.
1. Open the calendar and select **Share** from the menu at the top.
1. Enter a user or group, and then select **Delegate** from the drop-down menu.
1. Select **Share**, and then select **Done**.

The manager should now be able to return to Outlook to continue management of the delegates from the client.

## Troubleshoot Resource Booking Assistant issues

When your users attempt to use Resource Booking to schedule a resource, such as a conference room, with Microsoft Outlook, they might notice the following behavior when Resource Booking is unsuccessful:

- The Resource does not automatically respond to meeting requests.
- The Resource does not correctly respond to meeting requests.
- The Resource is double-booking.

This problem is usually caused by incorrect mailbox configuration, or mail flow set up with resource mailboxes.

The following high-level steps might help resolve this problem:

1. Ensure the mailbox is configured as a resource.
1. Confirm the mailbox is configured to AutoAccept so that both the calendar attendant (which updates the calendar) and resource booking attendant (which evaluates the request against the policies) are enabled:

    ``` powershell
    Get-CalendarProcessing <Identity> | fl AutomateProcessing
    Set-CalendarProcessing <Identity> -AutomateProcessing AutoAccept
    ```

These two steps might resolve the issue, but if not, continue with the additional guidance documented here: [Resources in Exchange don't respond to meeting requests](https://support.microsoft.com/topic/resources-in-exchange-don-t-respond-to-meeting-requests-e6d24af5-36ae-5d87-b615-f292f3953dac).

## Determine why content for a shared calendar is not updated

If users don't receive shared calendar updates, it could be related to the update failing to propagate automatically from the originator of the update in Outlook. For example, a user creates a new appointment in a shared calendar, but the update doesn't sync automatically to Exchange Online. Consequently, other users are unaware of the update. However, if, when a user presses F9, updates are propagated, then the problem might be related to two settings in Outlook:

- Download shared folders
- Turn on shared calendar improvements

To resolve the issue, perform the following steps:

1. Open **Outlook** and select **File**, point to **Accounts Settings**, and then click **Account Settings**.
1. Select the appropriate account, and then click **Change**.
1. In the **Exchange Account Settings** dialog box for the selected account, click **More Settings**.
1. In the **Microsoft Exchange** dialog box, select the **Advanced** tab.
1. Clear the **Download shared folders** check box.
1. Enable the **Turn on shared calendar improvements** check box.
1. Click **OK**, click **Next**, and then click **Close**.
1. Close and reopen **Outlook**.

:::image type="content" source="../media/advanced-settings.png" alt-text="A screenshot that displays the Microsoft Exchange dialog box with the settings configured as per the preceding text.":::

## Review and analyze diagnostic logs

We discussed earlier in this module how to enable and review Microsoft Outlook logs on Windows. If you've been unable to resolve your user's calendaring issue using the procedures discussed in this unit, then consider reviewing troubleshooting logs. In addition, you can also access specific calendar logs that track all calendar items and meeting messages.

### Review calendar and mailbox diagnostics

You can also use the `Get-CalendarDiagnosticObjects` cmdlet to collect a range of calendar logs. Some of the data that's returned includes:

- **AppointmentState**. Values are:

    - 1 = The appointment is a meeting
    - 2 = The appointment has been received
    - 4 = The appointment has been cancelled
    - 8 = the appointment is a forwarded appointment

- **CalendarLogTriggerAction**. The action that's taken on the item, for example:

    - Create
    - Update

- **ClientInfoString**. The entity that made the change, for example:

    - Client=OWA
    - Client=WebServices

- **MeetingRequestType**. Possible types are:

    - 1 = The meeting message is a meeting request
    - 65536 = The meeting message is a full update to an existing meeting
    - 131072 = The meeting message is an informational update to an existing meeting
    - 262144 = The meeting message is a silent update
    - 524288 = The update is outdated
    - 1048576 = The meeting message is forwarded to a delegate, and the copy is marked as informational

- **OriginalLastModifiedTime**. Used as the primary sort field to order the events.
- **ResponseType**. Possible response types are:

    - 0 = The organizer hasn't received a response
    - 1 = The organizer's copy of the meeting
    - 2 = Tentative
    - 3 = Accept
    - 4 = Decline
    - 5 = The attendee hasn't responded

- **ResponsibleUserName**. The LegacyExchangeDN value of the user who made the change.

For example, to retrieve calendar data for a user called **AdeleV** for a meeting called **Sales Meeting**, run the following command:

``` powershell
Get-CalendarDiagnosticObjects -Identity "Adele Vance" -Subject "Sales Meeting" -ExactMatch $true
```

The output might look something like the following:

:::image type="content" source="../media/calendar-log.png" alt-text="A screenshot that displays a Windows PowerShell window with the output from the preceding command. ":::

In addition, the `Export-MailboxDiagnosticLogs` cmdlet enables you to retrieve logging information from a user's mailbox. For example, the following command retrieves and displays the calendar permissions for a user called Adele Vance:

``` powershell
Export-MailboxDiagnosticLogs -ComponentName CalendarPermissions -Identity "Adele Vance"
```

The following component names are useful when diagnosing problems with calendaring:

- CalendarPermissions
- CalendarSharingLocalFolder
- FreeBusyPublishingAssistantQuickLog
- InternetCalendar
- InternalCalendarSharingMigration
- OnlineMeetings

## Learn more

- [Export-MailboxDiagnosticLogs](/powershell/module/exchange/export-mailboxdiagnosticlogs)
- [Sharing policies in Exchange Online](/exchange/sharing/sharing-policies/sharing-policies)
- [Calendar Checking Tool for Outlook](https://www.microsoft.com/download/details.aspx?id=28786)
- [Information about the Calendar Checking Tool for Outlook (CalCheck)](https://support.microsoft.com/topic/information-about-the-calendar-checking-tool-for-outlook-calcheck-0d2ccac8-f8dd-9289-82cc-943650e36a76)