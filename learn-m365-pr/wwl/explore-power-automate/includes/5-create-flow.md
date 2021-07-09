Power Automate enables users to create a flow from the browser, their phone, or from within Microsoft Teams.

 -  To create a flow from a browser, the user must log into [flow.microsoft.com](https://flow.microsoft.com/?azure-portal=true).
 -  To create a flow from a phone, the user must download and run the Power Automate mobile app on the phone.
 -  To create a flow a flow from a Teams channel, the user must first add a tab, then choose Flow and save it. This installs Flow, which is necessary for users to create a flow within Teams.

When creating a flow, users can start from one of three scenarios that are available within Power Automate:

 -  **From blank.** Starting from scratch, users can create a custom flow to meet their needs.
 -  **From a template.** Power Automate offers hundreds of predefined templates that make getting started easy; plus, the templates are customizable and can be tailored to meet an organization’s business requirements.
 -  **From a connector.** The user starts with services and applications that they're familiar with (such as Outlook, SharePoint, and OneDrive) and links them together to automate tasks.

### Building a flow

This section focuses on the steps and components available when using a browser to build an automated flow from blank. The approach and concepts described in this section are consistent for the different types of flows.

 -  **Triggers.** All flows require a trigger to start. With an automated flow, the user is presented with the various triggers supported by the different connectors. During the build process, the user may be prompted to authenticate with the connector and to select various parameters associated with the chosen trigger. For example, selecting the trigger “when a file is created in a folder” for the SharePoint connector prompts the user to enter the SharePoint site address and the folder name.
 -  **Actions.** When a user creates a flow, they must define the steps the flow will complete. Within each step, they must select the action(s) to be completed within that step. The list of available actions the user can choose from depends on the actions supported by the available connectors, controls, data operations, variables, and so on. For example, the user can add an action to send an email using Outlook 365. Once the action is selected, the user is prompted for any information needed to execute the action. When sending an email, the user must specify the email address, subject, the contents for the body of the email, attachments, and so on. ‎
 -  **Dynamic content.** When configuring an action, Power Automate gives users the option to create expressions and add dynamic content from the apps and connectors already being used in the flow. For example, when sending an email, Power Automate can include in the body of the email the content from the SharePoint connector that was used in the trigger, such as the Content type, File name, and so on. If the dynamic content isn't immediately displayed, the user can search for it. Included in the set of actions are controls, which include “do until” loops, “apply to each”, “condition” statements, and more.
 -  **Peek code.** This feature is popular with experienced developers, since it displays other options, including peek code. Peek code includes the full JSON representation of an action.
 -  **Functions.** Power Automate supports various functions that can be used within expressions, including string functions, logical comparison functions, collection functions and more. For more information, see the [reference guide to using functions in Azure Logic Apps and Power Automate](/azure/logic-apps/workflow-definition-language-functions-reference) for more information.
 -  **Advanced functionality.** Advanced functionality is available when building workflows include the use of solutions to host flows for portability between environments, as well the use of AI builder. AI Builder allows users to incorporate published AI models in Power Automate with manually triggered flows embedded in a solution. For more information on these advanced features, see the [Solutions overview](/power-automate/overview-solution-flows) and [Use AI Builder in Power Automate](/ai-builder/use-in-flow-overview).

The Power Automate Designer is a feature-rich tool that enables users to configure every detail of flow logic. Sometimes, users may want to sketch the flow before they start to build it. To sketch a flow, users can start Microsoft Visio directly from within Power Automate by selecting Visio from the templates option. For more information, see [Design flows in Microsoft Visio](/power-automate/visio-flows).

Once the user has competed adding steps to the flow and saved it, the flow can be checked for errors and tested. The Flow Checker checks for any errors or warnings in your flow and calls out the actions where the errors or warnings occur.

Power Automate also enables users to test the flow. For example, with an automated flow, users can complete the trigger action to test the flow. When doing so, Power Automate displays the status of each step in the flow. Expanding each action on the flow provides more detailed information on the execution of the step. With a successfully tested flow, users can share and run their apps.
