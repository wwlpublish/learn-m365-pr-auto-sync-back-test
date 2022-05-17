Organizations should consider the following performance issues when determining which migration method to use.

:::row:::
  :::column:::
    **Migration method**
  :::column-end:::
  :::column:::
    **Microsoft 365 user throttling**
  :::column-end:::
  :::column:::
    **Microsoft 365 migration-service throttling**
  :::column-end:::
  :::column:::
    **Microsoft 365 resource health-based throttling**
  :::column-end:::
  :::column:::
    **Observed average throughput per hour and per client (if applicable)**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    IMAP migration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    10-14 GB (20 concurrency)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cutover migration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    10-14 GB (20 concurrency)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Staged migration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    10-14 GB (20 concurrency)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hybrid migration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    10-14 GB per on-premises Exchange 2013 or 2010 CAS (Microsoft Exchange Mailbox Replication service) with 20 concurrent moves; **see footnote 1.**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Third-party MAPI migration
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    4-12 GB (20 concurrency); **see footnote 2.**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Third-party Exchange Web Services migration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    5-10 GB (20 concurrency); **see footnote 3.**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Client uploading (from Outlook .pst files)
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    0.5 GB
  :::column-end:::
:::row-end:::


#### Footnotes

1.  Observed single mailbox move throughput is in the 0.3–1.0 GB/hour range. Greater than 1000 MB/h per mailbox throughput rate can be achieved. However, the network must sustain less than a 2 percent transient failure stall time and less than 100-ms network latency. More concurrent mailbox migrations can be used to achieve higher data migration rates. Single mailbox move throughput will slow down when any of the following conditions occur:
    
     -  The on-premises Client Access server is at hardware capacity.
     -  The network bandwidth isn’t sufficient.
     -  The network latency is too high.
    
    Consider adding more servers or temporarily improving network connectivity to increase migration velocity
2.  Observed single MAPI migration throughput is in the 0.1-0.5 GB/hour range. More concurrent migrations can be used to achieve higher data-migration rates. Single MAPI migration throughput will slow down when either the on-premises servers or the network is at capacity.
3.  Observed single Exchange Web Services migration throughput is in the 0.2–0.5 GB/hour range. More concurrent migrations can be used to achieve higher data migration rates. For example, with 20 concurrent migrations, the overall throughput will be in the 4-10 GB/hour range. Single Exchange Web Services migration throughput will slow down when either the on-premises servers or the network is at capacity.
