When an ActiveSync connection is established between a mobile device and Exchange, the mobile device stores company data from the user’s mailbox. This data includes the user’s domain credentials, which are the username and password needed to authenticate to Exchange. If a device is lost or stolen, that data can be compromised.

Because the risk of losing a mobile device is always possible, it’s essential that messaging administrators secure the data on mobile devices. You can secure mobile devices by enforcing an ActiveSync policy that specifies password requirements for the device. However, an ActiveSync policy doesn't prevent data from being compromised when devices are lost or stolen.

### Protect company data on lost and stolen devices

Exchange provides an option called Remote Wipe to protect the company data that was stored on lost or stolen devices. When the Remote Wipe command is issued, it deletes all data on the phone and storage cards and resets all settings to factory defaults.

Restoring settings to factory defaults prevents any unauthorized user from accessing the account data or data cached on the device. If you’re planning to run a remote device wipe on a mobile phone in your possession and you want to keep the data on the storage card, remove the storage card before you start the remote device wipe.

> [!WARNING]
> Since some smartphones don't have removable storage, it’s important to remember that, by default, Remote Wipe destroys all data on the device, including personal photos and data!

If your organization allows employee-owned devices (BYOD), you should educate your users about remote wiping and what it does with personal data. Failure to do so can result in legal issues in several countries/regions. For example, consider the scenario where a user loses their phone, which triggers the messaging administrator to do a remote wipe on the device per the company’s policy. The next day the user finds the phone, only to discover that all the personal photos and files have been deleted.

The Remote Wipe command can be issued in either of two ways:

 -  By the user of a specific mobile device through the Outlook on the Web interface.
 -  By the administrator through the Exchange Admin Center (EAC) or Exchange Management Shell.

The Remote Wipe command will only be accepted by the device if it still has a connection with the Exchange server, either by data (3G, LTE, or similar mobile data service) or by Wi-Fi.

Remote Wipe won't work if the connection is lost. For example, when the Subscriber Identity Module, or SIM, card is removed, or the ActiveSync account is manually removed from the device. As such, if you plan to issue a Remote Wipe command, you should do so as soon after a device is lost or stolen.

> [!WARNING]
> After a remote device wipe, data recovery is difficult, if not impossible. This situation is especially true when the device supports a strong encryption of all device data. If the device isn't encrypted, it may still be possible to retrieve data from a device using sophisticated forensic investigation tools.

### Use the Exchange admin center to wipe a user’s phone

You can use the Exchange admin center (EAC) to wipe a user’s phone or cancel a remote wipe that hasn't yet completed by doing the following steps:

1.  In the EAC, navigate to **Recipients** &gt; **Mailboxes**.
2.  Select the user, and under **Mobile Devices**, choose **View details**.
3.  On the **Mobile Device Details** page, select the lost mobile device, and then select **Wipe Data**.
4.  Select **Save**.

### Use the Exchange Management Shell to wipe a user’s phone

You can use the **Clear-MobileDevice** cmdlet in the EMS to wipe a user’s phone. For example, the following PowerShell command wipes the device named WM\_TonySmith and sends a confirmation message to admin@contoso.com.

```powershell
Clear-MobileDevice -Identity WM_TonySmith -NotificationEmailAddresses admin@contoso.com
```

#### Delete only company data

Starting with Exchange ActiveSync version 16.1, it’s possible to run an “Account-only remote wipe” that deletes only Exchange company data and leaves personal data untouched. You can issue an account only remote wipe by adding the -AccountOnly switch when using the **Clear-MobileDevice** cmdlet.

The previous command will now appear as follows assuming Contoso only requires company data to be removed when doing a remote wipe:

```powershell
Clear-MobileDevice -Identity WM_TonySmith -AccountOnly -NotificationEmailAddresses admin@contoso.com 
```

### Use Outlook on the web to wipe a user’s phone

By completing the following steps, your users can wipe their own phones using Outlook on the web:

1.  In Outlook on the web, select **Settings &gt; Phone &gt; Mobile devices**.
2.  Select the mobile phone.
3.  Select or tap the **Wipe Device** icon.

### Verify the remote wipe completed successfully

There are several ways to verify that the remote wipe completed:

 -  Run the **Clear-MobileDevice** cmdlet with the –NotificationEmailAddresses parameter configured. A message will be sent to the supplied email address when the remote wipe has completed.
 -  In the EAC, check the status of the mobile device. The status will change from **Wipe Pending** to **Wipe Successful**.
 -  In Outlook on the web, check the status of the mobile device. The status will change from **Wipe Pending** to **Wipe Successful**.

### Local device wipe

Local device wipe occurs when a mobile device wipes itself without the request coming from the server. For example, your organization can implement a mobile device mailbox policy that specifies that when a maximum number of unsuccessful password attempts is exceeded, the mobile device should run a local device wipe.

The result of a local device wipe is the same as a remote device wipe - the device is returned to its factory default condition. When a mobile device completes a local device wipe, no confirmation is sent to the Exchange server.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.