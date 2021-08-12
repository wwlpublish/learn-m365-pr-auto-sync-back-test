In this module, we'll explain Office activation and packaging options, Office servicing for software update management, and how to inform software update approaches based on how devices are used.

## Office activation and packaging options

Office is available as part of Microsoft 365 or, in volume licensing editions, with Office 2019 Professional Plus and Office 2019 Standard. The Microsoft 365 versions are assigned to users, and activation is subscription-based. Office 2019 versions are activated based on device and use Key Management Service infrastructure (KMS) through your servers or Multiple Activation Key (MAK) through the Internet.

Microsoft 365 Apps and Office 2019 versions both use the same application packaging, called **Click-to-Run**, and share the same installation approach. You can also use Group Policy with Microsoft 365 Apps and Office 2019 volume licensing editions.

A common misperception is that all Click-to-Run packages use subscription activation, but that's not true. Office 2019 apps are only available as Click-to-Run packages and use the same volume activation methods, KMS and MAK, that they've used since Office 2007. Microsoft 365 versions of Office use Microsoft 365 user-based subscription activation.

## Office servicing

With the introduction of Microsoft 365 versions of Office, you no longer have to wait years for new features and capabilities. While Office versions like 2016 and 2019 have static feature sets over their support life cycles, Microsoft 365 apps are continuously improved through monthly and semi-annual updates.
One major difference between Microsoft 365 Apps and Office 2019 versions is that Microsoft 365 Apps versions get monthly feature updates by default in addition to security and reliability fixes. Microsoft 365 Apps has four update channels:

- **Monthly channel** – providing the newest features of Office as soon as they're available.
- **Semi-annual channel** – delivering new features in Office a few times a year.
- **Semi-annual channel (targeted)** – intended for pilot users and compatibility testers to validate the next Semi-Annual Channel before its release.
- **Monthly channel (targeted)** – closest to the Office Insiders release, providing advance releases of monthly channel builds for testing and validation

Both the Office 2019 releases and Semi-Annual Channel releases receive security and reliability fixes between new releases. For Office 2019 versions, the feature set is static (unchanging) for the duration of the product support lifecycle.

## Discover how Office is used to inform servicing decisions

Your next step is to determine how Office is used on different PCs and to inventory COM add-ins and VBA macro-enabled files in use in your environment. By determining usage, you can define software update approaches to help save time with software update management, allowing some of your systems to automatically update from the Internet. This is especially useful for systems with Microsoft 365 Apps, where Feature Updates include security and bug fixes and are released monthly.

Typically, Office usage falls into two categories:

### General purpose

- Minimal customizations, COM add-ins, or VBA macros in use.
- Typically represents the majority of users. General purpose devices should use monthly channel updates whenever possible delivered directly from the Internet by the Content Delivery Network (CDN).

### Business essential

- More COM add-ins installed – often for Excel power users. If issues occur in response to an update, users may lose essential functionality.
- Business essential devices should use semi-annual channel updates to keep features more consistent over time.

You can use Microsoft Endpoint Configuration Manager (1902 and newer) to take an inventory of COM add-ins and the devices where they're installed. Configuration Manager discovers Office add-ins using a hardware inventory and reports Office client information. Another option is to use the Readiness Toolkit for Office to inventory COM add-ins. You can define systems with minimal customizations and COM add-ins as general purpose, and then set policies to update those systems automatically.
