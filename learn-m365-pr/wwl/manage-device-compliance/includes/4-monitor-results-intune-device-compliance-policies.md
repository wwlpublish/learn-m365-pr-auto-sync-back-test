Compliance reports help an organization understand when devices fail to meet its compliance configurations. They can also help identify compliance-related issues. Organizations can use these reports to view information on:

 -  The overall compliance states of devices.
 -  The compliance status for an individual setting.
 -  The compliance status for an individual policy.
 -  Drill down into individual devices to view specific settings and policies that affect the device.

### Use the Intune Device compliance dashboard

Organizations can use the Intune Device compliance dashboard to monitor the results of its device compliance policies. Complete the following steps to open the Intune Device compliance dashboard:

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane.
3.  On the **Devices \| Overview** page, select the **Compliance status** tab.

> [!IMPORTANT]
> Devices must be enrolled into Intune to receive device compliance policies.

The dashboard opens displays an overview with all the compliance reports. These reports enable organizations to check for:

 -  Overall device compliance
 -  Per-policy device compliance
 -  Per-setting device compliance
 -  Threat agent status
 -  Device protection status

As an organization investigates this reporting, it can also see any specific compliance policies and settings that apply to a specific device, including the compliance state for each setting.

### Device compliance status chart

The Device compliance status chart shows the compliance states for all Intune enrolled devices. The device compliance states are kept in two different databases: Intune and Azure Active Directory.

> [!IMPORTANT]
> Intune follows the device check-in schedule for all compliance evaluations on the device. For more information, see [Learn more about the device check-in schedule](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned?azure-portal=true).

The device compliance policy states include:

 -  **Compliant**. The device successfully applied one or more device compliance policy settings.
 -  **In-grace period**. The device is targeted with one or more device compliance policy settings. But, the user hasn't applied the policies yet. This status means the device is not-compliant, but it's in the grace period defined by the admin. For more information, see [Actions for noncompliant devices](/mem/intune/protect/actions-for-noncompliance?azure-portal=true).
 -  **Not evaluated**. An initial state for newly enrolled devices. Other possible reasons for this state include:
     -  Devices that aren't assigned a compliance policy and don't have a trigger to check for compliance.
     -  Devices that haven't checked in since the compliance policy was last updated.
     -  Devices not associated to a specific user, such as:
         -  iOS/iPadOS devices purchased through Apple's Device Enrollment Program (DEP) that don't have user affinity.
         -  Android kiosk or Android Enterprise dedicated devices.
     -  Devices enrolled with a device enrollment manager (DEM) account.
 -  **Not-compliant**. The device failed to apply one or more device compliance policy settings. Or, the user hasn't complied with the policies.
 -  **Device not synced**. The device failed to report its device compliance policy status for one of the following reasons:
     -  **Unknown**. The device is offline or failed to communicate with Intune or Azure AD for other reasons.
     -  **Error**. The device failed to communicate with Intune and Azure AD, and received an error message with the reason.

> [!NOTE]
> Devices that are enrolled into Intune, but not targeted by any device compliance policies, are included in this report under the **Compliant** bucket.

#### Device behavior with a compliance setting in Error state

When a setting for a compliance policy returns a value of **Error**, the compliance state of the device remains unchanged for up to seven days. This grace period allows time for the compliance calculation to complete correctly for that setting.

 -  Within those seven days, the device's existing compliance status continues to apply until the compliance policy setting evaluates as **Compliant** or **Not compliant**.
 -  If a setting still has a status of **Error** after seven days, the device immediately becomes **Not compliant**. Grace periods don't apply to compliance policies with a setting in an **Error** state.

