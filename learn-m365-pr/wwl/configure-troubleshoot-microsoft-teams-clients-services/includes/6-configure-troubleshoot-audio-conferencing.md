When users are unable to use a computer to attend a meeting, audio conferencing can provide the solution. Instead of using the full Teams client, users can dial-in using their phones. 

## Setup audio conferencing

To setup audio conferencing in Teams, you’ll need to complete the following high-level steps:

1. Configure conference bridges. Conferencing bridges allow users to dial into meetings through their phones. When configuring Audio Conferencing in your Office 365 environment, you’ll receive phone numbers for your users from what is called an audio-conferencing bridge. 

   > [!TIP]
   > A conferencing bridge can contain one or more phone numbers.

   These phone numbers are used when the users dial in to a meeting. As an admin, you can choose to continue using the default settings for a conferencing bridge, or you can change the phone numbers (toll and toll-free) and other settings (as the PIN or the languages that are used). 

2. Configure bridge settings. You can control meeting entry and exit notifications, announcement types, whether users must record their names before joining, PIN length, and email notifications, as displayed in the following screenshot. 

   :::image type="content" source="../media/conference-bridge.png" alt-text="A screenshot that displays the Bridge settings blade in Conference bridges. Default values are selected.":::

3. Assign licenses. Audio Conferencing licenses are available as part of an Office 365 E5 subscription or as add-on licenses to an existing subscription. 
4. Enable audio conferencing for users. You must ensure that any meetings organizers have audio conferencing enabled on their accounts, configured with the appropriate dial-in settings. 
5. Manage audio conference policy settings. In the appropriate meeting policy, configure whether dial-in users can bypass the lobby by enabling the **Allow dial-in users to bypass the lobby** setting in the **Participants & guests** section.

> [!NOTE]
> Audio Conferencing supports up to 250 phone attendees.

## Configure user settings

Before users can enable audio conferencing for their meetings, they must be assigned a license.

### Enable audio conferencing

To enable audio conferencing for a meeting organizer, in the Microsoft Teams admin center: 

1. Select the appropriate user in **Users**. 
2. On the **Account** tab, verify the **Audio Conferencing** is **On**, and that related settings are configured. 
3. If not, select **Edit**, and then, on the **Audio Conferencing** blade, enable **Audio conferencing**.
4. Select a suitable **Toll number**, and choose whether to enable the **Include toll free numbers in meeting requests from this user** setting. If necessary, select a suitable toll free number.
5. Optionally enable the **Dial-in callers can be the first person in a meeting** setting.
6. Choose to which locations users can **Dial out from meetings**, if appropriate, and then select **Apply**.


> [!TIP]
> You can also reset the conference ID and reset the conference entry PIN on the Account tab.

## Manage licensing for audio conferencing and voice

Add-on licenses for voice capabilities and phone system features provide additional Teams features to users with an active subscription plan. 

For example, if a user is licensed with Microsoft 365 E3 and wants to use calling features for voice communication from their Teams client into PSTN, you can purchase a phone system add-on license and a calling plan license to provide:

- Usage rights for the phone systems of Office 365 (phone system add-on) 
- Credits to perform phone calls (calling plan add-on)

Depending on which plan you already have, the following add-on licenses are available to provide Microsoft Teams and voice calling features:

- Audio Conferencing. Enables users to provide dial-in phone numbers for Teams meetings. It is available for purchase by country/region, so you will need to check if your country is listed.
- Toll free numbers. Enables users to add regional, toll free dial-in phone numbers for conferencing. If you want to use toll-free numbers with Skype for Business and Microsoft Teams for calling, you must set up Communications Credits or a calling plan license.
- Phone System option. Enables users to use Teams with traditional on-premises and cloud Private Branch Exchange (PBX) phone system solutions that provide calling into PSTN. 

   > [!IMPORTANT]
   > This license only permits accessing an on-premises PBX system or the phone system capabilities offered by Office 365. Performing voice calls to PSTN when using cloud PBX also requires a calling plan.

- Calling Plans. Enables the users to call any phone numbers outside of your business. 
- Microsoft Teams Rooms. Enables you to use capable devices for connecting video, audio, and content sharing features to conference rooms.

### Assign licenses 

To assign a license for audio conferencing and phone system features, switch to the Microsoft 365 admin center, and then:

1. Select the appropriate user. 
2. On the user blade, select the **Licenses and apps** tab.
3. Verify the user is assigned an Office 365 license. 
4. Expand the **Apps** link.
5. In the **Show apps for** list, select the Office 365 license (such as **Office 365 E5**).
6. Ensure that **Microsoft 365 Audio Conferencing** and **Microsoft 365 Phone System** are enabled and, if needed, select **Save** **changes**.

> [!NOTE]
> You only need to set up and license Audio Conferencing for people that need to schedule or host meetings. Attendees that dial in don't need any setup or licenses assigned to them.