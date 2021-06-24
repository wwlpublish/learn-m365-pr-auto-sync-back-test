The second primary feature of SharePoint Syntex is the form processing model, which uses Microsoft Power Apps AI Builder for creation and, as a result, offers slightly unique features and a different process for building the model.

For Contoso Electronics, in addition to processing various documents comprised of blocks of text using document understanding models, your team will also need form processing for the sales order forms that are filled out and submitted by clients. To create these models specifically, your organization will need to use AI Builder, as opposed to the content center where your document understanding models originated.

Here, you will learn what the parts of SharePoint Syntex form processing models are so you can understand what kind of content these models should be applied to and when to use them.

## What is a form processing model?

Form processing models focus on identifying and extracting information from structured and semi-structured documents. At Contoso Electronics, this would include content like contracts, purchase orders, invoices, and billing statements, all of which have specific structures, or may look more like a “form.”  

Form processing models use machine learning technology from Microsoft Power Apps AI Builder. AI capabilities identify and extract necessary information, helping automate business processes.

Example files are used to train your AI model for what needs to be extracted and how it should be organized in your SharePoint document library. Training and publishing your model create a Power Automate Flow, which means that every time a new file is added to the SharePoint document library where the form processing model was added, the information will be automatically identified and extracted as trained.

![Invoice, application, or billing statement as an example document with several fields highlighted.]()

## What is AI Builder?

Form processing models are created directly in the SharePoint document library they need to be applied to, but they use AI Builder, a feature in Microsoft Power Apps, to be built, instead of the content center. With AI Builder, you can create AI-powered form processing models without having to know any complicated coding. AI Builder walks you through the entire process to create your form processing model. The basic process of AI Builder includes:

- Naming your form processing model
- Selecting the example files for analysis
- Identifying the form fields you want to extract
- Training your model
- Publishing your model
- Using your model

![Where AI Builder is in the dropdown on the SharePoint document library.]()

## How do the parts of a form processing model work together?

Form processing models are pre-built, automated, and contain fewer parts than a document understanding model.  

- **AI Builder** – Instead of the content center, form processing models are created using the AI Builder option in the SharePoint library you want to create the model for. The model can only be used in the library where it was created.
- **Settable classifier** – Like document understanding models, form processing models also utilize classifiers, though they don’t use extractors.
