An important benefit of using a Mobile Device Management (MDM) solution for managing devices is that organizations can restrict access to e-mail and documents only from devices that are managed by MDM and follow company policy.

This unit examines how MDM policies control security in a real-world scenario.

### Example

Holly Dickson, Contoso's Enterprise Administrator, created a company policy that includes the following rules:

 -  User passwords must be complex.
 -  Local data on devices must be encrypted.
 -  The latest updates must be installed on devices.

A group of users at Contoso can each access their Exchange Online mailbox from their primary devices. All of the primary devices meet company policy.

Each user also has a secondary device. The secondary devices haven't been updated in some time. As such, they don't have the latest updates installed. So how did this scenario affect Contoso's users?

 -  Before Holly created the company policy, the users could access their Exchange Online mailboxes from their secondary devices.
 -  Once Holly's company policy went into effect, none of the users could read their e-mails from their secondary devices.

If all other prerequisites are met, the users can access their mailboxes from their secondary devices AFTER they install the latest updates. At that point, the secondary devices will be compliant with company policy.

### Using MDM policies in Microsoft 365

Organizations can define company policy by using Device Security policy in Microsoft 365. They can control access to e-mail, documents, and other cloud apps by using Conditional Access policies. Compliance with company policy is just one criterion that can be evaluated in a Conditional Access policy. Organizations can also evaluate sign in risk, device type, location, and client apps.

Devices that aren't enrolled to MDM can't have their compliance evaluated. However, organizations can still prevent access to mailboxes, documents, and cloud apps from such devices. If a user tries to access their mailbox from such a device, depending on how the policy is set up, the user may experience one of the following outcomes:

 -  They're blocked from accessing Microsoft 365 resources.
 -  They're redirected to enroll the device to MDM.
 -  The user could have access, but Microsoft 365 would report a policy violation.

:::image type="content" source="../media/benefits-of-using-mdm-f8697a73.jpg" alt-text="Diagram showing the benefits of using mobile device management to manage devices.":::


**Additional reading.** For more information, see [Access control for Office 365 email and documents](https://support.office.com/article/capabilities-of-built-in-mobile-device-management-for-office-365-a1da44e5-7475-4992-be91-9ccec25905b0#bkmk_accesscontrol?azure-portal=true).
