Assessments are the core component of Compliance Score. An Assessment is an assessment of a Microsoft service against a certification standard or data protection regulation (such as ISO 27001:2013). Assessments help discern an organization's data protection and compliance posture against the selected industry standard for the selected Microsoft cloud service. Assessments are completed by the implementation of the controls that map to the certification standard being assessed.

The structure of an Assessment is based on the responsibility that's shared between Microsoft and your organization for:

 -  assessing security and compliance risks in the cloud.
 -  implementing the data protection safeguards specified by a compliance standard, a data protection standard, a regulation, or a law.

An Assessment is made of the following components:

 -  **In-Scope Services**. Each assessment applies to a specific set of Microsoft services.
 -  **Customer-Managed Controls**. Collection of controls that are managed by your organization. An organization is responsible for implementing these controls as part of its compliance process for a given standard or regulation. Customer-managed controls are also organized into control families for the corresponding certification or regulation. An organization should use the customer-managed controls to implement the recommended actions suggested by Microsoft as part of the organization's compliance activities.<br><br>An organization can use the prescriptive guidance and recommended Customer Actions in each customer-managed control to manage the implementation and assessment process for that control. Customer-managed controls in Assessments also have built-in workflow management functionality that can manage and track an organization's progress towards completing the Assessment.<br><br>For example, an organization's Compliance Officer can assign an Action Item to an IT admin who has the responsibility and necessary permissions to complete the actions that are recommended for the control. When that work is complete, the IT admin can upload evidence of their implementation tasks (for example, screenshots of configuration or policy settings). The admin can then assign the Action Item back to the Compliance Officer to complete the following tasks:
    
     -  Evaluate the collected evidence.
     -  Test the implementation of the control.
     -  Record the implementation date and test results in Compliance Manager.
 -  **Microsoft-Managed Controls**. For each cloud service, Microsoft implements and manages a set of controls as part of Microsoft's compliance with various standards and regulations. These controls are organized into control families that align with the structure from the corresponding certification or regulation that the Assessment is aligned to. For each Microsoft-managed control, Compliance Score provides details about how Microsoft implemented the control, along with how and when that implementation was tested and validated by an independent third-party auditor.

The following diagram is taken from an Assessment of Microsoft 365 and GDPR for a fictitious organization:

:::image type="content" source="../media/compliance-score-assessment-example-aec11bfd.png" alt-text="Screenshot of compliance score assessment for a fictitious company":::


This Assessment diagram displays the following Microsoft-managed controls (A through D) in the Security control family:

**A. The Controls/Articles section.** This section specifies the following information from the certification or regulation that maps to the Microsoft-managed control:

 -  **Control ID**. The section or article number from the certification or regulation that the control maps to.
 -  **Title**. The title from the corresponding certification or regulation.
 -  **Article ID**. This field is included only for GDPR assessments, as it specifies the corresponding GDPR article number.
 -  **Description**. Text of the standard or regulation that maps to the selected Microsoft-managed control.

**B. The Compliance Score.** This score indicates the level of risk (due to non-compliance or control failure) associated with each Microsoft-managed control. Compliance Scores are rated from 1 to 10 and are color-coded. Yellow indicates low risk controls, orange indicates medium-risk controls, and red indicated high-risk controls.

**C. The Control information section.** This section displays information about the implementation status of a control, the date the control was tested, who completed the test, and the test result.

**D. More drop-down arrow.** For each control, you can select **More** to see additional information. This information includes details about:

 -  Microsoft's implementation of the control.
 -  How the control was tested and validated by an independent third-party auditor.

**Additional reading.** For more information, see [how your compliance score is calculated and continuously monitored](https://docs.microsoft.com/microsoft-365/compliance/compliance-score-methodologyhttps://docs.microsoft.com/microsoft-365/compliance/compliance-score-setuphttps://docs.microsoft.com/microsoft-365/compliance/compliance-score-calculation?azure-portal=true).
