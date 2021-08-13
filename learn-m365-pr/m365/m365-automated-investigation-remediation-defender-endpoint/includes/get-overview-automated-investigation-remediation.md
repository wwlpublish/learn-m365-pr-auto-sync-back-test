As a security analyst on your team, you understand that threats can impact many devices simultaneously. This could result in many events to investigate and address, which can be time consuming, and could distract your team from investigating more crucial and complex threats. As a result, you need to be able to efficiently investigate threats and respond to and remediate them quickly.

In this module, you'll learn how automated investigation and remediation (AIR) can help you to better investigate and respond to threats across devices.

## What is AIR?

Microsoft Defender for Endpoint comes with built-in capabilities that you can use to automatically examine alerts and take immediate response actions to remediate potential breaches. You can use these capabilities to reduce the average volume of alerts, and focus your attention on threats that are more sophisticated. 

You can initiate automated investigations in two different ways:

- **Alert triggered**
  - For example, suppose that an alert is triggered due to a suspicious file on one of your devices. You can configure Defender for Endpoint to automatically initiate an investigation process on the device in response. If other alerts are then triggered because of this same file, they will be added to the automated investigation for you.
- **Manually initiated**
  - You can manually initiate automated investigations. For example, suppose you're reviewing a group of devices and you find out that one of your devices is at high risk of a threat. You can select the device in Defender for Endpoint and then manually initiate an automated investigation from the device's page.

Your automated investigations will automatically expand in their scope. This is helpful to you because your organization has many devices. When one of your automated investigations is running on a device because of a single alert, any other alerts generated for the device will also be included in the investigation until the investigation is finished. If the same threat is identified across multiple devices, those devices are also added to the running investigation.

## What are automated remediation actions?

With automated investigations, you can collect evidence, and generate a verdict for each piece of evidence. Your evidence will be labeled for you with one of the following verdicts:

- Malicious
- Suspicious
- No threats found

Based on the verdict, the type of threat, and how your device groups are configured, automated investigations will provide you with remediation actions that you can implement to deal with security issues. These remediation actions are wide ranging and can include:

- Isolate the device
- Run an antivirus scan
- Request a sample
- Restrict code execution
- Stop and quarantine

You can ensure that actions run automatically or only when approval has been provided, depending on your team's security needs.

## What are automation levels?

You want to know whether AIR is flexible enough to meet your team's particular needs. For example, what if your team wants to manually approve automated actions before they're carried out on some folders? You can configure AIR using three levels of automation. You can use automation levels to dictate whether the remediation actions in response to automated investigations should be carried out automatically, only after approval, or not at all.

- Full automation
- Semi-automation (which comes in different types)
- No automated response

### Full automation

When you use the full automation level, remediation actions are carried out automatically following an automated investigation. Full automation is enabled by default for you.

### Semi-automation

Semi automation comes in different types, including:

- **Require approval for any remediation**
  - You use this semi-automation type to ensure that your approval must be obtained before any remediation action is carried out after automated investigations.
- **Require approval for core folders**
  - You use this semi-automation type to specify that your approval must be obtained before any remediation actions are carried out on executables or files in any core folder on your devices. For example, core folders can include operating system folders on Windows 10 devices.
- **Require approval for non-temp folders**
  - Use this to ensure that your approval must be obtained before remediation actions can be carried out on executables and files outside of temporary folders on your devices.

### No automated response

You use this automation level to make sure that automated investigations aren't carried out on your organization's devices. But this also means that no remediation actions are done automatically. This automation level is not recommended, so you should avoid using this level.
