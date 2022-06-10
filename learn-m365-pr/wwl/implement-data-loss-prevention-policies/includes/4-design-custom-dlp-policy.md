Taking the time to design a DLP policy before you implement it will get you to the desired results faster, and with fewer unintended issues, than creating it and then tuning by trial and error alone. Having your policy designs documented will also help you in communications, policy reviews, troubleshooting, and further tuning.

Designing a DLP policy typically involves:

 -  Clearly defining your business needs.
 -  Documenting them in a policy intent statement.
 -  Mapping those needs to your policy configuration.

You'll use the decisions you made in your planning phase to inform some of your policy design decisions.

### Define intent for the DLP policy

An organization should be able to summarize in a single statement the business intent for every DLP policy. Developing this statement will drive conversations about the policy throughout the organization. When the statement is fully fleshed out, it will directly link the policy to a business purpose and provide a roadmap for policy design.

**Additional reading**. For help on getting started on your DLP policy intent statement, see [Plan for data loss prevention (DLP)](/microsoft-365/compliance/dlp-overview-plan-for-dlp?azure-portal=true).

Earlier in this training, you learned that all DLP policies require that an organization:

 -  Choose what it wants to monitor.
 -  Choose where it wants to monitor.
 -  Choose the conditions that must be matched for a policy to be applied to an item.
 -  Choose the action to take when the policy conditions are met.

For example, here's a fictitious first draft of an intent statement that provides answers to all four questions for Contoso Ltd.:

*"Contoso is a U.S. based organization, and we need to detect Office documents that contain sensitive health care information covered by HIPPA that are stored in OneDrive/SharePoint and protect against that information being shared in Teams chat and channel messages and restrict everyone from sharing them with unauthorized third parties".*

As an organization develops its policy design, it will likely modify and extend the statement.

### Map business needs to policy configuration

To map business needs to policy configuration, an organization should begin by breaking the draft down into shorter segments. It can then map each segment to DLP policy configuration points.

The following table maps the business needs of Contoso's fictitious first draft statement to its policy configuration.

| **Statement**                                                                                                                                    | **Configuration question answered and configuration mapping**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "Contoso is a U.S. based organization, and we need to detect Office documents that contain sensitive health care information covered by HIPPA... | - **What to monitor**: Office docs, use the U.S. Health Insurance Act (HIPAA) template.<br>\- **Conditions for a match**: (preconfigured but editable) - item contains U.S. SSN and Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), content is shared with people outside my organization<br>\- drives conversations to clarify the triggering threshold for detection like confidence levels, and instance count (called leakage tolerance). |
| ...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages...                   | - **Where to monitor**: Location scoping by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups.                                                                                                                                                                                                                                                                                                                                                                                       |
| ...and restrict everyone from sharing those items with unauthorized third parties."                                                              | - **Actions to take**: You add *Restrict access or encrypt the content in Microsoft 365 locations*<br>\- drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action.                                                                                                                                                                          |

This example doesn't cover all the configuration points of a DLP policy. A real-world statement would need to be expanded. However, it should get you thinking in the right direction as you develop your own DLP policy intent statements.

> [!IMPORTANT]
> Keep in mind that the location(s) you pick effect whether you can use sensitive information types, sensitivity labels, and retention labels, as well as the actions that are available.

### Policy Design Process

1.  Complete the steps in the prior unit on how to [Plan for data loss prevention](/microsoft-365/compliance/dlp-overview-plan-for-dlp?azure-portal=true). When planning for DLP, remember to:
     -  Identify your stakeholders.
     -  Describe the categories of sensitive information to protect.
     -  Set goals and strategy.
     -  Define your policy deployment plan.
2.  Familiarize yourself with [Data Loss Prevention policy reference](/microsoft-365/compliance/dlp-policy-reference?azure-portal=true) so that you understand all the components of a DLP policy and how each one influences the behavior of a policy.
3.  Familiarize yourself with [What the DLP policy templates include](/microsoft-365/compliance/what-the-dlp-policy-templates-include?azure-portal=true).
4.  Develop your policy intent statement with your key stakeholders. Refer to the example earlier in this article.
5.  Determine how this policy fits into your overall DLP policy strategy.
    
    > [!IMPORTANT]
    > Policies can't be renamed once they're created. If you must rename a policy, you'll have to create a new one with the desired name and then retire the old one. So decide on the naming structure that all your policies will use now.
6.  Map the items in your policy intent statement to configuration options.
7.  Decide which policy template you will start from, predefined or custom.
8.  Go through the template and assemble all information required before you create the policy. It's likely that you will find that there are some configuration points that aren't covered in your policy intent statement. That's ok. Go back to your stakeholders to iron out the requirements for any missing configuration points./li&gt;
9.  Document the configuration of all the policy settings and review them with your stakeholders. You can re-use your policy intent statement mapping to configuration points, which is now fully fleshed out.
10. Create a draft policy and refer back to your policy deployment plan.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”