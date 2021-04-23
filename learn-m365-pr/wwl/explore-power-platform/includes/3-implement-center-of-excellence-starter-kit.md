A Center of Excellence (CoE) in an organization drives innovation and improvement by bringing together like-minded people with similar business goals to share knowledge and success. At the same time, a CoE provides standards, consistency, and governance to the organization.

The Microsoft Power Platform CoE Starter Kit is a collection of components and tools designed to help organizations develop a strategy for adopting and supporting Microsoft Power Platform. The focus of the starter kit is on Power Apps and Power Automate. The kit doesn't represent the entire CoE, because managing a CoE requires more than tools alone. The CoE also requires people, communication, and defined requirements and processes. The tools provided in the starter kit are just a means to get to the end goal. The CoE itself must be thoughtfully designed by each organization based on their needs and preferences.

**Additional reading.** For more information, see [What is a Center of Excellence?](https://docs.microsoft.com/power-platform/guidance/coe/motivation?azure-portal=true)

The Center of Excellence starter kit provides some automation and tooling to help teams build monitoring and automation necessary to support a CoE. The foundation of the kit is a Microsoft Dataverse data model and workflows to collect resource information across the environments in the tenant. The kit includes multiple apps and Power BI analytics to view and interact with the data you collect. It also includes flows to collect data across environments and help with workflows for your compliance needs. The kit also provides several templates and suggested patterns and practices for implementing CoE efforts.

### Using the CoE Power BI dashboard

Enterprise administrators and Power Platform administrators want visibility into how their organization is using Power Apps and Power Automate. Insights into their adoption will help you govern and secure the platform, identify patterns, and enable you to nurture your makers to accelerate adoption.

The [admin analytics](https://docs.microsoft.com/power-platform/admin/analytics-powerapps?azure-portal=true) that are part of the [Power Platform admin center](https://aka.ms/ppac?azure-portal=true) provide you with environment-level analytics that are based on your usage for the past 28 days. As your adoption grows, you may need customized dashboards that show you more insights and enable you to apply richer filters to your data over a longer period of time.

The Power BI dashboard of the Center of Excellence (CoE) Starter Kit provides visualizations and insights into resources in your tenant. These resources include environments, apps, Power Automate flows, connectors, connection references, makers, and audit logs. Telemetry from the audit log is stored from the moment you set up the CoE Starter Kit, so over time you can look back and identify trends for longer than 28 days.

The dashboard provides analytics and data for the following areas:

 *  **[Monitor](https://docs.microsoft.com/power-platform/guidance/coe/power-bi-monitor?azure-portal=true).** With the Monitor section of the CoE Power BI dashboard, you can query basic inventory (environments, apps, flows, makers, connectors, and audit logs) to monitor usage across your entire tenant and within each environment. These reports also support drill-downs and filtering. For example, by maker department/country or region/city, connector usage, or premium feature usage.
    
 *  **[Govern](https://docs.microsoft.com/power-platform/guidance/coe/power-bi-govern?azure-portal=true).** As an admin, you'll want to use the insights you gather to drive action, such as performing risk assessments and identifying critical, orphaned, or unused resources. The pages in the Govern section of the CoE Power BI dashboard enable you to drive action directly from within the Power BI report through an embedded app. The app can be used to grant yourself or others ownership of a resource, archive it, or delete it.
 *  **[Nurture](https://docs.microsoft.com/power-platform/guidance/coe/power-bi-nurture?azure-portal=true).** As you establish your CoE, a significant part of your activity will be nurturing your maker community and enabling them to follow best practices. You also want to work with them to identify whether they or their resources need additional support. The Nurture section of the CoE Power BI dashboard helps you find your "star" app and flow makers. It also enables you to see what connectors they're using, where they're based (department/country or region/city), and how they're adopting Microsoft Power Platform.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”