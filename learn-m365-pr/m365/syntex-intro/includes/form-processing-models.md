In addition to processing various text documents using document understanding models, your team also needs form processing for the sales order forms that are filled out and submitted by clients. To create these models, you'll need to use AI Builder, instead of the content center where your document understanding models originated.

Here, you'll learn what SharePoint Syntex form processing models are so you can understand what kind of content these models should be applied to and when to use them.

## What is a form processing model?

Form processing models focus on identifying and extracting information from _structured_ and _semi-structured_ documents. At Contoso Electronics, these documents would include content like contracts, purchase orders, invoices, and billing statements, all of which have specific structures, or may look more like a "form."

Form processing models use machine learning technology from Microsoft Power Apps AI Builder. AI capabilities identify and extract necessary information, helping automate business processes.

Example files are used to train your AI model what text needs to be extracted and how it should be organized in your SharePoint document library. Training, publishing, and using your model creates a Power Automate Flow, which means that every time a new file is added to the SharePoint document library where the form processing model was added, the information will be automatically identified and extracted.

![A screenshot of a sample invoice with information fields selected that might be used to train a form processing model.](../media/invoice-image.png)

### What is AI Builder?

Form processing models are pre-built, automated, and contain fewer parts than a document understanding model. These models are _created_ directly in the SharePoint document library where they're used, but they're _built_ with AI Builder, a feature in Microsoft Power Apps. AI Builder helps you create AI-powered form processing models without having to know any complicated coding. AI Builder walks you through the entire process to create your form processing model:

1. Name your form processing model
1. Select the example files for analysis
1. Identify the form fields to extract
1. Train your model
1. Publish your model
1. Use your model

## Learn more

- [What is AI builder?](/ai-builder/overview)
