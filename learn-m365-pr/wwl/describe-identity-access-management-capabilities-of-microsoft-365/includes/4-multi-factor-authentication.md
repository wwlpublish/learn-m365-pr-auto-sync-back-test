Most security breaches are a result of attackers stealing a user’s identity. Over the years, attackers have become increasingly effective in using third-party breaches and using sophisticated phishing attacks. As soon as an attacker gains access to even low privileged user accounts, it's relatively easy for them to gain access to important company resources. Most breaches are the result of compromised passwords.

Microsoft 365 and Azure AD can improve an organization’s security posture by adopting more secure authentication methods, such as MFA or passwordless authentication measures.

## Secure authentication

Helping secure your users helps protect against breaches. And one important area is the quality of user passwords. Passwords are problematic. Users are expected to remember complex passwords for a variety of different accounts, both personal and for work. Issues with passwords include:

- Strong passwords can be difficult to remember.
- Users often reuse passwords on multiple different sites.
- Server breaches can expose symmetric network credentials (passwords).
- Passwords are subject to replay attacks.
- Users can inadvertently expose their passwords due to phishing attacks.

This poses a significant security risk as once bad actors get compromised passwords, they can sign in to multiple sites. Most breaches are a result of compromised passwords.

Watch this video for a brief introduction into the options available to bolster and improve your network security:  


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4zhD7]

Now let's explore each of these in more detail.

## Use multi-factor authentication to improve authentication security

Multi-factor authentication (MFA) is a process whereby a user is prompted during the sign-in process for an additional form of identification, such as using a code issued from their phone or providing a fingerprint scan.

If you only use a password to authenticate a user, it leaves an insecure vector for attack. If the password is weak or has been exposed elsewhere, is it really the user signing in with the username and password, or is it an attacker? When you require a second form of authentication, security is increased as this additional factor isn't something that's easy for an attacker to obtain or duplicate.

Azure Multi-Factor Authentication works by requiring two or more of the following authentication methods:

- **Something you know** – typically a password
- **Something you have** – such as a trusted device that is not easily duplicated, like a phone or hardware key
- **Something you are** - biometrics like a fingerprint or face scan

Azure Multi-Factor Authentication helps safeguard access to data and applications while maintaining simplicity for users. It provides additional security by requiring a second form of authentication and delivers strong authentication via a range of easy to use authentication methods. Users may or may not be challenged for MFA based on configuration decisions that an administrator makes.

Your applications or services don't need to make any changes to use Azure Multi-Factor Authentication. The verification prompts are part of the Azure AD sign-in event, which automatically requests and processes the MFA challenge when required.

When a user signs in to an application or service and receives an MFA prompt, they can choose from one of their registered forms of additional verification. An administrator could require registration of these Azure Multi-Factor Authentication verification methods, or the user can access their own [My Profile](https://myprofile.microsoft.com/) to edit or add verification methods.

The following additional forms of verification can be used with Azure Multi-Factor Authentication:

- Microsoft Authenticator app
- SMS
- Voice call
- OATH Hardware token

## Use passwordless authentication

Users want to be productive and sometimes feel that security measures infringe on productivity. Passwordless authentication is a form of Multi-Factor Authentication that replaces a password with a secure alternative. Using Passwordless authentication methods removes vulnerable passwords from the equation entirely so that users authenticate by using something they have (like a smartphone or badge), something they are (biometrics), or something they know (a PIN tied to a specific device).

Passwordless authentication:

- Removes the biggest vulnerability to the security perimeter: weak passwords that can be stolen.
- Uses facial recognition and biometrics authentication to help ensure the right person has the right access.
- Ties your PIN to your device so that a hacker would need to steal both.



### Implement Passwordless authentication with Azure AD

Azure AD supports Fast Identity Online 2 (FIDO2). FIDO2 is an open standard for passwordless authentication. FIDO2 allows users and organizations to leverage the standard to sign in to their resources without a username or password using an external security key or a platform key built into a device.


Users can access a device based on organization controls and authenticate based on a PIN or biometric and using devices such as USB security keys and NFC-enabled smartcards, keys, or wearables.
Passwordless authentication with Azure AD is applicable for shared PCs and where a mobile phone is not a viable option (such as for help desk personnel, public kiosk, or hospital team).

Learn more at [FIDO2 security keys](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless%23fido2-security-keys)

## Windows Hello

Windows 10 now provides a passwordless solution through the Windows Hello application. It replaces passwords with strong two-factor authentication on PCs and mobile devices. This authentication consists of a new type of user credential that is tied to a device and uses a biometric or PIN.

Windows Hello addresses the following problems with passwords:

- Strong passwords can be difficult to remember, and users often reuse passwords on multiple sites.
- Passwords are subject to replay attacks.
- Users can inadvertently expose their passwords because of phishing attacks.

Windows Hello lets users authenticate to:

- A Microsoft, Active Directory, or Microsoft Azure Active Directory (Azure AD) account.
- An Identity Provider Services or Relying Party Services that support Fast ID Online (FIDO) v2.0 authentication

After an initial two-step verification of the user during enrollment, Windows Hello is set up on the user's device. The user provides the gesture to verify their identity. Windows then uses Windows Hello to authenticate users.

### Biometric sign-in

Windows Hello provides reliable, fully integrated biometric authentication based on facial recognition or fingerprint matching. Windows Hello uses a combination of special infrared (IR) cameras and software to increase accuracy and guard against spoofing. On devices that support Windows Hello, an easy biometric gesture unlocks users' credentials.

- **Facial recognition**. This type of biometric recognition uses special cameras that see in IR light, which allows them to reliably tell the difference between a photograph or scan and a living person.
- **Fingerprint recognition**. This type of biometric recognition uses a capacitive fingerprint sensor to scan your fingerprint. Fingerprint readers have been available for Windows computers for years, but the current generation of sensors is significantly more reliable and less error-prone.

Windows stores all biometric data that is used to implement Windows Hello securely on the local device only. The biometric data doesn't roam and is never sent to external devices or servers. Because Windows Hello only stores biometric identification data on the device, there's no single collection point an attacker can compromise to steal biometric data.

Windows Hello helps protect user identities and user credentials. Because the user doesn't enter a password (except during provisioning), it helps circumvent phishing and brute force attacks.

## Microsoft Authenticator

You may already be using the Microsoft Authenticator App as a convenient multi-factor authentication option in addition to a password. You can also use the Authenticator App as a passwordless option.

:::image type="content" source="../media/4-microsoft-authenticator-concept-v2.png" alt-text="Diagram showing how the microsoft authenticator works":::

The Authenticator App turns any iOS or Android phone into a strong, passwordless credential. Users can sign in to any platform or browser by getting a notification to their phone, matching a number displayed on the screen to the one on their phone, and then using their biometric (touch or face) or PIN to confirm.

Before users can perform passwordless sign-in with Microsoft Authenticator, you should ensure that:

- Their accounts are enabled for Azure MFA
- They enroll their devices by using Microsoft Intune or a third-party endpoint management solution

> [!IMPORTANT]
> The Microsoft Authenticator app works with any account that uses two-factor verification and supports the time-based one-time password (TOTP) standards.

You can use the Microsoft Authenticator app in multiple ways, including:

- Respond to a prompt for authentication after you sign in with your username and password.
- Sign in without entering a password, using your username, the authenticator app, and your mobile device with your fingerprint, face, or PIN.
- As a code generator for any other accounts that support authenticator apps.
