If there's a problem delivering a message, you receive a Delivery Status Notification (DSN). The most common type of DSN is a Non-Delivery Report (NDR). NDRs contain an error code indicating the reason for non-delivery.

## Understanding an NDR

The NDR includes:

- The cause of the non-delivery.
- Person required to fix the issue.
- Instructions for fixing the issue for the end-user.
- More detailed information for an email admin, including the NDR code.

## Common NDR codes

|NDR code|Description|
|-|-|
|5.1.1|Recipients email address does not exist|
|5.2.x|Number of messages permitted to be sent or received per hour exceeded|
|5.7.x|Sender denied by sending or receiving system|

## How to interpret an NDR

If you receive an NDR from a server that's not an Exchange Online mail server, such as a generic Internet email server, the NDR might be less graphical and more text-based. The information included is still the same.

## Learn more

[List of NDR codes](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online?azure-portal=true)
