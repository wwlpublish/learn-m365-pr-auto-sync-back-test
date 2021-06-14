No two organizations are the same, but there are similar situations that organizations may find themselves in when understanding and organizing their content.

For the Contoso Electronics company example, the documents and forms utilized may have variations across organizations, but they all contain similar properties and structures to the content other organizations are likely to use or experience.  

In this unit, you will learn about several use cases for SharePoint Syntex as experienced by Contoso Electronics, allowing you to determine when the features of Syntex are most applicable to your organization’s needs.

## When to use form processing models

Form processing models are created using AI Builder directly within the SharePoint document library where you want to apply the model. These models are most useful for structured or semi-structured documents that need to be organized and classified within your document library.

When considering Contoso Electronics, there are a wide variety of structured or “form-like” documents that may need to be organized and more easily located within a document library. For example, customer purchase orders would easily fall into this category. Customer purchase order forms are structured very similarly, requesting information such as name and address or more detailed information such as products ordered and installation requirements information.

![Example of a purchase order form with fields like “name” and “address” called out.]()

Invoices for goods and services would be another valuable structured document to evaluate using a form processing model. Within invoices, there are detailed control and routing information designated by similar field names. Information such as “Invoice Date” or “Account Number” could be crucial information to extract and make more readily available for customer service representatives assisting customers.

![Example of an invoice with “Invoice Date” and “Account Number” fields called out.]()

A form processing model would be appropriate for use in both situations, considering that form processing models will utilize the machine learning capabilities of AI Builder to automatically identify and extract the pre-designated fields from all your classified forms.

## When to use document understanding models

Different from form processing models, document understanding models should be applied to unstructured documents, such as letters or contracts. Document understanding models also automate content understanding using the power of AI and machine learning, but this is done within the content center, not AI Builder.

An example of content that Contoso Electronics could use with document understanding models are sales letters sent to customers. While many companies deal with a high volume of forms, there will also be less structured documents, such as letters detailing proposed delivery and cost of goods and services, or sales contracts that Contoso Electronic’s management and legal teams will need to review.  

Document understanding models can be used to automate the classification of these letters and the extraction of the values you and your team designate for removal. Values in the letters such as when it was dated or the department it is addressed to can help streamline processing these documents, ensuring they reach the right internal teams and are processed in a timely manner.  

![Example of a sales contract, including fields such as “Date” and “Department” called out.]()

## Identify which type of model to use

Here are some questions you can ask to better pinpoint which model works best for the type of content you want to classify and organize within your document library.

- What is the document type?
  - Document understanding model: Unstructured documents, such as letters or contracts
  - Form processing model: Structured and semi-structured documents, such as applications, forms, or invoices
- Where should you create the model?
  - Document understanding model: In the SharePoint content center, automatically making it a part of your SharePoint Content Types gallery
  - Form processing model: Directly in the SharePoint document library that form processing has been enabled for, specifically using the AI Builder option in the document library
- Where should you apply the model?
  - Document understanding model: After being created in the content center and added as a content type, document understanding models can be applied to any SharePoint document library that you have access
  - Form processing model: Form processing models also create a ‘new’ content type within your Content Types gallery, but they can only be applied to the original SharePoint document library where the model was created
