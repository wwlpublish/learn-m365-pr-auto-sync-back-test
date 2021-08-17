When it comes to preparing your network for a deployment, you need to take into consideration any and all components that have an impact on bandwidth. The most important considerations are:

- PC imaging and app installations
- Software updates
- User personalization

**PC imaging and app installations.** For Windows images with no customization plan for 3 GB per PC; customized images with apps need 6 GB or more. You may also need to consider driver packages - these can range from a few hundred megabytes per PC up to 1 GB.

Other components can also impact your network bandwidth, including the initial installation of Office apps and any language support for deployments (of Office or Windows) that use multiple languages.  

**Software updates.** Windows 10 and Microsoft 365 Apps use a new servicing model delivering monthly and semi-annual updates. The new servicing model includes feature updates for Windows twice a year, Office semi-annual channel updates, and monthly Windows and Office quality updates.

Feature updates are typically 2 – 4 GB in size, while Office semi-annual channel updates are 300 – 400 MB per update. Monthly quality updates can range from a few hundred megabytes to over a gigabyte because monthly updates are cumulative - these increase in size over the servicing lifetime for each Windows 10 version. Microsoft offers tools to help reduce the amount of data that must pass over the network to implement updates.

**User personalization.** Plan network bandwidth to accommodate restoring user files, settings, and applications as part of the PC refresh or replacement process. Together, these items often exceed 20 GB per PC; for some users these may exceed 100 GB.

## Remote access options

If you have users that will access corporate resources remotely, you'll want to consider the bandwidth required for remote access, both now and after deployment. The amount of bandwidth required varies depending on your company's policies. Two remote access types are **Always on VPN** and **Remote Desktop Services.**

- **Remote Access Always On VPN** - Always On VPN provides a single, cohesive solution for remote access. It supports domain-joined, non-domain-joined (workgroup), or Azure AD–joined devices, even personally owned devices.

- **Remote Desktop Services** - Remote Desktop Services supports virtualized applications, secure mobile and remote desktop access, and running apps and desktops from the cloud. All of these consume bandwidth, depending on your RDS configuration.
