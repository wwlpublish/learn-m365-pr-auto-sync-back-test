## Labels past and present

The Azure Information Protection client, released in 2016, was the first Microsoft product to introduce labeling. Labels were applied on top of the already available Azure Rights Management service with the purpose of classifying and protecting documents and emails.

Microsoft introduced Office 365 retention labels in 2017 as part of the Advanced Data Governance offering, which focused on helping organizations find and retain information important to the organization and deleting information that was not.

Based on customer feedback, the decision was made to integrate Azure Information Protection labeling capabilities more tightly into Microsoft 365 and other Microsoft services and also provide a way for other software vendors to incorporate Microsoft's information protection and governance functionality into their products. The bringing together of the complementary capabilities of Azure Information Protection and the governance capabilities of Advanced Data Governance have become Microsoft's solutions for information protection and governance.

The following changes were needed to make that decision a reality.

- **Microsoft Information Protection Software Development Kit released**. The Microsoft Information Protection SDK brings the classification, labeling, and protection capabilities of Microsoft Information Protection into a simple, lightweight, cross-platform software development kit that enables any application to label and protect information.
- **Administrative experience changes**. The Microsoft 365 Defender portal and Microsoft 365 compliance center were extended to incorporate information protection label management, a feature previously only available in Azure Information Protection.
- **Azure Information Protection labels renamed sensitivity labels**. One kind of label, retention labels, already existed as part of Advanced Data Governance. The development team concluded introducing another capability called "labels" into Microsoft 365 administrator experience could cause confusion. The decision was made to refer to what were called "labels" in Azure Information Protection labels as "sensitivity labels" going forward to differentiate them from retention labels.

These changes resulted in the creation of a new unified label management experience, client support based on the Microsoft Information Protection SDK, and the availability of sensitivity labels across Microsoft 365.

## Microsoft Information Protection value for Azure Information Protection customers

Microsoft recommends organizations plan for the transition to the new information protection solution. Here are some reasons to consider migrating to Microsoft Information Protection:

- **Built-in Office client**. Windows users running Microsoft 365 Apps for enterprise (formerly known as Office 365 ProPlus) version 1910 or higher on Windows may not need to install an Office Add-in. Unified labeling support is built into the client.
- **Unified experience**. The same sensitivity labels can be used across Microsoft 365 applications and services. Sensitivity label capabilities can also be extended into other applications from Microsoft and third parties. Examples include the sensitivity label integration added to Microsoft Power BI and the work Adobe has done to support the framework in PDF documents.
- **Innovation**. All future innovation and development will use the Microsoft Information Protection framework.

## Learn more

- [Microsoft Information Protection (MIP) SDK setup and configuration](/information-protection/develop/setup-configure-mip?azure-portal=true)
- [PDF readers that support Microsoft Information Protection](/azure/information-protection/rms-client/protected-pdf-readers?azure-portal=true)
