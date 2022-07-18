For live events or videos sent out to large portions of your organization, there could be a significant amount of internet bandwidth consumed by viewers. For organizations that want to reduce this internet traffic for live events, live events solutions are integrated with Microsoft's trusted video delivery partners offering software defined networks (SDNs) or enterprise content delivery networks (eCDNs). These SDN/eCDN platforms enable organizations to optimize network bandwidth without sacrificing end user viewing experiences. 

The Teams administrator can set up a support URL and configure a video distribution provider. Before you can enable a video delivery provider to be used with Teams, you must purchase and set up the SDN/eCDN solution outside and separate from Teams.

> [!NOTE]
> These settings will be applied to all Live events that are created in an organization.

You can manage Live events settings in the Microsoft Teams admin center or PowerShell.

## Use Teams admin center

1. Sign into the **Microsoft Teams admin center** with your admin account.
2. Select **Meetings** and then choose **Live events settings**.
3. On the **Live events settings** page, in the **Support URL** section, you can define the URL that will be shown to your attendees who will participate at the Live event.

4. If your company purchased a Software Defined Network (SDN) solution or enterprise Content Delivery Network (eCDN) solution, you can configure the provider by completing the following steps:

	- **Video distribution provider**. Turn this option On to enable the video distribution provider.
	- **SDN provider name**. Select the provider.
	- **SDN Configuration**. Depending on the selected SDN provider, enter the configuration details you received from your provider contact.
		- SDN provider API token 
		- Provider License key and SDN Configuration 
		- SDN API template URL

		:::image type="content" source="../media/live-event-settings.png" alt-text="Screenshot of Live event settings.":::  

5. Select the **Save** button.
 
## Use PowerShell

### Set up the Support URL

To set up the Support URL using PowerShell, you must run the following command:

```powershell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL "{your URL}"
```

### Configure the video provider

Organizations can optionally configure their third-party video provider using Windows PowerShell. To do so, they must first obtain the license ID or API token and API template from their provider contact. Once they have that information, they should run the following command (in this example, the provider is Hive Streaming):

```powershell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl "{API template URL provided by Hive}"
```

> [!WARNING]
> If you want to create Live events using an external app or device, you must first [configure your eCDN provider with Microsoft Stream](/stream/network-caching?azure-portal=true).

 

 
