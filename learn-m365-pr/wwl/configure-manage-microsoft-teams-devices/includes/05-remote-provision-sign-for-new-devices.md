IT admins can remotely provision and sign in to a Teams Android device. To provision a device remotely, the admin must upload the MAC IDs of the devices being provisioned and create a verification code. The entire process can be completed remotely from the Teams admin center.

## Add device MAC addresses

Complete the following steps to provision a new device:

1.  Sign in to the Teams admin center.
2.  Expand **Teams Devices**.
3.  Select **Provision new device** from the **Actions** tab.

In the **Provision new devices** window, you can either add the MAC address manually or upload a file.


### Manually add a device MAC address

1. From the **Waiting on activation** tab, select **Add MAC ID**.
1. Enter the MAC ID.
1. Enter a location, which helps technicians identify where to install the devices.
1. Select **Apply** when finished.
   
   :::image type="content" source="../media/remote-provision-6.png" alt-text="Screenshot of Manually add a device mac address.":::


### Upload a file to add a device MAC address

1. From the **Waiting on activation** tab, select **Upload MAC IDs**.
2. Download the file template.
3. Enter the MAC ID and location, and then save the file.
4. **Select file**, and then select **Upload**.

## Generate a verification code

You need a verification code for the devices. The verification code is generated in bulk or at the device level and is valid for 24 hours.

1. From the **Waiting on activation** tab, select an existing MAC ID.
   A password is created for the MAC address and is shown in the **Verification Code** column.

2. Provide the list of MAC IDs and verification codes to the field technicians. You can export the detail directly in a file and share the file with the technician who is doing the actual installation work.

## Provision the device

When the device is powered on and connected to the network, the technician provisions the device. These steps are completed on the Teams device.

1. The technician selects **Provision device** from the **Settings**.  
   
   :::image type="content" source="../media/provision-device-1.png" alt-text="Screenshot of Provision new device option from the Actions tab.":::
  
2. The technician enters the device-specific verification code in the provided input field.
   
   :::image type="content" source="../media/provision-device-verification-1.png" alt-text="Provision new device verification.":::

   Once the device is provisioned successfully, the tenant name appears on the sign-in page.
   
   :::image type="content" source="../media/provision-code.png" alt-text="Screenshot of Tenant name on sign-in page.":::

## Sign in remotely

The provisioned device appears in the **Waiting for sign in** tab. Start the remote sign-in process by selecting the individual device.

1. Select a device from the **Waiting for sign in** tab.

   
   :::image type="content" source="../media/remote-device-1.png" alt-text="Screenshot of The window with a list of devices ready for sign in.":::

2. Follow the instructions in **Sign in a user**, and then select **Close**.

   :::image type="content" source="../media/sign-in-user.png" alt-text="Screenshot of Sign in a user window for individual device.":::

## Enroll Teams Rooms Windows devices in Intune

Teams Rooms comes with a specially configured Windows 10 image supplied by the original equipment manufacturer (OEM). Successful installation and deployment of Teams Rooms requires preparation, such as account provisioning and a device deployment and enrollment strategy. 

There are two methods for enrolling Teams Rooms Windows devices in Intune. It is recommended to use bulk enrollment, which allows you to also set up the device in shared device mode.

1. [Bulk enrollment for Windows devices ](/mem/intune/enrollment/windows-bulk-enroll)

2. Use a Teams resource or DEM account to enroll the device in Intune

For more information, see [Enrolling Microsoft Teams Rooms on Windows devices with Microsoft Endpoint Manager](https://techcommunity.microsoft.com/t5/intune-customer-success/enrolling-microsoft-teams-rooms-on-windows-devices-with/ba-p/3246986?azure-portal=true).




