Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room, projector, and other resources. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room that will automatically accept or decline meeting invites depending on its calendar availability.

When a person schedules a room, it's this resource mailbox that's invited to the meeting. This mailbox will accept or decline the meeting invite for the room.

This resource account is also the account that signs into the Microsoft Teams Rooms app. The account must be enabled for Skype for Business and Microsoft Teams. It's recommended that organizations establish a naming convention for resource accounts, particularly when organizations move to Azure Active Directory (Azure AD) and employ dynamic groups. A resource account can automatically be added to Azure AD groups based on the organization's naming convention.

There are four primary steps to configure a resource account for Teams room. 

**Step 1** - Create a new resource account. Or, if a room mailbox already exists and you want to convert it to a resource account, you can modify an existing Exchange room mailbox.

**Step 2** - Then, configure your account for Teams Meetings.

**Step 3** - If the resource account is going to be associated with a shared device, such as Teams displays with hot-desking, turn off password expiration.

**Step 4** - Lastly, assign a meeting room license so the account can access Microsoft Teams.

## Teams Rooms licenses

It's recommended that organizations assign the Teams Rooms Basic or Teams Rooms Pro license to all Teams Rooms resource accounts.

- **Teams Rooms Basic license** - provides core meeting experiences to organizations that purchase a certified Microsoft Teams Rooms device, at no additional cost. The Teams Rooms Basic license includes scheduling, joining meetings, content sharing, and collaborative white boarding, as well as basic security and management capabilities out-of-the-box.

   You can assign up to 25 Microsoft Teams Rooms Basic licenses to Teams Rooms devices in your organization. If you need to license more than 25 devices, those additional licenses need to be Teams Rooms Pro licenses.

- **Teams Rooms Pro license** - This license includes everything in the Basic license, plus enhanced in-room meeting experiences like intelligent audio and video, front row and large galleries, and multi-screen support. The Teams Rooms Pro licenses also provides advanced management features like remote device management, conditional access policies, and detailed device analytics.

    :::image type="content" source="../media/standard-premium-license.png" alt-text="Diagram showing Basic versus Pro licenses."::: 

## Configure a resource account 

### Use Microsoft 365 admin center
Complete the following steps to create a new resource account using the Microsoft 365 admin center. These instructions will create a user account record for the resource account, and then assign it a password and a license.

#### Step 1: Create a resource account

1. Navigate to the Microsoft 365 admin center (admin.microsoft.com) and sign in with an admin account.
2. In the left-hand navigation pane, select **Show all**, select **Resources**, and then select **Rooms & equipment**.
  
   :::image type="content" source="../media/resource-account-resources-tab.png" alt-text="Screenshot of Microsoft 365 admin center resources tab Rooms & equipment option.":::

3. On the **Rooms & equipment** window, select the **+Add resource** option on the menu bar to add a new resource account.

   :::image type="content" source="../media/rooms-equipment-view.png" alt-text="Screenshot of the Rooms & equipment page with the +Add resource option on the menu bar highlighted.":::

4. In the **Add resource** pane that appears, update the following fields:

   :::image type="content" source="../media/add-resource-form.png" alt-text="Screenshot of Focus Room configuration.":::

   1. Select **Room** as the **Resource type**.
   1. Add a friendly name in the **Name** field. This value is what users will see when scheduling the room in Outlook or Microsoft Teams.
   1. The **Email** address is automatically populated. Edit this address as necessary to conform to your organization's naming standard for Teams Rooms. Select the appropriate **Domain** for your organization.
   1. The **Capacity**, **Location**, and **Phone number** fields are all optional.

5. Select **Save**.

6. After the resource account has been created, you’ll receive an acknowledgment that the Room mailbox is ready to use.

   :::image type="content" source="../media/add-resource-acknowledgment.png" alt-text="Screenshot of Acknowledgment of mailbox creation.":::

#### Step 2: Configure mailbox properties

7. Once you've created a resource account, you can edit its booking options. On the acknowledgment window that you received in the prior step, under the **Next steps** section, select **Edit booking options**.

    If you closed the acknowledgment window before selecting **Edit booking options**, then select the resource account on the **Rooms & equipment** window. In the detail pane that appears for the account, select **Edit** under the **Booking options** section.  

    Both methods described in this step will open the **Edit booking options** pane.

   :::image type="content" source="../media/edit-booking-options.png" alt-text="Screenshot of Edit the booking options.":::

8. In the **Edit booking options** pane, update the following settings:

   - **Allow repeating meetings** - This option, which controls recurring appointments, is enabled by default.
   - **Allow scheduling only during work hours** - If this option isn't selected, the room can be scheduled any time of day. If this option is selected, then the room can only be scheduled during work hours.

       To set the work hours for this resource account, sign in as the resource account into Outlook on the web to change its working hours.
   - **Automatically decline meetings outside of limits** - This option is enabled by default. If this option is selected, the resource account won't accept meetings that are scheduled to last longer than the value entered in the **Booking duration (hours)** field or that are scheduled beyond the value entered in the **Booking windows (days)**.

   - **Auto accept meeting requests** - This option is selected by default. Most organizations will leave this option selected. This option is only unselected if the room requires human intervention to accept or decline meeting requests.

9. Select **Save changes**.


#### Step 3: Turn off password expiration

10. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Users** > **Active users**.

