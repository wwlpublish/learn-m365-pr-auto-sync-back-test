Windows Hello is a more personal way to sign in to your Windows devices. Windows Hello introduces system support for a personal identification number (PIN) and biometric authentication. With just a look, a touch, or a unique PIN, users get enterprise-grade security without having to type in a password.

### Using Windows Hello instead of passwords

Windows Hello addresses the following problems with passwords:

 -  Strong passwords can be difficult to remember, and users often reuse passwords on multiple sites.
 -  Server breaches can expose symmetric network credentials (passwords).
 -  Passwords are subject to [replay attacks](https://go.microsoft.com/fwlink/p/?LinkId=615673).
 -  Users can inadvertently expose their passwords due to [phishing attacks](/windows/security/threat-protection/intelligence/phishing).

#### Windows Hello with PIN

Windows Hello enables users to sign in to their device using a PIN. At first, a PIN can appear similar to a password. It could be simple set of numbers, or something more complex that includes letters and special characters. However, unlike a password, the PIN is tied to the device where it was set up. If a user's password is stolen, that password could potentially be used on another device. If the PIN is stolen, the PIN is useless without the device where it was created.

#### Windows Hello using Biometrics

Windows Hello introduces system support for biometric authentication – using your face, iris, or fingerprint to unlock your devices. You– uniquely you– plus your device are the keys to your Windows experience, apps, data, and even websites and services. Modern sensors recognize your unique personal characteristics to sign you in on a supporting Windows device. A PIN is also created when setting up biometrics, and can be used in the event biometric authentication doesn't work properly (such as a sensor failure).

### Using Windows Hello

In order to use Windows Hello, you must have a PIN for your sign in already setup. On your PC select theStart button, then select **Settings** &gt; **Accounts** &gt; **Sign in options** to set up Windows Hello. Under Windows Hello, you’ll see options for face, fingerprint, or iris if your PC has a fingerprint reader or a camera that supports it. Once you’re set up, you'll be able to sign in with a quick scan on your fingerprint reader or glance at your camera.

> [!NOTE]
> Windows Hello features will only appear if your computer includes hardware to support it.

:::image type="content" source="../media/windows-hello-camera-only-78f11e17.jpg" alt-text="Screenshot of Windows Hello.":::


### Windows Hello for Business

Windows Hello for Business replaces passwords with strong two-factor authentication on PCs and mobile devices. This authentication consists of a new type of user credential that is tied to a device and uses a biometric or PIN.

Unlike Windows Hello, Windows Hello for Business Windows Hello for Business is configured by Group Policy or mobile device management (MDM) policy and uses key-based or certificate-based authentication. As an administrator in an enterprise or educational organization, you can create policies to manage Windows Hello for Business use on Windows 10 or Windows 11 devices that connect to your organization.

Windows Hello for Business lets users authenticate to:

 -  A Microsoft account
 -  An Active Directory account
 -  A Microsoft Azure Active Directory (Azure AD) account
 -  Identity Provider Services or Relying Party Services that support Fast ID Online (FIDO) v2.0 authentication (in progress)

After an initial two-step verification of the user during enrollment, Windows Hello is set up on the user's device and Windows asks the user to set a gesture, which can be a biometric, such as a fingerprint, or a PIN. The user provides the gesture to verify their identity. Windows then uses Windows Hello to authenticate users.

> [!NOTE]
> When Windows 10 first shipped, it included Microsoft Passport and Windows Hello, which worked together to provide multi-factor authentication. Windows Hello for Business combines these technologies.
