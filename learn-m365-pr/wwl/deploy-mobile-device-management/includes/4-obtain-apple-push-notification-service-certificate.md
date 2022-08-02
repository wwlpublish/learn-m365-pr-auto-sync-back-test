Organizations don't need to add certificates to MDM to manage Windows or Android devices with either Intune or Basic Mobility and Security. However, if they want to manage any Apple-related products such iPad, iPhone, and Mac devices by using MDM, they need an Apple Push Notification Service (APNS) certificate to communicate securely with those devices.

Apple requires that every MDM use its own certificate when communicating on Apple’s Push Notification Messaging network. Without the APNS certificate, iOS devices can't be enrolled or managed. After an organization adds the certificate to Intune or Microsoft 365, its users can enroll their iOS and macOS devices by using:

 -  the Company Portal app
 -  Apple's bulk enrollment methods, such as the Device Enrollment Program, Apple School Manager, or Apple Configurator

By default, the APNS certificate is valid for one year. An organization must renew its APNS certificate before it expires. When an organization renews the certificate, it must use the same Apple ID that it used when it first created the APNS certificate. If an organization's APNS certificate expires, enrollment of new iOS devices will fail, and enrolled iOS devices can't be managed until the certificate is renewed.

:::image type="content" source="../media/apple-push-notification-certificate-0343b206.jpg" alt-text="screenshot of MDM push certificate":::


An organization can obtain an APNS certificate and add it to Microsoft Endpoint Manager by completing following steps:

1.  Grant Microsoft permission to send user and device information to Apple.
2.  Download the **Intune certificate signing request** required to create an Apple MDM push certificate.
3.  Create an Apple MDM push certificate.
4.  Enter the Apple ID used to create your Apple MDM push certificate.
5.  Browse to your Apple MDM push certificate to upload.

:::image type="content" source="../media/configure-mdm-push-certificate-window-e49b0a10.jpg" alt-text="screenshot of Install Apple Push Notification Certificate page":::


**Additional reading.** For more information, see the following resources:

 -  [Get an Apple MDM push certificate](/intune/apple-mdm-push-certificate-get?azure-portal=true).
 -  [Setting up Mobile Device Management for Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”