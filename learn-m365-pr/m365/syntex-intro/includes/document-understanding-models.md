Syntex is made up of two main features that make it a service for content understanding, processing, and compliance:

1. Document understanding models  
1. Form processing models

At Contoso Electronics, your organization will need to have clear understanding of documents such as sales letters. To process these kinds of documents and extract knowledge from them, your organization will need to use the SharePoint content center to build document understanding models, which will include features such as retention labels, classifiers, and extractors to produce the outcomes your organization wants for organizing its document libraries.

Here, you will learn what the parts of document understanding models are so you can understand how they all work together for clearer knowledge gathering and processing in your document libraries.  

## How does content understanding inform document understanding models?

We’ve already touched a bit on content understanding as the basis of Syntex and the motivation for document understanding models. Content understanding is the ability to identify and classify documents that are a part of your SharePoint document libraries, allowing you to extract information from these files.

For Contoso Electronics, an example of content understanding would be to properly identify all the sales letters as the right document type. Then, if you want to pull out when these letters were dated, you can extract this information and add it as a column in your document library.

Content understanding is what sets you up to create document understanding models by classifying and extracting the data using the AI guidelines you set.  

## What is a document understanding model?

A document understanding model uses AI to automatically classify your documents within a SharePoint document library and, if you so choose, to extract specific information from these documents.  

Document understanding models are created in the content center and will classify and extract information from unstructured documents.  

For Contoso Electronics, an unstructured document may be product testing reports, project documents, or anything that is more of a block of text as opposed to a form with a very specific structure.  

![A report with several blocks of text and a few key phrases highlighted, such as the date and name.]()

## What is a content center?

You should think of the content center as the hub for your document understanding models. This is where you not only create your document understanding models, but also view and track which models are applied to which document libraries.

A default content center is created during the SharePoint admin setup process, but admins can create additional content centers as it makes sense for your organization. When considering Contoso Electronics, there is most likely an internal team that deals directly with client relations, as well as another team focused on sales. The company has many departments which may require different documents and different models. As a result, your company admin may want to create different content centers to house each of their unique models.

![Image of example content center.]()

## What is an extractor?

An extractor is what pulls the information out of your document understanding model. You can create an extractor before or after you’ve created your document understanding model.  

For example, at Contoso Electronics, if you’ve already created a document understanding model that classifies all of your sales letters as such, you may realize later on that it would be helpful to easily extract and see when the letter was dated, allowing you to archive some letters and more quickly address others. You can create an extractor for Date Sent so the model can analyze the documents for the “date sent” field that you identify, then placing this value into a column for each of your documents in the SharePoint document library.

## What is a retention label?

Retention labels are also optional for document understanding models. They are originally created in the Microsoft 365 Compliance Center but will appear as part of the Security and compliance section of your model once they’re created in the Compliance Center.  

These labels can be particularly helpful when dealing with any sensitive information within your SharePoint document library that should be retained for records purposes. For instance, at Contoso Electronics, there may be letters received from the government regarding standards compliance requirements. A retention label titled Legal could be added to these documents to ensure any document with this label is never deleted and is retained in your library forever. That way, if a team member attempts to delete the labeled document at some point, they won’t be able to.

## What is a classifier?

Unlike extractors, which are applied to your model, classifiers are a type of document understanding model that will identify the document type in your SharePoint document library and then classify it accordingly.

With Contoso Electronics, there are several classifier models you may want. You could create a classifier model that identifies government letters and is called such, or you could also create a classifier model specifically for sales letters.

## What is an explanation?

An explanation is part of your classifier model and extractors. This is how you define the value for what will either be classified or what will be extracted.

Explanations come in three main types:

- _Phrase list_ – Words, phrases, numbers, or other characters that are part of the document type
  - Example – When processing sales contracts at Contoso Electronics, this could be a text string such as Requester Company Type so you can easily pull and analyze the industries your company is successfully selling into.
- _Pattern list_ – Patterns of numbers, letters, or other characters that are part of the document type
 - Example – Going back to our Date Sent example for Contoso Electronics, a pattern list would be the explanation type when defining the extractor for the date field that you want to extract.
- _Proximity_ – How close the phrase or pattern lists are to one another
 - Example – If Requester Company Type and Date Sent are always within a certain distance from each other, then this can be defined by a proximity explanation.

## How do the parts of the document understanding model work together?

When creating a document understanding model, it helps to understand how each of the parts flow into one another and inform each other.  

- **Content center** – This is where you’ll begin, considering it’s the point where you will create your model. Either a default content center will be used, or an admin will need to create others as your business sees fit.

- **Classifier model** – This is the document understanding model type you’ll create within the content center.

- **Explanations** – Explanations are part of your classifier model and must be included so that the model knows exactly what it’s looking for and how it’s classifying the documents.

- **Extractor** – Creating an extractor is not mandatory. It can be created before or after you build your document understanding. If you already know the information that you want to extract, create the extractor beforehand, or, if you don’t, wait until you have a better understanding of your model.

- **Retention label** – This is optional but can be applied to any document understanding model. It can even be added to a document library that has already had the document understanding model applied.
