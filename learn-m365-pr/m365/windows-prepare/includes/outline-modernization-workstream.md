
Your technical director wants to use Desktop Analytics to help facilitate the feature update. As the process manager, you want the team to better understand what Desktop Analytics is, and how the team will use it as part of the deployment process.

## Benefits of Desktop Analytics

As the process manager, you explain that Desktop Analytics provides Woodgrove with many advantages that it can use to improve the environment's application and device readiness. For example:

- **Device and software inventory**: Easily manage an inventory of devices and applications across your whole estate
- **Pilot identification**: Desktop Analytics helps Woodgrove identify what should be the best and smallest number of devices that it should use to validate for widest coverage of real-world usage

- **Issue identification**: Desktop Analytics can identify potential issues proactively and will suggest recommendations to deal with issues

## Requirements for Desktop Analytics

You explain that Woodgrove needs to meet [requirements](/configmgr/desktop-analytics/overview#prerequisites) to use Desktop Analytics, including the following:

- An Active Azure subscription, along with an account that has the Global Administrator role
- Configuration Manager (version 1902 or later), with the Full Administrator role
- Devices can connect to Microsoft's public cloud services
- Access to Windows Diagnostic data (at least Basic level, Enhanced level is recommended)
- Valid Windows 10 Enterprise licenses (E3, E5, A3, or A5)

## Desktop Analytics tasks

The Woodgrove infrastructure team have confirmed that the organization can successfully meet the requirements, it can start to take advantage of Desktop Analytics. At a higher level, you highlight that Woodgrove will have to perform the following tasks to successfully use Desktop Analytics:

1. **Set up Desktop Analytics**. This step involves:
    - Accessing the [Desktop Analytics portal](https://aka.ms/desktopanalytics)
    - Reviewing and accepting the service agreement
    - Setting up a Desktop Analytics workspace
1. **Connect Configuration Manager**. Woodgrove can do this by:
    - Updating Configuration Manager site to version 1902 or later, installing the version 1902 update rollup, and updating clients using automatic client upgrade
    - Connecting to the service by connecting to Desktop Analytics using the Azure Services wizard in Configuration Manager
1. **Enroll devices**: Desktop Analytics doesn't need agents for device enrollment. Instead, Woodgrove should use Configuration Manager to deploy enrollment settings to the clients it wants to enroll in Desktop Analytics.

Use the [how-to guide](/configmgr/desktop-analytics/set-up) for a detailed step-by-step walkthrough on setting up and using Desktop Analytics.
