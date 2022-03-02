An increasing number of devices use wireless connections as the primary method for accessing corporate intranets and the Internet. Additionally, many users have come to expect a wireless infrastructure in a corporate workplace. As a result, a good-working knowledge of wireless connectivity is a requirement for today’s networking environment.

### Configuring Wi-Fi Settings/Profile

Windows makes it very easy to connect to and configure wireless network settings. Use the following procedures to manage your wireless network connections.

:::image type="content" source="../media/windows-10-configure-wifi-fbd67219.jpg" alt-text="Diagram showing the relationship of IPv4.":::


#### Connect to a wireless network

To connect to a wireless network:

1.  Tap the wireless network icon on the notification area to see a list of available wireless networks.
2.  Tap the network of your choice.
3.  Tap **Connect**.
4.  When prompted, enter the security information required by the wireless hub to which you are connecting your device, and then tap **Next**.

You are connected.

#### Configure wireless networks

To configure your wireless networks:

1.  Open **Settings**.
2.  Select **Network &amp; Internet**.
3.  Select **Wi-Fi**.
4.  On the **Wi-Fi page**, choose the following options:
    
     -  **Connect to suggested open hotspots**
     -  **Let me use Online Sign-Up to get connected**
     -  **Get online when you’re on the go by buying Wi-Fi**
5.  At the top of the page, select **Manage known networks**.
6.  On the **Manage known networks** page, tap the network you want to manage.
7.  Tap to view **Properties or Forget** the network.
8.  Configure advanced wireless properties

From the Network and Sharing Center, you also can configure advanced wireless properties:

1.  In the **Network and Sharing Cente**r, tap the name of your wireless network adapter on the right.
2.  In the **Wi-Fi Status** dialog box, you can view the properties of your wireless connection.
3.  Tap **Wireless Properties** to view additional information, including the security settings of the connection.

You can use Windows Server Group Policy Objects (GPOs) to configure wireless profiles. This saves your users from having to configure their wireless connections manually.

## Miracast

Windows has built-in support for the Wi-Fi Alliance Miracast devices. Miracast is a protocol that will transmit audio and video between devices via Wi-Fi. It is peer-to-peer and uses Wi-Fi Direct for the connection. It is not necessary that both devices are connected to the Internet. They only need to share the same local wireless network. The shared information is sent by the device via Wi-Fi through a Wi-Fi Direct connection to a receiver connected to the display device. The receiver then decodes the video signal and passes it to the TV display (or other display device). Miracast supports WPA2-PSK encryption, so all content you share is safe.

## Near Field Communication

Windows has built-in support for Near Field Communication (NFC), which is still an emerging technology based on short-range wireless radio technologies using radio frequency identification (RFID). NFC-enabled printing enables users to “tap” a device (such as a tablet or phone) onto a printer to connect to it. Where the components cannot be tapped together, NFC should still work if the devices are brought close together, within a maximum distance of 4 inches (10 centimeters).

NFC is similar to Bluetooth, but without the option to manually pair—the communication is triggered due to physical proximity. NFC uses short-range radio waves for discovery and for transmitting data, and requires some form of NFC-enabled hardware, such as a smart tag, sticker, key fob, or wallet card, which may also be located inside a laptop or tablet. Most smartphones have NFC built into the devices, which enables NFC sharing of photos between NFC-connected devices.

Once an enterprise has made available NFC-enabled devices, administrators can perform the following management tasks:

 -  Add an NFC smart tag to their printer, or purchase printers with NFC built in.
 -  Enable the following connection types to be used: Universal Naming Convention (UNC), Web Services on Devices (WSD), and Wi-Fi Direct.
 -  Optionally, use the PowerShell cmdlet Write-PrinterNfcTag to provision an NFC tag with information about a printer.
 -  Although NFC built-in support is provided by Windows, this is available for OEMs and ISVs to produce NFC-enabled hardware. NFC offers mobile devices significant opportunities to access resources by using proximity alone. Other emerging technologies include Windows support for the Windows Sensor and Location platform, and support for the Windows Biometric Framework (WBF). These frameworks enable developers to utilize support for sensors, which can be attached or embedded within modern Windows devices (phone, tablets, Internet of Things, PCs), and include capabilities such as:
 -  Speed, motion, acceleration, gyrometer
 -  GPS location, elevation, inclinometer, compass orientation
 -  Humidity, temperature, light, atmospheric pressure
 -  Biometric human proximity, human presence
