The purpose of multifactor authentication (MFA) is to increase security. Traditional authentication requires knowledge of sign-in credentials, typically consisting of a user name and the associated password. MFA adds an extra verification that relies either on having access to a device that is presumably in the possession of the rightful owner or having the correct fingerprint, retinal structure, or other configured biometric marker. This extra requirement makes it considerably more difficult for an unauthorized individual to compromise the authentication process.

### Azure Active Directory multifactor authentication

‎Multifactor authentication is integrated into Azure Active Directory. It enables the use of a phone as the physical device that can provide the means of confirming the user’s identity. The process of implementing MFA for an Azure AD user account starts when a user with the global administrator role enables the account for multifactor authentication from the Azure portal. At their next sign-in attempt, the user is prompted to set up the authentication by selecting one of the following options:

 -  **Office phone.** Requires the specification of the Office Phone entry of the user’s contact info in Azure AD. The administrator must preconfigure this entry, and the user can't modify or provide this entry at the verification time.
 -  **Mobile app.** Requires the user to have a smart phone on which they must install and configure the mobile phone app.
 -  **Mobile phone.** Requires the user to provide a mobile phone number. The verification can be in the form of a phone call (at the end of which, the user must press the pound key), or a text message.
