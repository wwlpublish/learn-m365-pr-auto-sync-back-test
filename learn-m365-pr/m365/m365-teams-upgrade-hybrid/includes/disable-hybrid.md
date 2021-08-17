After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. Aside from removing any hardware, a critical step is to logically separate that on-premises deployment from Microsoft 365 by disabling hybrid. Disabling hybrid consists of three steps:

1. Update DNS records to point to Microsoft 365.
2. Disable split domain in the Microsoft 365 tenant.
3. Disable ability in on-prem to communicate with Microsoft 365.

These steps should be done together as a unit as described in [Disable hybrid to complete migration to the cloud](/SkypeForBusiness/hybrid/cloud-consolidation-disabling-hybrid).
