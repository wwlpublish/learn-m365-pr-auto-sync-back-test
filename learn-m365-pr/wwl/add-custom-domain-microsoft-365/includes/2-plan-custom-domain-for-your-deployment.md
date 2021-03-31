There are several factors you need to consider when planning to add custom domains to Microsoft 365. These factors can differ with the Microsoft 365 subscription you select. The following table sets out the planning factors that must be taken into consideration.

:::row:::
  :::column:::
    <p><b>Factor</b></p>
  :::column-end:::
  :::column:::
    <p><b>Considerations</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Multiple domains</p>
  :::column-end:::
  :::column:::
    <p>Plan to add the main domain that your company currently uses along with any other domain that it uses for email messages within the organization. This scenario is common when the overall company is a business group, or the organization has been through a merger process and some employees still have alternative email addresses.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Subdomains</p>
  :::column-end:::
  :::column:::
    <p>You might want to register subdomains; for example, registering content.adatum.com within the account for Adatum Corporation. Microsoft 365 Business Premium and Enterprise plans enable you to add subdomains under your root domain.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Domain numbers</p>
  :::column-end:::
  :::column:::
    <p>You can register up to 900 domains with Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Domain adding order</p>
  :::column-end:::
  :::column:::
    <p>Root domains must be added before subdomains. So in the previous example, Adatum.com must be registered before you add content.Adatum.com.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>DNS record hosting</p>
  :::column-end:::
  :::column:::
    <p>DNS records might be hosted by your organization’s DNS servers or by an external hosting provider.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Access to the DNS console</p>
  :::column-end:::
  :::column:::
    <p>Check with your DNS hosting provider about the level of access that you have to the DNS console. To configure Microsoft 365 services, you must be able to add the <b>A</b>, <b>CNAME</b>, <b>TXT</b>, <b>MX, </b>and <b>SRV</b> records. If your DNS hosting organization does not provide that level of access, you might have to send a request to the DNS hosting provider to change DNS records needed for your Microsoft 365 deployment.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Not registering DNS</p>
  :::column-end:::
  :::column:::
    <p>It's rare that you would not want to register a DNS domain with Microsoft 365, but it is a possible option—for example, if you want to have a separate email and directory service for your Microsoft 365 users. One possible scenario is a university that may want to host its faculty members in the on-premises environment and have the students in Microsoft 365 with a different domain name.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Not changing all records</p>
  :::column-end:::
  :::column:::
    <p>You may not want to change all the DNS records to point to Microsoft 365. An upcoming unit in this module identifies how to handle the verification process when you do not change all DNS records.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>DNS record propagation timings</p>
  :::column-end:::
  :::column:::
    <p>DNS records can take up to 72 hours to propagate. Reducing the Time to Live (TTL) value can speed up this process, but you still need to plan for the replication time.</p>
  :::column-end:::
:::row-end:::
