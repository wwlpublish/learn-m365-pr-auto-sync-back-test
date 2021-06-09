For each rule in a DLP policy, policy tips can be configured to:

 -  **Notify the person that the content conflicts with a DLP policy.** This message will enable the user to take action to resolve the conflict. You can use the default text (see the tables below) or enter custom text about your organization's specific policies.<br>
 -  **Allow the person to override the DLP policy.** You can optionally:<br>
    
     -  Require the person to enter a business justification for overriding the policy. This information is logged and can be viewed in the DLP reports that appear in the Reports section of the Security and Compliance Center.<br>
     -  Allow the person to report a false positive and override the DLP policy. This information is also logged for reporting. By logging this information, organizations can use false positives to fine-tune their DLP rules.<br>

:::image type="content" source="../media/user-override-for-policy-tips-bc5d889d.png" alt-text="screenshot of the SCC window for entering user override messages in a DLP policy rule":::


### Example scenario

Let's look at an example as to how an organization creates rules to govern the use of policy tips. Each rule consists of conditions and actions. If the conditions are true, the actions are performed. In this case, Contoso has created a DLP policy that applies to its OneDrive for Business sites. The policy detects personal information, and Contoso has configured the policy to include the following rules:

 -  **Rule \#1 - Send a notification.**
    
     -  Conditions (boolean And):
        
         -  Fewer than five instances of this sensitive information are detected in a document.
         -  The document is shared with people inside the organization.<br>
     -  Actions:
        
         -  The **Send a notification** action displays a policy tip.

> [!NOTE]
> For policy tips, no override options are necessary because this rule is just notifying people and not blocking access.<br>

 -  **Rule \#2 - Block access with override option.** 
    
     -  Conditions (boolean And):
        
         -  Greater than five instances of this sensitive information are detected in a document.<br>
         -  The document is shared with people inside the organization.
     -  Actions:
        
         -  The **Block access to content** action restricts the permissions for the file.
         -  The **Send a notification** action allows users to override the actions in this rule by providing a business justification.

> [!NOTE]
> An organization's business sometimes requires internal people to share personal data. In these instances, organizations don't want their DLP policy to block the work.<br>

 -  **Rule \#3 - Block access with no override option.** 
    
     -  Conditions (boolean And):
        
         -  Greater than five instances of this sensitive information are detected in a document.
         -  The document is shared with people outside the organization.
     -  Actions:
        
         -  The **Block access to content** action restricts the permissions for the file.
         -  The **Send a notification** action doesn't allow people to override the actions in this rule because the information is shared externally.

> [!IMPORTANT]
> Under no circumstances should people in your organization be allowed to share personal data outside the organization.<br>

### Considerations when overriding a rule

Organizations should consider the following issues when using a policy tip to override a rule:

 -  **The override option is on a per-rule basis.** The override option overrides all of the actions in the rule, except sending a notification. Sending a notification can't be overridden.<br>
 -  **Content matches several rules.** It's possible for content to match several rules in a DLP policy. When this situation occurs, only the policy tip from the most restrictive, highest-priority rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that just sends a notification. This scenario prevents people from seeing a cascade of policy tips.<br>
 -  **Overriding the most restrictive rule.** If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules the content matched.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”