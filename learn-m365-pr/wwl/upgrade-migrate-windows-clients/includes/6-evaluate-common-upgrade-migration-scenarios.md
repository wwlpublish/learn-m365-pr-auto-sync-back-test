Because in-place upgrades are the preferred upgrade method, you should select the migration scenario only when an in-place upgrade would not work. You need to look for any deciding factor that would cause you to choose one over the other. Read the scenarios and choose between:

 -  In-place upgrade
 -  In-place upgrade using feature update
 -  Side-by-side migration
 -  In-place migration

### Scenario 1

Contoso Pharmaceuticals owns 100 workstations on which Windows 8.1 was manually installed. They want to upgrade these workstations to Windows 10, and switch to a more standardized and managed deployment. What is the best upgrade method for Contoso?

### Scenario 2

Litware, Inc. is in the process of upgrading all devices from Windows 10 to Windows 11. There are some devices that will not upgrade because TPM 2.0 was not detected. They intend to replace any devices that require hardware upgrades. Which upgrade methods should be performed?

### Scenario 3

A.Datum Corporation has 5000 client computers running Windows 8.1 in a managed environment. All computers have the same set of applications installed. They want to upgrade to Windows 10. What is the best upgrade method for A.Datum?

### Scenario 4

Contoso Pharmaceuticals is upgrading from Windows 8.1 to Windows 10. Some devices are running the 32-bit edition of Windows 8.1, however all the devices meet the minimum 64-bit specifications for Windows 10. Which upgrade methods should be performed?

#### Answers

 -  *Scenario 1: In-place migration is best. As the devices are Windows 8.1, an in-place migration that images the devices with Windows 10 will ensure a standard configuration going forward.*
 -  *Scenario 2: In-place upgrade using feature updates can be used for devices that meet Windows 11 hardware requirements. Devices reporting no TPM 2.0 should be verified that that TPM is not disabled. Side-by-side migration should be used for devices that need to be replaced.*
 -  *Scenario 3: In-place upgrade is best as the devices have an acceptable configuration and do not need to be reimaged.*
 -  *Scenario 4: In-place upgrade for devices running 64-bit editions of Windows 8.1. As 32-bit editions cannot be upgraded to 64-bit, a migration must be performed. Since the hardware is 64-bit capable, an in-place migration can be performed.*
