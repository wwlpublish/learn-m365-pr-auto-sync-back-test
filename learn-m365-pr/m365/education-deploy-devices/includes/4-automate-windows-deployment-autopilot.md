The preparation of new and existing computer devices for the new school year's start can create a burden of work for any school IT department. Microsoft provides two tools, Windows Autopilot and Autopilot Reset, which can simplify the administrative overhead.

In your role as the school's IT administrator, you want to understand how Windows Autopilot can help in the setup and configuration of classroom Windows devices. You also want to see how you can use Autopilot Reset to ready existing devices for the beginning of the new school year.

Here, you'll learn about Windows Autopilot and Autopilot Reset.

## Windows Autopilot for Education

Windows Autopilot allows you to deploy devices at scale across your whole school.  Windows Autopilot can reduce the time and resources needed by deploying and managing Windows devices across your school.

:::image type="content" source="../media/4-autopilot-for-education.png" alt-text="Diagram showing the steps to follow to deploy classroom-ready Windows devices using Windows Autopilot for Edu.":::

### Windows Autopilot deployment in user-driven mode

Windows Autopilot user-driven mode can automate the deployment of configuration profiles for out-of-the-box (OOBE) devices by enabling the teacher or student to configure their own devices when they're first turned on.  

Once enabled, the student or teacher would follow this process:

1. Turn on the device.
1. Choose their preferred language.
1. Configure one or more keyboards.
1. Connect to the School Wi-Fi or wired network.
1. Sign in to the school network using their student or teacher authentication credentials.

While the device enrolls, the user can't interact with it until the setup is complete.

### Prerequisites for using Windows Autopilot

Before you can use Windows Autopilot in your schools Intune for Education, you'll need to make sure your school environment meets these requirements:

#### Windows Autopilot requirements

Windows Autopilot depends on specific features available in Windows 10, Azure Active Directory, and MDM services, such as Microsoft Intune.  To use Windows Autopilot and access these features, some software requirements must be met.

> [!NOTE]
> Windows Autopilot does not support products that are beyond their support lifecycle. For more information, see Microsoft Lifecycle Policy.

The following Windows editions are supported:

- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Pro for Workstations
- Windows 10 Enterprise
- Windows 10 Education
- Windows 10 Enterprise 2019 LTSC

#### Determine user permissions

During Windows Autopilot registration, you'll need to assign group tags to your devices. If you require different user permissions on other devices, you'll need to split the devices into two group tags, according to permissions. Provide unique names for each group, for example, *teachers* and *students*.

#### Order and register the school devices

Before deploying a device using Windows Autopilot, the device must be registered with the Windows Autopilot deployment service. Ideally, this registration is performed by the OEM, reseller, or distributor from which the devices were purchased. However, the school's IT department can also do the registration by collecting the hardware identity and uploading it manually.

#### Configure your tenant for Intune for Education

After your Azure tenant syncs your school's information, the School Data Sync (SDS) will automatically create a school group and create student and teacher groups.

#### Configure your school's branding

Go to the Microsoft Azure portal to add your organization's branding to your school devices.

### Things to consider when using Windows Autopilot

Windows Autopilot automates the setup and configuration of the classroom devices to the users.  There are many things to consider when using this approach:

- All the students signing in at the same time. If all the computers try to download profile configurations, including apps and other resources, at the same time, this will create a burden on the school network and could lead to slow setup times.
- Each classroom device needs to be plugged in or fully charged before the setup will run.  This could create a problem in classrooms where plug points are limited.
- The setup time can be around an hour for a lightweight setup and considerably longer for larger configurations, for instance, when installing Office.  The length of time it takes can also be impacted by the number of concurrent students trying to set up the computers simultaneously.

### Configure Autopilot deployment profiles

For Windows Autopilot to work, you'll need to create a deployment profile. It's good practice to configure the default Autopilot deployment profile for regular user permissions first before starting the deployment profiles with administrator permissions.

Note that Intune for Education only supports user-driven mode and doesn't require you to configure company branding.

### Group Autopilot-registered devices using a group tag

When creating Windows Autopilot policies, it's a good idea to create a group tag. Creating a group tag rule will automatically populate a group with devices as they complete the Autopilot registration process.

1. Go to Groups, and select **Create group**.
1. Name your group.
1. Under Group type, select Dynamic.
1. Under Rules:
   1. Select Devices.
   1. Select Windows.
   1. Select the Device that starts with the group tag.
   1. Type in the name of the group tag.
1. Select **Create group**. All Autopilot-registered devices with the specified group tag will be added to your new group.
1. Next, go to **Settings** then select **Windows Device Settings**.  Now select **Enrollment** and choose **Windows Autopilot** to configure your group's deployment profile.

## Windows Autopilot Reset

Through Windows Intune, Autopilot Reset lets remotely wipe all the data on your devices in your school in preparation for the new school year start. It removes all the apps, settings, and user data but preserves the device's enrollment in Azure AD and Intune.  Once reset, the Windows device will be refreshed with the latest Intune policies needed for that classroom.

A reset can also be applied to a group of devices.

1. From the Windows Intune for Education portal, select **Groups**
1. Choose a device group.
1. Choose a single device or group of devices, then select **Autopilot Reset**.
1. To confirm the reset, select **Autopilot Reset** again.

The selected device(s) will reset the next time they connect to the school network, either in the classroom or remotely.

> [!NOTE]
> You cannot use Autopilot Reset to reset an entire group. Autopilot Reset can reset up to 2000 devices at a time, and you can select the devices you want to reset either from the device list in a group or the full device list in the *Devices* blade. If you choose to use the *Devices* blade, you can apply filters to the device list to limit the operation to 2000 or fewer devices. Use the *Select all* box at the top to select the entire filtered list.
