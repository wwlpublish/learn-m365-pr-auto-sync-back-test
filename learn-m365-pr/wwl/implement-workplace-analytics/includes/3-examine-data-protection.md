Workplace Analytics produces powerful insights into how an organization functions. It uses data from everyday work in Microsoft 365 to identify collaboration patterns that impact productivity, workforce effectiveness, and employee engagement. However, by analyzing Microsoft 365 collaboration data and organizational data (such as Human Resource (HR) data), the Workplace Analytics service has access to potentially sensitive information about how a company operates. Because of this, successful implementation and use of Workplace Analytics requires careful thought and planning about data protection.

This unit provides a basic overview of the roles, responsibilities, types of data, and data privacy recommendations that organizations should consider when implementing Workplace Analytics. The general suggestions offered here are a starting point for planning your data protection strategy and deployment.

> [!IMPORTANT]
> Organizations typically address data protection issues by engaging with legal, privacy, human resources, and other subject matter experts. The information provided in this unit is NOT intended as a replacement for engaging with these experts on data protection issues.

### Data protection roles and responsibilities

There are two major compliance roles that are used in Workplace Analytics - the Data Controller role and the Data Processor role. Your organization will take on the Data Controller role, and Microsoft will take on the Data Processor role. When personal data is involved, these roles provide a framework for understanding data protection when using Workplace Analytics, no matter where your organization is located. That being said, organizations should still rely upon the advice of their legal, privacy, HR, and other subject-matter experts to modify the framework provided in these roles so that they're in compliance with the data privacy laws of their country/region.

#### Your organization's role: Data Controller

The Data Controller role determines the purpose and means of processing a user's personal data. As a data controller, your organization should:

 -  Determine the scope of data to be analyzed.
 -  Propose goals for data analysis.
 -  Work with the organization’s legal, privacy, and HR teams.
 -  Use Workplace Analytics privacy controls to direct what data is analyzed, how the data will appear in results, who will have access to the raw data, and the results of the analysis.
 -  Be familiar with the Workplace Analytics [privacy documentation](/workplace-analytics/privacy/privacy-and-data-access) provided by Microsoft.

#### Microsoft's role: Data Processor

The Data Processor role processes personal data on the behalf of the data controller. When your organization uses Workplace Analytics, Microsoft is the data processor. As a data processor, Microsoft will:

 -  Process personal data under the organization’s instructions, which are reflected in the Workplace Analytics configuration settings.
 -  Use Workplace Analytics to process all data provided to Microsoft (including personal data) according to the same [general privacy and security terms in the Online Services Terms (OST)](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=46?azure-portal=true) as Microsoft 365.
 -  Implement technical and organizational security measures to protect the confidentiality of the organization’s (and employees’) data in Workplace Analytics.
 -  Provide Workplace Analytics features that help organizations meet their data-controller obligations and honor data-subject rights. These rights include the right of exclusion from processing, access, and erasure, and include the right of transparency about methods of processing.

> [!NOTE]
> Microsoft doesn't use data for advertising nor does it volunteer to provide data to law enforcement.

### De-identification of data

To keep from exposing personal data, Workplace Analytics de-identifies user data by using pseudonymization and other techniques, including aggregation. For more information, see [De-identification of personal data](/workplace-analytics/privacy/de-identify-data).

### Types of data used in Workplace Analytics

Before an organization begins using Workplace Analytics, it should first determine what types of data it wants to analyze. Consider whether including personal data is necessary to fulfill the purpose of your analysis, or whether other non-identifying types of data could produce results that are as effective and insightful.

While an organization may have its own data-classification system, it should consider the following types of data when it implements Workplace Analytics:

 -  **Personal data.** This form of data has the highest privacy risk. This information directly or indirectly identifies a person.
 -  **Pseudonymized data.** This form of data has a high privacy risk because the information is still personal, even though it doesn’t directly identify the person. Instead, the identity is replaced with a numerical value that has no empirical significance.
 -  **Aggregated data.** This form of data has a low privacy risk because the collected information comes from multiple individuals or sources.
 -  **De-identified data.** This form of data has the lowest privacy risk because the information doesn’t relate to a specific individual. This data type doesn’t increase the likelihood that a specific individual can be identified. The data has been rendered in a way so that it can’t be used to identify a specific individual.

### Data protection guidelines

Consider the following data protection guidelines before using Workplace Analytics in your organization:

 -  **Develop a clear analysis plan**. By using Workplace Analytics, data can be processed in several ways. Before beginning, it’s important to have a rational purpose for what you want to analyze and why. Determine what specific questions about your organization you want to answer and then consider how Workplace Analytics might help you find those answers.
 -  **Determine whether to complete a Data Protection Impact Assessment (DPIA).** The privacy risk to employees and other users in your organization is largely within your control. The risk depends primarily on the organizational dataset that you import into Workplace Analytics and how you use that data. After developing an analysis plan, determine whether you need to complete a DPIA. If your proposed use of Workplace Analytics involves processing personal data that could lead to high risks to the rights of employees and other users in your organization, completing a DPIA might be warranted. If you're unsure whether a DPIA is required, consult your organization’s privacy subject matter experts, such as legal or HR personnel.<br>
 -  **Use aggregated or de-identified data whenever possible.** Minimize privacy risk and use the minimum data necessary to conduct your research. Adopt a strict policy of never using personal data and minimizing use of pseudonymized data in combination with identifying attributes can help address many of the risks inherent in using such data. These policies can restrict the type of analysis that Workplace Analytics can do. It's up to your organization to decide the best approach and policy for your organization.
 -  **Work closely with subject matter experts.** Consult with your organization’s HR, privacy, and legal subject matter experts in the countries/regions where you would like to use Workplace Analytics. Due diligence is important in highly regulated jurisdictions. Analysis that is acceptable in one country/region may be illegal or subject to other requirements (for example, notice and consent obligations) in other countries/regions. 
