To align with the new method of delivering feature updates and quality updates in Windows 10, Microsoft introduced the servicing channels to let you choose how frequently your devices are updated. For example, an organization may have test devices that the IT department can update with new features as soon as possible, and then specialized devices that require a longer feature update cycle to ensure continuity. 

There are three servicing channels: 

- **Windows Insider Program**. Pre-release Windows builds  that let you explore and test new features before they're released to the wider public. You can also provide feedback to Microsoft (through the Feedback Hub) to help resolve any issues with updates. Feature updates are released to the Windows Insider program about once a week.

- **Semi-annual channel**. Twice-yearly feature updates. Devices in the semi-annual channel receive updates as soon as Microsoft publishes them. 

When Microsoft officially releases a feature update for Windows 10, it's available to any PC not configured to defer feature updates. You can defer the installation of these updates by using Windows Server Update Services (WSUS), Microsoft System Center Configuration Manager, or Windows Update for Business. In this scenario, the content available for the Semi-Annual Channel will be available to devices but not necessarily mandatory to install, depending on the policy you are using. 

Start targeted deployments within your organization as soon as a SAC release is available, deploying to an initial servicing ring, or rings, for validation. Target specific devices until you feel confident to make the decision to deploy broadly, at which time you'll update all of the devices in your organization.

- **Long-term servicing channel**. Specialized systems — such as PCs that control medical equipment, point-of-sale systems, and ATMs — often require a longer servicing option because of their purpose. These devices typically perform a single important task and don’t need feature updates as frequently as other devices in your organization. It’s more important that these devices be kept as stable and secure as possible than up to date with user interface changes. Deploy the LTSC release to these devices to prevent them from receiving the usual feature updates. The LTSC is updated with quality updates to ensure that device security stays up to date.

The long-term servicing channel is only available in the Windows 10 Enterprise LTSC edition. This edition of Windows 10 doesn’t include a number of applications, like Microsoft Edge, Microsoft Store, Cortana (limited search capabilities remain available), Microsoft Mail, Calendar, OneNote, Weather, News, Sports, Money, Photos, Camera, Music, and Clock. These apps aren’t supported on Windows 10 Enterprise LTSC, even if you install them using sideloading.
