# Microsoft 365 endpoint categories

The set of DNS domain names, URLs, and IP address ranges for Microsoft 365 services on the Internet are known as endpoints. Microsoft 365 endpoint categories are Optimize, Allow, and Default:

- Optimize 

  Required for connectivity to every Microsoft 365 service and represent over 75% of Microsoft 365 bandwidth, connections, and volume of data. These endpoints represent Microsoft 365 scenarios that are the most sensitive to network performance, latency and availability.

- Allow 

  Required for connectivity to specific Microsoft 365 services and features but are not as sensitive to network performance and latency as those in the Optimize category.
- Default 

  Represent Microsoft 365 services and dependencies that do not require any optimization. You can treat Default category endpoints as normal Internet traffic.

To optimize network performance, you must apply special treatment for traffic to Optimize and Allow category endpoints.

Next: Local Internet connections
 
