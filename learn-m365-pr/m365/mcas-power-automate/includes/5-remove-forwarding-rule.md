Malicious inbox forwarding rules can be used to automatically forward confidential information. For example, an inbox rule could have been created to forward any emails containing the string "purchase order". The attacker could then approach prospective clients with slightly cheaper bids in the knowledge that they are undercutting your prices every time.

Microsoft Cloud App Security includes a policy that triggers an alert when suspicious inbox forwarding rules are set on a user's inbox, such as the following rule:

:::image type="content" source="../media/5-inbox-rule.png" alt-text="Inbox forwarding rule":::

To create a more sophisticated alert handling response, you can forward these alerts to Power Automate.

## Removing a malicious inbox forwarding rule using Power Automate

To remove a malicious inbox forwarding rule using Power Automate, perform the following steps:

1. Create a flow in Power Automate to handle the alert.

    :::image type="content" source="../media/5-power-automate-flow.png" alt-text="Power Automate flow":::

2. There are several key components for this flow:

    a. The flow is triggered by an alert from Microsoft Cloud App Security.

    b. Two variables store the Microsoft Cloud App Security tenant url and the API token value generated from the portal.

    c. User details are gathered from the alert.

    d. User manager is gathered from Office 365.

    e. Call the Microsoft Cloud App Security API to gather more information.

    :::image type="content" source="../media/5-get-mcas-alert.png" alt-text="Get MCAS Alert":::

    f. Parse the alert JSON.

    g. Filter the array to only have entities of type **ruleName**.

    h. Call Microsoft Graph to search in the user mailbox for inbox rules with a name that matches the name retrieved from the Microsoft Cloud App Security API.

    :::image type="content" source="../media/5-inbox-rule-id.png" alt-text="Get inbox rule ID":::

    i. Add a switch to look for a length greater than 0 to test whether a valid rule has been found.

    j. If a rule has been found, make an API call with a **PATCH** method to set the **isEnabled** value to **false**.

    :::image type="content" source="../media/5-switch.png" alt-text="Set isEnabled to False":::

    k. Finally resolve the Microsoft Cloud App Security alert and send an email to the user and their manager.

3. Enable the Microsoft Cloud App Security policy **Suspicious inbox forwarding**.
4. Edit the **Suspicious inbox forwarding** policy, select **Send alerts to Power Automate**, and select the Power Automate flow that you created to handle these alerts.

<!-- The following video gives you an overview of removing a malicious inbox forwarding rule using Power Automate:

THESE VIDEOS MUST BE HOSTED ON RED TIGER

WE NEED PERMISSIONS TO USE THESE VIDEOS

Add video: [(83) Auto-disable malicious inbox rules using MCAS & Power Automate - YouTube](https://www.youtube.com/watch?app=desktop&v=RapWRInUmHQ&feature=emb_title) -->
