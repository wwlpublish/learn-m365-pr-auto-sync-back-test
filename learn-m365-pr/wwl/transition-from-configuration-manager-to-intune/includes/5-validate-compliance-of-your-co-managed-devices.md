Most companies typically define a required configuration for their devices. For IT departments, it's important to quickly view whether devices are compliant and configured in an expected way. To achieve this goal, either Configuration Manager or Microsoft Intune can be used.

To check whether devices are compliant, you must first define compliance policies. Compliance policies are a set of device settings and configurations that devices must meet to be considered compliant. Examples of these settings include operating system version, password complexity, and disk encryption.

You can configure compliance policies in Configuration Manager and Microsoft Intune. With co-management enabled, you can control from where and to which devices the compliance policies will be applied.

After you create a compliance policy, you must assign it to one or more groups. Devices in a group can compare their configuration with the compliance policy that's assigned to the group and report back their compliance status. You can view information about:

 -  the overall compliance state of devices.
 -  the compliance state for an individual setting.
 -  the compliance state for an individual policy.

You can then drill down into an individual device to view the settings and policies for that particular device.

For devices that apply compliance policies from Configuration Manager, you can view compliance results in the Configuration Manager console or by using reports. For devices that apply compliance policies from Intune, you can view their compliance status in the Intune section on the Azure portal.

### Device compliance dashboard

In the Device compliance dashboard, you can monitor the compliance of different devices, their protection status, and more. You can also view the following reports:

 -  Overall device compliance aggregate
 -  Per-policy device compliance
 -  Per-setting device compliance
 -  Device protection status
 -  Threat agent status

You can also view the specific compliance policies and settings that apply to an individual device, and the final compliance state for each of those settings on the device.

### Overall device compliance aggregate report

This report displays the aggregate compliance state for all co-managed devices for which Intune is managing compliance policy. Device compliance state can have one of the following values:

 -  **Compliant.** The device successfully applied one or more device compliance policies and it meets all the policy settings.
 -  **Not-compliant.** The device failed to apply one or more device compliance policy settings, or it doesn't meet policy settings.
 -  **In grace period.** The device was targeted with one or more device compliance policies, but policies haven't been applied yet. This setting means the device is not-compliant, but it’s in the grace-period.
 -  **Not evaluated.** The device failed to report its device compliance policy status for one of the following reasons:
    
     -  **Unknown.** The device is offline or failed to communicate with Intune or Azure AD for other reasons.
     -  **Error.** The device failed to communicate with Intune and Azure AD, and it received an error message with the reason.

:::image type="content" source="../media/device-compliance-chart-91711f77.jpg" alt-text="device compliance circle chart showing the number of devices that are compliant, not compliant, in a grace period, and not evaluated.":::


### Notifying users about non-compliant devices

Actions can be configured and applied to devices that don’t meet the device compliance policy. By default, when a device doesn't meet the device compliance policy, Intune immediately marks it as non-compliant. You can use the **Actions for noncompliance** setting of the compliance policy to configure what to do when a device is non-compliant. You can configure two actions:

 -  **Send email to end user.** You can customize an email notification that can be sent to the user of a non-compliant device. Intune provides customization of the subject, message body, company logo, company name, and contact information.
 -  **Mark device noncompliant.** You can define a schedule to determine how many days after non-compliance the device should be marked as non-compliant.

**Additional reading.** For more information, see the following articles on monitoring compliance status within [Configuration Manager](/sccm/compliance/deploy-use/monitor-compliance-settings) and [Microsoft Intune](/intune/compliance-policy-monitor).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”