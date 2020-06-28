**Microsoft Compliance Score** is a preview feature in the Microsoft compliance center that helps you understand your organization's compliance posture. It calculates a risk-based score measuring your progress in completing actions that help reduce risks around data protection and regulatory standards.

You can use Compliance Score as a tool to track all of your risk assessments. It provides workflow capabilities to help you efficiently complete your risk assessments through a common tool.

The main Compliance Score page is your custom dashboard. It shows your current score, helps you see what needs attention, and guides you to actions to improve your score. Your Compliance Score dashboard will look like this:



:::image type="content" source="../media/4-compliance-score-view-3.png" alt-text="Screenshot of Compliance Score preview page":::

You can also see your Compliance Score broken down into specific categories.

:::image type="content" source="../media/4-compliance-score-breakdown-v2.png" alt-text="Screenshot showing Compliance Score breakdown":::

Compliance Score helps simplify compliance management by providing:

- **Continuous assessments**: automatically scans through your Microsoft 365 environments to detect and monitor the effectiveness of data protection controls in your system
- **Recommended actions**: provides recommendations and step-by-step guidance for how to implement controls to maximize your score
- **Built-in control mapping**: helps you stay current with the evolving compliance landscape by providing a built-in common control framework

### Key components

Compliance Score uses several components to help you manage your compliance activities. As you use Compliance Score to assign, test, and monitor compliance activities, it's helpful to have a basic understanding of the key components: controls, assessments, templates, and groups.

- **Controls** - A control defines how you assess and manage system configuration, organizational process, and people responsible for meeting a specific requirement of a regulation, standard, or internal policy. Compliance Score tracks two types of controls:

  - **Microsoft-Managed Controls** - For each cloud service, Microsoft implements and manages a set of controls as part of Microsoft's compliance with various standards and regulations. Each control provides details about how Microsoft implemented the control, and how and when that implementation was tested and validated by Microsoft and/or by an independent third-party auditor. 
  - **Customer-Managed Controls** - This is the collection of controls that are managed by your organization. Your organization is responsible for customer-managed control implementation as part of your compliance process for a given standard or regulation. Customer-managed controls are organized into control families for the corresponding certification or regulation. Use the customer-managed controls to implement the recommended actions suggested by Microsoft as part of your compliance activities. 

