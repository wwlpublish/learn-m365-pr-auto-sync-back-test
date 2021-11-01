A mobile device mailbox policy lets an organization apply a common set of security and mobile device settings to a group of users. Each recipient in the organization must be assigned a mobile device mailbox policy.

 -  When you install Exchange Server or provision Exchange Online, a default mobile device mailbox policy is created. Users are then automatically assigned this policy.
 -  You can also create multiple mobile device mailbox policies that you can manually apply to different types of users.

Mobile device mailbox policies can be created in the Exchange Admin Center (EAC) or the Exchange Management Shell (EMS).

 -  If you create a policy in the EAC, you can configure only a subset of the available settings.
 -  If you create a policy using EMS, you can configure all available settings.

**Additional reading**. For a complete list of policy settings, see [Mobile Device Mailbox Settings](/exchange/clients/exchange-activesync/mobile-device-mailbox-policies?azure-portal=true).

### Edit an existing policy

You can use the EAC or PowerShell to edit a mobile device mailbox policy. In the EAC, you should complete the following steps to edit a mobile device mailbox policy:

1.  In the EAC, select **mobile** in the left-hand navigation pane, and then select the **mobile device mailbox policies** tab.
2.  Select a policy from the List view and select the **Edit** (pencil) icon in the menu bar.
3.  On the **Mobile Device Mailbox Policy** window, select the **general** and **security** tabs in the left-hand pane to edit the mobile device mailbox policy settings. For example, in the **security** tab, select **Require a password** to enable a mobile device password and set the minimum password length to six characters.
4.  Select **Save** to update the policy.

You can edit a mobile device mailbox policy by using the **Set-MobileDeviceMailboxPolicy** cmdlet in the EMS. For example, you should run the following command to edit the default mobile device mailbox policy that will configure these settings:

 -  Enable passwords with alphanumerical characters.
 -  Store the recovery password in Exchange.
 -  Allow two weeks of email items to synchronize to the mobile device.
 -  Allow wireless internet access.
 -  Allow mobile devices to access information stored on a storage card.

```powershell
Set-MobileDeviceMailboxPolicy -Identity:Default ‘  
-PasswordEnabled:$true ‘  
-AlphanumericPasswordRequired:$true ‘  
-PasswordRecoveryEnabled:$true ‘  
-MaxEmailAgeFilter:TwoWeeks ‘  
-AllowWiFi:$True ‘  
-AllowStorageCard:$true ‘  
-IsDefault:$true

```

### Create a new policy

You can use the EAC to create a new mobile device mailbox policy by completing the following steps:

1.  In the EAC, select **mobile** in the left-hand navigation pane, select the **mobile device mailbox policies** tab, and then select the **plus (+) sign** icon on the menu bar to add a new policy.
2.  Use the various check boxes and drop-down lists to configure the settings for the mobile device mailbox policy.
3.  Select **Save**.

You can make the new mobile device mailbox policy the default mobile mailbox policy by selecting **This is the default policy**. After you make a mobile mailbox policy the default policy, all new users will automatically be assigned this policy when their user account is created.

You can create mobile device mailbox policy by using the **New-MobileDeviceMailboxPolicy** cmdlet. For example, you should run the following command to create a new mobile device mailbox policy that will configure these settings:

 -  Create a new mobile device mailbox policy named “Management”.
 -  Allow Bluetooth, browser, and camera.
 -  Enable password with alphanumerical characters.
 -  Store recovery password in Exchange.
 -  Allow two weeks of email items to synchronize to the mobile device.
 -  Allow wireless internet access.
 -  Allow mobile device to access information stored on a storage card.

```powershell
New-MobileDeviceMailboxPolicy -Name:"Management" ‘  
-AllowBluetooth:$true ‘  
-AllowCamera:$true ‘  
-PasswordEnabled:$true ‘  
-AlphanumericPasswordRequired:$true ‘  
-PasswordRecoveryEnabled:$true ‘  
-MaxEmailAgeFilter: TwoWeeks ‘  
-AllowWiFi:$true ‘  
-AllowStorageCard:$true

```

### Add or remove users from a policy

You can use the EAC to assign a user’s mobile device mailbox policy by completing the following steps:

1.  In the EAC, select **recipients** in the left-hand navigation pane, select the **mailboxes** tab, and then select a mailbox.
2.  In the Details pane that appears for the selected mailbox, in the **Phone and Voice Features** section, select **View details** under the **Mobile Devices** group.
3.  In the **Mobile Device Details** page, the mobile device mailbox policy that’s currently assigned is displayed. To change the mobile device mailbox policy, select **Browse**.
4.  Choose the appropriate mobile device mailbox policy from the list, select **OK**, and then select **Save**.

You can also use PowerShell to assign a user’s mobile device mailbox policy. For example, to assign a mobile device mailbox policy named “Sales” to the Contoso user named Stacy, run the following command.

```powershell
Set-CASMailbox -Identity stacy@contoso.com ‘  
-ActiveSyncMailboxPolicy "Sales"

```
