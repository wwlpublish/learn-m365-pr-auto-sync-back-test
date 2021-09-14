After a device is enrolled to Intune, a built-in device MDM agent automatically begins to sync the device details to Intune. Device details include information such as:

 -  Name of the device
 -  Operating system
 -  Total and free storage space
 -  Enrolled date
 -  Encrypted
 -  Compliance

Organizations can view device information in the Microsoft Endpoint Manager admin center or when generating reports. They can also use synchronized device attributes when specifying membership rules for dynamic groups. Groups can be used in Intune for deploying profiles, policies, and apps.

**Additional reading.** For more information, see [Device data that is available in Intune](/intune/device-inventory?azure-portal=true).

### Group membership

In the Microsoft Endpoint Manager admin center, organizations can create user and device groups with static and dynamic membership. These user groups and device groups are used by Intune, which doesn't have its own groups.

A group can be created with dynamic membership by specifying a rule that determines membership. The rule can be based on user or device properties. When the attributes of a user or device changes, Microsoft 365 evaluates all dynamic groups in a directory to see if the change would trigger any group membership changes. If a user or device satisfies a rule on a group, they're added as a member of that group. If they're a group member but no longer satisfy the rule, they're removed from the group.

A group membership rule automatically populates a group with users or devices. This rule is a binary expression that results in a True or False outcome. The three parts of a simple group membership rule include:

 -  Specifies the object attribute. For example, **user.department** can be used to reference the **Department** attribute of a user object, or **device.displayName** to reference the **displayName** attribute of a device object.
 -  Can be one of many supported operators, such as Equals (-eq), Starts With (-startsWith), Contains (-contains), or Match (-match).
 -  The value against which you want to evaluate the property by using the operator.

For example, the following group membership rule includes all devices that were manufactured by Microsoft:

`device.deviceManufacturer -eq "Microsoft"`

The following table identifies the attributes that can be used when creating a dynamic device group.

:::row:::
  :::column:::
    

**Device attribute**


  :::column-end:::
  :::column:::
    

**Values**


  :::column-end:::
  :::column:::
    

**Example**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

accountEnabled


  :::column-end:::
  :::column:::
    

true false


  :::column-end:::
  :::column:::
    

(device.accountEnabled -eq true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

displayName


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.displayName -eq "Rob IPhone”)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceOSType


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.deviceOSType -eq "iPad") -or (device.deviceOSType -eq "iPhone")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceOSVersion


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.OSVersion -eq "9.1")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceCategory


  :::column-end:::
  :::column:::
    

a valid device category name


  :::column-end:::
  :::column:::
    

(device.deviceCategory -eq "BYOD")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceManufacturer


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.deviceManufacturer -eq "Samsung")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceModel


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.deviceModel -eq "iPad Air")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceOwnership


  :::column-end:::
  :::column:::
    

Personal, Company, Unknown


  :::column-end:::
  :::column:::
    

(device.deviceOwnership -eq "Company")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

domainName


  :::column-end:::
  :::column:::
    

any string value


  :::column-end:::
  :::column:::
    

(device.domainName -eq "contoso.com")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

enrollmentProfileName


  :::column-end:::
  :::column:::
    

Apple Device Enrollment Profile or Windows Autopilot profile name


  :::column-end:::
  :::column:::
    

(device.enrollmentProfileName -eq "DEP iPhones")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

isRooted


  :::column-end:::
  :::column:::
    

true false


  :::column-end:::
  :::column:::
    

(device.isRooted -eq true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

managementType


  :::column-end:::
  :::column:::
    

MDM (for mobile devices) PC (for computers managed by the Intune PC agent)


  :::column-end:::
  :::column:::
    

(device.managementType -eq "MDM")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

organizationalUnit


  :::column-end:::
  :::column:::
    

any string value matching the name of the organizational unit set by an on-premises Active Directory


  :::column-end:::
  :::column:::
    

(device.organizationalUnit -eq "US PCs")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

deviceId


  :::column-end:::
  :::column:::
    

a valid Azure AD device ID


  :::column-end:::
  :::column:::
    

(device.deviceId -eq "d4fe7726-5966-431c-b3b8-cddc8fdb717d")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

objectId


  :::column-end:::
  :::column:::
    

a valid Azure AD object ID


  :::column-end:::
  :::column:::
    

(device.objectId -eq 76ad43c9-32c5-45e8-a272-7b58b58f596d")


  :::column-end:::
:::row-end:::


## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Create device categories](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E5-T1/index.html?azure-portal=true).

This simulation guides you through the steps to create device categories for the fictitious company known as Adatum Corporation. Adatum wants to implement device categories that will enable it to automatically add devices to groups based on defined categories.
