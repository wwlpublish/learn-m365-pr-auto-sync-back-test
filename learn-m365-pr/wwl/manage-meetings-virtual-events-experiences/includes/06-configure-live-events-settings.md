Settings for the Live events that are held within an organization can be configured in the Microsoft Teams admin center. The Teams administrator can set up a support URL and configure a third-party video distribution provider.

> [!NOTE]
> These settings will be applied to all Live events that are created in an organization.

You can manage Live events settings in the Microsoft Teams admin center.

1. Sign into the **Microsoft Teams admin center** with your admin account.
2. Select **Meetings** and then choose **Live events settings.**
3. On the **Live events settings** page, in the **Support URL** section, you can define the URL that will be shown to your attendees who will participate at the Live event.   
‎:::image type="content" source="../media/live-event-settings.png" alt-text="Live event settings":::  


4. If your company purchased a Software Defined Network (SDN) solution or enterprise Content Delivery Network (eCDN) solution through a Microsoft video delivery partner, you can configure the provider by completing the following steps:

	- **Use a third-party distribution provider.** Turn this option On to enable the third-party video distribution provider.
	- **SDN provider name.** Enter the provider who's being used.
	- **Provider license key.** Enter the license ID, which you received from your provider contact.
	- **SDN API template URL.** Enter the API template URL, which you received from your provider contact.

5. Select the **Save** button.
 
## Set up the Support URL using Windows PowerShell

To set up the Support URL using PowerShell, you must run the following command:

```powershell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL "{your URL}"
```

## Configure the third-party video provider using Windows PowerShell

Organizations can optionally configure their third-party video provider using Windows PowerShell. To do so, they must first obtain the license ID or API token and API template from their provider contact. Once they have that information, they should run the following command (in this example, the provider is Hive Streaming):

```powershell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl "{API template URL provided by Hive}"
```

> [!WARNING]
> If you want to create Live events using an external app or device, you must first [configure your eCDN provider with Microsoft Stream](/stream/network-caching).

 

 
