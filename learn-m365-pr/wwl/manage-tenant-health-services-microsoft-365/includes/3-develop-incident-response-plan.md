Microsoft 365 is known as a Managed Evergreen environment. This title means that Microsoft 365 is always changing and updating to give its customers the best service it can. At times, this type of dynamic environment can lead to incidents in the service, such as a short outage or a degradation in a valued service such as SharePoint or Skype for Business. When these incidents occur, it's the duty of the Microsoft 365 Enterprise Administrator to monitor these events and develop a plan.

The following graphic displays the fact that single services can be degraded dependent on the tenant location. In this example, the health of Exchange Online is normal for a company's US tenant, but degraded for its European tenant.

:::image type="content" source="../media/m365-service-health-by-location-ef70ca7c.jpg" alt-text="graphic shows that all Microsoft 365 services for a US tenant are fine, but the health of Exchange Online in its European tenant is degraded":::


Enterprise Administrators should complete the following steps to develop an incident response plan:

1.  **Validate the incident and confirming that your environment is affected.** This step is necessary because some service incidents may not affect your environment. Since Microsoft 365 is a global service and spans across multiple data centers, the notifications go out in mass when they hit a certain threshold of tenant saturation. The Enterprise Administrator can confirm the issue is present by running self-assessments, and stop false positive notifications from occurring.
2.  **Determine whether the incident is relevant to your company.** There are times that the specific incident is related to a service that doesn’t interfere with daily business operations. By collaborating with your specialized administrators to tap into their product knowledge, you can determine if the incident is relevant to your company.
3.  **Review for timeline checks once relevancy and degradation have been established.** The purpose of this step is to determine whether the service group has set a specific timeframe on when they expect the service to be in a non-degraded state. If no timeline has been set for the incident, you can submit a service request to see if there's an opening on the timeline. You should have the incident number ready and added to the service request to speed up the resolution time.
4.  **Develop a backup solution in case the service is degraded for longer than an acceptable timeframe.** While this step can be an inconvenience, it’s necessary to have a remedy in place when unexpected incidents occur. For example, you may need to work from the cloud until the incident is resolved. You may also need to work locally and on a reliable system during the down time.

> [!TIP]
> Enterprise Administrators should always check the Service Health dashboard for updates and use the service request as needed. The service is free and provided with your subscription.
