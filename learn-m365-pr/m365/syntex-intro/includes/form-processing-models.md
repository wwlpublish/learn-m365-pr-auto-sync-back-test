For Contoso Electronics, in addition to processing various documents comprised of blocks of text using document understanding models, your team will also need form processing for the sales order forms that are filled out and submitted by clients. To create these models, your organization will need to use AI Builder, as opposed to the content center where your document understanding models originated.

Here, you will learn what the parts of SharePoint Syntex form processing models are so you can understand what kind of content these models should be applied to and when to use them.

## What is a form processing model?

Form processing models focus on identifying and extracting information from structured and semi-structured documents. At Contoso Electronics, these documents would include content like contracts, purchase orders, invoices, and billing statements, all of which have specific structures, or may look more like a “form.”  

Form processing models use machine learning technology from Microsoft Power Apps AI Builder. AI capabilities identify and extract necessary information, helping automate business processes.

Example files are used to train your AI model what text needs to be extracted and how it should be organized in your SharePoint document library. Training, publishing, and using your model creates a Power Automate Flow, which means that every time a new file is added to the SharePoint document library where the form processing model was added, the information will be automatically identified and extracted.

![A screenshot of a sample invoice with information fields selected that might be used to train a form processing model.](../media/invoice.png)

### What is AI Builder?

Form processing models are pre-built, automated, and contain fewer parts than a document understanding model. These models are _created_ directly in the SharePoint document library where they are used, but they are _built_ with AI Builder, a feature in Microsoft Power Apps, instead of in the content center. With AI Builder, you can create AI-powered form processing models without having to know any complicated coding. AI Builder walks you through the entire process to create your form processing model. The basic process of AI Builder includes:

- Naming your form processing model
- Selecting the example files for analysis
- Identifying the form fields you want to extract
- Training your model
- Publishing your model
- Using your model

## Learn more

- [What is AI builder?](/en-us/ai-builder/overview)
