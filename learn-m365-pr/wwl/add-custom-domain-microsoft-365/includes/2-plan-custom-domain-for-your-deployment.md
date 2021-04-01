There are several factors you need to consider when planning to add custom domains to Microsoft 365. These factors can differ with the Microsoft 365 subscription you select. The following table sets out the planning factors that must be taken into consideration.

:::row:::
  :::column:::
    Factor
  :::column-end:::
  :::column:::
    Considerations
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Multiple domains
  :::column-end:::
  :::column:::
    Plan to add the main domain that your company currently uses along with any other domain that it uses for email messages within the organization. This scenario is common when the overall company is a business group, or the organization has been through a merger process and some employees still have alternative email addresses.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Subdomains
  :::column-end:::
  :::column:::
    You might want to register subdomains; for example, registering content.adatum.com within the account for Adatum Corporation. Microsoft 365 Business Premium and Enterprise plans enable you to add subdomains under your root domain.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Domain numbers
  :::column-end:::
  :::column:::
    You can register up to 900 domains with Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Domain adding order
  :::column-end:::
  :::column:::
    Root domains must be added before subdomains. So in the previous example, Adatum.com must be registered before you add content.Adatum.com.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DNS record hosting
  :::column-end:::
  :::column:::
    DNS records might be hosted by your organization’s DNS servers or by an external hosting provider.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Access to the DNS console
  :::column-end:::
  :::column:::
    Check with your DNS hosting provider about the level of access that you have to the DNS console. To configure Microsoft 365 services, you must be able to add the **A**, **CNAME**, **TXT**, **MX**, and **SRV** records. If your DNS hosting organization does not provide that level of access, you might have to send a request to the DNS hosting provider to change DNS records needed for your Microsoft 365 deployment.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Not registering DNS
  :::column-end:::
  :::column:::
    It's rare that you would not want to register a DNS domain with Microsoft 365, but it is a possible option—for example, if you want to have a separate email and directory service for your Microsoft 365 users. One possible scenario is a university that may want to host its faculty members in the on-premises environment and have the students in Microsoft 365 with a different domain name.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Not changing all records
  :::column-end:::
  :::column:::
    You may not want to change all the DNS records to point to Microsoft 365. An upcoming unit in this module identifies how to handle the verification process when you do not change all DNS records.
  :::column-end:::
:::row-end:::
