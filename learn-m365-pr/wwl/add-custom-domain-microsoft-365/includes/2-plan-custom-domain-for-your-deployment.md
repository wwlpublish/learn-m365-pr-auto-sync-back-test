There are several factors an organization must consider when planning to add custom domains to Microsoft 365. These factors can differ with the Microsoft 365 subscription it selects. The following table sets out the planning factors that must be taken into consideration.

:::row:::
  :::column:::
    **Factor**
  :::column-end:::
  :::column:::
    **Considerations**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Multiple domains
  :::column-end:::
  :::column:::
    An organization should plan to add the main domain that it currently uses along with any other domain that it uses for email messages within the organization. This scenario is common when the overall company is a business group, or the organization has been through a merger process and some employees still have alternative email addresses.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Subdomains
  :::column-end:::
  :::column:::
    An organization may want to register subdomains. Microsoft 365 Business Premium and Enterprise plans enable subdomains to be added under the root domain. For example, within the account for Adatum Corporation, the **sales.adatum.com** subdomain can be registered under the **adatum.com** root domain.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Domain numbers
  :::column-end:::
  :::column:::
    An organization can register up to 900 domains with Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Domain adding order
  :::column-end:::
  :::column:::
    Root domains must be added before subdomains. So in the previous example, the **adatum.com** root domain must be registered before the **sales.adatum.com** subdomain is added.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DNS record hosting
  :::column-end:::
  :::column:::
    DNS records may be hosted by an organization’s DNS servers or by an external hosting provider.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Access to the DNS console
  :::column-end:::
  :::column:::
    An organization should check with its DNS hosting provider about the level of access that it has to the DNS console. To configure its Microsoft 365 services, an organization must have access to add the **A**, **CNAME**, **TXT**, **MX**, and **SRV** records. If the DNS hosting provider doesn't provide that level of access, the organization may have to send a request to the DNS hosting provider to change DNS records needed for its Microsoft 365 deployment.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Not registering DNS
  :::column-end:::
  :::column:::
    It's rare that an organization wouldn't want to register a DNS domain with Microsoft 365, but it's a possible option—for example, if the organization wants to have a separate email and directory service for its Microsoft 365 users. One possible scenario is a university that may want to host its faculty members in the on-premises environment and have the students in Microsoft 365 with a different domain name.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Not changing all records
  :::column-end:::
  :::column:::
    An organization may not want to change all the DNS records to point to Microsoft 365. An upcoming unit in this module identifies how to handle the verification process when you don't change all the DNS records.
  :::column-end:::
:::row-end:::
