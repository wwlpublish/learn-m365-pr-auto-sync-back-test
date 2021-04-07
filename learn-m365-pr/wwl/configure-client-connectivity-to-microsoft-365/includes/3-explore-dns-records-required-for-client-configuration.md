Outlook and other Office-related clients can use the Autodiscover process to automatically locate services in Microsoft 365. Using Autodiscover in this manner requires that you first configure the appropriate DNS records on the publicly available DNS servers on the Internet.

 *  In organizations where the internal DNS namespace, such as Adatum.local, is different from the Internet DNS namespace, such as Adatum.com, the internal DNS servers forward internal client queries to Internet DNS servers.
 *  In organizations that use split-brain DNS, where internal and Internet DNS namespaces are the same, such as Adatum.com, you should configure both the internal and Internet DNS servers to resolve the Autodiscover records in Microsoft 365.

The following table identifies the Autodiscover records that Outlook clients need to connect to Exchange Online in Microsoft 365.

:::row:::
  :::column:::
    <p><b>DNS record</b></p>
  :::column-end:::
  :::column:::
    <p><b>Purpose</b></p>
  :::column-end:::
  :::column:::
    <p><b>Value to use</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b><br></p>  <p><b>(Exchange Online)</b></p>
  :::column-end:::
  :::column:::
    <p>The Autodiscover service configures Outlook for users.</p>
  :::column-end:::
  :::column:::
    <p><b>Alias:</b> Autodiscover<br></p>  <p><b>Target: </b>autodiscover.outlook.com</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b><br></p>  <p><b>(Exchange federation)</b></p>
  :::column-end:::
  :::column:::
    <p>The Autodiscover service configures Outlook for users in Exchange federation scenarios. This record is optional, and it's needed when you deploy Exchange in a hybrid configuration with Microsoft 365.</p>
  :::column-end:::
  :::column:::
    <p><b>Alias:</b> For example, Autodiscover.service.adatum.com<br></p>  <p><b>Target:</b> autodiscover.outlook.com</p>
  :::column-end:::
:::row-end:::


The following graphic shows that the domain suffix of a user's email address is resolved against DNS and redirected to Exchange Online, which then delivers the correct Autodiscover.xml file back to the Outlook client, which contains all configuration information.

:::image type="content" source="../media/domain-suffix-resolved-to-dns-877a81c1.jpg" alt-text="graphic shows that the domain suffix of a user's email address is resolved against DNS and redirected to Exchange Online, which then delivers the correct Autodiscover.xml file back to the Outlook client":::


The following table identifies the DNS records that are needed for VOIP Services to connect to Skype for Business Online in Microsoft 365.

:::row:::
  :::column:::
    <p><b>DNS record</b></p>
  :::column-end:::
  :::column:::
    <p><b>Purpose</b></p>
  :::column-end:::
  :::column:::
    <p><b>Value to use</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b><br></p>  <p><b>(VOIP Services)</b></p>
  :::column-end:::
  :::column:::
    <p>Used originally by the Skype for Business clients to find the Skype for Business Online service in Microsoft 365 and sign in, it's now used by the Teams client.</p>
  :::column-end:::
  :::column:::
    <p><b>Alias:</b> sip<br></p>  <p><b>Target:</b> sipdir.online.lync.com</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b><br></p>  <p><b>(VOIP Services)</b></p>
  :::column-end:::
  :::column:::
    <p>Used originally by the Skype for Business clients to find the Skype for Business Online service in Microsoft 365 and sign in, it's now used by the Teams client.</p>
  :::column-end:::
  :::column:::
    <p><b>Alias:</b> Lyncdiscover<br></p>  <p><b>Target:</b> webdir.online.lync.com</p>
  :::column-end:::
:::row-end:::


Fortunately, the Microsoft 365 portal provides the administrator who is doing the initial configuration of Microsoft 365 with all the DNS records that are required for proper name resolution. For some DNS providers such as GoDaddy, Microsoft 365 can automatically create all necessary records.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”