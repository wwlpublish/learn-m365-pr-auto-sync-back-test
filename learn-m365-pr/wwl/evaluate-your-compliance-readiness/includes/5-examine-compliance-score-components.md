Compliance Score uses several components to help organizations manage their compliance activities. As organizations use Compliance Score to assign, test, and monitor compliance activities, it’s helpful to have a basic understanding of these key components. The following diagram shows the relationships among these components.

:::image type="content" source="../media/compliance-manager-relationships-3a64b180.png" alt-text="Diagram of compliance score.":::
<br><br>

### **Controls**

A control defines how an organization assesses and manages system configuration, organizational process, and people accountability to meet a specific requirement of a regulation, standard, or internal policy.

Compliance Score tracks two types of controls:

 -  **Microsoft-managed controls.** Controls for Microsoft cloud services, which Microsoft is responsible for implementing.
 -  **Customer-managed controls.** Controls managed by your organization, which you're responsible for implementing.

### **Assessments**

An assessment is an evaluation of a template that starts the scoring process for an organization. Assessments group the actions necessary to meet the requirements of a standard, regulation, or law. For example, you may have an assessment that, when you complete all actions within it, brings your Microsoft 365 settings in line with ISO 27001 requirements.

By default, Compliance Score provides an organization with an assessment based on the Microsoft 365 data protection baseline. This recommendation is used for reducing an organization's data protection and compliance risks.

**Additional reading.** For more information on how the Compliance Score is calculated, see [Compliance score calculation](https://docs.microsoft.com/microsoft-365/compliance/compliance-score-calculation?azure-portal=true).

### **Templates**

Compliance Score provides pre-configured templates for assessments. Compliance Score also allows organizations to create templates for their own assessments to suit their needs. For example, you can create a template for your business process control, or a template for a regional data protection or compliance standard that isn’t covered by one of the pre-configured templates. By creating your own templates, you can create custom assessments to ensure that Compliance Score tracks not only Microsoft cloud assessments, but also any other risk assessments in scope for your organization.

**Additional reading.** For more information on creating templates, see [Microsoft Compliance Manager](https://docs.microsoft.com/microsoft-365/compliance/compliance-manager?azure-portal=true).

### **Groups**

Groups allow you to organize assessments in a way that is logical to you. For example, you may choose to group assessments by year, compliance standard, service, teams within your organization, or some other way.

When two different assessments in the same group share customer-managed actions, the completion of implementation details, testing, and status for the action in one assessment automatically synchronizes to the same action in any other assessment in the group. This design unifies the assigned improvement actions across the group and reduces duplicating work.

**Additional reading.** For more information on setting up Compliance Score, see [Microsoft Compliance Score setup](https://docs.microsoft.com/microsoft-365/compliance/compliance-score-setup?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”