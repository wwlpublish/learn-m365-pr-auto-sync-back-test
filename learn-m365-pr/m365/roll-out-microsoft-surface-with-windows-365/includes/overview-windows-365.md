Today, businesses need to react faster, deliver sooner, and reduce costs without sacrificing security or regulatory compliance. This poses new challenges for IT departments, especially now that a large part of an organization's staff manages their working time between home and your on-premises offices. This increased flexibility creates additional demands to maintain the hardware and software, especially with added BYOD usage on the corporate network.

In this unit, you'll get an introduction to Windows 365, and then understand the nature of the Cloud PC lifecycle.

## What is Windows 365?

To meet these new challenges, Microsoft has created Windows 365. This cloud-based service lets you create a new virtual machine called a Cloud PC. Windows 365 combines the power and security of the cloud with the versatility and simplicity of the PC. This new type of computer can be assigned much as you would provision a new laptop or desktop device, and removes the headache of hardware procurement and dispatch. The benefit of this type of service is that the Cloud PC can be provisioned to meet any employee or team need. It works the same as a regular desktop and has the added advantage of being accessible from anywhere in the world using a regular remote desktop connection.

The Cloud PC becomes the new desktop for each employee, giving them the same functions, apps, and collaboration tools they already use. It allows IT departments to improve security and meet regulatory compliance. A Cloud PC can also be accessed from any device that can connect to the internet.

Windows 365 enables you to:

- Procure, provision, and deploy in minutes, with optional automated OS updates.
- Offer users access to their personalized Windows desktop experience wherever they are.
- Tailor compute and configurations for an elastic workforce.
- Pick up where you left off on the device of your choice.
- Optimize experiences on Windows endpoints.
- Scale confidently with per-user pricing.

### The Cloud PC lifecycle

The lifecycle of a Cloud PC is very similar to that of a regular desktop, with the exception that there's no physical machine to procure and ship. The following image shows the typical lifecycle of a Cloud PC:

:::image type="content" source="../media/lifecycle-stages.png" alt-text="Image showing the typical lifecycle of a Cloud P C.":::

### Provision

Each Cloud PC is provisioned from a trusted operating system image optimized for Windows and Microsoft 365. You can also use your own custom operating system images to complete your organization's workload. For example, a Windows 365 Cloud PC may be provisioned as a Windows 365 service. You'll connect it to Azure AD and enroll it using Microsoft Endpoint Manager.

### Configuration

By enrolling the Cloud PC through Microsoft Endpoint Manager, it's ready to be configured with Azure AD Conditional Access and any other compliance policies.

### Protection

Windows 365 Cloud PCs are fully integrated with Microsoft 365. This means you can use the full capabilities of Microsoft Defender for Endpoint to protect your Windows 365 machine from the moment it's provisioned. Cloud PCs can still use multi-factor authentication and other controls to maintain user authentication and security.

### Monitor

With Windows 365 Cloud PCs, you can use endpoint analytics to measure the load and usage of your Cloud PCs, allowing you to scale up or down to meet demands.

### Deprovision

At some point, whatever the reason, you'll no longer require the use of a Cloud PC. To deprovision, remove the Windows 365 license from the target users. You'll have a seven-day grace period to reassign the license. After this, the Cloud PC is deprovisioned, and any associated storage is removed.

## Windows 365 options

Windows 365 comes in two editions-Business and Enterprise. Each is designed to meet the specific needs of your organization.

### Windows 365 Business

Windows 365 Business is a version of Windows 365 developed explicitly for use in small companies and doesn't have any licensing prerequisites. However, each user does require a Windows 365 Business license. When the license is assigned to a user, it can take around 30 minutes for it to become active.

Windows 365 Business is ideally suited to organizations with less than 300 users.

### Windows 365 Enterprise

Windows 365 Enterprise is designed for larger companies who need the capability to create an unlimited number of Cloud PCs. It provides greater administrative, security, and end-user tools. In addition, all Cloud PCs are managed using Microsoft Endpoint Manager, allowing for seamless configuration, update, and app management.
