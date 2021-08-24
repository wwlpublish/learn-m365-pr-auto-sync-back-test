All clients that use Office 365 cloud-based services, including Microsoft Teams, need to connect to the Office 365 endpoints. Office 365 endpoints represent set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.

Different Office 365 clients and devices connect to Office 365 services through multiple network paths and network equipment, including switches, routers, proxy servers, and firewalls. To optimize the performance to Office 365 cloud-based services, the network admins should configure network equipment according to the Office 365 endpoints requirement.

For Teams, you must open TCP ports 80 and 443 and UDP ports 3478 through 3481 from the clients to the internet. The TCP ports are used to connect to web-based content such as SharePoint, Exchange Online, and the Teams Chat services. Plug-ins and connectors also connect over these TCP ports. The four UDP ports are used for media such as audio and video, to ensure they flow correctly.

| Scenario            | Source IP/Port            | Destination IP/Port         |
|-|-|-|
| Non-real-time traffic   | Client IP / High ports        | Office 365 / 80, 443 TCP         |
| Real-time media traffic | Client IP / 50,000-50,059 UDP | Transport Relays / 3478-3481 UDP |


## Change management for Office 365 IP addresses and URLs

The Office 365 endpoints change regularly. If you do not manage these changes, you can end up with users blocked or with poor performance after a new IP address or URL is added in Office 365, but the firewall team has not been informed.
 
Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can use RSS feeds or the Office 365 IP Address and URL Web Service to get change notification.

### Change notification using the Web Service

You can use the Office 365 IP Address and URL Web Service to get change notification. We recommend you call the **/version** web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the **/endpoints** web method and optionally get the differences from the **/changes** web method. It is not necessary to call the **/endpoints** or **/changes** web methods if there has not been any change to the version you found.

### Change notification using RSS feeds

The Office 365 IP Address and URL Web Service provide an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance-specific pages for the IP addresses and URLs. 

### Change notification and approval review using Power Automate

You can also use Power Automate to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.

For more information, see:

- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)

- [Office 365 IP Address and URL Web Service](/microsoft-365/enterprise/microsoft-365-ip-web-service).
 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”