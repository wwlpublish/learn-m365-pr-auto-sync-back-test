To help its customers focus on breach prevention and spend less on breach recovery, Microsoft has created the Microsoft Intelligent Security Graph, or Microsoft Graph for short. The Intelligent Security Graph uses advanced analytics to link a massive amount of threat intelligence and security data from Microsoft and partners to combat cyber threats. Insights from the Intelligent Security Graph power real-time threat protection in Microsoft products and services. Every second, hundreds of GB's worth of data is added to the Security Graph. This anonymized data comes from:

 -  over a hundred Microsoft data centers across the globe.
 -  threats faced by over 1 billion PCs that are updated by Windows Update each month.
 -  external data points that are collected through extensive research and partnership with industry and law enforcement. This research is accomplished through Microsoft’s Digital Crime Unit and Cybersecurity Defense Operations Center.

Threat intelligence in Microsoft 365 is powered by the Microsoft Intelligent Security Graph, which:

 -  Consumes 6.5 trillion signals daily across the Microsoft 365 network. A signal is a term meaning information traffic.
 -  Uses advanced analytics consisting of artificial intelligence and machine learning capabilities.
 -  Integrates this data across Microsoft's threat detection and response capabilities to address different attack scenarios.

The signals are obtained from the Intelligent Security Graph, plus other third-party feeds, including teams of experts hunting for malicious activities around the globe. Machine learning models and artificial intelligence analyze vast security signals to identify vulnerabilities and threats. The massive scope of signals enables Microsoft to understand the full context of an event to power quick threat detection and automated response.

These signals are fed into Microsoft’s three major platforms: Windows, Azure, and Microsoft 365. Microsoft then integrates these signals so that security services in one platform can communicate with security services in one of the other platforms.

As a result, any threat seen in Windows is automatically and quickly added to the set of threats that Microsoft 365 views. This design provides deep insight into the evolving cyber threat landscape.

:::image type="content" source="../media/microsoft-intelligent-security-graph-0ed4d5c7.png" alt-text="Diagram showing statistics involving the Microsoft Intelligent Security Graph.":::


### Microsoft Graph Security API

Microsoft Graph also supports the Microsoft Graph Security API. The Graph Security API provides a unified gateway to share and act on security insights across the Microsoft platform and partner solutions. This design enables organizations to integrate their security solutions to improve security operations and efficiency. Developers can use the Security Graph to build intelligent security services that:

 -  Integrate and correlate security alerts from multiple sources.
 -  Unlock contextual data to inform investigations.
 -  Automate SecOps for greater efficiency.

The Microsoft Graph Security API is a unified API that provides a standard interface and uniform schema. It integrates security alerts and threat intelligence from multiple sources, enriches alerts and data with contextual information, and automates security operations.

The security API is part of the Microsoft Graph. It's a unified REST API for integrating data and intelligence from Microsoft and partner products and services. Using Microsoft Graph, customers and partners can rapidly build solutions that authenticate once and use a single API call to access or act on security insights from multiple security solutions. More value is uncovered when you explore the other [Microsoft Graph entities](/graph/overview?azure-portal=true) (Microsoft 365, Azure Active Directory, Intune, and more) to tie business context with your security insights.

Microsoft enables technology partner integration in two key ways.

1.  As a consumer of information from Microsoft Graph, you can enrich your solutions with information contained in Microsoft Graph. You can also use the Microsoft Graph API to perform tasks on behalf of a customer.
2.  You can also contribute your alerts and actions to Microsoft Graph alongside Microsoft providers.

:::row:::
  :::column:::
    **How do you integrate?**
  :::column-end:::
  :::column:::
    **Data available**
  :::column-end:::
  :::column:::
    **Capabilities supported**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Integrate your application with the Microsoft Graph Security API.
  :::column-end:::
  :::column:::
    

Alerts from Microsoft Graph Security Providers

Secure Scores from Microsoft


  :::column-end:::
  :::column:::
    

Query alerts/Secure Score

Call a Microsoft Graph Security Action

Update a Microsoft Graph Security alert

Upload Customer threat indicators to Microsoft


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Enable others to integrate with your products through the Microsoft Graph Security API.
  :::column-end:::
  :::column:::
    

Alerts from your security products


  :::column-end:::
  :::column:::
    

Security Actions for your security product


  :::column-end:::
:::row-end:::


**Additional reading**. For more information, see [Partnering with the Microsoft Graph Security API – technology partner opportunities](/graph/security-partner-overview?azure-portal=true).
