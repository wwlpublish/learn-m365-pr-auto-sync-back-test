A publicly available DNS zone setup is critical during the Microsoft 365 deployment for organizations that want to use custom domains. An organization can prove that it owns the DNS zone if it's able to edit records within that zone. When an organization owns the DNS zone, the Microsoft 365 setup wizard can create the tenant with the organization’s custom domain, such as adatum.com.

Furthermore, during the setup, the Microsoft 365 setup wizard will instruct organizations on which DNS records they must add to the public DNS zone. Once the organization configures the DNS zone per these instructions, client software such as Outlook or the Skype for Business Client will use auto discover services and resolve custom domain names with the IP addresses of Microsoft 365 servers. This process enables an organization’s client computers to connect to Microsoft 365 services, such as Exchange Online or Skype for Business Online.

Organizations use internal DNS zones configured on internal DNS servers, so that internal clients can resolve computer names and services. Organizations also use external, public DNS zones configured on Internet‑accessible DNS servers so that clients located on the Internet can resolve computer names and services. A couple of options are available for hosting the DNS zone for a custom domain:

 -  **Have a third-party provider, such as GoDaddy, host the DNS zone for the custom domain.** This scenario enables an organization to manage DNS through a web portal. It still needs a way to handle internal name resolution if it uses the name for resources that are on-premises. Companies usually choose to host an internal DNS zone for the domain.
 -  **Host the DNS zone on-premises by using or deploying DNS servers.** This scenario enables an organization to have DNS servers in the perimeter network so that internet users can resolve the organization's internet-facing domain resources. Internal DNS servers can also be used to handle name resolution for resources on the local area network.

When an organization plans the DNS zones for a custom domain, it can choose between the following scenarios:

 -  The internal DNS zones and external DNS zones have different names.
 -  The internal DNS zones and external DNS zones have the same name. This scenario is referred to as "split brain DNS", or "split DNS" for short.

### Internal DNS zones and external DNS zones have different names

Companies in this scenario can set up their own internal DNS for their internal domain, such as adatum.local. They can then use a DNS forwarder on the internal DNS servers to redirect name resolution requests for external domains to an external name server.

For example, a request for **mail.adatum.local** would be redirected to an internal IP address, such as 192.168.20.10. Conversely, a request for **mail.adatum.com** may go to 131.107.43.19, which is the company’s external IP address for that host name.

Internal clients that connect to Microsoft 365 services from the internal network will submit resolution requests to the local DNS servers. Then, a local DNS server will forward the client’s request to the external DNS server. The DNS server will then resolve the request and return the answer to the company’s internal DNS server. Finally, the local DNS server will forward the resolved request to internal clients.

### Internal DNS zones and external DNS zones have the same name (referred to as split brain DNS or "split DNS" for short)

Split DNS is a configuration in which the internal and external DNS environments provide different IP addresses to requests for the same host name. The IP address that's provided will depend on which server is used for name resolution.

For example, if a request for **mail.adatum.com** comes from inside the **adatum.com** network, the address returned may be 192.168.20.10 (a private IP address). However, if a user directly connected to the Internet made the same request for **mail.adatum.com**, the IP address returned may be 131.107.43.19 (a public IP address). This configuration is achieved by creating a zone on the internal DNS server for **adatum.com**.

When a client on the internal network makes a request for **mail.adatum.com**, the internal DNS server responds with the IP address for that host. In doing so, it uses the A (Address) or CNAME (common name) records that the server maintains for that zone. There's no requirement to forward on the name resolution request to the external DNS servers. However, external clients who try to contact mail.adatum.com receive a response from the external DNS server that's authoritative for that zone.

Internal clients that connect to Microsoft 365 services from the internal network will submit resolution requests to the local DNS servers. For a local DNS server to resolve the request to Microsoft 365 services, the local DNS zones and external DNS zones should both be configured with the same records requested by the Microsoft 365 setup wizard. Once both the internal and external DNS zones are configured with the same records, clients can connect to Microsoft 365 services from either inside the company or through the internet.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”