Consider the following examples of this scenario:

 -  A device is initially marked **Compliant**. Later, a setting in one of the compliance policies targeted to the device reports **Error**. After three days, compliance evaluation completes successfully and the setting now reports **Not compliant**. The user can continue to use the device to access Conditional Access-protected resources within the first three days after the setting states changes to **Error**. However, once the setting returns **Not compliant**, the device is marked **Not compliant** and this access is removed until the device becomes **Compliant** again.
 -  A device is initially marked **Compliant**. Later, a setting in one of the compliance policies targeted to the device reports **Error**. After three days, compliance evaluation completes successfully, the setting returns **Compliant**, and the device's compliance status becomes **Compliant**. The user is able to continue to access Conditional Access protected resources without interruption.
 -  A device is initially marked **Compliant**. Later, a setting in one of the compliance policies targeted to the device reports **Error**. The user is able to access Conditional Access protected resources for seven days. However, after seven days, the compliance setting still returns **Error**. At this point, the device immediately becomes **Not compliant**. The user also loses access to the protected resources until the device becomes **Compliant**. This result occurs even if there's a grace period set for the applicable compliance policy.
 -  A device is initially marked **Not compliant**. Later, a setting in one of the compliance policies targeted to the device reports **Error**. After three days, compliance evaluation completes successfully, the setting returns **Compliant**, and the device's compliance status becomes **Compliant**. The user is prevented from accessing Conditional Access protected resources for the first three days (while the setting returns **Error**). Once the setting returns **Compliant** and the device is marked **Compliant**, the user can begin to access protected resources on the device.

#### Drill down for more details

In the Device compliance status chart, select a status. For example, select the **Not complian**t status:

:::image type="content" source="../media/select-not-compliant-status-ec208278.png" alt-text="Screenshot of the Device compliance status chart with the Not compliant status highlighted.":::


That action opens the **Device compliance** window and displays devices in a **Device status** chart. The chart displays more details on the devices in that state, including operating system platform, last check-in date, and more.

:::image type="content" source="../media/drill-down-details-13f48d32.png" alt-text="Screenshot of the Device compliance window showing all devices with a Not compliant state.":::


If you want to see all the devices owned by a specific user, you can also filter the chart report by typing the user's e-mail.

> [!TIP]
> If no user is signed in to the device, the device with the targeted device compliance policy will send a compliance report back to Intune showing **System Account** as the user principal name. This situation occurs when a device compliance policy was targeted to either a group of users or devices, and no user was signed into the device at the time the compliance policy was evaluated.

The compliance report may show the same device multiple times if the following conditions occur:

 -  There are multiple users signed into the same device.
 -  The device is targeted with a compliance policy that's scoped to cover all users that are currently signed in the device.

In this situation, the same device is shown multiple times because every user signed into the device has to evaluate the device compliance policy and report it back to Intune.

When assigning a compliance policy to a device group and a user is signed in, it will cause two compliance evaluations:

 -  One for the user.
 -  One for the System account.

In this scenario, the System Account evaluation could fail, causing the device to be "Not compliant". To prevent this behavior, you should complete either of the following actions depending on the user's sign-in status:

 -  For devices with a user signed in, assign the compliance policy to a User group.
 -  For devices without a user signed in, assign the compliance policy to a Device group.

#### Filter and columns

:::image type="content" source="../media/filter-columns-578ae70c.png" alt-text="Screenshot of the menu bar on the Device compliance window showing the Filter option.":::


When you select the **Filter** button, the filter fly-out opens with more options, including the **Compliance state**, **Jailbroken devices**, and more. Apply the filter to update the results.

Use the **Columns** property to add or remove columns from the chart output. For example, **User principal name** may display the email address registered on the device. **Apply** the columns to update the results.

### Device details chart

In the **Device details** chart, select a specific device, and then select **Device compliance**:

:::image type="content" source="../media/see-policies-applied-specific-device-0bac732d.png" alt-text="Screenshot of the Device compliance window showing the details for a selected device.":::


Intune displays more details on the device compliance policy settings applied on that device. When you select the specific policy, it shows all the settings in the policy.

### Devices without compliance

On the **Compliance status** page, next to the **Policy compliance** chart, select the **Devices without compliance policy** tile to view information about devices that don't have any compliance policies assigned:

:::image type="content" source="../media/devices-without-policies-f5f9de71.png" alt-text="Screenshot of the Devices without compliance window showing the devices without an assigned compliance policy.":::


