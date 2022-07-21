Windows as a service (WaaS) is a way to simplify the lives of IT pros and maintain a consistent Windows 10 and 11 client experience for their customers. By implementing WaaS, organizations can:

 -  Maximize customer involvement in Windows development.
 -  Simplify the deployment and servicing of Windows 10 and 11 client computers.
 -  Level out the resources needed to deploy and maintain Windows over time.

Prior to Windows 10, Microsoft released new versions of Windows every few years. This traditional deployment schedule imposed a training burden on users because the feature revisions were often significant. It also meant waiting long periods without new features. This scenario doesn’t work in today’s rapidly changing world, where new security, management, and deployment capabilities are necessary to address challenges. To help address these issues, Windows as a service delivers smaller feature updates two times per year, around March and September.

In the past, when Microsoft developed new versions of Windows, it typically released technical previews near the end of the process, when Windows was nearly ready to ship. Starting with Windows 10, new features are now delivered to the [Windows Insider community](https://insider.windows.com/?azure-portal=true) as soon as possible during the development cycle, through a process called **flighting**. This Windows as a service program enables organizations to see exactly what Microsoft's developing, and start their testing as soon as possible.

Microsoft also depends on receiving feedback from organizations throughout the development process. By doing so, it can make adjustments as quickly as possible rather than waiting until after release. During Microsoft's extensive internal testing, engineering teams install new builds daily, and larger groups of employees install builds frequently, all before those builds are ever released to the Windows Insider Program (which is examined later in this unit).

### Deploy Windows 10 and 11 clients

Deploying Windows 10 and Windows 11 is simpler than with previous versions of Windows. When an organization migrates from earlier versions of Windows to Windows 10 or 11, it can use an easy, in-place upgrade process that automatically preserves all apps, settings, and data. Afterwards, deployment of feature updates is easy.

#### Application compatibility

Application compatibility testing has historically been a burden on organizations when they've approached a Windows deployment or upgrade. However, application compatibility from the perspective of desktop applications, websites, and apps that were built on the Universal Windows Platform (UWP) has improved tremendously over older versions of Windows.

> [!IMPORTANT]
> For the most important business-critical applications, organizations should still perform regular testing to validate compatibility with new builds. For remaining applications, organizations should consider validating them as part of a pilot deployment process. Doing so will reduce the time spent on compatibility testing.

Desktop Analytics is a cloud-based service that integrates with Configuration Manager. This service provides insight and intelligence for organizations to make more informed decisions about the update readiness of its Windows endpoints, including assessment of its existing applications.

### Windows Servicing

Traditional Windows servicing included several release types:

 -  Major revisions (for example, the Windows 8.1, Windows 8, and Windows 7 operating systems)
 -  Service packs
 -  Monthly updates

With Windows 10 and Windows 11, there are two release types:

 -  **Feature updates**. Adds new functionality by packaging new features into feature updates. Organizations can deploy these updates using existing management tools. These changes come in bite-sized chunks rather than all at once, decreasing user readiness time.
 -  **Quality updates**. Provides security and reliability fixes. Monthly updates in previous Windows versions were often overwhelming because of the sheer number of updates available each month. Organizations then tried to figure out which updates they needed, which ultimately caused platform fragmentation. Many organizations selectively chose which updates they wanted to install and which they didn’t. As such, countless scenarios were created in which organizations deployed essential security updates but picked only a subset of non-security fixes.
    
    With quality updates, administrators see one cumulative monthly update that supersedes the previous month’s update. This cumulative update contains both security and non-security fixes. This approach makes updating simpler. It also ensures that devices are more closely aligned with the testing done at Microsoft, reducing unexpected issues resulting from updates.

### Servicing channels

Servicing channels are the first way to separate users into deployment groups for feature and quality updates. There are three servicing channels, each of which provides different levels of flexibility over when these updates are delivered to client computers:

 -  General Availability Channel
 -  Long-Term Servicing Channel
 -  Windows Insider Program

Each of these channels is examined in greater detail in the following sections.

> [!NOTE]
> Servicing channels aren't the only way to separate groups of devices when consuming updates. Each channel can contain subsets of devices, which stagger servicing even further. For information about the servicing strategy and ongoing deployment process for Windows 10 and later, including the role of servicing channels, see [Plan servicing strategy for Windows client updates](/windows/deployment/update/waas-servicing-strategy-windows-10-updates?azure-portal=true).

#### General Availability Channel

The General Availability Channel receives feature updates as soon as they're available. This servicing model is ideal for pilot deployments and testing of feature updates. It's also ideal for users, such as developers, who need to work with the latest features. Once the latest release has gone through pilot deployment and testing, an organization will be able to choose the timing at which it goes into broad deployment.

When Microsoft officially releases a feature update, it makes it available to any device that isn't configured to defer feature updates. By doing so, those devices can immediately install it. However, organizations that use Windows Server Update Services (WSUS), Microsoft Endpoint Configuration Manager, or Windows Update for Business, can defer feature updates to selective devices by withholding their approval and deployment. In this scenario, the content available for the General Availability Channel will be available. However, it won't necessarily be mandatory right away. That decision will depend on the policy of the management system.

With each General Availability release, it's recommended that organizations immediately deploy to devices selected for early adoption (targeted validation) and ramp up to full deployment at their discretion. This process enables an organization to gain access to new features, experiences, and integrated security as soon as possible.

> [!NOTE]
> All releases of Windows 10 and later have 18 months of servicing for all editions. These updates provide security and feature updates for the release. However, fall releases of the Enterprise and Education editions will have an extra 12 months of servicing for specific Windows 10 and later releases, for a total of 30 months from initial release. This extended servicing window applies to Enterprise and Education editions starting with Windows 10, version 1607.

Organizations can delay feature updates into as many phases as they wish by using one of the available servicing tools. For more information, see the **Servicing tools** section at the end of this unit.

#### Long-term Servicing Channel

The Long-term Servicing Channel (LTSC) is designed only for specialized devices, which typically don't run Office. Specialized systems—such as devices that control medical equipment, point-of-sale systems, and ATMs—often require a longer servicing option because of their purpose. These devices typically perform a single important task. As such, they don’t need feature updates as frequently as other devices in the organization. It’s more important that these devices be kept as stable and secure as possible than up to date with user interface changes.

The LTSC servicing model prevents Enterprise LTSC devices from receiving the usual feature updates. It only provides quality updates to ensure that device security stays up to date. However, customers can choose to defer them by using one of the servicing tools mentioned in the Servicing tools section at the end of this unit.

> [!TIP]
> The Long-term Servicing channel isn't intended for deployment on most or all the devices in an organization. It should only be used for special-purpose devices. As a general guideline, a device with Microsoft Office installed is a general-purpose device that's typically used by an information worker. As such, this type of device is better suited for the General Availability channel.

Microsoft never publishes feature updates through Windows Update on devices that run Windows 10 and later Enterprise LTSC. Instead, it typically offers new LTSC releases every two to three years. Organizations can choose to install them as in-place upgrades or even skip releases over the product lifecycle. An organization should always check its individual LTSC release to verify its servicing lifecycle. For more information, see [release information](/windows/release-health/release-information?azure-portal=true).

> [!NOTE]
> LTSC releases support the currently released processors and chipsets at the time of release of the LTSC. As future CPU generations are released, support will be created through future LTSC releases that customers can deploy for those systems. For more information, see the section titled **Supporting the latest processor and chipsets on Windows** in [Lifecycle support policy FAQ - Windows Products](/lifecycle/faq/windows?azure-portal=true).

The Long-term Servicing Channel is available only in the Windows 10 and 11 Enterprise LTSC editions. This edition of Windows doesn’t include many standard applications, such as Microsoft Edge, Microsoft Store, Cortana (though limited search capabilities remain available), Microsoft Mail, Calendar, OneNote, Weather, News, Sports, Money, Photos, Camera, Music, and Clock. These apps aren't supported in the Enterprise LTSC editions, even if it's installed by using sideloading.

#### Windows Insider Program

The Windows Insider Program provides organizations with the opportunity to test and provide feedback on features that will be shipped in the next feature update. These features will be provided before they’re available to the General Availability Channel. For many IT pros, gaining visibility into feature updates early can be intriguing and valuable for future end user communications. It can also provide the means to test for any issues on the next General Availability release. Windows Insiders can consume and deploy preproduction code to their test machines, gaining early visibility into the next build. Testing the early builds helps Microsoft customers because they have the opportunity to discover possible issues before the update is ever publicly available. It also helps Microsoft, since the issues can be reported to Microsoft for correction.

It's recommended that all organizations have at least a few devices enrolled in the Windows Insider Program and provide feedback on any issues they encounter. For more information about the Windows Insider Program for Business, see [Windows Insider Program for Business](/windows-insider/business/register?azure-portal=true).

### Servicing tools

There are many tools an organization can use to service Windows as a service. Each option has its pros and cons, ranging from capabilities and control to simplicity and low administrative requirements. Several servicing tools are available to manage Windows as a service updates, including:

 -  **Windows Update (stand-alone)**. Provides limited control over feature updates. IT pros must manually configure the device to be in the General Availability Channel. Organizations can target which devices defer updates by selecting the **Defer upgrades** check box in **Start\\Settings\\Update &amp; Security\\Advanced Options** on a Windows client device.
 -  **Windows Update for Business**. Includes control over update deferment and provides centralized management using Group Policy or Mobile Device Management (MDM). Windows Update for Business can be used to defer updates by up to 365 days, depending on the version. These deployment options are available to clients in the General Availability Channel. Besides being able to use Group Policy to manage Windows Update for Business, either option can be configured without requiring any on-premises infrastructure by using Microsoft Intune.
 -  **Windows Server Update Services**. Provides extensive control over updates. It's natively available in the Windows Server operating system. Organizations can use this tool to both defer updates and add an approval layer for updates. They can also use this tool to deploy updates to specific computers or groups of computers whenever they're ready.
 -  **Microsoft Endpoint Configuration Manager**. Provides the greatest control over servicing Windows as a service. IT pros can defer updates, approve them, and have multiple options for targeting deployments and managing bandwidth usage and deployment times.

The following table provides a comparison of these servicing tools.

| **Servicing tool**             | **Can updates be deferred?** | **Can updates be approved?** | **Peer-to-peer option**                                                                                                                                                                                                                                                                                                                                                                                     | **Other features**                               |
| ------------------------------ | ---------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| Windows Update                 | Yes (manual)                 | No                           | Delivery Optimization                                                                                                                                                                                                                                                                                                                                                                                       | None                                             |
| Windows Update for Business    | Yes                          | No                           | Delivery Optimization                                                                                                                                                                                                                                                                                                                                                                                       | Other Group Policy objects                       |
| Windows Server Update Services | Yes                          | Yes                          | BranchCache or Delivery Optimization                                                                                                                                                                                                                                                                                                                                                                        | Upstream/downstream server scalability           |
| Configuration Manager          | Yes                          | Yes                          | BranchCache, Client Peer Cache, or Delivery Optimization. For the latter, see [peer-to-peer content distribution](/configmgr/sum/deploy-use/optimize-windows-10-update-delivery#peer-to-peer-content-distribution?azure-portal=true) and [Optimize Windows Update Delivery](/windows/deployment/do/waas-optimize-windows-10-updates?azure-portal=true). | Distribution points, multiple deployment options |

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”