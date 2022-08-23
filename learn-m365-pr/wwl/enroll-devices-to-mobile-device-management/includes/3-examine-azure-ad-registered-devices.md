The goal of Azure AD registered devices (also known as Workplace joined devices) is to provide an organization's users with support for Bring Your Own Device (BYOD) and mobile device scenarios. In these scenarios, a user can access an organization’s resources using a personal device.

Azure AD registered devices are signed in to using a local account, such as a Microsoft account on an Android phone. These devices have an Azure AD account for access to organizational resources. Access to resources in the organization can be limited based on that Azure AD account and Conditional Access policies applied to the device identity.

Administrators can secure and further control these Azure AD registered devices using Mobile Device Management (MDM) tools like Microsoft Intune. MDM provides a means to enforce organization-required configurations, such as:

 -  Requiring storage to be encrypted.
 -  Password complexity.
 -  Security software kept updated.

Azure AD registration can be accomplished when accessing a work application for the first time or manually using the Windows 10 or 11 Settings menu.

The following table summarizes the features associated with Azure AD registered devices.

| **Azure AD Registered** | **Description**                                                                                                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Definition              | Registered to Azure AD without requiring organizational account to sign in to the device.                                                                                                                        |
| Primary audience        | Applicable to all users with the following criteria:<br>\- Bring your own device<br>\- Mobile devices                                                                                                            |
| Device ownership        | User or Organization                                                                                                                                                                                             |
| Operating Systems       | Windows 10 or 11, iOS, Android, and macOS                                                                                                                                                                        |
| Provisioning            | - Windows 10 or 11 – Settings<br>\- iOS/Android – Company Portal or Microsoft Authenticator app<br>\- macOS – Company Portal                                                                                     |
| Device sign in options  | - End-user local credentials<br>\- Password<br>\- Windows Hello<br>\- PIN<br>\- Biometrics or pattern for other devices                                                                                          |
| Device management       | - Mobile Device Management (example: Microsoft Intune)<br>\- Mobile Application Management                                                                                                                       |
| Key capabilities        | - Single Sign On (SSO) to cloud resources<br>\- Conditional Access when enrolled into Intune<br>\- Conditional Access through App protection policy<br>\- Enables Phone sign-in with Microsoft Authenticator app |

### Scenarios

Tailspin Toys has created an MDM policy in Intune that allows its users to access the company's benefits enrollment tool. However, the policy only allows users to access the tool from Intune compliant devices. Patti Fernandez is a Sales rep for Tailspin. Patti works remotely, and she wants to access the company's benefits enrollment tool from her home PC. To do so, Patti must register her home PC with Azure AD. Once Patti's home PC is registered with Azure AD, Tailspin's required Intune policy will be enforced, and Patti will have access to the benefits enrollment tool.

Lucerne Publishing has created an Intune policy related to compliant devices. This policy blocks a rooted device from accessing organizational resources. A rooted device is any device in which users gained access to the administrative commands and functions - that is, the "root" permissions - of the device's operating system. Lucerne Publishing implemented this policy because rooted devices are more susceptible to virus infection. Allan Deyoung, the company's Sales Manager, wants to access his organizational email on his personal Android phone. However, Allan's phone has been rooted. Because of Lucerne's Intune policy, Allan is prevented from accessing organizational resources on his phone.

:::image type="content" source="../media/azure-ad-registered-device-5f476374.png" alt-text="Diagram showing how Azure A D registered devices support bring your own devices and mobile device scenarios.":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”