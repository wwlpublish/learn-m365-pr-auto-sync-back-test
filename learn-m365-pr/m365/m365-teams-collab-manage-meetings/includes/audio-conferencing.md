Audio Conferencing is the ability to join a Teams meeting from a regular phone and call out from a meeting to a phone number, allowing users to call in to meetings when they can't use a Teams client. Up to 1000 attendees can attend a Teams audio conference.

Calling in (also known as dialing in) to meetings is very useful for users who are on the road and can't attend a meeting using the Microsoft Teams app on their laptops or mobile devices. There are additional scenarios in which using a phone to attend a Microsoft Teams meeting can be a better option than using an app on a computer:

- When internet connectivity is limited
- When a meeting is audio only
- When there's an inability to join from Teams

The advantages are:

- The call quality is better when calling in.
- People can join a meeting *hands free* using Bluetooth devices.
- People find it's easier and more convenient for their situation.

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. One Audio Conferencing license is required for each person who is going to schedule/host an audio meeting. Meeting attendees who call in don't need any licenses assigned to them or any other setup.

After attendees have joined the meeting, they can also call out and invite other callers into a Microsoft Teams meeting.

## Audio Conferencing prerequisites

Before you can set up Audio Conferencing for Teams, consider the following questions:

- Is Audio Conferencing available for my country/region?
  
  To see if your area is covered, see the link below under **Learn more.**

- Do my users have the proper licensing for Teams Audio Conferencing?

  Audio Conferencing licenses are available as part of an Office 365 E5 subscription or as an add-on service for a Microsoft 365 Business Standard, Office 365 E1, or Office 365 E3 subscription.

- Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?

  Communications Credits are a convenient way to pay for Audio Conferencing and calling plan minutes.

## Core deployment decisions for Audio Conferencing

The settings most organizations want to change (if the Teams default settings don't meet their needs) are shown in this table.

| Setting | Considerations |
|---|---|
| Teams administrator roles |Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. |
| Conferencing bridges and phone numbers | Conferencing bridges let people call into meetings using a phone. You can use the default settings for a conferencing bridge or change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used. |
| Default and alternate languages |Teams Audio Conferencing lets you set up default and alternate languages for a conferencing bridge.  |
| Conferencing bridge settings | After setting up your conferencing bridge, including default and alternate languages, you should verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use. If they're not, you can change them. |
| Dial-in phone number settings for users who lead meetings | After you create your Audio Conferencing bridge, you need to set the toll and/or toll-free numbers that users who lead meetings will use. |
| Communications Credits | To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization.  |

## Additional deployment decisions

In addition to the core deployment decisions, it's important to also consider the following when deploying Audio Conferencing.

| Setting | Considerations |
|---|---|
| Outbound calling restriction policies |As an administrator, you can use outbound call controls to restrict the type of Audio Conferencing and end-user PSTN calls that are made by users in your organization. |
| Dial plans | A dial plan, as part of Phone System in Microsoft 365, is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing. |
| Monitor and troubleshoot meeting and call quality | Teams gives you two ways to monitor and troubleshoot call quality problems:  **Call Analytics** and **Call Quality Dashboard.** Both tools are described in the unit **Monitor call quality.**|

## Try it - configure audio conferencing

Now that you've learned the basics for audio conferences, it's time to try configuring the settings yourself.

In this exercise, you will:

- Get and configure the conferencing bridge number.
- Assign a dial-in number for meeting leaders.

Click [Configure Audio Conferencing for Teams](https://aka.ms/AudioConferencingInteractiveGuide?azure-portal=true) to start the exercise. Be sure to return to this page when you're finished with the exercise, to complete this module.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Learn how to deploy audio conferencing in Microsoft Teams](/MicrosoftTeams/deploy-audio-conferencing-teams-landing-page)
- [Audio Conferencing common questions](/MicrosoftTeams/audio-conferencing-common-questions)
- [Country and region availability for Audio Conferencing and Calling Plans](/MicrosoftTeams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)
