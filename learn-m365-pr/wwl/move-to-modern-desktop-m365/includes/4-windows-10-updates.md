In the past, you could expect to update your Windows PCs every two to three years - typically when the next major version of Windows was released. Between those updates, you might have deployed service packs for known issues or security updates. With Windows 10, your update schedule is now dramatically reduced - from years between updates to just months. Windows 10 operates as a service, meaning updates become smaller and more frequent maintenance tasks, instead of large and disruptive projects. 

Let’s discuss the different types of updates and how best to deploy them in your organization, based on your specific needs. 

## Types of updates 
There are two types of updates in the Windows as a service model: 
 
- **Feature updates**. These updates provide new functionality and are usually released twice a year. You should deploy these updates using your existing tools. Because these new features come out more often, the individual updates themselves are smaller, making it easier to deploy across your organization. It also introduces less change per update – less for your users to get used to with each update. 
- **Quality updates**. These updates provide security updates and fixes and are usually released once a month. On the second Tuesday of the month (“patch Tuesday”), Microsoft releases a cumulative update that includes all the past quality updates. This helps make sure your devices are up to date and, to make our own testing more effective, more closely aligned to the devices we use for testing at Microsoft.

## Choose the right update channel 
You determine which devices in your environment get which updates when by using channels. There are three servicing channels in Windows as a service: 
 
- **Windows Insider Program**. Get early access to pre-release Windows 10 builds, which update frequently (sometimes weekly). Use Insider builds to explore and test new and modified features before you deploy them. You can also provide direct feedback to Microsoft on these updates, helping improve the experience for others. 
- **Semi-Annual Channel**. Updated twice a year with new features. Devices in the semi-annual channel get updates as soon as Microsoft releases them. You can further control the timing of when specific devices get updated by using the deferral feature (available with Windows Update for Business, Configuration Manager, or Windows Server Update Services) to delay installation until it's convenient for your organization. 
- **Long-term Servicing Channel**. Designed to be used only with specialized devices that can’t be regularly updated or that don’t need to be updated (like ATMs or a PC that runs medical equipment). The long-term servicing channel is released every two to three years. (Note that this channel is updated with security fixes as needed – your devices will still be secure.) Office 365 ProPlus isn’t supported on this channel. 
 
## Choose the right deployment ring 
Windows 10 uses deployment rings with update channels to control how and when updates are applied to your devices. At its most basic, a deployment ring is a group of devices to update at the same time. The number of rings you need depends on a variety of factors, including the number of devices you have, how many different update channels you need to use, or even how many organizations you have in your company. No one can tell you how many rings you should have or which (and how many) devices should go in each ring – that all depends on your organization and is entirely up to you. 

By defining and using deployment rings, you can effectively control how feature and quality updates are deployed through your organization. You should start to think about using Windows as a service as an ongoing process, rather than a specific project to update Windows. 

Here’s an example deployment ring strategy. These ring names are examples and aren’t related to specific builds. (For example, unlike Office 365 ProPlus, Windows as a service doesn’t have a release called “Targeted.”) Choose ring names that make sense for you. These deployment rings also have different settings for deferring updates – use Windows Update for Business, Configuration Manager, or Windows Server Update Services to control deferral periods. 

|Ring name|Microsoft channel|Defers feature updates?|Defers quality updates?|Description|
|-|-|-|-|-| 
|Preview|Windows Insider Program|No|No|A small group of devices that can test pre-release builds without affecting productivity. |
|Test|Semi-Annual Channel|No|No|Another group of devices to test the update before you deploy it to the majority of your devices. |
|Organization|Semi-Annual Channel|120 days|7 to 14 days|Most of your users. Use the deferment period to make sure you‘ve thoroughly tested the updates before you deploy them. <br><br>**Note:** You can pause an update if you run into issues. |
|Line of Business|Semi-Annual Channel|180 days|30 days|Devices that are mission-critical and are only updated once all other devices have successfully updated. |
|LTSC|Long-term servicing channel|n/a|n/a|Isolated devices that can’t use the Semi-annual Channel. |
