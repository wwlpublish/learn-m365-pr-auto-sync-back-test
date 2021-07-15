To configure Skype for Business hybrid, you need to:

1. Configure your on-premises Edge service to federate with Microsoft 365.

   Federation allows users in your on-premises deployment to communicate with Microsoft 365 users in your organization.

1. Configure your on-premises environment to enable shared SIP address space with Microsoft 365.

   You must also configure your on-premises environment to trust Microsoft 365 and enable shared SIP address space with Microsoft 365. This means Microsoft 365 can potentially host user accounts for the same set of SIP domains as your on-premises environment. Messages can be routed between users hosted on-premises and online.

1. Enable shared SIP address space in your Microsoft 365 tenant.

   In addition to the change you made in your on-premises deployment, make the corresponding change in your Microsoft 365 tenant to enable shared SIP address space with your on-premises deployment.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Configure Skype for Business hybrid](/SkypeForBusiness/hybrid/configure-federation-with-skype-for-business-online)
