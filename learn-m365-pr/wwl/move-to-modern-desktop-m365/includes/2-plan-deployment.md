The two most critical parts of planning an enterprise deployment of Windows 10 and Microsoft 365 Apps are (1) assessing your environment and network, and (2) making sure your existing hardware and applications will work with the new software. 

## Assess hardware and application compatibility

Almost all the applications written in the last 10 years will run on Windows 10, and almost all add-ins and Visual Basic for Applications (VBA) macros that are based on previous versions of Office will continue to work on the latest versions of Office. However, depending on the size and age of your organization, verifying application and hardware compatibility will still be an essential first step in deploying the modern desktop. 

Microsoft offers several tools to help with making sure your applications and hardware are compatible, including: 

- **Windows Upgrade Readiness**. The recommended tool for assessing desktop device and application readiness. It provides application and driver compatibility information to give you a detailed assessment of issues that might block your upgrade. It's supported with links to suggested fixes known to Microsoft. 
- **The Readiness Toolkit for Office add-ins and VBA**. This tool can help you identify compatibility issues with your Microsoft VBA macros and add-ins that you use with Office. The toolkit can scan for VBA macros in Word, Excel, PowerPoint, Outlook, Access, Project, Visio, and Publisher files for Office versions as far back as Office 2003. It can also scan for certain types of add-ins used with Office. 
- **Desktop App Assure**. The FastTrack Center Benefit for Windows 10 provides access to Desktop App Assure, a new service designed to address issues with Windows 10 and Microsoft 365 Apps application compatibility. For customers with an eligible subscription, a Microsoft engineer works with you to address valid application issues. 

As part of your testing process, we recommend deploying Windows 10 and Microsoft 365 Apps first to a pilot group of users and client devices from across your organization. For example, you might want to include devices from your finance department, because those devices probably include specialized line-of-business applications and macros. This pilot group can test the initial deployment of Windows 10 and Microsoft 365 Apps as well as future updates. 

## Assess and optimize your network

Network bandwidth is a critical consideration when deploying and managing updates for Windows 10 and Microsoft 365 Apps. Installation files for Microsoft 365 Apps, for example, are at least 1.6 GB in size for the core files, plus at least 250 MB for each language deployed. 

Microsoft has built-in methods for automatically limiting bandwidth, including reducing the size of update downloads with express update delivery and binary delta compression. As a result, you'll download only the changes between the current update and the previous update, which can significantly minimize the impact to your network. 

Peer-to-peer options help shift traffic related to Windows 10 and Microsoft 365 Apps away from the center of the network and reduce the need for classic throttling approaches. They let computers find the update files they need on peers in their local network, rather than downloading them from a distribution point or the internet. Microsoft 365 includes the following peer-to-peer options: 

- **BranchCache** can help you download source files in distributed environments without saturating the network. BranchCache fetches content from your main office or hosted cloud content servers and caches the content at branch office locations, allowing client computers at branch offices to access the content locally. 
- **Peer cache** is a solution in Configuration Manager that enables clients to share source files with other clients directly from their local cache. You can use peer cache to help manage deployment of source files to clients in remote locations. BranchCache and peer cache are complementary and can work together in the same environment. 
- **Delivery Optimization** allows clients to download source files from alternate sources (such as other peers on the network) in addition to the traditional Internet-based Windows Update servers. You can use Delivery Optimization with Windows Update, Windows Server Update Services (WSUS), Windows Update for Business, or Configuration Manager.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Manage Windows upgrades with Upgrade Readiness](https://docs.microsoft.com/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness)
- [The Readiness Toolkit for Office add-ins and VBA](https://docs.microsoft.com/DeployOffice/use-the-readiness-toolkit-to-assess-application-compatibility-for-office-365-pro)
- [Desktop App Assure](https://docs.microsoft.com/windows/compatibility/app-assure)
