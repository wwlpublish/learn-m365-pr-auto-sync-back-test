Audio Conferencing is the ability to join a Teams meeting from a regular phone and call out from a meeting to a phone number. This functionality enables users to call in to meetings when they can’t use a Teams client. 

Calling in to meetings is useful for users who are on the road and can’t attend a meeting using the Microsoft Teams app on their laptops or mobile devices. There are other scenarios in which using a phone to attend a Microsoft Teams meeting can be a better option than using an app on a computer, such as:

- When internet connectivity is limited
- When a meeting is audio only
- When there’s an inability to join from Teams

The advantages of calling in to meetings include:

- The call quality is better when calling in.
- People can join a meeting *hands-free* using Bluetooth devices.
- People find it’s easier and more convenient for their situation.

 Audio Conferencing must be set up for people who plan to schedule or lead meetings. One Audio Conferencing license is required for each person who is going to schedule/host an audio meeting. Meeting attendees who call in don't need a license assigned to them or any other setup.

After attendees have joined a Microsoft Teams meeting, they can call out and invite other callers into the meeting.

:::image type="content" source="../media/audio-conference.png" alt-text="Screenshot of Audio Conferencing for Teams.":::   ‎

## Deployment decisions for Audio Conferencing

Organizations should consider the following areas and questions before setting up Audio Conferencing for Microsoft Teams:

### Audio conferencing licenses

Audio Conferencing licenses are available as part of a Microsoft 365 or  Office 365 E5 subscription or as an add-on service for a Microsoft 365 Business Standard, E1, or E3 subscription.  

* Is Audio Conferencing available for my country/region?
	
	To find out the availability, see [Country and region availability for Audio Conferencing and Calling Plans](/MicrosoftTeams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans?azure-portal=true).

* Do my users have the proper licensing for Teams Audio Conferencing?
* Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?

### Teams administrator roles 

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization.

* Who will be assigned the Teams Communications Administrator role?
* Who will be assigned the Teams Communications Support Engineer role?
* Who will be assigned the Teams Communications Support Specialist role?


### Conference bridges and phone numbers 

Conference bridges let people dial into meetings using a phone. Organizations can use the default settings for a conference bridge. If necessary, they can change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used. 

* Do I need to add new conference bridge numbers?
* Do I need to port numbers to use with audio conferencing?

There are two types of audio conferencing phone numbers that can be assigned to a conference bridge:  

* **Shared phone numbers** are those phone numbers that can be shared with other Microsoft 365 or Office 365. You can't change the languages that are used when someone calls in to one of these numbers.

* **Dedicated phone numbers** are those phone numbers that are only available to users within your organization. You can change the languages that are used when someone calls in to one of these numbers.

### Default and alternate languages 

Teams Audio Conferencing lets organizations set up default and alternate languages for a conference bridge. It's only possible to change the languages of **Dedicated** audio conferencing numbers. 

* Which languages should I choose for auto attendant greetings?

### Conference bridge settings 

After setting up your conferencing bridge, including default and alternate languages, you should verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use. If they're not, you can change them.

* Will attendees hear a notification when a user joins or exits a meeting?
* What is the required length of the PIN that a meeting organizer uses to start the meeting?

### Dial-in phone number settings for users who lead meetings 

After you create your Audio Conferencing bridge, you need to set the toll and/or toll-free numbers that users who lead meetings will use.

* Which conference bridge numbers will I assign to each user who leads meetings?

### Communications Credits

To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization. 

* Are Communications Credits required for my Audio Conferencing implementation?
* Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?
* If they're required, how much should I purchase?
* Do I want to configure an automatic recharge amount?

### Outbound calling restriction policies

As an administrator, you can use outbound call controls to restrict the type of audio conferencing and end user PSTN calls that can be made by users in your organization.

* Will I limit the type of outbound calls that are allowed?

### Dial plans

A dial plan, as part of Teams Phone in Microsoft 365 or Office 365, is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

* Does my organization need a customized dial plan?	
* Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?	

## Configure dedicated conference bridge numbers

A dedicated number is a number that's only available to an organization's users. To use a dedicated number, an organization must first get the number, assign it to its conference bridge, and then assign the number to each person who will lead meetings.

After an organization has its number, it should assign the number to its conference bridge by completing the following steps:

1. Sign into the **Microsoft Teams admin center**.
2. Select **Meetings**, and then select **Conference bridges**.
3. On the **Conference bridges** page, select **+ Add**.
4. In the drop-down list, select either **Toll number** or **Toll-free number**.
5. On the **Add phone number** pane, select the phone number you want to add, and then select **Apply**.

	:::image type="content" source="../media/conference-bridge-add-number.png" alt-text="Screenshot of Conference bridges.":::   ‎

## Change the default conference bridge number

The default phone number of an organization's conference bridge defines the caller ID that will be used when an outbound call is placed by a participant or the organizer from within a meeting.

Only a service toll number can be set as the default number for an organization's conference bridge. Service toll-free numbers can't be set as the default number for a conference bridge. 

To change the default number for an audio conference bridge, complete the following steps:

1. On the **Conference bridges** page, highlight the service toll number that you want to configure as the default.
‎
2. Select **Set as default** on the menu bar.

	:::image type="content" source="../media/default-conference-bridge-number.png" alt-text="Screenshot of Default conference bridge number.":::  
## Configure conference bridges settings 

Conference bridge settings allow organizations to change the settings for meeting notifications and the meeting join experience, and set the length of the PINs that are used by meeting organizers in Microsoft Teams. Complete the following steps to configure the conference bridge settings:

1. On the **Conference bridges** page, select **Bridge settings**.
2. On **Bridge settings** pane, you may choose to configure the following:

	- **Meeting entry and exit notifications**. An organization can turn this setting On or Off, depending on whether it wants users who have already joined the meeting to be notified when someone enters or leaves the meeting. If this setting is turned On, the following options can be updated:
	- **Entry/exit announcement type**. Select one of the following options:
		- **Names or phone numbers**: When users dial in to a meeting, their phone number will be played when they join it.
		- **Tones**: When users dial in to a meeting, an audio tone will be played when they join it.
	- **Ask callers to record their name before joining the meeting**. If you turn this setting Off, callers won't be asked to record their name before they join a meeting.
	- **Pin length**. Set the PIN length from 4 to 12; the default value is 5.
	- **Automatically send emails to users if their dial-in settings change**. This option should be enabled or disabled.

3. Select **Apply** to confirm the settings.

Organizations can also use PowerShell to update these settings by using the ```Set-CsDialinConferencingBridge``` cmdlet. 

:::image type="content" source="../media/conference-bridges.png" alt-text="Screenshot of Conference Bridges settings.":::

## Assign dial-in phone numbers for users who lead meetings

After an organization has created an Audio Conferencing bridge, it must complete the following steps to set the toll and toll-free numbers for all users who lead or schedule meetings:

1. From the Teams admin center, select **Users** > **Manage users**, select the user from the list.
2. Select **Edit** next to **Audio Conferencing**, and then in the Audio Conferencing pane, choose a number in the Toll number and Toll-free number lists.
3. Select **Apply**.

	:::image type="content" source="../media/assign-user-conference-bridges.png" alt-text="Screenshot of Assign dial-in phone numbers for users.":::


