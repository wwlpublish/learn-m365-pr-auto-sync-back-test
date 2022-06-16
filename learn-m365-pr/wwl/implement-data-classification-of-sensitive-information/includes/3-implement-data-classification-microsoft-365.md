Data classification in Microsoft 365 scans an organization's sensitive content and labeled content before the organization creates any policies. This process is called zero change management. It enables an organization to see the effect that all the retention and sensitivity labels are having in its environment. It also empowers the organization to start assessing its protection and governance policy needs.<br>

The data classification features in Microsoft 365 help an organization gain insight into what's being classified. By doing so, the organization can establish the policies it needs to protect and govern its sensitive data. As a Microsoft 365 administrator or compliance administrator, you can evaluate and then tag content in your organization. As such, you can:

 -  control where it goes.
 -  protect it no matter where it is.
 -  ensure that it's preserved and deleted according to your organization's needs.

Tagged content is evaluated through the application of sensitivity labels, retention labels, and trainable classifiers. There are various ways to do the discovery, evaluation, and tagging. The end result is that an organization may have large numbers of documents and emails that are tagged and classified with one or more of these labels. After an organization applies its retention and sensitivity labels, it will want to see how the labels are being used across its tenant, and what's being done with those items.

### Data classification in the Microsoft Purview compliance portal

In Microsoft 365, visibility into tagged content is provided on the **Data classification** page in the Microsoft Purview compliance portal. This page provides visibility into:

 -  the number items that have been classified as a sensitive information type and what those classifications are
 -  the top applied sensitivity labels in both Microsoft 365 and Azure Information Protection
 -  the top applied retention labels
 -  a summary of activities that users are taking on your sensitive content
 -  the locations of your sensitive and retained data

You can also manage the following compliance features on the **Data classification** page:

 -  Trainable classifiers
 -  Sensitive information types
 -  Exact data match-based sensitive information types
 -  Content explorer
 -  Activity explorer

Data classification in Microsoft 365 scans an organization's sensitive content and labeled content before the organization creates any policies. This process is called zero change management. It enables an organization to see the effect that all the retention and sensitivity labels are having in its environment. It also empowers the organization to start assessing its protection and governance policy needs.

Once an organization has developed its data classification framework, its next step is implementation. The Microsoft Purview compliance portal enables administrators to discover, classify, review, and monitor their data in accordance with their data classification framework. Sensitivity labels can be used to help an organization protect its data. It does so by enforcing various protections, such as encryption and content marking. They can be applied to data manually, by default based on policy settings, or automatically, as the result of a condition such as personal user information.<br>

For smaller organizations or organizations with a relatively streamlined data classification framework, creating a single sensitivity label for each of their data classification levels may suffice. The following example shows a one-to-one data classification level to sensitivity label mapping:

| **Classification label** | **Sensitivity label** | **Label settings**          | **Published to** |
| ------------------------ | --------------------- | --------------------------- | ---------------- |
| Unrestricted             | Unrestricted          | Apply 'Unrestricted' footer | All users        |
| General                  | General               | Apply 'General' footer      | All users        |

> [!TIP]
> During a Microsoft internal information protection pilot, there were difficulties with the understanding and use of the 'Personal' label. Users were confused as to whether this meant PII or merely related to a personal matter. As such, the label was changed to 'non-business' to be clearer. This example shows that taxonomy doesn't need to be perfect from the start. Start with what you think is right, pilot it, and adjust the label based on feedback if needed.<br>

Larger organizations with a global reach or more complex information security needs may find this one-to-one relationship between the number of classification levels in their policies and the number of sensitivity labels in their Microsoft 365 environment to be a challenge. This challenge is especially true in global organizations where a given data classification level such as 'Restricted' may have a different definition or a different set of controls depending on region.

### Microsoft Purview Data classification

Data classification features in Microsoft 365 are located in the Microsoft Purview compliance portal. When an organization selects **Data classification** on the compliance portal's navigation pane, the **Data classification** page that's returned will help it discover, classify, review, and monitor sensitive and business-critical data.

