Windows 10 devices have mobile device management features built in to the operating system. Therefore, the preferred method for managing these devices is to enroll them as a mobile device with Intune. You must use device enrollment for devices running any operating system other than Windows, such as those running iOS, MacOS, or Android. 

You can use automatic enrollment to MDM for Windows 10 devices. Other devices, such as Android and iOS devices can only be enrolled to MDM manually by using the Company Portal app. The Company Portal app is available as a free app in the Google Play store and the Apple App Store. 

This video demonstrates how Intune is used to implement the mobile device management approach



Intune supports devices running the following operating systems through device enrollment:

- Apple iOS 9.0 and later
- Mac OS X 10.9 and later
- Android 4.4 and later, including Android for Work and Samsung Knox 
- Windows Phone 8.1, Windows RT 8.1, and Windows 8.1 (sustaining mode)
- Windows 10 and Windows 10 Mobile
- Windows 10 IoT Enterprise and Windows 10 IoT Mobile Enterprise

After you have enrolled devices, you can use Intune device profiles to manage various aspects of your devices’ configuration. The following table shows the most common device profiles for Windows 10.

|Profile|Description|
|-|-|
|Email|	Manages Exchange ActiveSync settings on devices.|
|Wi-Fi|	Allows you to manage wireless network settings for users and devices. In Windows 10, managing settings for users allows them to connect to corporate Wi-Fi without having to configure the connection manually. Instead, they can import a configuration that was previously exported from another device.|
|VPN|	Configures VPN settings for devices.|
|Education|	Configures options for the Take a Test app in Windows 10.|
|Certificates|	Allows you to configure trust and other certificates used for Wi-Fi, VPN, and email profiles.|
|Edition upgrade|	Allows you to permit users to upgrade some versions of Windows 10.|
|Endpoint protection|	Configures settings for BitLocker and Windows Defender.|
|Windows Information Protection|	Allows you to configure Windows Information Protection for data loss prevention.|