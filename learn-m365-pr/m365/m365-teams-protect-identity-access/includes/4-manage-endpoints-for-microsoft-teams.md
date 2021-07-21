Microsoft Teams endpoints can be defined as any PC, Mac, tablet, or mobile device running the Teams client. The term endpoint not only encompasses the device itself, but also how a user connects to the device. For example, by using the device's built-in mic or speaker, earbuds, or an optimized headset. After they're deployed, endpoints mustn't be forgotten. The Teams endpoints require ongoing care and maintenance.

## Endpoint requirements

One of the key benefits of Teams is that the client is kept up to date automatically. The clients on the PC and Mac are updated by using a background process that checks for new builds and downloads the new client when the app is idle. The Teams mobile apps are kept current through their respective app stores.
The Teams client has minimum requirements for its underlying software platform. These requirements might change over time, so it's important that you monitor for changes. For example, the Teams client has a minimum iOS version. If the client uses an internet browser, that also needs to be kept current. You'll find a link to a list of supported platforms in **Get clients for Microsoft Teams**, located in the **Learn more** section below.

## Endpoint firewalls

Client-side firewalls can have a significant impact on the user experience. Client-side firewalls might affect call quality and even prevent a call from being established. After the appropriate exclusions on the client firewall have been configured, they need to be kept up to date. Your third-party vendor will have specific guidance for how to update the exclusions.

## Wi-Fi drivers

Wi-Fi drivers could be problematic. For example, a driver might have aggressive roaming behaviors between access points that can induce unnecessary access-point switching, leading to poor call quality. A poorly performing Wi-Fi driver might be discovered through a Quality of Experience review. See **Monitor and improve call quality for Teams** located in the **Learn more** section below. It's essential to implement a quality-driven process that monitors new Wi-Fi drivers and ensures that they're tested before being deployed to the general user population.

## Endpoint management

A catalog of supported endpoints and interface devices, such as headsets, should be available and maintained. This catalog will include a list of approved devices that were selected and validated as part of the Envision and Onboard phases. Typically, specific devices are selected for each persona type in your organization, to meet the needs of that persona's attributes. All endpoints have a lifecycle, and you need to manage the vendor contracts, warranty, replacement, distribution, and repair policies associated with these devices.

## Endpoint troubleshooting

Even if you've followed the previous guidance, users in your organization might still run into issues with Teams. Although the problem might not be with the endpoint itself, the symptoms are typically surfaced through the client to the user. The following guidance is intended to provide general steps you can take to resolve the issue; it's not meant to be a comprehensive troubleshooting guide. The steps are provided in a specific order, but they don't have to be followed explicitly and might not be applicable, depending on the nature of the issue.

1. **Validate service health**: The issue a user might be experiencing can be related to an event that negatively affects the Teams service or its dependent services. As a first step, we recommend that you confirm there are no active service issues. Consult **How to check Office 365 service health**, located in the **Learn more** section below. Remember to check for the status of dependent services (for example, Exchange, SharePoint, OneDrive for Business).
1. **Validate client connectivity**: Connectivity issues cause functionality or sign-in problems in Teams. We recommend (especially for new sites or locations) that you validate connectivity to the service. Ensure the following Microsoft 365 URLs and IP address range guidance is followed for each site. Use the Microsoft Network Assessment Tool to do a connectivity test to validate that the media ports have been opened correctly for cloud voice capabilities. Detailed steps on how to run the connectivity tests are provided in the network readiness guidance.
1. **Check the known issues list**: Consult Teams Troubleshooting to determine whether the user has been negatively affected by one of these issues. Follow the workaround provided (if there is one) to resolve the issue.
1. **Visit the Microsoft Teams community**: The Microsoft Teams community offers dedicated spaces for Teams. The Teams community provides a discussion list, blog posts, and announcements centered around Teams. You can post a question or search previous discussions for solutions to your issue.
1. **Contact Microsoft Support**: You can contact Microsoft Support, online or by phone, to deal with Teams issues. For information, see Contact support for business products. For Premier customers, support requests can be started by following the guidance at Contact support for Microsoft Teams (Premier customers).

## Maintenance tasks

To maintain good service to your users, try to execute these tasks on a regular or semi-regular basis:

| **Activity** | **Description** | **Cadence** |
| --- | --- | --- |
| Endpoint requirements | Ensure that the Teams endpoint continues to meet all the software requirements listed in Get clients for Microsoft Teams. | Monthly |
| Endpoint firewalls | Maintain the appropriate exclusions on the endpoint firewall based on the information in Office 365 URLs and IP address ranges. Your third-party vendor will have specific guidance for how to maintain the exclusions. Subscribe to the RSS feed to be notified automatically of changes. | As needed |
| Wi-Fi drivers | Test and update Wi-Fi drivers on the PC. Validate the results by using CQD (improve and monitor call quality for Teams). | As needed |
| Endpoint management | Maintain the catalog of supported endpoints and interface devices (such as headsets). Manage vendor contracts, warranty, distribution, replacement, and repair policies. | Monthly |
| Endpoint troubleshooting | Troubleshooting tasks can include verifying connectivity, consulting the known issues list, log gathering, analysis, and escalation to Microsoft Support or third-party vendors. | As needed |

## Mobile device management (MDM)

Your corporate IT department can manage the entire device. With MDM, you can:

- Enforce the use of a device-level PIN and specific OS versions.
- Push device configurations, such as VPN settings, to the device.
- Deploy specific applications to the device so that all of your line-of-business apps are automatically deployed.
- Enforce device encryptions and, if necessary, wipe corporate data from the device.

MDM is ideal for company owned devices.

## Mobile app management (MAM)

Only specific applications on Android and iOS devices are managed by the IT department. These applications need to support management via MAM. Teams is one of the applications that supports MAM. With MAM, you can enforce an application-specific PIN. For example, the user is prompted for a PIN when launching Teams. As with MDM, you can enforce compliant devices such as the OS version.
You can implement data loss preventions to stop copy and paste from managed apps to unmanaged apps. For example, a user couldn't copy data from Teams and paste it into their private email account. You could also prevent a user from saving files to a private store.
You can enforce application-level encryption and wipe application data.
MAM is ideal for bring your own device (BYOD) scenarios.

## Windows Information Protection (WIP)

WIP allows specific applications on Windows 10 to be managed by corporate IT. These applications need to be written to support management via WIP. WIP is a policy that IT admins create to protect data from accidentally being copied to the wrong place. WIP tags content as "work" and allows the user to copy and paste across work-related apps. For example, copying from Excel into PowerPoint. If the user attempts to copy work documents into their private email account, a warning will be displayed.

## Conditional Access (CA)

Conditional Access allows only specific services to be accessed under certain conditions. CA allows you to define how people use an application and how they authenticate. For example, you can define how specific users and groups sign in, the platform they're using based on subnets, or the state of the device. You can require access to Teams, for example, only with multifactor authentication, only if the device is compliant, and if it's joined to Azure Active Directory. Teams will apply any SharePoint and Exchange Conditional Access policies because it's using SharePoint and Exchange in the backend. Any policies you configure for SharePoint and Exchange will apply to a user in Teams.

> [!NOTE]
> CA policies are independent from any MDM/MAM configurations.

## Learn more

- [Get clients for Microsoft Teams](/MicrosoftTeams/get-clients)
- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)
- [Monitor and improve call quality for Teams](/microsoftteams/monitor-call-quality-qos)
- [How to check Microsoft 365 service health](/office365/enterprise/view-service-health)
- [Protect your enterprise data using Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)
- [Contact support for Microsoft Teams (Premier customers)](https://support.microsoft.com/premier/contacts)
