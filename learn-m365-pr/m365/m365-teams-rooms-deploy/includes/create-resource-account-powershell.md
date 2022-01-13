You can also use PowerShell to create resource accounts. PowerShell is the fastest way to create accounts in bulk. If you need to create multiple accounts, you can create a PowerShell script to automate the account creation. There are also some features and settings that are only available via PowerShell.

There are two mandatory PowerShell modules needed to create a resource account. One is **MSOnline**, which is the Azure Active Directory PowerShell module. The other is the **Exchange Online** PowerShell module.

1. To connect to Microsoft 365, run the `Connect-MsolService` and `Connect-ExchangeOnline` cmdlets, passing in your credentials when prompted.
2. Make sure you have enough licenses by running the following PowerShell cmdlet:

   ```powershell
   Get-MsolAccountSku | where-object {$_.AccountSkuID -like "*meeting*"}
   ```

   :::image type="content" source="../media/see-licenses.png" alt-text="Screenshot displays See your licenses by running the PowerShell cmdlet." lightbox="../media/see-licenses.png":::

   In this example, you can see there are 25 Meeting Room licenses and 19 of them have been consumed (or assigned). This means there are six licenses available to assign to resource accounts.

   When creating accounts via PowerShell, it is advantageous to use variables to store values. Throughout these following cmdlets, you'll reuse the same values several times. Storing these values in a variable will make these commands easier to run successfully. It also sets the stage for writing your own script if you need to create many resource accounts at once.

3. Create a few variables (in this case) like account UPN, mailbox name, mailbox alias, and password.

   **Account name**

   ```powershell
   $acctUpn=mtrfocusroom1@contoso.com
   ```

   **The unique name of the mailbox**

   ```powershell
   $MailBoxName='focusroom'
   ```

    **Specify the Exchange alias** (also known as the mail nickname) for the recipient

   ```powershell
   $MailBoxAlias='focusroom'
   ```

    **Define the password for the account**

   ```powershell
   $Password='ThisIs1ReallyLongPassword!'
   ```

    **Set the license to assign**

   ```powershell
   $ADLicense='teamsdevicesdemo:MEETING_ROOM'
   ```

    **Two letter ISO code** for the country where the tenant is registered

   ```powershell
   $UsageLocation='US'
   ```

   - Note that the password is in clear text. If you set the password using this method, be sure to immediately go into the Microsoft 365 Admin Center and change the password to something else.

4. As mentioned earlier, the resource account is really an Exchange mailbox. Here's the command to create the mailbox as a resource account.

   ```powershell
   New-Mailbox -MicrosoftOnlineServicesID $acctUpn -Name $DisplayName -Alias $MailBoxAlias -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String $Password -AsPlainText -Force)
   ```

5. The next thing you need to do is enable calendar processing. You do this using the `Set-CalendarProcessing` cmdlet.

   ```powershell
   Set-CalendarProcessing -Identity $MailBoxAlias -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false ‐RemovePrivateProperty $false
   ```

   - After identifying the account that was created in the previous command, the `AutomateProcessing` parameter is set to `AutoAccept`. This tells the resource account to automatically process meeting invites instead of waiting for human intervention.  
   - `AddOrganizerToSubject` is set to `$false`.  That means when the meeting is shown on the center of table console, it will only show the meeting name and not *both* the organizer and meeting name. For example, it will display "Weekly Status Meeting" instead of "Sara Perez Weekly Status Meeting."
   - The `DeleteComments` parameter is set to `$false`. This means the body of the e-mail will not be deleted. This parameter is required to be false when using third-party guest join (for example, being able to join Cisco or Zoom meetings via Teams Rooms).
   - You can choose to delete the Subject of the meeting invite using the `DeleteSubject` parameter. Then the meetings on Teams Rooms will be called by the name of the meeting organizer, such as "Sara Perez." This is a security feature to prevent someone from walking through a restricted area and seeing meeting subjects that might leak information, such as "Meeting About Acquisition of Tailspin Toys." If you enable deleting the subject, the meeting title would be "Sara Perez Meeting" and you would have no idea what the meeting is about.

6. If the meeting is flagged as private, set `RemovePrivateProperty` to `$false`.
7. Set the resource account password to never expire and then assign the license.

   ```powershell
   Set-MsolUser -UserPrincipalName $acctUpn -PasswordNeverExpires $true ‐UsageLocation $UsageLocation

   Set-MsolUserLicense -UserPrincipalName $acctupn -AddLicenses $ADLicense
   ```

## Convert a Skype for Business user account

Teams Rooms can join both Skype for Business and Teams meetings. If you have Skype for Business in your organization, this section will help you set up the resource account to work with Skype meetings. You should also follow these steps if you only use Skype for Business in your organization.

In Skype for Business, you have two options.

- Use a Skype for Business user account and configure the Exchange settings to **auto accept**.
- Convert a user account to a meeting room account.

There are a few unique considerations when converting a user account to a meeting room account.

- The resource account will now always join via the lobby. When joining a meeting, the room is entered through the lobby and the organizer will have to manually add the room into the meeting.
- Another change when converting a user to a meeting room is that Skype for Business now knows a meeting room has been invited. Attendees will be asked if they want to mute their devices before joining the meeting in order to limit echo and feedback.
- You should also be aware that when you convert a user to a meeting room, that meeting room will no longer appear when you run the `Get-CsUser` Skype for Business PowerShell cmdlet. Instead, you'll have to run `Get-CsMeetingRoom` to list your meeting rooms.

Create an Exchange Resource Mailbox as described above and then run the Skype for Business PowerShell cmdlet `Enable-CsUser`. In the following examples, be sure to replace skypepool.contoso.com and contoso.com to the correct values for your organization.

```powershell
Enable-CsUser -Identity MTR-STP-Avanti-1@contoso.com -RegistrarPool "skypepool.contoso.com" -SipAddressType SamAccountName -SipDomain contoso.com
```

You can also do this using the Skype for Business control panel.

Here's the command to convert this account to a meeting room. Note that the Identity parameter is the same as in the previous command.

```powershell
Enable-CsMeetingRoom -Identity MTR-STP-Avanti-1@contoso.com -RegistrarPool "skypepool.contoso.com" -SipAddressType SamAccountName -SipDomain contoso.com
```

## Learn more

- [PowerShell module browser](/powershell/module/?azure-portal=true)
- [Deploy Microsoft Teams Rooms with Microsoft 365](/MicrosoftTeams/rooms/with-office-365?azure-portal=true)
