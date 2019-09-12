Christina travels from the home office in Seattle to the Tokyo office for the first time. Identity Protection could have triggered a risk detection requiring  MFA. Christina needs to use MFA to register the new device. If the IT department can’t validate the device and suspect something is wrong, they can force all of all devices registered under Christina to reset their MFAs. 

## Require  MFA
Microsoft 365 uses MFA to help provide an extra layer of security and is managed from the admin center. Office 365 offers the following subset of MFA authentication capabilities:
- Use mobile apps (online and one-time password) as a second authentication factor
- Use a phone call as a second authentication factor

Here are some recommended methods to enforce MFA:
- Require users to authenticate their smart phone, laptop, or other device with MFA before they register it with Intune to access your network.
- Monitor the health of your user accounts with Azure AD, and when needed, require users to reset their password, re-register for MFA, or revoke existing MFA sessions from their user object.

## Learn More
- (Conditional Access policy)[https://docs.microsoft.com/azure/active-directory/conditional-access/overview]
- (Require multi-factor authentication at device enrollment)[https://docs.microsoft.com/intune/multi-factor-authentication]
- (Configure Conditional Access policy to require MFA)[https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#plan-conditional-access-policies]
- (Manage user settings)[https://docs.microsoft.comazure/active-directory/authentication/howto-mfa-userdevicesettings]

## Planning a cloud-based Azure MFA deployment

A Conditional Access policy can require MFA when criteria such as these are met:
- Is it a specific grouping of users, such as: 
   - all users 
   - a specific user
   - all users assigned to a specific role
- Is a specific cloud application being accessed?
- Is a device compliant and healthy?
- Is the device outside of expected network location or geo-located IP address?

## Learn More
- (Conditional Access policy)[https://docs.microsoft.com/azure/active-directory/conditional-access/overview]