11. Select the check box of the account. A **Key** icon (Reset a password) will appear to the right of the display name. 

12. Select the **Key** icon. 

13. Uncheck **Require this user to change their password when they first sign in**.

      - You can unselect the **Automatically create a password** check box. By unselecting this option, a **Password** field will appear. Enter the password for this room in this field.  

      - You can select the **Email the sign-in info to me** check box if you want to receive an email with the password information you just entered.

      :::image type="content" source="../media/resource-account-with-key.png" alt-text="Screenshot of Find your new resource account and click Key to reset password.":::

14. Select **Reset password**, and then select **Close** once the password has been reset.

#### Step 4: Assign a meeting room license

To complete the resource account configuration, you must assign a license to the resource account. 

15. On the **Active users** window, select the room’s display name to open the properties pane for this account.

16. Select **Licenses and apps** tab from the properties pane.

      - Select the country or region where the device will be installed from **Select location** dropdown menu. 

      - Select the check box next to the appropriate license for this resource account.

17. Select **Save changes** and then close the properties pane.

      :::image type="content" source="../media/resource-account-license-form.png" alt-text="Screenshot of the Active Users window.":::

### Use PowerShell

PowerShell can also be used to create resource accounts. PowerShell is the fastest way to create accounts in bulk. If you need to create multiple accounts, you can create a PowerShell script to automate the account creation. There are also some features and settings that are only available through PowerShell.

There are two mandatory PowerShell modules that must be installed to create a resource account. One is the **Microsoft Online** module, which is the Azure Active Directory PowerShell module. The other is the **Exchange Online** PowerShell module.


#### Step 1: Create a resource account

By default, room mailboxes don't have associated accounts. Add an account when you create a room mailbox so it can authenticate with Microsoft Teams.

Here's the command to create a new resource mailbox with the following settings:

* Account: ConfRoom1@contoso.com
* Name: focusroom
* Alias: focusroom
* Account password: P@$$W0rd5959

   ```powershell
   ## Set account name
   $acctUpn=ConfRoom1@contoso.com

   ## Set the unique name of the mailbox
   $MailBoxName 'focusroom'

   ## Specify the Exchange alias(also known as the mail nickname) for the recipient
   $MailBoxAlias='focusroom'

   ## Define the password for the account
   $Password='P@$$W0rd5959'

   ## Create a new resource mailbox
   New-Mailbox -MicrosoftOnlineServicesID $acctUpn -Name $DisplayName -Alias $MailBoxAlias -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String $Password -AsPlainText -Force)
   ```

#### Step 2: Configure mailbox properties

The next thing you need to do is enable calendar processing. You do this using the ```Set-CalendarProcessing``` cmdlet.

```powershell
Set-CalendarProcessing -Identity $MailBoxAlias -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
```
   * **AutomateProcessing:** ```AutoAccept``` Meeting organizers receive the room reservation decision directly without human intervention.
   * **AddOrganizerToSubject:** ```$false``` The meeting organizer isn't added to the subject of the meeting request.
   * **DeleteComments:** ```$false``` Keep any text in the message body of incoming meeting requests. This is required to process external Teams and third-party meetings to provide One Touch Join experience.
   * **DeleteSubject:** ```$false``` Keep the subject of incoming meeting requests.
   * **ProcessExternalMeetingMessages:** ```$true``` Specifies whether to process meeting requests that originate outside the Exchange organization. Required for external Teams meetings and third-party meetings.
   * **RemovePrivateProperty:** ```$false``` Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.
   * **AddAdditionalResponse:** ```$true``` The text specified by the AdditionalResponse parameter is added to meeting requests.

   * **AdditionalResponse:** **"This is a Microsoft Teams Meeting room!"** The additional text to add to the meeting acceptance response.


#### Step 3: Turn off password expiration

If the resource account password expires, the device won't sign in after the expiration date. The password will then need to be changed for the resource account and then updated on each device. To avoid this, you can turn off password expiration. 

Here's the command to set the resource account password to never expire and location in US:

```powershell
Set-AzureADUser -ObjectID ConfRoom1@contoso.com -PasswordPolicies DisablePasswordExpiration -UsageLocation 'US'
```

#### Step 4: Assign a meeting room license

1. Connect to Azure AD and use ```Get-AzureADSubscribedSku``` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.

   ```powershell
   ## Connect to Azure AD
   Connect-AzureAD
   ## Check available SKUs
   Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
   ```

   :::image type="content" source="../media/see-licenses.png" alt-text="Screenshot of See your licenses.":::

2. Use the ```Set-AzureADUser``` cmdlet to assign the license. Convert the license SKU ID into a PowerShell license type object. Then, assign that object to the resource account.

   Here's the command to assign **Microsoft Teams Rooms Pro** (license SKU ID 4cde982a-ede4-4409-9ae6-b003453c8ea6) to the account ConfRoom1@contoso.com.


   ```powershell
   #Create an object for a single license type
   $License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
   $License.SkuId = "6070a4c8-34c6-4937-8dfb-39bbc6397a60" 

   #Create an object for a multiple license type
   $Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 

   #Add the single license object to the multiple license object
   $Licenses.AddLicenses = $License 

   #Assign the license to the resource account
   Set-AzureADUserLicense -ObjectId ConfRoom1@contoso.com -AssignedLicenses $Licenses
   ```
