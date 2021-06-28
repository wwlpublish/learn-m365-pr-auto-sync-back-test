Microsoft Teams includes cloud voice capabilities that are delivered from Office 365 and provide:

- Private Branch Exchange (PBX) functionality 
- Options for connecting to the Public Switched Telephone Network (PSTN). 

> [!NOTE]
> Microsoft’s technology that enables call control and PBX capabilities is titled Phone System.

Phone System in Microsoft Teams allows users to:

- Place and receive calls
- Transfer calls
- Mute or unmute calls

Calling in Teams supports basic Phone System features, such as call answering and initiating (by name and number) with integrated dial pad, call holding and retrieving, call forwarding and simultaneous ringing, call history, voicemail, and emergency calling. 

Users can also use a different range of devices to establish calls, including mobile devices, headset connected to a computer, and an IP phone.

## Manage phone numbers

Before you can assign phone numbers to the users or services in your organization, you must first get phone numbers. There are three ways to get phone numbers:

- Use the Microsoft Teams admin center. For some countries/regions, you can get numbers for your users using the Microsoft Teams admin center.
- Port your existing numbers. You can port or transfer existing numbers from your current service provider or phone carrier.
- Use a request form for new numbers. Depending on your country/region, you may not be able to get your new phone numbers using the Microsoft Teams admin center, or you will need specific phone numbers or area codes. In either case, you will need to download a form, complete it, and return it to Microsoft.

The number of phone numbers for users (subscribers) is equal to:

- The total number of Domestic Calling Plan and/or Domestic and International Calling Plan licenses you have assigned multiplied by 1.1, plus 10 additional phone numbers. 

For example, if you have 50 users in total with a Domestic Calling Plan and/or Domestic and International Calling Plan, you can acquire 65 phone numbers (50 x 1.1 + 10).

### Types of phone numbers

Microsoft Teams uses different telephone number types depending on the purpose for which the phone number will be used:

- User numbers. You can assign these numbers to users in your organization for calling purposes.
- Service numbers. You can assign these numbers to services such as:

   - Audio Conferencing
   - Auto attendants
   - Call queues

> [!TIP]
> Service phone numbers, which have a higher concurrent call capacity than user numbers, vary by country/region and the type of number (whether it's a toll or toll-free number).

## Assign phone numbers to users

To assign phone numbers to users, you create calling plans. You can use the Microsoft Teams admin center to assign a phone number to a user, and later to change or remove the phone number if needed. To assign a number:

1. Open the **Microsoft Teams admin center**.
2. In the left navigation, select **Voice** and then select **Phone numbers**.
3. On the **Phone numbers** page, select an unassigned number in the list, and then select **Edit**.
4. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then select **Assign**.
5. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.
6. Select **Save**.

## Troubleshoot calling features

Calling policies are used to control what calling features are available to your users in Teams. If a user doesn’t have the required call settings, verify they’ve been assigned a calling policy, and that it contains the appropriate settings. 

> [!TIP]
> You can use the **Global (Org-wide default)** policy and customize it to your needs, or else create one or more custom calling policies for people that have phone numbers in your organization.

The available options in a calling plan are described in the following table. 

| Setting                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Make private calls                                           | Controls all calling capabilities in  Teams. Turn off to disable all calling functionality in Teams. |
| Call forwarding and simultaneous ringing  to people in your organization | Determines whether incoming calls are  forwarded to other users or can ring another person at the same time. |
| Call forwarding and simultaneous ringing  to external phone numbers | Determines whether incoming calls can be  forwarded to an external number or can ring an external number at the same  time. |
| Voicemail is available for routing inbound  calls            | Enables inbound calls to be sent to voicemail.  Valid options are: **Enabled** (Voicemail is always available for inbound  calls), **Disabled** (Voicemail is not available for inbound calls), and **User  controlled** (Users can determine whether they want voicemail to be  available). |
| Inbound calls can be routed to call groups                   | Determines whether incoming calls can be  forwarded to a call group. |
| Delegation for inbound and outbound calls                    | Enables inbound calls to be routed t   - delegates, allowing delegates to make outbound calls on behalf of the users  for whom they have delegated permissions |
| Prevent toll bypass and send calls through  the PSTN         | When this setting is **On**, calls are  sent through the PSTN and incur charges rather than sending them through the  network and bypassing the tolls. |
| Busy on busy is available when in a call                     | Enables you to configure how incoming  calls are handled when a user is already in a call or conference or has a  call placed on hold. New or incoming calls can be rejected with a busy signal  or can be routed accordingly to the user's unanswered settings. |
| Web PSTN calling                                             | Enables users to call PSTN numbers using  the Teams web client. |

 

To configure a calling plan, in the Microsoft Teams admin center:

1. Expand **Voice** in the navigation pane, and then select **Calling policies**. 
2. Select the appropriate policy. 
3. Configure the required settings, and then select **Save**. 
4. On the **Calling policies** page, select the **Group policy assignment** tab, and select **Add group**.
5. On the **Assign policy to group** blade, enter the group name, select the rank, and then select your policy. 
6. Select **Apply**.

:::image type="content" source="../media/call-policy.png" alt-text="A screenshot displays the settings in the Global (Org-wide default) calling policy. Values are at their defaults.":::


> [!TIP]
> You can also use the `Set-CSTeamsCallingPolicy` PowerShell cmdlet to configure calling policy settings.

### Troubleshoot dial pad issues

A user cannot make outbound calls because the dial pad in the Calls section of Teams is missing. This can occur for the following reasons:

- **The user doesn’t have an assigned Teams license**. Use the guidance described earlier to assign the user the required license. 
- **The user hasn't been assigned a Calling Plan**. Review the [Which Calling Plan is right for you?](/microsoftteams/calling-plan-landing-page) document and then assign the user a Calling Plan.
- **The user hasn't been enabled for Enterprise Voice**. Use the `Get-CsOnlineUser -Identity $user|Select EnterpriseVoiceEnabled` PowerShell command to verify. 

   If EnterpriseVoiceEnabled is false, then complete the procedures outlined in the [Enable users for Enterprise Voice online and Phone System Voicemail](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-enterprise-voice-online-and-phone-system-voicemail) document.

- **The `OnlineVoiceRoutingPolicy` value isn't set correctly for the user**. To resolve this issue, use the following procedure:

   Run the following PowerShell command: 

   ```PowerShell
   Grant-CsOnlineVoiceRoutingPolicy -Identity "User" -PolicyName $Null
   ```

   Then run:

   ```PowerShell
   Grant-CsOnlineVoiceRoutingPolicy -Identity "User" -PolicyName "PolicyName"
   ```

  > [!IMPORTANT]
  > Remember to replace *User* with your user’s name and *PolicyName* with your policy’s name.

These actions force an update of the policy in the back-end environment of Teams. After this change is made, the user should see the dial pad appear under Calls within four hours.