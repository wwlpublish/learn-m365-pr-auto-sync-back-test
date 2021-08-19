Now that you've learned about alerts and incidents, learn how to respond appropriately. You can use Microsoft Defender for Endpoint to take advantage of a wide range of response actions that enable you to address the threats that you've identified. Here, you'll get an overview of those response actions, and also learn about Live Response.

## Take actions on devices

With the appropriate role assignment, you can respond to detected threats on your devices to protect your environment. To do this, you can take response actions from the device page for a device.

:::image type="content" source="../media/3-device-actions-inline.png" lightbox="../media/3-device-actions-expanded.png" alt-text="The device page.":::

The response actions you can take on devices include:

- **Start an automated investigation**
  - Use automated investigation to detect and respond to threats effectively and consistently, at scale. You can use automated investigation to cover multiple devices simultaneously. That's because if a threat is identified across multiple devices, all of those devices will then be included in your automated investigation.
- **Collect an investigation package**
  - You can use an investigation package, which is a Zip file that contains information about suspicious entities and events on a device. Use investigation packages to understand the present state of the affected device, and to also identify the techniques and tools that an attacker used.
- **Run antivirus scan**
  - You can also use next-generation protection to remotely start an antivirus scan for your devices to find and address malware on any device.
- **Restrict app execution**
  - You can restrict specific applications from running on a device. This is a way to prevent attackers from gaining control over your device, and prevent other devices from being compromised through the same app. Users will receive a notification if they attempt to start a restricted app.
- **Isolate devices**
  - Based on how severe the attack is, and the priority level of the device, it might be necessary to isolate the device from the rest of your network. This is a good way to stop an attacker from gaining more control and performing lateral movement attacks against the rest of your network.

## Take actions on files

You can also respond to detected threats by taking actions on files. You're able to take response actions from the file page for a file:

:::image type="content" source="../media/3-file-page-inline.png" lightbox="../media/3-file-page-expanded.png" alt-text="The file page for a file.":::

The response actions you can take on files include:

- **Stop and quarantine a file**
  - You're able to contain attacks by stopping any malicious processes associated with the file. You can also quarantine the file and data, such as registry keys, that is persistent.
- **Add an indicator to block or allow a file**
  - You can take action to prevent further proliferation of an attack across your environment by banning suspected malware or malicious files. This action will ensure a file can't be read, written to, or executed on your devices.
- **Download a file**
  - For custom analysis, you can download a password enabled Zip file that contains your file. You'll need to provide a reason for downloading the file. Also, you can't download files if they are quarantined already.

Additionally, you're able to submit any of your files for deep analysis and get the file to run on a secure cloud sandbox. You can do this from the file page under the **Deep analysis** tab.

:::image type="content" source="../media/3-submit-file-deep-analysis-inline.png" lightbox="../media/3-submit-file-deep-analysis-expanded.png" alt-text="The deep analysis tab.":::

You'll receive a breakdown report with information about how the file behaves including information such as communications to IP addresses and any registry modifications.

## Investigate using Live Response

Live Response is a way for you to use a remote shell connection to instantly access a device. Use Live Response sessions to perform deeper investigations and take immediate actions to promptly address threats. You're able to start a Live Response session from the devices page by selecting **Initiate Live Response Session**.

:::image type="content" source="../media/3-initiate-live-response-inline.png" lightbox="../media/3-initiate-live-response-expanded.png" alt-text="Initiate a Live Response session.":::

Use Live Response to expand your investigative capabilities and to run scripts, access, gather forensic data, identify suspicious entities (for example, a file), and proactively hunt and remediate emerging threats.

:::image type="content" source="../media/3-live-response-inline.png" lightbox="../media/3-live-response-expanded.png" alt-text="Live Response in action.":::

With a Live Response session, you're able to perform key tasks:

- Run basic or advanced commands to carry out investigative work on a device
- Download malware sample files, results files for PowerShell scripts, and other files. You can also download files in the background.
- Upload executables and PowerShell scripts and running them on your devices at a tenant level.