The **Data classification** page is organized into the following tabs:

 -  **Overview**. This tab displays information that shows how sensitive info and labels are being used across an organization. You can view insights like:
     -  top sensitive info types.
     -  how many items contain each type.
     -  an overview of the top classification activities detected across Microsoft 365 locations.
     -  the top sensitivity and retention labels applied to content.
 -  **Trainable classifiers**. An organization can use this tab to refine its classification strategy by defining new categories of sensitive information and content. Trainable classifiers use machine learning to help identify categories of content in an organization. Microsoft provides built-in classifiers for identifying common content types like Resume and Source Code, and offensive language like profanity and threats. These classifiers are ready to use in compliant solutions like retention labels, sensitivity labels, and communication compliance. If the built-in classifiers don't meet an organization's needs, it can create custom ones to identify specific types of content, such as company contracts. After an organization creates a custom classifier, it will train the classifier to improve accuracy until it's ready to be published for use in its compliance solutions.
 -  **Sensitive info types**. Besides trainable classifiers, an organization can also use sensitive information types to help refine its classification strategy. Sensitive information types are used to help identify sensitive items so that you can prevent them from being inadvertently or inappropriately shared. They can also be used to help locate relevant data in eDiscovery, and to apply governance actions to certain types of information. For example, they can be used to classify and protect information such as credit card and bank account numbers. Microsoft provides many built-in types for detecting sensitive info spanning regions around the globe. Alternatively, an organization can also create custom types tailored to its sensitive information. You define a custom sensitive information type (SIT) based on:
     -  patterns
     -  keyword evidence such as employee number, social security number, or ID
     -  character proximity to evidence in a particular pattern
     -  confidence levelsExact data matches
 -  **Exact data matches**. What should an organization do if it wants a custom sensitive information type that uses exact or nearly exact data values, instead of one that found matches based on generic patterns? Exact Data Match (EDM)-based classification enables organizations to create custom sensitive information types that refer to exact values in a database of sensitive information. The database can be refreshed daily, and contain up to 100 million rows of data. So as employees, patients, or clients come and go, and records change, an organization's custom sensitive information types remain current and applicable. It can also use EDM-based classification with policies, such as Microsoft Purview Data Loss Prevention policies or Microsoft Cloud App Security file policies. With EDM-based classification, an organization can create a custom sensitive information type that's designed to:
     -  be dynamic and easily refreshed.
     -  be more scalable.
     -  result in fewer false-positives.
     -  work with structured sensitive data.
     -  handle sensitive information more securely, not sharing it with anyone, including Microsoft.
 -  **Content explorer**. An organization can use Content explorer to review how many items contain sensitive information types, and how many items have sensitivity labels or retention labels applied. To review specific items, drill down by selecting the information type or label, and opening the location where the item's stored. You can also use the **Search** feature to quickly find specific locations until you see the list of email and documents with that information or label. Use Search again to find items based on their name, file type, and more. The Search feature also displays quick insights into the sensitive information types within an item, such as how many instances there are and their confidence level. An organization can go deeper by opening the source content. Doing so enables it to review the sensitive information and context, and the file's metadata. Organizations can then export the results to an Excel spreadsheet containing details like file names and their sensitive info types and applied labels.
 -  **Activity explorer**. Organizations can use Activity explorer to review classification activity across locations. For example, which labels were changed, and which files were modified. Activity can be filtered by date range, activity type, location, user, sensitivity label, and even more using the Filter menu. The historical chart organizes recent activity by color. Hover over a column to see how many instances occurred that day. Scroll through the complete list of each activity logged across Microsoft 365 locations and devices. Then select an activity to review more detail. An organization can also customize the list to show the data that best suits its administrative needs.

Sensitive data is created and shared daily, so discovering, classifying, and reviewing it should be an ongoing process. Organizations should monitor the **Overview** tab to discover new insights to help ensure data is being detected, protected, and governed appropriately.
