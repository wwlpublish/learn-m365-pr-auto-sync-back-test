In Windows 10, you can use deployment rings to control how and when updates are applied to your devices. Defining deployment rings is generally a one-time event (or at least infrequent), but you should revisit these groups periodically to ensure that the sequencing is still correct. Also, there are times in which client computers could move between  deployment rings when necessary. 

A typical deployment ring strategy is described in the following table. These ring names are only examples and not related to specific build versions. (For example, there is no "Pilot" version of the SAC.) Choose ring names that are relevant for your organization.

|Name of ring|	Channel	|Feature update deferral| 	Quality update deferral	|Description|
|-|-|-|-|-|
|Preview|	Windows Insider Program|	None|	None|	For testing updates on a small group of devices before they become more widely available on the semi-annual channel.|
|Pilot|	Semi-annual channel |	None|None|	Used to evaluate a significant update before deploying it to most other devices.|
|Broad|	Semi-annual channel|	120 days|	7 to 14 days|	Use this ring to deploy the update to most of your users’ devices.<br><br> Use the deferment period to thoroughly test the updates before further deployment.<br><br> Note: You can pause updates if you encounter significant problems or issues.|
|Critical|	Semi-annual channel|	180 days|	30 days|	Reserved for devices that are critical and are only updated when the updates have been thoroughly tested throughout the rest of your organization.| 

By defining and using deployment rings, you can effectively control how feature and quality updates are deployed through your organization. You should start to think about using Windows as a service as an ongoing process, rather than a specific project to update Windows builds. The following diagram shows how you can use servicing channels to create an update timeline that includes a planning and preparation phase, pilot deployments, and general deployment. 

![Windows as a service deployment rings](../media/4-waas-rings.png)

You don't need to deploy all feature updates; you can opt to bypass those updates that do not add value for your users. Bear in mind, however, that support for a feature update continues for 18 months after its release. 