Before an organization gets started with insider risk management, there are important planning activities and considerations that should be reviewed by its Information Technology (IT) and Compliance Management teams. Thoroughly understanding and planning for an insider risk management deployment helps organizations ensure their implementations go smoothly and are aligned with the best practices for the solution.

**Additional reading**. For more information and an overview of the planning process to address risky activities in your organization, select the following link to download the article titled: [Starting an insider risk management program](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf?azure-portal=true).

**Additional viewing**. Watch the following short videos for more information on insider risk management:

 -  Watch the video titled [Insider Risk Management](https://www.microsoft.com/videoplayer/embed/RE4OUXB?postJsllMsg=true?azure-portal=true) to learn how the insider risk management workflow can help your organization prevent, detect, and contain risks while prioritizing your organization values, culture, and user experience.
 -  Watch the video titled [Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ?azure-portal=true) to learn how insider risk management and communication compliance work together to help minimize data risks from users in an organization.

### Work with stakeholders in your organization

An organization should identify the appropriate stakeholders who will be members of its insider risk management team.

 -  Certain members of the team should be assigned responsibility for taking actions on insider risk management alerts and cases.
 -  Other stakeholders should be responsible for the initial planning and the end-to-end insider risk management workflow. These stakeholders are usually people from the following areas of an organization:
     -  IT
     -  Compliance
     -  Privacy
     -  Security
     -  Human resources
     -  Legal

### Determine regional compliance requirements

Different geographic and organizational areas may have compliance and privacy requirements that are different from other areas of an organization. Work with the stakeholders in these areas to ensure they understand:

 -  The compliance and privacy controls in insider risk management.
 -  How these controls should be used across different areas of the organization.

In some scenarios, compliance and privacy requirements may require policies that designate or restrict some stakeholders from investigations and cases. These requirements may be based on the case for a user, or regulatory or policy requirements for the area.

If an organization has requirements for specific stakeholders to be involved in case investigations that involve users in certain regions, roles, or divisions, it may want to implement separate (even if identical) insider risk management policies targeting the different regions and populations. This configuration will make it easier for the right stakeholders to triage and manage cases that are relevant to their roles and regions.

### Plan for the review and investigation workflow

Organizations that want to manage insider risk management policies and alerts must assign users to specific role groups to manage different sets of insider risk management features. For example:

 -  It can assign users with different compliance responsibilities to specific role groups to manage different areas of insider risk management features.
 -  It can also assign all user accounts for designated administrators, analysts, investigators, and viewers to the **Insider Risk Management** role group.

Organizations should use a single role group or multiple role groups to best fit its compliance management requirements. They can choose from the role group options and solution actions in the following table when working with insider risk management.

| **Actions**                                    | **Insider Risk Management** | **Insider Risk Management Admin** | **Insider Risk Management Analysts** | **Insider Risk Management Investigators** | **Insider Risk Management Auditors** |
| ---------------------------------------------- | --------------------------- | --------------------------------- | ------------------------------------ | ----------------------------------------- | ------------------------------------ |
| Configure policies and settings                | Yes                         | Yes                               | No                                   | No                                        | No                                   |
| Access analytics insights                      | Yes                         | Yes                               | Yes                                  | No                                        | No                                   |
| Access &amp; investigate alerts        | Yes                         | No                                | Yes                                  | Yes                                       | No                                   |
| Access &amp; investigate cases         | Yes                         | No                                | Yes                                  | Yes                                       | No                                   |
| Access &amp; view the Content Explorer | Yes                         | No                                | No                                   | Yes                                       | No                                   |
| Configure notice templates                     | Yes                         | No                                | Yes                                  | Yes                                       | No                                   |
| View &amp; export audit logs           | Yes                         | No                                | No                                   | No                                        | Yes                                  |

Organizations should ensure they always have at least one user in the **Insider Risk Management** or **Insider Risk Management Admin** role groups (depending on the option they choose). By doing so, a company's insider risk management configuration won't get in a 'zero administrator' scenario if specific users leave the organization.

Members of the following roles can assign users to insider risk management role groups and have the same solution permissions included with the **Insider Risk Management Admin** role group:

 -  Azure Active Directory Global Administrator
 -  Azure Active Directory Compliance Administrator
 -  Microsoft Purview compliance portal Organization Management
 -  Microsoft Purview compliance portal Compliance Administrator

### Understand requirements and dependencies

Depending on how it plans to implement insider risk management policies, an organization must have the proper Microsoft 365 licensing subscriptions. It must also understand and plan for some solution prerequisites.

#### Licensing

Insider risk management is available as part of wide selection of Microsoft 365 licensing subscriptions. For details, see [Getting started with insider risk management](/microsoft-365/compliance/insider-risk-management-configure?azure-portal=true).

> [!IMPORTANT]
> Insider risk management is currently available in tenants hosted in geographical regions and countries supported by Azure service dependencies. To verify that insider risk management is supported for your organization, see [Azure dependency availability by country/region](/troubleshoot/azure/general/dependency-availability-by-country?azure-portal=true).

If an organization doesn't have an existing Microsoft 365 Enterprise E5 plan, but it wants to try insider risk management, it can add Microsoft 365 to its existing subscription or sign up for a trial of Microsoft 365 Enterprise E5.

#### Policy template requirements

Depending on the policy template that an organization chooses, there are requirements that it must understand and plan for prior to configuring insider risk management:

 -  **Data theft by departing users template**. A Microsoft 365 HR connector must be configured to periodically import resignation and termination date information for an organization's users. See the [Import data with the HR connector](/microsoft-365/compliance/import-hr-data?azure-portal=true) article for step-by-step guidance to configure the Microsoft 365 HR connector.
 -  **Data leaks templates**. At least one Microsoft Purview Data Loss Prevention (DLP) policy must be configured to define sensitive information in the organization and to receive insider risk alerts for High Severity DLP policy alerts. See the [Create, test, and tune a DLP policy](/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide) article for step-by-step guidance to configure DLP policies.
 -  **Security policy violation templates**. Microsoft Defender for Endpoint must be enabled for insider risk management integration in the Defender Security Center to import security violation alerts. For step-by-step guidance to enable Defender for Endpoint integration with insider risk management, see [Configure advanced features in Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features?azure-portal=true).
 -  **Disgruntled user templates**. A Microsoft 365 HR connector must be configured to periodically import performance or demotion status information for an organization's users. See the [Import data with the HR connector](/microsoft-365/compliance/import-hr-data?azure-portal=true) article for step-by-step guidance to configure the Microsoft 365 HR connector.

### Test with a small group of users in a production environment

Before an organization enables the insider risk management solution broadly in its production environment, it should consider testing the policies with a small set of production users while conducting for the necessary compliance, privacy, and legal reviews. Evaluating insider risk management in a test environment requires that you generate simulated user actions and other signals to create alerts for triage and cases for processing. This approach isn't practical for most organizations. As such, testing insider risk management with a small group of users in a production environment is preferred.

During testing, keep the anonymization feature in policy settings enabled. This setting will anonymize user display names in the insider risk management console during testing to maintain privacy within the tool. Doing so helps protect the privacy of users that have policy matches. It can also help promote objectivity in data investigation and analysis reviews for insider risk alerts.

If no alerts immediately appear after configuring an insider risk management policy, it may mean the minimum risk threshold hasn't been met yet. A good way to check if the policy is triggered and working as expected is to see if the user is in-scope for the policy on the **Users** page.
