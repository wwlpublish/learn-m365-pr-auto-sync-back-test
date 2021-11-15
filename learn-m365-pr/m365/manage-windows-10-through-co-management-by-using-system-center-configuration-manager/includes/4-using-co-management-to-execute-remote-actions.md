IT must be able to ensure that every device they manage is reachable – no matter where it is – whenever it connects. IT must also provide each device and device user with everything needed to stay productive while protecting the apps and data being used. With the device actions supported by Intune and co-management, these critical functions can be solved remotely.

|||
| :--- | :--- |
| :::image type="icon" source="../media/video-icon.png"::: | In the following video, principal program manager Heidi Cheng and senior program manager Danny Guillory discuss and demo remote actions with co-management.|

>[!VIDEO https://www.youtube.com/embed/MVKvN_JirHs]

## Available remote actions

Use these remote actions from Intune once you enable co-management in Configuration Manager.

|||
| :--- | :--- |
| **Remove devices** | **Retire**: This action removes managed apps and data (where applicable), settings, and e-mail profiles that were assigned to that device. The device is then removed from Intune management. This process happens the next time the device checks in and receives the remote retire action. The Retire function leaves the user's personal data on the device.<br /><br />**Wipe**: This action restores a device to its factory default settings. If you choose the option to Retain enrollment state and user account, then the user data is kept. Otherwise the drive is securely erased.<br /><br />**Delete**: If you want to remove devices from the Intune on Azure portal, delete them from the specific device pane. The next time the device checks in, it removes any organizational data stored on it. |
| **Selective wipe** | When you choose an App selective wipe, it removes company app data without removing personal data. Use this action when a device is reported as lost or stolen. |
| **Sync** | The Sync device action forces the selected device to immediately check in with Intune. When a device checks in, it immediately receives any pending actions or policies that you've assigned to it.<br /><br />This feature can help you immediately validate and troubleshoot policies you've assigned, without waiting for the next scheduled check-in. |
| **Restart** | The **Restart** device action causes the device you choose to restart. This action is useful when there's a pending reboot, but the user isn't available to do it. |
| **Fresh Start** | The Fresh Start device action removes any apps installed on a device running Windows 10, version 1703 or later. Fresh Start helps remove pre-installed (OEM) apps that are typically installed with a new device.<br /><br />If you choose not to retain user data, the device restores to its out-of-box state. It unenrolls from Azure AD and MDM.<br /><br />If you have predetermined standards regarding what apps should be on the device, then this action eliminates the ones that don't meet your criteria. |
| **Remote control** | Devices managed by Intune can be administered remotely using SCCM or [TeamViewer](https://www.teamviewer.com/). TeamViewer is a third-party program that you acquire separately. |

Other than remote control via TeamViewer, to start using these remote device actions in Intune, no additional setup is required after you [enable co-management](/sccm/comanage/how-to-enable?azure-portal=true).

## Learn more

- [Tutorial: Enable co-management for existing Configuration Manager clients](/configmgr/comanage/tutorial-co-manage-clients?azure-portal=true)
- [Mobile device management](/windows/client-management/mdm/?azure-portal=true)
