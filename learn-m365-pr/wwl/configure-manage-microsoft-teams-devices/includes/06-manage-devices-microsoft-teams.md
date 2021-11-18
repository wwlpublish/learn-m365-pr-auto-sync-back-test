Admins can manage devices used with Microsoft Teams. They can use the Microsoft Teams admin center to complete the following tasks:

- View and manage their organization's device inventory
- Change device configuration
- Restart devices
- Manage updates
- Monitor diagnostics
- View device and peripheral health
- Create and assign configuration profiles to a device or groups of devices

To manage devices in Microsoft Teams, you must be assigned one of the following Microsoft 365 admin roles:

- Microsoft 365 Global admin
- Teams admin
- Teams Device admin

You can manage any device that's certified for, and enrolled in, Teams. Admins can manage the following types of certified devices:

* Teams Rooms on Windows
* Teams Rooms on Android
* Panels
* Phones
* Displays


## Manage devices

Devices must be enrolled in Microsoft Teams before they can be managed through the Teams admin center. Organizations can use the Teams admin center to view and manage devices. The following information can be maintained and displayed for each device:

- Device name
- Manufacturer
- Model
- User
- Status
- Action
- Last seen
- History

If an organization is signed up for Microsoft Intune, then all devices are automatically enrolled in Intune. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device.

The following chart displays examples of how an organization can manage devices.  

| To do this task...                           | Complete these steps                                                                                                                                                                                                                                                                                                      |
|--------------------|---------------------------------------------------------|
| Change device information               | Select a device > **Edit**. You can edit details such as device name, asset tag, and add notes.                                           |
| Manage software updates                 | Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install.                                         |
| Upgrade Teams phones to Teams displays  | On the **IP phones** page, select one or more Teams phones > **Upgrade**. This option is available only to phones that support upgrading to Teams displays. To learn more, see [Upgrade Teams phones to Teams displays](/microsoftteams/devices/upgrade-phones-to-displays?azure-portal=true).                                                      |
| Assign or change configuration policies | Select one or more devices > **Assign configuration**.                                                                                                                                                                                                                                                       |
| Add or remove device tags               | Select one or more devices > **Manage tags**.                                                                                                                                                                  |
| Restart devices                         | Select one or more devices > **Restart**.                                                                                                                                                                                                                                                                    |
| Filter devices using device tags        | Select the filter icon, select the **Tag** field, specify a device tag to filter on, and select **Apply**.  |
| View device history and diagnostics     | Under the **History** column, select the **View** link for a device to view its update history and diagnostic details. |

:::image type="content" source="../media/manage-phones.png" alt-text="Manage phones" lightbox="../media/manage-phones.png":::

## Manage Teams Rooms devices

Organizations can use the Teams admin center to view and remotely manage their Teams Rooms devices. The Teams admin center makes it easy to see, at a glance, which devices are healthy and which need attention. It also lets admins focus on specific devices to monitor information about device health, meeting performance, call quality, and peripherals.

The following chart displays examples of how an organization can manage its Teams Rooms devices. Teams Rooms devices can be found in the [Microsoft Teams admin center](https://admin.teams.microsoft.com?azure-portal=true) under **Devices** > **Teams Rooms**.

For details about how to manage your Teams Rooms devices, see [Manage Microsoft Teams Rooms](/microsoftteams/rooms/rooms-manage).

| To do this task...                          | Complete these steps                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Change settings on one or more devices | Select one or more devices > **Edit settings**. If you select multiple devices, the values you change will replace the values on all the selected devices.                                                                                                                                                                                                                       |
| Restart devices                        | Select one or more devices > **Restart**. When you restart a device, you can choose whether to restart the device immediately or select **Schedule restart** to restart the device at a specific date and time. The date and time you select are local to the device being restarted.                                                                                            |
| View meeting activity                  | Select a device name to open device details > **Activity**. When you open the **Activity** tab, you can see all the meetings that the device has participated in. This summary view shows the meeting start time, the number of participants, its duration, and the overall call quality.                                                                                        |
| View meeting details                   | Select a device name to open device details > **Activity** > select a meeting. When you open a meeting's details, you can see all of the participants in the meeting, how long they were in the call, the Teams session types, and their individual call quality. If you want to see technical information about a participant's call, select the participant's call start time. |

:::image type="content" source="../media/admin-1.gif" alt-text="Manage Teams Rooms devices" lightbox="../media/admin-1.gif":::  
