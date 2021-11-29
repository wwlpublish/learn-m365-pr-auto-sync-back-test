Microsoft Defender for Cloud gives detailed information about the security of your environment, at-a-glance from one central location.

As the Azure security administrator, you'll want to ensure your organization's systems, users, and data are protected. You also need to make sure that the company meets its compliance requirements wherever it operates.

Here, you'll see how the workload protection dashboard can give you a detailed understanding of your environment's security.

## Workload protection dashboard

As a unified infrastructure security management system, Microsoft Defender for Cloud is designed to help you:

- Strengthen the security posture of your organization.
- Meet compliance requirements.
- Provide threat protection for your Azure and non-Azure workloads.

Use the workload protection dashboard in the Azure portal to obtain and manage an organization level overview of the company's security posture, compliance, and any threats.

:::image type="content" source="../media/2-dashboard-inline.png" lightbox="../media/2-dashboard-expanded.png" alt-text="workload protection dashboard":::

The workload protection dashboard consists of a few high-level sections:

### Policy & compliance

Microsoft Defender for Cloud looks at your whole environment and provides an aggregate score to give you an idea of how secure it is. This is the Secure Score for your environment that you can find in this Policy & compliance section.

You can also use this section to find out if you're meeting compliance requirements, and how to address them. For example, you'll see if there are any storage accounts that don't meet a particular compliance control. You can then act accordingly to implement the remediation steps that Microsoft Defender for Cloud recommends.

Microsoft Defender for Cloud also enables you to set up security policies to protect different parts of your environment. This means you can also see which areas of the environment aren't adhering to security policies, and how to address them.

### Resource security hygiene

Use this section to understand which common security hygiene issues are affecting your resources. These issues will be labeled as low, medium, or high severity, based on the impact they might have on your organization's security. For example, Microsoft Defender for Cloud tells you whether there are any Azure SQL Database servers that don't have advanced data security enabled. You can then let Microsoft Defender for Cloud automatically remediate this situation using Quick Fix:

:::image type="content" source="../media/2-resource-hygiene-inline.png" lightbox="../media/2-resource-hygiene-expanded.png" alt-text="Resource hygiene":::

### Threat protection

Microsoft Defender for Cloud will actively detect and help you address threats for resources inside Azure, and workloads like servers outside of Azure, on-premises, or in other clouds. Use this section in the workload protection dashboard to help understand where an attack might have originated, and how it could impact your resources. You can then do better investigations and address threats more effectively.

Microsoft Defender for Cloud also natively integrates with Microsoft Defender for Endpoint. Machines with Linux or Windows will receive security recommendations that can be used to enhance security posture. You can also use adaptive application controls to let Microsoft Defender for Cloud learn about the kind of apps that normally run on your machines. It then uses that intelligence to scrutinize every app running on any of your machines and alert you with steps to deal with the situation. For example, if an unapproved application is running on a machine that normally doesn't run that kind of application.
