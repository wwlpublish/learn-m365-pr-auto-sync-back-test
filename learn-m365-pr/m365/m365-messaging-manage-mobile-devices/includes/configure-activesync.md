If you support legacy clients that use Exchange ActiveSync (EAS) to connect to Exchange Online, you should use mobile device mailbox policies to control their access. Let's examine those policies and how they differ from the policies that you've already seen.

## What are mobile device mailbox policies?

Some users may prefer to use their device's built-in mail app to access their email, or you may have legacy devices that don't support Outlook for iOS and Android. If you want to enable these clients to synchronize calendar and contact information, as well as emails, you might have to use Exchange ActiveSync (EAS). In this case, you can take control of EAS clients by using mobile device mailbox policies.

>[!NOTE]
> Mobile device mailbox policies were formally known as Exchange ActiveSync policies and were specifically designed to manage EAS clients. These are separate objects from security policies in Mobile Device Management (MDM).

## Find out about mobile device mailbox policies

You can manage mobile device mailbox policies in the Exchange admin center, but only a subset of the complete range of properties is available. For complete functionality, you must use Exchange Online PowerShell.

To list the mobile device mailbox policies that exist in your subscription, use this command:

``` powershell
Get-MobileDeviceMailboxPolicy
```

Now that you have a list of policies, you can find out what settings each policy enforces by using the same cmdlet with the **-identity** argument. This example examines a policy named "LegacyDevices":

``` powershell
Get-MobileDeviceMailboxPolicy -Identity "LegacyDevices"
```  

## Create a new mobile device mailbox policy

To create a new mobile device mailbox policy and set the properties that it enforces, use the **New-MobileDeviceMailboxPolicy** cmdlet.  

This example creates a policy that controls aspects of the user's password:

``` powershell
New-MobileDeviceMailboxPolicy -Name "LegacyDevices"  

   -PasswordEnabled $true 

   -AlphanumericPasswordRequired $true 

   -AllowSimplePassword $false 

   -PasswordRecoveryEnabled $true 
```

## Apply a mobile device mailbox policy to a user

The first mobile device mailbox policy that you create in your tenant is marked as the default policy and will apply automatically to all EAS clients when they next connect to Exchange Online. If you're creating a new policy later, and want the new policy to become the default policy, you can use the -IsDefault argument:

``` powershell
New-MobileDeviceMailboxPolicy -Name "LegacyDevices"  

   -IsDefault $true 

   -PasswordEnabled $true 

   -AlphanumericPasswordRequired $true 

   -AllowSimplePassword $false 

   -PasswordRecoveryEnabled $true 
```

You might also want to create a policy that only applies to specific users. For example, you might want to apply a stricter policy to Exchange Online administrators, because those powerful accounts are more likely to be targeted by attackers. In such a case, don't set the strict policy as the default, but instead, assign each administrator's mailbox to the strict policy. You can do this in Exchange admin center or by using the Set-CASMailbox cmdlet:

``` powershell
Set-CASMailbox exchangeadmin@contoso.com -ActiveSyncMailboxPolicy "AdminPolicy" 
```

## Learn more

- [Exchange ActiveSync in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync?azure-portal=true)
- [Connect to Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?azure-portal=true)
- [Set-MobileDeviceMailboxPolicy](/powershell/module/exchange/devices/set-mobiledevicemailboxpolicy?azure-portal=true)
- [Set-CASMailbox](/powershell/module/exchange/client-access/set-casmailbox?azure-portal=true)
