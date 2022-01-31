The use of audio and video devices in Teams is important for a rich user experience. However, users can occasionally experience problems with audio and video device configuration. 

## Verify Teams policy settings

Before you investigate specific device configuration, verify the any policies assigned to a user don’t prohibit the use of audio or video. For problems in meetings, a good place to start is by reviewing the Audio & video policy settings. 

Open the **Microsoft Teams admin center**, and review the **Audio & video** section of the appropriate meeting policy, as shown in the following screenshot.

:::image type="content" source="../media/audio-video-settings.png" alt-text="A screenshot that displays the Audio & video meeting policy settings. Defaults are configured.":::

Ensure that the **Mode for IP audio** and **Mode for IP video** are both enabled. Also ensure that **Allow IP video** is enabled. 

> [!TIP]
> If video quality is poor, increase the **Media bit rate (Kbps)** value. 

## Verify network settings

Specific network ports must be accessible in Teams. These can be reviewed or managed in the **Meeting settings** page in the **Microsoft Teams admin center**. Ensure that the audio and video ports are available. 

:::image type="content" source="../media/share-ports.png" alt-text="A screenshot that displays the Network section of Meeting settings. Default values are displayed.":::

## Verify audio and video device configuration

If you’ve verified that the policy configuration is correct, then you can move on to examine the device configuration. Start by verifying if the audio and video devices installed in the user computer work in other apps. If they do, then the problem might be related to the Teams client only. If not, then start by troubleshooting the devices in Windows. 

To troubleshoot audio devices in Windows:

1. Open **Settings** and then select **Devices**. Verify the presence and functionality of the devices. 
2. Then, in **Settings**, select **System** and then select **Sound**. 
3. Adjust volume and input levels, and if necessary, select the **Troubleshoot** button beneath each device. 

To troubleshoot video devices in Windows:

1. In Settings, in search, enter **camera**, and then select Choose which apps can access your camera. 
2. Ensure that under the **Allow access to the camera on this device setting** heading, Camera access for this device is on. If not, select **Change**, and toggle the setting to **On**.
3. Scroll down to the **Allow desktop apps to access your camera** section, and verify that Microsoft Teams is listed. 

If your devices don’t display properly in Settings, consider advanced troubleshooting in Device Manager. Use the following procedure to troubleshoot audio and video devices in Device Manager:

1. Right-click **Start** and select **Device Manager**.
2. Locate **Cameras**, and then select your camera in the device list. 
3. If the device shows as in error, remove the device and then scan for hardware changes. The device will be detected and the driver installed from the driver store. 
4. Right-click the device and select **Properties**.
5. On the **Driver** tab, if the driver has been recently updated, consider rolling back the driver. Alternatively, if the driver is quite old, consider updating the driver. 
6. In Device Manager, under **Sound, video, and game controllers**, repeat the preceding steps for the displayed audio device.

If the audio and video devices work with Windows and with other Windows apps, then review the audio and video devices settings in Teams: 

1. In Teams, select the ellipsis button and then select **Settings**. 
2. Select the **Devices** tab, as displayed in the following screenshot. 
3. Verify that the correct audio and video devices are selected. 
4. If necessary, make a test call. 
5. Close Settings. 

:::image type="content" source="../media/teams-audio-video-settings.png" alt-text="A screenshot that displays the Device tab in Settings in the Teams desktop client.":::

## Resolve issues with 4K/UHD monitors

Overall Teams performance can be impacted on laptops that are docked to external 4K or UHD monitors. If your users experience this problem, consider performing one or more of the following tasks:

- Close any other apps and unused browser tabs
- Reduce the resolution of the monitor temporarily to 1920 x 1080
- Undock from the UHD monitor
- Turn off the webcam
- Turn off incoming video during the meeting
