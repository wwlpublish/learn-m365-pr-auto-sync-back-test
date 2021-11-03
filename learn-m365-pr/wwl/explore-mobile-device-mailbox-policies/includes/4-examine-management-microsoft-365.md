Exchange ActiveSync provides basic functionality to secure mobile devices that contain your company messaging data. However, it's not as powerful as some full-featured mobile device management solutions.

For example, ActiveSync can't protect your users from accessing documents or downloading and storing company data on potentially unsafe locations. Microsoft provides a solution for those scenarios called Mobile Device Management (MDM) for Microsoft 365. When configured, MDM replaces Active Sync.

Mobile Device Management for Microsoft 365 is included with many of the Microsoft 365 commercial subscriptions.

> [!NOTE]
> Policies and access rules created in MDM for Microsoft 365 override both Exchange ActiveSync mobile device mailbox policies and device access rules created in the Exchange Admin Center. After a device is enrolled in MDM for Microsoft 365, any Exchange ActiveSync mobile device mailbox policy or device access rule applied to the device will be ignored.

When planning your Mobile Device Management strategy, you may choose between built-in Microsoft 365 mobile device management capabilities or using another product, such as the more powerful Microsoft Intune or other third-party products, depending on your organization’s requirements.

### Considerations for deploying MDM for Microsoft 365

Administrators should consider the following items when deploying MDM for Microsoft 365:

 -  When you create a new policy, you may want to set the policy to allow access and report a policy violation when a user's device isn't compliant with the policy. This design displays how many mobile devices would be impacted by the policy without blocking access to Microsoft 365.
 -  Before you deploy a new policy to everyone in your organization, it's recommended that you first test it on the devices used by a few users.
 -  Before you deploy policies, let your organization know the potential impacts of enrolling a device in MDM for Microsoft 365. Depending on how you set up the policies, devices that don't follow these policies (non-compliant devices) could be blocked from accessing Microsoft 365. Non-compliant devices can also have apps installed, photos, and other personal information. On an enrolled device, these objects could be deleted if the device is wiped.

### How to configure Mobile Device Management for Microsoft 365

To configure MDM for Microsoft 365, you should complete the following steps:

1.  **Configure domains for MDM**. First, you must add two publicly accessible DNS CNAME records in your custom public DNS zone that point to Mobile Device Management for Microsoft 365. These records, which are used by clients to access and enroll in MDM, are called **EnterpriseEnrollment** and **EnterpriseRegistration**. The following table displays the DNS records needed for MDM in Microsoft 365.<br>
    
    :::row:::
      :::column:::
        **Host name**
      :::column-end:::
      :::column:::
        **Record type**
      :::column-end:::
      :::column:::
        **Address**
      :::column-end:::
      :::column:::
        **TTL**
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        EnterpriseEnrollment
      :::column-end:::
      :::column:::
        CNAME
      :::column-end:::
      :::column:::
        EnterpriseEnrollment.manage.microsoft.com
      :::column-end:::
      :::column:::
        3600
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        EnterpriseRegistration
      :::column-end:::
      :::column:::
        CNAME
      :::column-end:::
      :::column:::
        EnterpriseRegistration.windows.net
      :::column-end:::
      :::column:::
        3600
      :::column-end:::
    :::row-end:::
    

2.  **Configure an APNS Certificate for iOS devices**. iOS devices such as iPads and iPhones can be managed in Mobile Device Management for Microsoft 365. To do so, you must complete the following steps to create an APNS certificate or token in the Azure portal:<br>
    
    1.  In the Azure portal, on the **Notification Hub** page, select **Apple (APNS)** on the left menu.
    2.  For **Authentication Mode**, select either **Certificate** or **Token**.
    3.  If you select **Certificate**:
    4.  Select the file icon, and then select the .p12 file you want to upload.
    5.  Enter a password.
    6.  Select **Sandbox** mode. Or, to send push notifications to users who purchased your app from the store, select **Production** mode.
    7.  If you select **Token**:
    8.  Enter the values for **Key ID**, **Bundle ID**, **Team ID**, and **Token**.
    9.  Select **Sandbox** mode. Or, to send push notifications to users who purchased your app from the store, select **Production** mode.

3.  **Set up multifactor authentication (MFA)**. Configuring MDM for Microsoft 365 doesn't require MFA. However, it’s recommended that you implement MFA because it provides an extra layer of security. MFA asks users for a second form of authentication, such as a phone call, text message, or app notification on their mobile device after they correctly enter their work account and password.
4.  **Manage device security policies**. Device security policies should be created and deployed according to your organization's security business requirements. To do so, you must complete the following steps:
    
    1.  In the Microsoft 365 admin center, navigate to the **EndPoint Manager admin center** and then select **Devices** in the left-hand navigation pane.
    2.  On the **Devices \| Overview** page, under the **Policy** section in the middle pane, select **Compliance policies**.
    3.  Select **Create Policy** and then select the platform the policy will apply to.
    4.  Select **Create**.
    5.  Enter a name and optionally a description for the policy.
    6.  Configure the policy settings, which are divided into functional areas such as **Device health, Device properties, Configuration Manager Compliance,** and **System Security.**
    7.  Select the action you want run on noncompliant devices.
    8.  Select who to assign the policy to (**Selected groups** or **All users**).
    9.  Review and create the policy.

In Microsoft 365, you can also subscribe to Intune. Microsoft Intune is a more advanced Mobile Device Management and Mobile Application Management (MAM) solution. Intune is covered in another module in this learning path.

**Additional reading**. For more information, see [Choose between MDM for Office 365 and Microsoft Intune](/microsoft-365/admin/basic-mobility-security/choose-between-basic-mobility-and-security-and-intune?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.