Endpoint Analytics can provide insights to help organizations monitor transitions to cloud management solutions. Endpoint Analytics reviews configurations and provides guidance for IT to enabling employees to work from anywhere, as well as assists in planning for Windows 11 migrations.

### Work from anywhere report

This report offers insights into how prepared your workforce is to be productive from anywhere. From this report, you can review your scores and how they compare to the selected baseline. Learn how to improve your scores by reviewing the insights and recommendations for each of them.

#### Work from anywhere score

This score represents a weighted average of the percent of devices that have deployed the various insights for helping your end users be productive from anywhere. The score is computed for all Intune and Configuration Manager devices that have opted into Endpoint analytics.

The following metrics are weighted and used to compute the **Work from anywhere score**:

 -  Windows
 -  Cloud management
 -  Cloud identity
 -  Cloud provisioning

#### Windows

Newer versions of Windows provide a better user experience than older versions of Windows. The Windows metric measures the percent of devices on supported versions of Windows. The recommended remediation actions vary depending on how the devices are managed.

#### Windows 11 hardware readiness

The Windows metric provides Windows 11 hardware readiness insights for devices that are enrolled via Intune, co-management, or Configuration Manager version 2107 or newer with tenant attach enabled.

To determine how many of your enrolled devices meet the minimum system requirements for Windows 11, select **Windows** to open the flyout on the **Overview** page in **Work from anywhere**. A chart is displayed showing which specific hardware requirements are the top blockers in your organization.

:::image type="content" source="../media/windows-hardware-766b20f8.png" alt-text="Screenshot of the Windows flyout that displays a chart showing top hardware blockers in your organization." lightbox="../media/windows-hardware-766b20f8.png":::


In the **Windows** tab, a device-by-device view of Windows 11 hardware readiness is displayed. This includes whether the device is already upgraded or not, if the device is capable of upgrading, and which specific hardware requirements that aren't met for devices that have a readiness status of *Not capable*. Devices may show with a Windows 11 readiness status of *Unknown*, which are likely inactive. To verify this, review the device's last check-in time.

Windows 11 hardware readiness insights do not affect your Work from anywhere score.

#### Cloud management

The Cloud management metric measures the percent of PCs that have attached to the Microsoft 365 cloud to unlock additional capabilities. These capabilities are often dependent on how the devices are managed. This view provides guidance and recommendations for achieving several productivity benefits.

#### Cloud identity

Cloud identity provides users with many productivity benefits including device-wide single sign-on to apps and services, Windows Hello sign-in, self-service BitLocker recovery, and corporate data roaming. The Cloud identity metric measures the percent of devices enrolled in Azure Active Directory (AD) or hybrid Azure AD.

:::image type="content" source="../media/8668496-cloud-identity-f4c76cc4.png" alt-text="Screenshot of the Cloud identity fly out showing insights for the metric." lightbox="../media/8668496-cloud-identity-f4c76cc4.png":::


#### Cloud provisioning

Cloud provisioning provides a simpler initial provisioning experience for Windows PCs than the native experience. It reduces the number of screens in the Out Of Box Experience (OOBE) and provides defaults, to ensure the device is correctly provisioning from the factory or on reset. The Cloud provisioning metric measures the percentage of machines that are either Windows 365 Cloud PCs or Windows Intune devices that are both registered and have a deployment profile created for Autopilot. This view can be especially helpful when transitioning to modern management, and identifying devices that are still provisioned through traditional management methods.

:::image type="content" source="../media/8668496-cloud-provisioning-b2989f35.png" alt-text="Screenshot of the cloud provisioning tab showing the device list." lightbox="../media/8668496-cloud-provisioning-b2989f35.png":::
