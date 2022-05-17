Outlook and other Office-related clients can use the Autodiscover process to automatically locate services in Microsoft 365. For an organization to use Autodiscover in this manner, it must first configure the appropriate DNS records on the publicly available DNS servers on the Internet.

 -  In organizations where the internal DNS namespace, such as **adatum.local**, is different from the Internet DNS namespace, such as **adatum.com**, the internal DNS servers forward internal client queries to Internet DNS servers.
 -  In organizations that use split-brain DNS, where internal and Internet DNS namespaces are the same, such as **adatum.com**, both the internal and Internet DNS servers should be configured to resolve the Autodiscover records in Microsoft 365.

The following table identifies the Autodiscover records that Outlook clients need to connect to Exchange Online in Microsoft 365.

:::row:::
  :::column:::
    **DNS record**
  :::column-end:::
  :::column:::
    **Purpose**
  :::column-end:::
  :::column:::
    **Value to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **CNAME**
**(Exchange Online)**
  :::column-end:::
  :::column:::
    The Autodiscover service configures Outlook for users.
  :::column-end:::
  :::column:::
    **Alias:** Autodiscover
**Target:** autodiscover.outlook.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **CNAME**
**(Exchange federation)**
  :::column-end:::
  :::column:::
    The Autodiscover service configures Outlook for users in Exchange federation scenarios. This record is optional, and it's needed when you deploy Exchange in a hybrid configuration with Microsoft 365.
  :::column-end:::
  :::column:::
    **Alias:** For example, Autodiscover.service.adatum.com
**Target:** autodiscover.outlook.com
  :::column-end:::
:::row-end:::


The following graphic shows that the domain suffix of a user's email address is resolved against DNS. It's then redirected to Exchange Online, which in turn delivers the correct Autodiscover.xml file back to the Outlook client. This file contains all the configuration information.

:::image type="content" source="../media/domain-suffix-resolved-to-dns-877a81c1.jpg" alt-text="graphic shows that the domain suffix of a user's email address is resolved against DNS and redirected to Exchange Online, which then delivers the correct Autodiscover.xml file back to the Outlook client":::


The following table identifies the DNS records that are needed for VOIP Services to connect to Skype for Business Online in Microsoft 365.

:::row:::
  :::column:::
    **DNS record**
  :::column-end:::
  :::column:::
    **Purpose**
  :::column-end:::
  :::column:::
    **Value to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **CNAME**
**(VOIP Services)**
  :::column-end:::
  :::column:::
    This record was originally used by the Skype for Business clients to find the Skype for Business Online service in Microsoft 365 and sign in. It's now used by the Microsoft Teams client.
  :::column-end:::
  :::column:::
    **Alias:** sip
**Target:** sipdir.online.lync.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **CNAME**
**(VOIP Services)**
  :::column-end:::
  :::column:::
    This record was originally used by the Skype for Business clients to find the Skype for Business Online service in Microsoft 365 and sign in. It's now used by the Microsoft Teams client.
  :::column-end:::
  :::column:::
    **Alias:** Lyncdiscover
**Target:** webdir.online.lync.com
  :::column-end:::
:::row-end:::


The Microsoft 365 portal provides the administrator who's doing the initial Microsoft 365 configuration with all the DNS records that are required for proper name resolution. For some DNS providers such as GoDaddy, Microsoft 365 can automatically create all necessary records.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”