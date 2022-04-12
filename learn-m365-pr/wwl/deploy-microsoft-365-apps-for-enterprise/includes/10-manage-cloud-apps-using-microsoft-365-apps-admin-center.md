The Microsoft 365 Apps admin center provides modern management in the cloud for organizations who deploy and manage Microsoft 365 Apps for enterprise. The Microsoft 365 Apps admin center can be accessed from the Microsoft 365 admin center by completing the following steps:

1.  From the **Microsoft 365 admin center**, select **...Show all** in the navigation pane.
2.  Under the **Admin centers** group, select **All admin centers**.
3.  On the **All admin centers** page, select **Office configuration**.

The Microsoft 365 Apps admin center provides insights into various features that support app management. These features are introduced in the following sections. Links are provided for more detailed information.

### Office cloud policy service

The Office cloud policy service enables organizations to enforce policy settings for Microsoft 365 Apps for enterprise on a user's device. The Office cloud policy service is available even if the device isn't domain joined or otherwise managed. When a user signs into Microsoft 365 Apps for enterprise on a device, the policy settings roam to that device. You can also enforce some policy settings for Office for the web. These settings apply both for users who are signed in and for users who access documents anonymously. For more information, see [Overview of the Office cloud policy service for Microsoft 365 Apps for enterprise](/deployoffice/admincenter/overview-office-cloud-policy-service?azure-portal=true).

### Office Customization Tool

The Office Customization Tool creates the configuration files that are used to deploy Office in large organizations. These configuration files give you more control over an Office installation. You can define:

 -  Which applications and languages are installed.
 -  How those applications should be updated.
 -  Application preferences.

After creating the configuration files, you can use them with the Office Deployment Tool to deploy a customized version of Office. For more information, see [Overview of the Office Customization Tool](/deployoffice/admincenter/overview-office-customization-tool?azure-portal=true).

### Microsoft 365 Apps health

Microsoft 365 Apps health monitors reliability and performance metrics and provides custom guidance to help optimize and troubleshoot Microsoft 365 Apps on your client devices. If you're curious about application crash rate or boot time on a specific Microsoft 365 Apps version, you can see the insights within Apps Health. For more information, see [Microsoft 365 Apps health](/deployoffice/admincenter/microsoft-365-apps-health?azure-portal=true).

### Office Inventory

The Inventory page in the Microsoft 365 Apps admin center displays information about the state of Office installations on devices in your organization. These insights can help you identify issues with those Office installations, such as identifying devices that are running an older, unsupported build of Office. Insights are also available about add-ins that are installed on those devices.

From the Inventory page, you can drill down to see detailed information about a specific device, including:

 -  hardware information
 -  the device's operating system
 -  the Office software running on the device
 -  add-ins or macros that are present on the device
 -  the last signed in user

For more information, see [Overview of inventory](/deployoffice/admincenter/inventory?azure-portal=true).

### Service update status

You can use the security update status page in the Microsoft 365 Apps admin center to see which devices have installed the latest security updates for Office. The Security Update Status page can help organizations track their progress on getting devices up to date and secure with each security update.

You can also use this page to set a security implementation goal. You can specify as your goal the percentage of devices you want to update within a given timeframe (in days). Setting a goal doesn't create any policies or changes to your devices. The goal is used only for your personal reporting on the Security Update Status page. For more information, see [Overview of the security update status](/deployoffice/admincenter/security-update-status?azure-portal=true).

### Servicing profile

With servicing profiles, you can automatically deliver monthly Office updates for specific users or groups. You can apply a servicing profile to a set of devices in the Microsoft 365 Apps admin center. When you apply the profile, the following changes occur:

 -  The devices are moved to the Monthly Enterprise Channel.
 -  Updates to the device come from the Office Content Delivery Network (CDN).
 -  The devices are managed by the servicing profile.

Devices in the servicing profile receive updates for the Monthly Enterprise Channel beginning the second Tuesday of every month. Updates are delivered in waves to limit the impact on the network. You can pause updates and investigate and resolve update issues. You can also set deadlines for updates to be installed and dates on which updates can’t be installed. This design enables maximum uptime and minimizes end user impact and interruption. For more information, see [Overview of servicing profile](/deployoffice/admincenter/servicing-profile?azure-portal=true).
