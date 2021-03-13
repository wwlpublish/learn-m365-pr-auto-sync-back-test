Before you begin synchronizing your Active Directory, you first must clean it up. Typically, older AD environments have some User and Group objects that have been inactive for months and sometimes years. Before you decide to migrate your Organizational Unit (OU) to your clean cloud environment, you should take inventory of the objects that can help facilitate your migration.

Taking inventory of these items typically includes the following steps:

1.  Ensure that each user who will be assigned Microsoft 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.
2.  Remove any duplicate values in the **proxyAddresses** attribute.
3.  If possible, ensure that each user who will be assigned Microsoft 365 service offerings has a valid and unique value for the **userPrincipalName** (UPN) attribute in the user’s user object.
    
     *  For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN.
     *  If a user does not have a value for the **userPrincipalName** attribute, then the user object must contain a valid and unique value for the **sAMAccountName** attribute.
     *  Remove any duplicate values in the **userPrincipalName** attribute.

The following are optional attributes that will optimize the Global Address List (GAL):

 *  givenName
 *  surname
 *  displayName
 *  Job Title
 *  Department
 *  Office
 *  Office Phone
 *  Mobile Phone
 *  Fax Number
 *  Street Address
 *  City
 *  State or Province
 *  Zip or Postal Code
 *  Country or Region

If you have trouble with your AD environment and you have multiple accounts with prohibited naming conventions, you can use the ID Fix tool to identify accounts and their attributes that are not within the Microsoft 365 standard naming conventions and will either give you a suggestion or you can provide the naming format.

**Additional reading.** For more information, see the following site on the [ID Fix tool](https://support.office.com/article/idfix-tool-f4bd2439-3e41-4169-99f6-3fabdfa326ac?azure-portal=true).
