Christina travels from the home office in Seattle to the Tokyo office for the first time. Identity Protection could have triggered a risk detection requiring multi-factor authentication (MFA). Christina needs to use MFA to register the new device. If the IT department can’t validate the device and suspect something is wrong, they can force all the devices registered under Christina to reset their MFAs.

## Require MFA

Microsoft 365 uses MFA to help provide an extra layer of security and is managed from the admin center. Microsoft 365 Apps offers the following subset of MFA authentication capabilities:

- Use mobile apps (online and one-time password) as a second authentication factor
- Use a phone call as a second authentication factor

Here are some recommended methods to enforce MFA:

- Require users to authenticate their smartphone, laptop, or other device with MFA before they register it with Intune to access your network.
- Monitor the health of your user accounts with Azure AD, and when needed, require users to reset their password, re-register for MFA, or revoke existing MFA sessions from their user object.

## Planning a cloud-based Azure MFA deployment

A Conditional Access policy can require MFA when criteria such as these are met:

- All users, a specific user, member of a group, or assigned role
- Specific cloud application being accessed
- State of device
- Network location or geo-located IP address
- Device health
- Client applications

## Learn More
- [Conditional Access policy](https://docs.microsoft.com/azure/active-directory/conditional-access/overview?azure-portal=true)
- [Configure Azure Multi-Factor Authentication settings](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings#activity-report?azure-portal=true)
- [Require multi-factor authentication at device enrollment](https://docs.microsoft.com/intune/multi-factor-authentication?azure-portal=true)
- [Configure Conditional Access policy to require MFA](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#plan-conditional-access-policies?azure-portal=true)
- [Manage user settings](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-userdevicesettings?azure-portal=true)
