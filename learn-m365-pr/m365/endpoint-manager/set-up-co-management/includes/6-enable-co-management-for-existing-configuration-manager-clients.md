## Path 1: Auto-enroll existing clients

Taking this path can get your existing Configuration Manager-managed devices quickly enrolled into Intune. The management of these devices from Configuration Manager is no different from before you enable co-management. Now you get all the cloud-based benefits. This path is transparent to your users.

Here's what you need to set it up:
- Hybrid Azure AD
    - One of the following [Azure AD hybrid identity options](/azure/active-directory/hybrid/plan-connect-user-signin.md):  
       - [Password hash synchronization](/azure/active-directory/hybrid/plan-connect-user-signin.md#password-hash-synchronization) with [Seamless Single Sign-on (SSO)](/azure/active-directory/hybrid/how-to-connect-sso.md)
       - [Pass-through authentication](/azure/active-directory/hybrid/how-to-connect-pta.md) with [Seamless Single Sign-on (SSO)](/azure/active-directory/hybrid/how-to-connect-sso.md)
       - [Federated SSO (with Active Directory Federation Services (AD FS))](/azure/active-directory/hybrid/plan-connect-user-signin.md#federation-that-uses-a-new-or-existing-farm-with-ad-fs-in-windows-server-2012-r2)
    - Azure AD Connect
    - Azure AD Premium license
    - Configure hybrid Azure AD-join (choose one option):
        - For managed domains
        - For federated domains
- Client agent setting for hybrid Azure AD-join
- Configure auto-enrollment of devices to Intune
- Enable co-management in Configuration Manager

For a tutorial on this path, see [Tutorial: Enable co-management for existing Configuration Manager clients](/mem/configmgr/comanage/tutorial-co-manage-clients.md).