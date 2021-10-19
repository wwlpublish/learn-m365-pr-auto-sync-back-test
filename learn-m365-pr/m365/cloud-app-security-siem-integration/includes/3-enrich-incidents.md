Azure Sentinel playbooks can call APIs to gather additional information about an alert. For example, an Azure Active Directory API could gather user information, an Azure Active Directory Identity Protection API could provide data to assess if the user is at risk, and a Microsoft Defender API could provide information about computers that the user uses.

The information that is gathered from the APIs is aggregated into a JSON file. This JSON file is the returned to the original Azure Sentinel playbook. The playbook can then perform more steps such as storing the JSON in Log Analytics, for future investigation, and sending the data to the Azure Sentinel incident comments. There are many other steps that this process can perform because it uses industry-standard http endpoints and JSON files.

For an in-depth demonstration of enriching incidents in Azure Sentinel with playbooks, follow the Azure Sentinel entities enrichment video link in the **Summary** unit of this module.
