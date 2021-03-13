Organizations should consider the following network issues when migrating mail to Microsoft 365.

:::row:::
  :::column:::
    <p><b>Factor</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
  :::column:::
    <p><b>Best practices</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Network capacity</p>
  :::column-end:::
  :::column:::
    <p>The amount of time it takes to migrate mailboxes to Microsoft 365 is determined by the available and maximum capacity of your network.</p>
  :::column-end:::
  :::column:::
    Identify your available network capacity and determine the maximum upload capacity.  Contact your ISP to confirm your allocated bandwidth and to get details about restrictions, such as the total amount of data that can be transferred in a specific period of time.  Use tools to evaluate your actual network capacity. Make sure you test the end-to-end flow of data from your on-premises data source to the Microsoft datacenter gateway servers.  Identify other loads on your network (for example, backup utilities and scheduled maintenance) that can affect your network capacity.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Network stability</p>
  :::column-end:::
  :::column:::
    <p>A fast network doesn’t always result in fast migrations. If the network isn’t stable, data transfer takes longer because of error correction. Depending on the migration type, error correction can significantly affect migration performance.</p>
  :::column-end:::
  :::column:::
    <p>Network hardware and driver issues often cause network stability problems. Work with your hardware vendors to understand your network devices and apply the vendor’s latest recommended drivers and software updates.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Network delays</p>
  :::column-end:::
  :::column:::
    <p>Intrusion detection functionality configured on a network firewall often causes significant network delays and affects migration performance.<br></p>  <p>Migrating data to Microsoft 365 mailboxes relies on your Internet connection. Internet delays effect overall migration performance.<br></p>  <p>Also, users in the same company might have cloud mailboxes that reside in datacenters in different geographical locations. Depending on the customer's ISP, migration performance may vary.</p>
  :::column-end:::
  :::column:::
    Evaluate network delays to all potential Microsoft datacenters to help ensure the result is consistent and the experience for end users is consistent. Work with your ISP to address Internet-related issues.  Add IP addresses for Microsoft datacenter servers to your allow list, or bypass all migration-related traffic from your network firewall. For more information about the Microsoft 365 IP ranges, see [Office 365 URLs and IP address ranges](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_home?azure-portal=true).
  :::column-end:::
:::row-end:::
