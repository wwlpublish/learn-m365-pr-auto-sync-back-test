Apps in Microsoft Teams allow you to leverage additional capabilities, enhance your experience, and make Teams work for you by adding your favorite Microsoft and third-party services.

In the modern business environment, users often want to use their own devices to access your systems. They might download and use apps from app stores and other locations that you can't control directly. You need to ensure that such practices don't put your sensitive and business-critical data at risk. Defender for Cloud Apps can assist with this task.

## What is Defender for Cloud Apps?

Microsoft Defender for Cloud Apps is a cloud access security broker. It's a layer between cloud applications and cloud application users. Microsoft Defender for Cloud Apps is designed for security professionals who need to monitor activity centrally and enforce security policies.

Microsoft Defender for Cloud Apps natively integrates with leading Microsoft solutions. It provides visibility into the apps being used, control over data travel, and analytics to identify and combat cyber threats.

:::image type="content" source="../media/dashboard-enhanced.png" alt-text="Defender for Cloud Apps dashboard" lightbox="../media/dashboard-enhanced.png":::

## The Defender for Cloud Apps framework

Defender for Cloud Apps uses a four-stage framework:

- **Discover and control the use of Shadow IT**: Identify the cloud apps, IaaS, and PaaS services used by your organization. Investigate usage patterns, assess the risk levels and business readiness of more than 16,000 SaaS apps and more than 80 risks.

- **Protect your sensitive information**: Understand, classify, and protect the exposure of sensitive information at rest. Use security policies and automated processes to apply controls in real time across all your cloud apps.

- **Detect cyber threats and anomalies**: Detect unusual behavior across cloud apps to identify ransomware, compromised users, or rogue applications. Analyze high-risk usage and remediate automatically to limit the risk to your organization.

- **Control the compliance of your cloud apps**: Assess if these cloud apps meet relevant requirements, including regulatory compliance and industry standards. Prevent data leaks to noncompliant apps, and limit access to regulated data.

## Architecture

Defender for Cloud Apps provides:

- **Cloud Discovery**: Analyzes your traffic logs against the Defender for Cloud Apps catalog of more than 16,000 cloud apps. Using more than 80 risk factors, the apps are ranked and scored to provide risk assessment reports.

- **Sanction or unsanction apps**: Apps should be sanctioned or unsanctioned after you've reviewed the list of discovered apps in your environment. Secure your environment by approving or sanctioning safe apps or prohibiting or unsanctioning unwanted apps.

- **App connectors**: Deploy app connectors that use the APIs of app providers to give visibility and control by Defender for Cloud Apps over the apps you connect to.

- **Conditional Access App Control**: Provides real-time protection, visibility, and control over access and activities within your cloud apps. Session controls in Defender for Cloud Apps work with the featured apps.

- **Policies**: Enables you to define the way you want users to behave in the cloud. You detect risky behavior, violations, or suspicious data points and activities in your cloud environment. If necessary, you can integrate remediation workflows to achieve complete risk mitigation.

:::image type="content" source="../media/cloud-app-security.png" alt-text="Diagram showing the Defender for Cloud Apps being used in an organization":::

## Conditional Access App Control

To allow featured apps to be controlled by Microsoft Defender for Cloud Apps Conditional Access App Control, there are four steps:

1. **Configure your identity provider (IdP)** to work with Defender for Cloud Apps.

2. **Sign into each app** with a user scoped to the policy.

3. **Verify the apps are configured** to use access and session controls.

4. **Test** the deployment.

You must also have Azure Active Directory (Azure AD) Premium P1 or higher, or the license required by your identity provider (IdP) solution, and licenses for Microsoft App Security.

## Policy control

You use policies to define the way you want users to behave in the cloud. Policies enable you to detect risky behavior, violations, or suspicious data points and activities in your cloud environment. You can integrate remediation workflows to mitigate risks. There are multiple types of policies that correlate to the different types of information you want to gather about your cloud environment, and the types of remediation actions you might take. Examples include:

- Quarantine a data violation threat.

- Block a risky cloud app from being used by your organization.

For more information, see:

- [Microsoft Defender for Cloud Apps overview](/cloud-app-security/what-is-cloud-app-security?azure-portal=true)

- [Protect apps with Defender for Cloud Apps Conditional Access App Control](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad#featured-apps?azure-portal=true)

- [Defender for Cloud Apps best practices](/cloud-app-security/best-practices?azure-portal=true)
