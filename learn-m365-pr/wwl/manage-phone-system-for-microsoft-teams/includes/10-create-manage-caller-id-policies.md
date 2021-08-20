By default, when a Teams user makes a call to a PSTN phone, the phone number of the Teams user is visible. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.

An organization can use caller ID policies to change or block the caller ID (also known as calling line ID). An organization's caller ID policies can be used to:

- display an alternate phone number for Teams users
- block the outbound phone number
- block an incoming number from being displayed
- set the Calling Party Name (CNAM)

For example, when a user makes a call, you can change the caller ID to display the organization's main phone number and company name instead of the user's phone number.

Caller ID policies can be managed in the Microsoft Teams admin center by navigating to **Voice** > **Caller ID policies**. An organization can use the global (Org-wide default) policy or create and assign custom policies. Users in an organization will automatically get the global policy unless a custom policy was created and assigned to them or to a group in which they're a member.

## Create a custom caller ID policy

1. In the left-hand navigation pane of the Microsoft Teams admin center, select **Voice** > **Caller ID policies**.
2. Select **Add**. <br>

	‎‎:::image type="content" source="../media/new-caller-id-policy.png" alt-text="Screenshot of new caller ID policy page in the admin center":::

3. Enter a name and description for the policy.
4. Select the settings that you want assigned to the policy:

    - **Block incoming caller ID**. Turn on this setting to block the caller ID of incoming calls from being displayed.
    - **Override the caller ID policy**. Turn on this option to let users override the settings in the policy that controls whether their phone numbers are displayed to callers. This option enables users to choose whether they want to display their caller ID. 
    - **Replace the caller ID with**. Set the caller ID to be displayed for users by selecting one of the following options:

        - **User's number**. Displays the user's number. 
        - **Service number**. Lets you set a service phone number to display as the caller ID.
        - **Anonymous**. Displays the caller ID as Anonymous.

    - **Replace the caller ID with this service number**. Choose a service number to replace the user's caller ID. This option is available if you selected **Service number** in **Replace the caller ID with**.

5. Select **Save**.

Once a custom caller ID policy is created, you can assign a policy directly to users, either individually or at scale through a batch assignment, or to a group that the users are members of. 


## Use PowerShell to manage caller ID policies

Caller ID policies can also be created in PowerShell using the following cmdlets:

* To create a new caller ID policy, use ```New-CsCallingIdentity``` cmdlet.

* To apply the policy setting you created to a user in your organization, use ```Grant-CsCallingLineIdentity``` cmdlet.

* To view all the caller ID policy settings in your organization, use ```Get-CsCallingLineIdentity``` cmdlet.

The following examples show PowerShell commands that use these cmdlets:

* To view all the caller ID policy settings in your organization, run the following command:

	```powershell
	Get-CsCallingLineIdentity |fl
	```

* To create a new caller ID policy that sets the caller ID to anonymous, run the following command:

	```powershell
	New-CsCallingLineIdentity  -Identity Anonymous -Description "Anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
	```

* To apply the new policy you created to Amos Marble, run the following command:

	```powershell
	Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName Anonymous
	```

If you've already created a policy, you can use the **Set-CsCallingLineIdentity** cmdlet to make changes to the existing policy, and then use the **Grant-CsCallingLineIdentity** cmdlet to apply the settings to your users.

* To block the incoming caller ID, run the following command:

	```powershell
	Set-CsCallingLineIdentity  -Identity "Block Incoming" -BlockIncomingPstnCallerID $true -EnableUserOverride $true
	```

* To apply the policy setting you created to a user in your organization, run the following command:

	```powershell
	Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Block Incoming"
	```

* To remove a policy from your organization, run the following command:

	```powershell
	Remove-CsCallingLineIdentity -Identity "My Caller ID Policy"
	```

* To remove a policy from a user, run the following command:

	```powershell
	Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName $null
	```