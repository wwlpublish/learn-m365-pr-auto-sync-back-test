Windows Information Protection (WIP) lets you protect your organization from accidental or malicious data leaks without requiring significant changes to your enterprise environment or apps or interrupting employee’s workflows. It provides this protection to both enterprise-owned devices and BYOD devices. 

WIP helps you to overcome several common challenges by providing:

- Separation between personal and corporate data. Users do not need to choose which app to use for which data.
- Additional protection to LOB apps. You can add protection without modifying the app.
- Ability to perform a selective wipe. You can remove corporate data from a device without removing personal data.
- Audit reporting. WIP gives you the ability to track and report on policy issues and the actions performed in response to policy violations.
- Management system integration. WIP integrates with Intune, System Center Configuration Manager (SCCM), and other MDM systems.

These benefits can help you to protect enterprise data in a variety of scenarios:

- Encrypt data on a device. When copying or downloading organizational data from SharePoint, OneDrive for Business, network shares, or other locations using a device that is managed by using WIP policies, WIP encrypts the data on the device even if the device is personally owned.
- Control which apps can access corporate data. Apps that you have included on the Allowed Apps list can access organizational data while apps that are not on the list have more limited capabilities. For example, if the policy is set to Override mode, when a user tries to copy data from an allowed app to a personal app a warning notice will ask for confirmation to perform a potentially unsafe action.
- Support apps that allow users to work with both personal and corporate data. Some apps, such as Word, automatically detect when a file contains corporate data and should be WIP-protected. They maintain that protection when saving a file locally or on removable media. This protection is maintained even if the file name changes or if the data is stored with unencrypted personal data.
- Prevent use of personal apps and services. You can prevent accidental release of organizational data to public spaces and social media by preventing users from using applications such as a personal OneDrive to store files. You can also prevent users from copying data from allowed apps to social media such as Twitter or Facebook.
- Remove corporate data from lost or stolen devices, or devices owned by ex-employees. You can remove organizational data from, and unenroll any devices (including personal devices) that are enrolled in Intune even if the device is lost or stolen. This does not affect personal data.