- **Assessments** - An assessment is an evaluation of a template that initiates the scoring process for your organization. Assessments group the actions necessary to meet the requirements of a standard, regulation, or law. For example, you may have an assessment that, when you complete all actions within it, brings your Office 365 settings in line with ISO 27001 requirements.
  Compliance Score provides your organization with an initial assessment based on the Microsoft 365 data protection baseline. This assessment is a recommendation for reducing your data protection and compliance risks ([learn more](https://docs.microsoft.com/microsoft-365/compliance/compliance-score-methodology?view=o365-worldwide#initial-score-based-on-microsoft-365-data-protection-baseline)).

  Assessments have several components:

  - **In-scope services**: the specific set of Microsoft services applicable to the assessment
  - **Microsoft-managed controls**: controls that Microsoft implemented and tested
  - **Customer-managed controls**: controls that you manage
  - **Assessment score**: the percentage of the points achieved by completing actions within that assessment
    Compliance Score becomes more powerful once you add assessments that are more relevant to your organization. For example, if your organization belongs to the financial services industry, you may want to add the FFIEC assessment. Learn how to [add assessments in Compliance Manager](https://docs.microsoft.com/microsoft-365/compliance/working-with-compliance-manager?view=o365-worldwide#assessments).

  > [!NOTE]
  > During public preview you will be directed to Compliance Manager to manage your assessments.

- **Templates** - Compliance Score provides pre-configured templates for assessments. You can also create a Custom Assessment by adding your own controls and actions to a pre-configured template. For example, you can create a template for your business process control, or a template for a regional data protection or compliance standard that isn't covered by one of the pre-configured templates.  The pre-configured templates for Compliance Score are listed here. 

- **Groups** - Groups allow you to organize assessments in a way that is logical to you. For example, you may choose to group assessments by year, compliance standard, service, teams within your organization, or some other way.

### Understand your score

The Compliance Score dashboard displays a score that measures your progress in completing improvement actions within controls.  

As mentioned above, Compliance Score tracks Microsoft-managed and customer-managed controls—each of which have points that contribute to your overall score:

Your score is calculated based on the completion of Microsoft-managed actions and customer-managed actions. Each action has a different impact on your score, depending on the potential risks involved. Your score can help prioritize which action to focus on to improve your overall compliance posture. Your points accrue when you complete actions.

Controls are assigned a score value based on whether they are mandatory or discretionary, and whether they are preventative, detective, or corrective.

- **Mandatory and discretionary controls**:
  - **Mandatory controls** are actions that can't be bypassed, either intentionally or accidentally. An example is a centrally managed password policy that sets requirements for password length, complexity, and expiration. Users must follow these requirements to access the system.
  - **Discretionary controls** rely upon users to understand policy and act accordingly. For example, a policy that requires users to lock their computer when they leave it is a discretionary control because it relies on the user.

- **Preventative, detective, and corrective controls**:
  - **Preventative controls** address specific risks. For example, protecting information at rest using encryption is a preventative control against attacks and breaches. Separation of duties is a preventative control to manage conflict of interest and guard against fraud.

  - **Detective controls** actively monitor systems to identify irregular conditions or behaviors that represent risk or that can be used to detect intrusions or breaches. System access auditing and privileged administrative actions auditing are types of detective monitoring controls. Regulatory compliance audits are a type of detective control used to find process issues.

  - **Corrective controls** try to keep the adverse effects of a security incident to a minimum, take corrective action to reduce the immediate effect, and reverse the damage if possible. Privacy incident response is a corrective control to limit damage and restore systems to an operational state after a breach.

Compliance Score continuously assesses controls. It does this by automatically scanning through your Microsoft 365 environment and detecting your system settings, and continuously and automatically updating your technical control status. Once you follow a recommendation to implement a control, you will see the control status updated the next day.

For example, if you turn on multi-factor authentication (MFA) in the Azure AD portal, Compliance Score detects the setting and reflects that in the control access solution details. Conversely, if you didn't turn on MFA, Compliance Score flags that as a recommended action for you to take.

### Relationship to compliance manager

If you already have or are familiar with Compliance Manager, think of Compliance Score as a simplified version of Compliance Manager. While the two exist as distinct yet integrated tools, Compliance Score makes it easier to monitor your overall compliance posture and take steps to improve it. 

Compliance Score shares the same backend with Compliance Manager, so any data you may already have in Compliance Manager will show in Compliance Score.

Some functionality remains solely in Compliance Manager during public preview, such as managing assessments and creating templates. We recommend beginning all of your compliance management activities in Compliance Score. When you come to functions handled by Compliance Manager, you'll be guided to that tool.

To learn more, visit [Microsoft Compliance Manager](https://docs.microsoft.com/microsoft-365/compliance/compliance-manager-overview?view=o365-worldwide)

## Walkthrough


### Task 1: Go to the Microsoft compliance center page
1. Go to the [Microsoft compliance center](https://compliance.microsoft.com) (resume where you left off from the previous unit). 

1. If you previously signed out, sign in with the global admin account credentials for your Microsoft 365 tenant. 


### Task 2: Explore the Microsoft Compliance Score
1. There are two ways you can get to the Compliance Score, the first is to use the Compliance Score Card’s **Manage Compliance Score**, the other is to select the **Compliance Score** option from the left-hand navigation. Both will take you to the Compliance Score view.
1. The first time you open the Compliance Score it’ll take a minute to set up and configure itself. Then you should see a view that is similar to this one. 

    :::image type="content" source="../media/4-compliance-score-preview.png" alt-text="Screenshot showing the Compliance Score preview page":::

1. The compliance view has a number of tabs, which you can review.
    - **Overview** – this is the default view
    - **Improvement Actions** – lets you see the actions you can take to improve your Compliance Score
    - **Solutions** – shows a list of the solutions that are contributing to your Compliance Score
    - **Assessment** – gives recommendations of regulatory requirements needed to meet compliance in your organization  
<br>

1. Select **Improvement actions**. Select any of the improvement actions listed to view available information. Actions you can take to improve your Compliance Score. Points may take up to 24 hours to update.
1. Close the page for the selected improvement action, by selecting the **X** on the top right of the page.
1. From the Microsoft Compliance Score page, select **Solutions** tab on the top of the page. The solutions tab lets you see which applications and services are able to, or already are contributing towards your compliance score. It’s a tabular view of all the solutions.
1. From the Compliance Score page, select the **Assessments** tab from the top of the page.  The assessment view lets you see which regulatory specific controls are implemented or are in progress.

   :::image type="content" source="../media/4-compliance-score-assessment.png" alt-text="Screenshot of the Compliance Score assessment page":::

1. As you can see, there is one assessment in progress, the Data Protection Baseline. As more regulatory assessments are added, they would be displayed here.
