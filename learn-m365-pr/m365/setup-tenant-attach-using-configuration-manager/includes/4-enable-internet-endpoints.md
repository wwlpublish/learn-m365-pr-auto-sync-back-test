Some Configuration Manager features rely on internet connectivity for full functionality. If your organization restricts network communication with the internet using a firewall or proxy device, make sure to allow specific endpoints.

Configuration Manager uses the following Microsoft URL forwarding services throughout the product:

- `https://aka.ms`
- `https://go.microsoft.com`
- `https://*.manage.microsoft.com`
- `https://dc.services.visualstudio.com`

The [service connection point](/mem/configmgr/core/servers/deploy/configure/about-the-service-connection-point) site system role makes a long standing outgoing connection to the notification service hosted on `https://*.manage.microsoft.com`. Verify the proxy used for the service connection point doesn't time out outgoing connections too quickly. We recommend 3 minutes for outgoing connections to this internet endpoint.

If your environment has proxy rules to allow only specific certificate revocation lists (CRLs) or online certificate status protocol (OCSP) verification locations, you must also allow the following CRL and OCSP URLs:

- `http://crl3.digicert.com`
- `http://crl4.digicert.com`
- `http://ocsp.digicert.com`
- `http://www.d-trust.net`
- `http://root-c3-ca2-2009.ocsp.d-trust.net`
- `http://crl.microsoft.com`
- `http://oneocsp.microsoft.com`
- `http://ocsp.msocsp.com`
- `http://www.microsoft.com/pkiops`

The service connection point validates important internet endpoints for tenant attach. These checks help make sure that the cloud service is available. It also helps you troubleshoot issues by quickly determining if network connectivity is a problem. For more information, see [Validate internet access](/mem/configmgr/core/servers/deploy/configure/about-the-service-connection-point#validate-internet-access).
