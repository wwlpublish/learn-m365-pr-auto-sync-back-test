While Microsoft has two solutions for MDM, Intune and Basic Mobility and Security, they don't have the same prerequisites. Preparing your MDM environment will be a bit different depending on which solution you want to use.
-  **Basic Mobility and Security.** Start by activating the Mobile Device Management service. Once you activate the MDM service, you must then do several other steps to complete the deployment.-  **Intune.** Choose the MDM authority before you can start managing devices.

### Basic Mobility and Security

In Microsoft 365, you activate the Basic Mobility and Security MDM service by running the following link:<br>

**`https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx#`**

It takes some time for the service to start, after which you'll receive an email that explains the next steps for setting up Basic Mobility and Security. These steps include:

1.  **Configure domains for Basic Mobility and Security.** If you don't have a custom domain associated with Microsoft 365 or if you're not managing Windows devices, you can skip this step. Otherwise, you'll need to add DNS records for the domain at your DNS host. If you've already added the records as part of setting up your domain with Microsoft 365, then this step is complete.<br><br>After you add the records, the Microsoft 365 users who sign in on their Windows device with an email address that uses your custom domain are redirected to enroll in Basic Mobility and Security.
2.  **Configure an Apple Push Notification Service (APNS) certificate for iOS devices.** This step is only required if you have iOS devices. To manage iOS devices like iPad and iPhones, you must first create an APNS certificate.<br>
3.  **Set up multi-factor authentication.** MFA helps secure user sign in to Microsoft 365 for mobile device enrollment by requiring a second form of authentication. Users must reply to a phone call, text message, or app notification on their mobile device after correctly entering their work account password. They can only enroll their device after this second form of authentication is completed. After users enroll their devices in Basic Mobility and Security, they can access Microsoft 365 resources with just their work account.<br>
4.  **Manage device security policies.** Organizations should create and deploy device security policies to help protect their Microsoft 365 data. For example, you can help prevent data loss if a user loses their device by creating a policy to lock devices after five minutes of inactivity and have devices wiped after three sign-in failures.<br>
5.  **Make sure users enroll their devices.** After you've created and deployed an MDM policy, each licensed Microsoft 365 user in your organization will receive an enrollment message the next time they sign into Microsoft 365 if the policy applies to their device. They must complete the enrollment and activation steps before they can access Microsoft 365 email and documents. Users with Android or iOS devices are required to install the Company Portal app as part of the enrollment process.

### Microsoft Intune

To set up Microsoft Intune for device management, organizations must configure the MDM authority. Device management in Intune is initially disabled and MDM authority is unknown. Before an organization can start enrolling and managing devices, it must configure the MDM authority by selecting one of three available options:
-  **Intune MDM Authority**. This option sets the MDM authority solely to Microsoft Intune. Intune is a cloud-only MDM solution, and it's managed by using a web browser. Microsoft recommends that organizations select this deployment option when using Intune.-  **Configuration Manager MDM Authority**. This option is referred to as Hybrid MDM because it assumes the organization uses Configuration Manager for managing on-premises devices. This scenario integrates Intune's MDM capabilities into Configuration Manager in the following manner:       -  It uses Intune as the delivery channel for policies, profiles, and applications to devices.    -  It uses Configuration Manager’s on-premises infrastructure to administer content and manage the devices.-  **None**. This option indicates that no MDM Authority has been chosen. Devices can only be managed by Intune if an MDM authority is chosen.

If organizations want to enroll and manage iOS devices, they must also add an APNS certificate to Intune. No certificate is needed for enrolling and managing Android and Windows 10 devices.<br>

If an organization wants to change its MDM authority setting, it can do so by using the Configuration Manager console. In the past, you had to contact Microsoft Support to make this change for you. You also had to unenroll and reenroll your existing managed devices. However, organizations can now make this change on their own, and they no longer need to unenroll and reenroll their existing managed devices.

To set up mobile device management with Intune, you must complete the following steps. Devices must be managed before you can give users access to company resources or manage settings on those devices. Some steps, such as setting up an Intune subscription and setting the MDM authority, are required for most scenarios. Other steps, such as configuring a custom domain or adding apps, are optional depending upon your company's needs.

1.  **Supported configurations.** Need-to-know information before you start. This information includes supported configurations and networking requirements.
2.  **Sign in to Intune.** Sign in to your trial subscription or create a new Intune subscription.
3.  **Configure domain name.** Set DNS registration to connect your company's domain name with Intune. This setting gives users a familiar domain when connecting to Intune and using resources.
4.  **Add users and groups.** Add users and groups, or connect Active Directory to sync with Intune. This step is required unless your devices are "userless", such as kiosk devices. Groups of users are used for assign apps, settings, and other resources.
5.  **Assign licenses.** Give users permission to use Intune. Each user or userless device requires an Intune license to access the service.
6.  **Set the MDM authority.** Use user and device groups to simplify management tasks. Groups are used to assign apps, settings, and other resources.
7.  **Add apps.** Apps can be assigned to groups of users and automatically or optionally installed.
8.  **Configure devices.** Set up profiles that manage device settings. Device profiles can preconfigure settings for email, VPN, Wi-Fi, and device features. They can also restrict devices to help protect both devices and data.
9.  **Customize Company Portal.** Customize the Intune Company Portal that users use to enroll devices and install apps. These settings appear in both the Company Portal app and the Intune Company Portal website.
10. **Enable device enrollment.** Enable Intune management of iOS/iPadOS, Windows, Android, and Mac devices by setting the MDM authority and enabling specific platforms.
11. **Configure app policies.** Supply specific settings based on app protection policies in Microsoft Intune.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”