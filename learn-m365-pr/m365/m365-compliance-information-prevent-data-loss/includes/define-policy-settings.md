There are two different workflows when you define policy settings: simple and advanced. The simple workflow starts if you choose the **Review and customize default settings from the template** option on the **Define policy settings** page. The more advanced flow is initiated if you choose **Create or customize advanced DLP rules**. 

## Simple workflow
The simple workflow lets you quickly:
- Specify the sensitive info types or labels you want to protect.
- Decide whether you want the policy to detect when the content is shared inside or outside your organization.
- Set up actions like access restrictions and user and admin notifications. 

Select this option if you want to quickly set up a policy that protects content based only on the sensitive information types from the policy template selected earlier. 

## Advanced workflow
The advanced workflow uses a rule editor to extend the options offered in the simple flow. You can use the advanced flow to refine the policy using rules that include more conditions, exceptions, and actions. The advanced workflow branch is also the only option available if Custom is selected during the Choose locations to apply the policy step. 

The image below shows the two workflow branches. Notice in the simple branch, listed first, the three sensitive information types that were inherited from the selection of the **U.K. Financial Data** policy template in the **Choose information to protect** step. We're going to use the advanced option in our examples, so the image shows Create or customize advanced DLP rules has been selected.

:::image type="content" source="../media/define-policy-settings.png" alt-text="A screenshot shows the Define policy settings page of the DLP solution, with the choice to Create or customize advanced DLP rules selected.":::

### Customize advanced DLP rules
Two rules will already be defined if you select a policy template in the Choose the information to protect step and selected the advanced DLP rules workflow branch. It will be up to you to define your own rules from scratch if you select the Custom option. Whatever the case in your situation you can edit any existing rules, delete them, or create completely new ones. The only requirement is you must have defined at least one rule before you can move to the next step in the process.

Using the **U.K. Financial Data** policy template we started with earlier, the image below shows a summary of the two default rules associated with this DLP policy. One rule is for detecting a low volume of content and a second rule is for detecting a high volume of content. Notice in the image below the Actions listed in the two rules are different. One set of actions is defined for when a low volume of content is detected, and a different set of actions is defined for when a high volume of data is detected. This allows you to respond differently based on the seriousness of the policy violation. For example, sending an email that includes one to two credit card numbers might be deemed acceptable and addressed with a simple warning to the user, while sending one with 1,000 credit card numbers may be considered a critical security breach and call for a different response entirely. It is up to your organization to decide how to respond and configure the DLP policy rules accordingly.
 
:::image type="content" source="../media/define-policy-settings.png" alt-text="A screenshot shows the Define policy settings page of the DLP solution, with the choice to Create or customize advanced DLP rules selected.":::

Edit rule
You can add additional rules or edit the rules that came with the DLP policy template. Each DLP policy rule can be edited. Even the default rules should be reviewed to determine they meet your requirements. Rules can include:
•	Conditions. Determine what types of information you are looking for, and when to take an action.
•	Exceptions. Prevents the application of a rule for content matching the exceptions. 
•	Actions. When content matches a condition in a rule, you can apply actions to automatically protect the content.
•	User notifications. Use notifications to educate your users about DLP policies and help them remain compliant without blocking their work.
•	User overrides. Allows the user to override the policy and share the content.
•	Incident reports. When a rule is matched, you can send an incident report to your compliance officer (or any people you choose) with details of the event.
•	Options. Provide more options to specify how the DLP policy is processed.
Conditions
The image below shows the Conditions section of the High volume of content detected U.K. Financial rule. Each condition shown is using the default settings from the policy template. The Content contains condition is relevant to all locations. By default, it looks for any of the three sensitive info types listed that exceed an instance count of 10. Additional sensitive info types can be added, and other changes can be made including changing the lower and upper threshold for the instance count. 
The second condition shown in the image, Content is shared from Microsoft 365, only applies to content shared from Exchange, SharePoint, OneDrive, and Microsoft Teams. It does not apply to the Windows 10 devices or Cloud App Security locations. 
 
Actions
The image below shows a modified Actions section of the High volume of content detected U.K. Financial rule. By default, users are blocked from sending email and Teams chats and channel messages that contain the type of content you are protecting outside the organization. The first action, enabled by default in this rule, Restrict access or encrypt the content in Microsoft 365 locations, adds files stored in SharePoint, OneDrive, and Teams to the locations where sharing is blocked. 
The second action, Audit or restrict activities on Windows devices, is not included by default. It has been added to restrict activities on Windows devices. When the activities listed are detected on Windows devices for supported files containing sensitive info that matches this policy's conditions, you can choose to do any of the following:
•	Audit the activity only
•	Block the activity entirely
•	Block the activity but allow users to override the restriction
The ability to audit or restrict activities on Windows devices is part of the functionality referred to as endpoint data loss prevention. In our example, we have chosen the option to block each type of endpoint activity, like printing and copying sensitive data to the clipboard, but allow it to be overridden by the user.
 
User notifications and overrides
The image below shows the default settings for the User notifications section of the High volume of content detected U.K. Financial rule. User notifications take the form of emails and/or policy tips designed to educate users on the proper use of sensitive information. There may be occasions where you want to notify someone else besides the user and/or customize the message or policy tip that is displayed. You have flexibility in deciding who is informed about the incident and how they are notified. 
 
User overrides are disabled by default for the High volume of content detected U.K. Financial rule but have been enabled in the image below. Options include requiring the user to enter a business justification when overriding the policy and/or allowing the policy to be overridden if the user reports it as false positive. Both options have been selected. The settings in this section are not relevant to Windows 10 devices as the override settings for Windows devices are configured under the Actions section in the rule editor.
 
Incident reports
When a rule is matched, different types of incident reports can be generated to make those with administrative or oversight responsibilities aware. You can send an incident report to your compliance officer, or anyone you choose, with details of the event. As with user notifications you have several options. In this example we have elected to both Send an alert to admins when a rule match occurs and Use email incident reports when a policy match occurs with a severity level of High. We can also see in the screen shot below the option to send the alert only when the volume of activity reaches a specified instance or volume threshold. 

