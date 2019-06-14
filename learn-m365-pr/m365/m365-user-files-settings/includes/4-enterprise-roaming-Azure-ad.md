With Windows 10, Azure AD users can securely synchronize their user and application settings data to the cloud. Enterprise state roaming provides a unified experience across Windows devices and reduces the time needed to configure a new device.

Enterprise state roaming incorporates:

- **Separation of corporate and consumer data.** Organizations are in control of their data, and there is no mixing of corporate data in a consumer cloud account or consumer data in an enterprise cloud account.
- **Enhanced security.** Data is automatically encrypted before leaving the user’s Windows 10 device by using Azure Rights Management (Azure RMS), and data stays encrypted at rest in the cloud. 
- **Better management and monitoring.** Provides control and visibility over who syncs settings in your organization and on which devices through the Azure AD portal integration.

Enterprise state roaming data is hosted in one or more Azure regions that best align with the country/region value set in the Azure Active Directory instance. The data is partitioned based on three major geographic regions: North America, EMEA, and APAC. Data for the tenant is locally located with the geographical region and is not replicated across regions.

To enable Azure enterprise state roaming, you’ll need to be in one of the [Azure regions that supports it]( https://azure.microsoft.com/global-infrastructure/regions/#services), and you’ll need a [Premium Azure subscription]( https://azure.microsoft.com/services/active-directory/).
