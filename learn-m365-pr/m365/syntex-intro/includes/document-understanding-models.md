SharePoint Syntex is made up of two main features that make it a service for content understanding, processing, and compliance:

1. Document understanding models  
1. Form processing models

Contoso Electronics needs a clear understanding of documents such as sales letters. To process these kinds of documents and extract knowledge from them, you will need to use the SharePoint content center to build document understanding models, which include features such as retention labels, classifiers, and extractors to produce the outcomes Contoso wants to organize its document libraries.

Here, you will learn what the parts of document understanding models are so you can understand how they work together for clearer knowledge gathering and processing in your document libraries.

## What is a document understanding model?

A document understanding model uses AI to automatically classify documents within a SharePoint document library and, if you so choose, to extract specific information from these documents. Document understanding models are created in the content center and classify and extract information from _unstructured_ documents.

For Contoso Electronics, unstructured documents may include product testing reports, project documents, or any text-based content lacking the specific structure of a form.

![A picture of a sample business letter with key fields highlighted for Document understanding model processing in SharePoint Syntex.](../media/document-example.png)

### What is a content center?

Content centers are a special SharePoint site that allows you to create, train, and manage models. The content center is not only create your document understanding models, but also where you can view and track which models are applied to which document libraries.

A default content center is created during the SharePoint admin setup process, but admins can create additional content centers as it makes sense for your organization. Contoso Electronics has many departments that require different documents and different models. For example, there is a Human Resources department that deals directly with employee relations, as well as another team focused on sales. For privacy and security compliance reasons, these two departments probably shouldn’t share a content center.  As a result, your company admin may want to create different content centers to house each of their unique models.

Content centers offer you control and clear insight into your content. Your content centers give you the power to ensure proper governance throughout your data by helping you establish the processes that adhere to the necessary compliance and security standards in your business.

![A screenshot of the Content center with the Model creation page and Model monitoring & management options in the page.](../media/content-center.png)

### What is a classifier?

Classifiers are a type of document understanding model that identify the document _type_ in your SharePoint document library and then classify it accordingly.

At Contoso Electronics, there are several classifier models you may want. You could create a classifier model that identifies government letters, or you could also create a classifier model specifically for sales letters.

### What is an extractor?

An extractor is _part_ of a document understanding model that pulls the information from your documents. You can create an extractor before or after you’ve created your document understanding model.

For example, at Contoso Electronics, if you’ve already created a document understanding model that classifies all of your sales letters as such, you may realize later on that it would be helpful to easily extract and see when the letter was dated, allowing you to archive some letters and more quickly address others. You can create an extractor for _'Date Sent'_ so the model can analyze the documents for the “date sent” field that you identify, then placing this value into a column for each of your documents in the SharePoint document library.

### What is a sensitivity label?

Sensitivity labels let you apply encryption, sharing, and conditional access policies to the documents that your models identify. For example, you want your model to not only identify financial documents that contain bank account numbers or credit card numbers that are uploaded to your document library, but also to apply an _Encryption_ sensitivity label to them to restrict who can access that content. SharePoint Syntex models honor the label order rules and do not overwrite an existing label that was manually applied by a user to the file.

> [!NOTE]
> At this time, sensitivity labels are available only for document understanding models. Support for sensitivity labels for form processing will be available shortly.

### What are retention labels?

Retention labels give you the option to apply retention settings to your documents. Retention settings are policies defining how documents are kept or deleted. Retention labels enforce who may delete documents and when they may delete them. They are created in the Microsoft 365 compliance center but will appear as part of the Compliance section of your model once they’re created in the compliance center.

Retention labels can be particularly helpful when dealing with any sensitive information within your SharePoint document library that should be retained for records purposes. For instance, at Contoso Electronics, there may be letters received from the government regarding regulatory standards and compliance requirements. A retention label titled _'Legal'_ could be added to these documents to ensure any document with this label is never deleted and is retained in your library forever. That way, if a team member attempts to delete the labeled document at some point, they won’t be able to.

### What is an explanation?

An explanation is _part_ of your classifier model or extractor. An explanation is used to describe the value for what will either be classified or what will be extracted.

Explanations types include:

- Phrase list – Words, phrases, numbers, or patterns that are part of the document type
  - Example – When processing sales contracts at Contoso Electronics, this could be a text string such as _'Requester Company Type'_, which would allow you to easily pull and analyze the industries your company is successfully selling.
- Proximity – How close one phrase is to another
  - Example – If _'Requester Company Type'_ and _'Date Sent'_ are always within a certain distance from each other, then this can be defined by a proximity explanation.

## How do the parts of the document understanding model work together?

When creating a document understanding model, it helps to understand how each of the parts flow into one another and inform each other.

- **Content center** – This is where you’ll begin, considering it’s the point where you will create your model. Either a default content center will be used, or an admin will need to create others as your business sees fit.
- **Classifier** – This is the document understanding model type you’ll create within the content center.
- **Extractor** – Creating an extractor is not mandatory. It can be created before or after you build your document understanding model. If you already know the information that you want to extract, create the extractor beforehand, or, if you don’t, wait until you have a better understanding of your model.
- **Sensitivity label** - Sensitivity labels can be used to apply encryption, sharing, and conditional access policies to documents.
- **Retention label** – This is optional but can be applied to any document understanding model. It can even be added to a document library that has already had the document understanding model applied.
- **Explanation** – Explanations are part of your classifier model and must be included so that the model knows exactly what it’s looking for and how it’s classifying the documents.
