Eventually, all good things come to an end. The same applies to your Surface devices. There are several reasons why you might want to repurpose, wipe or retire a Surface device. If the device has been lost or stolen, you'll want to remotely wipe it to prevent any sensitive or confidential data from being used. It might be that you want to change ownership of the Surface device---for example, when you have a new employee. Rather than give them a new device, you can repurpose an existing spare. Eventually, though, the Surface device will no longer be under warranty, and you'll want to retire it.

## Remote wipe a Surface device

Whether it's a routine process, or in response to a theft or loss, at some point you'll want to remotely wipe a Surface device. In the following steps, we'll show you how to accomplish this task. First, you need to decide if you're wiping the whole device or just organizational data. For now, you'll wipe the whole device and return it back to factory settings.

1. Open Microsoft Endpoint Manager admin center (<https://endpoint.microsoft.com>) and sign in with your admin credentials. In the left navigation, select **Devices**.
1. In the **Devices | Overview** pane, under **By platform**, select **Windows**.
1. In the **Windows | Windows devices** pane, select the Surface device you wish to wipe-for example, **DESKTOP-SURFACE-006**.
1. In the **DESKTOP-SURFACE-006** pane, on the menu, select **Wipe**.
1. In the **Are you sure you want to wipe DESKTOP-SURFACE-006** dialog box, select the **Wipe** device.

    You have now triggered Surface desktop device 006 to wipe.

    > [!NOTE]
    > With Windows 10 version 1709 and later, you have the option to wipe the device, and keep associated user account and enrollment state details.

    This table indicates what data is kept and what isn't.

    |Retained during wipe                               |Not retained                                    |
    |---------                                          |---------                                  |
    |User accounts associated with the device           |User files                                 |
    |Machine state (domain-joined, Azure AD-joined)     |User-installed apps (store and Win32 apps) |
    |Mobile device management (MDM) enrollment          |Non-default device settings                |
    |OEM-installed apps (store and Win32 apps)          |                                           |
    |User profile                                       |                                           |
    |User data outside of the user profile              |                                           |
    |User auto login                                    |                                           |

## Redeploy a Surface device to a new employee (Fresh Start)

A Surface device might outlast the individual it was assigned to, or you may want to pass it on to a new employee. To prepare the Surface device for the next user, you can use the Fresh Start option. When triggered, Fresh Start removes all the installed apps, and any pre-installed OEM apps.

If you don't wish to retain the user data, the device will be restored to the default out-of-box experience (OOBE) state.

To run a Fresh Start on a Surface device, use the following steps:

1. Sign in to the Microsoft Endpoint Manager admin center (<https://endpoint.microsoft.com>) with your admin credentials.
1. From the home page, select **Devices**, and then select **All devices**.
1. From the list of devices you manage, choose the Surface device you wish to redeploy.
1. Select **Fresh Start**.
1. Select **Retain user data on this device** to:
    1. Keep the device Azure AD-joined.
    1. Ensure the device is enrolled into mobile device management again when an Azure Active Directory enabled user signs into it.
    1. Keep the contents of the device user's Home folder, and remove apps and settings.
1. Select **OK**.
1. To see the status of this action, go back to **Devices** and Select **Device actions**.
1. The device will be restored to the initial sign-in screen.

## Retire a Surface device

Retiring a device means removing it as a Microsoft Endpoint Manager admin center managed device. As an administrator, you may need to retire the device if it was a BYOD, or if it's going to be scrapped. The retire action triggers the removal of managed app data, email profiles, and settings that were applied during the enrollment process.

After a Surface device has been marked as retired, this happens the next time someone connects to your organization's tenant.

Retirement leaves the user's personal data on the device.
