It would be easier for Christina, and safer for her company, if she didn’t have to remember a password at all. Her company recently implemented passwordless authentication. To access her devices, she can authenticate by using either facial recognition or biometrics on her mobile phone or Windows 10 laptop.

## What is passwordless authentication

Users want to be productive and sometimes feel that security measures infringe on productivity. Passwordless authentication methods remove vulnerable passwords from the equation entirely so that users are authenticated by combining something you have (like a smartphone or badge), something you are (biometrics), or something you know (a PIN tied to a specific device).

Passwordless authentication:

- Removes the biggest vulnerability to the security perimeter: weak passwords that can be stolen
- Uses facial recognition and biometrics authentication to help ensure the right person has the right access
- Ties your PIN to your device so that a hacker would need to steal both

## Passwordless authentication with Azure AD

Azure AD supports FIDO2, a new open standard for secure authentication that locks the credentials to a device. FIDO2 enables you to manage passwordless authentication for your users and groups to all your Azure AD-connected apps and services.

![Password Risk Data](../media/icon20.png)

That means you can keep identities safe no matter where you are physically. FIDO2 security keys offer flexibility for workers who rotate between computers/devices.

FIDO2 offers users these advantages:

- Password-free access to as many apps and devices as possible.  
- Strong two-factor authentication on Windows 10 devices with Windows Hello.
 
![Password Risk Data](../media/icon21.jpg)

In the above example, Christina would leverage Windows Hello directly on her laptop to sign in to the corporate network. She’d enter her PIN or look directly into the camera to verify identity. Windows Hello verifies her identity and generates the required security keys to grant the right access to the right materials.

## Microsoft Authenticator

The Microsoft Authenticator app is another passwordless solution. It uses technology similar to Windows Hello and is packaged into a simple app on an Android or iOS mobile device. It enables smartphone or tablet users to verify their identity and authenticate to their Azure AD account. Users confirm their identity through PIN, fingerprint scan, or facial or iris recognition.

![Password Risk Data](../media/icon22.png)

This works great for people who travel like Christina. She can switch between multiple devices and be authenticated from her phone through a PIN or biometric data.

Before users can perform passwordless sign in with Microsoft Authenticator, you should ensure that:

- Their accounts are enabled for Azure MFA
- They enroll their devices by using Microsoft Intune or a third-party endpoint management solution

Learn More
- [Windows Hello for Business Overview](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-overview)
- [Microsoft Authenticator App Overview](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-overview)
- [Passwordless sign-in with Microsoft Authenticator](https://docs.microsoft.com/azure/security/fundamentals/ad-passwordless#passwordless-sign-in-with-microsoft-authenticator)