When you select the tile, it displays all devices without a compliance policy. It also shows the user of the device, the policy deployment status, and the device model.

Organizations should be aware of the following issues when viewing this tile:

 -  With the **Mark devices with no compliance** policy assigned as the security setting, it's important to identify devices without a compliance policy. Then you can assign at least one compliance policy to them. The security setting is configurable in the Microsoft Endpoint Manager admin center. Navigate to **Devices** &gt; **Compliance policies** &gt; **Compliance policy settings**. Then, set **Mark devices with no compliance policy assigned as** to either **Compliant** or **Not compliant**.
 -  Users who are assigned a compliance policy of any type aren't shown in the report, regardless of device platform. For example, if you've assigned a Windows compliance policy to a user with an Android device, the device doesn't show up in the report. However, Intune considers that Android device non-compliant. To avoid issues, it's recommended that you create policies for each device platform and deploy them to all users.

### Per-policy device compliance chart

The **Policy compliance** chart displays the policies, and how many devices are compliant and noncompliant.

:::image type="content" source="../media/policy-compliance-chart-1eb651c5.png" alt-text="Screenshot of the Policy compliance chart showing how many devices are compliant and noncompliant.":::


### Setting compliance chart

The **Setting compliance** chart displays all device compliance policy settings from all compliance policies, the platforms the policy settings are applied to, and the number of noncompliant devices.

:::image type="content" source="../media/setting-compliance-chart-c8a2619e.png" alt-text="Screenshot of the Setting compliance chart showing the total of all device compliance policy settings from all devices.":::


### View compliance reports

In addition to using the charts on the **Compliance status** page, you can also navigate to **Reports** &gt; **Device compliance**.

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane.
3.  On the **Devices \| Overview** page, select **Monitor** in the middle navigation pane.
4.  On the **Monitor \| Assignment status** page, under the **Compliance** section in the middle navigation pane, select the report you want to view. Some of the available compliance reports include:
     -  Noncompliant devices
     -  Devices without compliance policy
     -  Setting compliance
     -  Policy compliance
     -  Noncompliant policies (preview)
     -  Windows health attestation report

**Additional reading**. For more information about reports, see [Intune reports](/mem/intune/fundamentals/reports?azure-portal=true).

### View the status of device policies

An organization can check the different states of it policies, by platform. For example, let's assume Contoso has a macOS compliance policy. Contoso wants to see the devices that are impacted by this policy. It also wants to see if there are conflicts or failures.

This feature is included in the device status reporting:

1.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane.
2.  On the **Devices \| Overview** page, select **Compliance policies** under the **Policy** section in the middle navigation pane.
3.  On the **Compliance policies \| Policies** page, a list of policies is shown, including the platform, if the policy is assigned, and more.
4.  Select a policy.
5.  On the **Overview** page, the policy assignment includes the following statuses:
     -  **Succeeded**. Policy is applied.
     -  **Error**. The policy failed to apply. The message typically displays along with an error code that links to an explanation.
     -  **Conflict**. Two settings are applied to the same device, and Intune can't sort out the conflict. An administrator should review.
     -  **Pending**. The device hasn't checked in with Intune to receive the policy yet.
     -  **Not applicable**. The device can't receive the policy. For example, the policy updates a setting specific to iOS 11.1, but the device is using iOS 10.
6.  To see details on the devices using this policy, select one of the statuses. For example, select **Succeeded**. In the next window, specific device details are displayed, including the device name and deployment status.

### How Intune resolves policy conflicts

Policy conflicts can occur when multiple Intune policies are applied to a device. If the policy settings overlap, Intune resolves any conflicts by using the following rules:

 -  If the conflict is between settings from an Intune configuration policy and a compliance policy, the settings in the compliance policy take precedence over the settings in the Intune configuration policy. This result happens even if the settings in the Intune configuration policy are more secure.
 -  If an organization deployed multiple compliance policies, Intune uses the most secure of these policies.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”