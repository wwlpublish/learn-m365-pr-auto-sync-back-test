An organization must first clean up its Active Directory before synchronizing it to Microsoft 365. Typically, older AD environments have some User and Group objects that have been inactive for months and sometimes years. Before migrating its Organizational Unit (OU) to its clean cloud environment, an organization should take inventory of the objects that can help its migration.

Taking inventory of these items typically includes the following steps:

1.  Ensure that each user who will be assigned a Microsoft 365 service offering has a valid and unique email address in the **proxyAddresses** attribute.
2.  Remove any duplicate values in the **proxyAddresses** attribute.
3.  If possible, ensure that each user who will be assigned a Microsoft 365 service offering has a valid and unique value for the **userPrincipalName** (UPN) attribute in the user’s user object.
    
     -  For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN.
     -  If a user doesn't have a value for the **userPrincipalName** attribute, then the user object must contain a valid and unique value for the **sAMAccountName** attribute.
     -  Remove any duplicate values in the **userPrincipalName** attribute.

The following are optional attributes that will optimize the Global Address List (GAL):

 -  givenName
 -  surname
 -  displayName
 -  Job Title
 -  Department
 -  Office
 -  Office Phone
 -  Mobile Phone
 -  Fax Number
 -  Street Address
 -  City
 -  State or Province
 -  Zip or Postal Code
 -  Country or Region

An organization can use the ID Fix tool if it has multiple accounts in its Active Directory that have prohibited naming conventions. The ID Fix tool identifies accounts and their attributes that aren't within the Microsoft 365 standard naming conventions. It can also provide suggested names, or the organization can provide the naming format.

**Additional reading.** For more information, see [ID Fix tool](https://support.office.com/article/idfix-tool-f4bd2439-3e41-4169-99f6-3fabdfa326ac?azure-portal=true).
