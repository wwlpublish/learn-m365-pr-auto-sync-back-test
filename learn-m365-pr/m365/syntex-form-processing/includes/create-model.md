In this unit, you will teach the Accounting department how to plan for and create a form processing model to extract data from POs. Currently, their POs are stored in Microsoft OneDrive. To apply form processing to existing POs and to every PO that is added to the file folder, you must make plans to import the forms to a dedicated SharePoint library.

1. Create a training set.
   1. Identify and isolate a group of files to be used to train the model you create.
   1. Five files is the required minimum.
   1. Copy your files into a file folder named _Training Set_.
   1. After you've brought over your PO examples, add at least two other files of the same type (PDF in this case) that are _not_ POs.
   1. For this example, Statements of Work in PDF format will suffice.
1. Create a SharePoint document library where your POs will be imported
   1. Click **"Site Contents"** in the left-hand pane of the Accounting department's SharePoint site.

    :::image type="content" source="../media/site-contents.png" alt-text="A screenshot of a SharePoint site with the Site contents button on the left-hand navigation menu highlighted.":::

1. Click **"New"** to create a new library dedicated to POs.
   1. Select **"Document Library"** from the dropdown of options.

    :::image type="content" source="../media/new-content.png" alt-text="A screenshot of the Site contents page showing available document libraries." lightbox="../media/new-content.png":::

1. The **Create document library** pane opens on the right-hand side of the screen.
   1. Name the site – in this case _"POs."_
   1. Click **"Create."**

    :::image type="content" source="../media/create-document-library.png" alt-text="A screenshot of the 'Create a document library' dialog box.":::

1. This creates a new, empty document library with no columns of useful information.

    :::image type="content" source="../media/empty-library.png" alt-text="A screenshot of a new, empty document library." lightbox="../media/empty-library.png":::

1. From within this empty SharePoint library, click on **"Automate"** in the upper right-hand navigation ribbon.
   1. From the dropdown, select **"AI Builder,"** which opens another option box
   1. Select **"Create a model to process forms."**

    :::image type="content" source="../media/ai-builder-entry-point.png" alt-text="A screenshot of the new document library with the AI Builder button, located in the Automate tab on the top navigation menu, higlighted." lightbox="../media/ai-builder-entry-point.png":::

1. A dialog box opens on the right-hand side of the page asking you to name your new model.
   1. The name you choose will be used as the content type in your new SharePoint library, so select a name that makes sense in reference to how the forms will be labeled.
   1. Type in the name. For this example, we'll use _"PO"_.
   1. In **Advanced Settings**, you have the choice between creating a new content type or selecting from a set of predefined content types available to SharePoint Syntex. For our purposes, you can leave the default **"Create new"** selected.
   1. Also, leave the box _checked_ for default view of the library. Unchecking this box removes the view the model creates to show the data the model is going to extract. Without this box checked, it may look as if your model failed.
   1. Click **"Create."**

    :::image type="content" source="../media/create-model-to-process-forms.png" alt-text="A screenshot of the 'Create a model to process forms' dialog box with the 'Create' button highlighted.":::

1. PowerApps AI Builder opens.
   - This transition may take a moment to complete as AI Builder creates your new model.
1. The AI Builder tool page opens on **"Choose information to extract."**
   - Accounting wants to see the PO number, the vendor's name, and the total PO amount in dollars.
1. Click **"Add."**
   1. Select **"Field."**

    :::image type="content" source="../media/add-field.png" alt-text="A screenshot of the 'Choose information to extract' dialog box with the 'Add' drop down and 'Field' selection highlighted":::

1. The **Field** dialog box opens, asking you to define the first field you want your AI model to extract.
   1. In this case, name the field _"PO-number."_
   1. Click **"Done.**"
   1. You'll see the field added to the page.
   1. Add another field called _"Vendor Name."_
   1. Add another field called _"PO-Total."_

    :::image type="content" source="../media/information-to-extract.png" alt-text="A screenshot of the 'Choose information to extract' dialog box with the fields and field types highlighted.":::

1. Click **"Next"** button at the bottom of the page.

## Train and test your model

1. The **"Add collections of documents"** page opens.
    1. Add the training files you identified earlier.
    1. Click **"New collection."**
    1. **"Add documents"** appears on the page with a button beneath it.
    1. Click the plus sign in that **"Add documents"** button.

    :::image type="content" source="../media/add-documents.png" alt-text="A screenshot of the 'Add collections of documents' pane with the 'New collection' and 'Plus' buttons highlighted.":::

1. The **"Collection 1"** pane opens in the right-hand part of the screen.
   1. The instructions tell you to select five or more documents with the same layout – like your collection of POs.
   1. Forms need to be either `.JPG`, `.PNG`, or `.PDF` files.
   1. Click **"Add documents."**

    :::image type="content" source="../media/add-five-or-more.png" alt-text="A screenshot of the 'Collection 1' pane with the 'Add documents' button and the text 'Add five or more documents with the same layout' highlighted.":::

1. The **"Select source"** window opens with a list of data sources.
   1. Select **"Upload from local storage."**
   1. Navigate to the location of the training files.
   1. Import all the training files.
   1. The files will load.
   1. While we're loading seven files, only five of them conform to the requirement of being POs.
   1. The two negative documents will be used while training your model.
   1. Click **"Add 7 documents."**

    :::image type="content" source="../media/upload-7-documents.png" alt-text="A screenshot of the 'Select source' window and seven selected documents with the 'Upload 7 documents' button highlighted.":::

1. The documents will take a few minutes to upload to the environment.
   1. When the upload completes, click **"Close."**
1. Click **"Analyze"** at the bottom of the screen.

    :::image type="content" source="../media/analyze.png" alt-text="A screenshot of the 'Add collections of documents' pane after documents have been added with the 'Analyze' button highlighted." lightbox="../media/analyze.png":::

1. The training center will begin analyzing the documents.
   - This step may take a few minutes to complete.
1. When the analyze documents step completes, AI Builder displays a rendering of the first PO in the Tag documents page of the AI Builder.
   1. A window pops up pointing out where the documents are listed in the right-hand pane of the AI Builder screen.
   1. You can browse through the documents by clicking **"Next."**
   1. To begin tagging the document fields, click the **"X"** in the upper right-hand corner of the window.
   1. For our purposes, click the **"X"** to close the window.

    :::image type="content" source="../media/x-or-next.png" alt-text="A screenshot of the first document to be analyzed in AI Builder and a panel on the right showing all documents for analysis." lightbox="../media/x-or-next.png":::

1. Begin tagging by highlighting the PO Number. Click and drag to draw a dotted line box around the PO Number in your document.

    :::image type="content" source="../media/po-number.png" alt-text="A screenshot of the highlighted PO number on the purchase order file.":::

1. When you release the mouse button, the box will solidify, and a dialog box opens listing the three fields you defined earlier: _PO-number_, _Vendor Name_, and _PO-Total_.
   1. The PO Number you highlighted is now listed at the top of the dialog box.
   1. Select the correct field. In this case, click the radio button beside _"PO-number."_

    :::image type="content" source="../media/specify-po-number.png" alt-text="A close screenshot of the dropdown list of fields that appears after tagging in AI builder with the 'PO number' field highlighted.":::

1. Once you make a selection, the dialog closes, the box around the PO number turns green, and a green check mark appears in the field list on the right-hand side of the AI Builder screen.

    :::image type="content" source="../media/turns-green.png" alt-text="A close screenshot of the Fields pane in AI builder after the PO number has been tagged with the PO-number field checked." lightbox="../media/turns-green.png":::

1. Repeat this process for the vendor name.
   1. Highlight the complete vendor name.
   1. Notice that when the dialog box opens, it contains only two field names.
   1. Make your selection, _"Vendor Name,"_ and check that box.
   1. As before, the box closes, the outline around the vendor name turns green, and the green check mark appears beside _"Vendor Name"_ in the list of fields on the right-hand side of the page.
1. Scroll down in the document to **"Total."**
   1. Highlight the dollar amount.
   1. When the dialog box opens, only _"PO-Total"_ remains as a choice.
   1. Click the radio button.
   1. You've successfully initiated training for your form processor.

    :::image type="content" source="../media/fields-complete.png" alt-text="A close screenshot of the Fields pane in AI builder after all fields have been tagged with all fields checked." lightbox="../media/fields-complete.png":::

1. Walk through each document in the same way until you reach the two `.PDF` files that are not POs.
   - As you move through the documents, AI Builder may automatically recognize some of your fields and automatically tag them for you.
1. For the documents that are not POs, you will mark the defined fields as **"Not available in document."**
   1. Bring up one of the training documents that is not a PO.
   1. In the right-hand pane, click on the three dots to the right of each possible field name.
   1. Select **"Not available in document."**
   1. Do this for each field in each negative document.

    :::image type="content" source="../media/not-available-in-document.png" alt-text="A close screenshot of the Fields pane in AI builder for a negative training example with a dropdown for the PO number field with the text 'Not available in document' selected.":::

1. Select **"Save and close"** in the upper right-hand corner of the screen.

    :::image type="content" source="../media/save-and-close.png" alt-text="A screenshot of AI builder after all documents have been analyzed with the 'Save and close' button highlighted." lightbox="../media/save-and-close.png":::

1. AI Builder saves the PO model.
1. Click the model name to open the model for next steps.

    :::image type="content" source="../media/purchase-order-model.png" alt-text="A screenshot of the 'My models' pan with the model name, 'Purchase Order', and model type, 'Form Processing', highlighted." lightbox="../media/purchase-order-model.png":::

1. The training page opens with the first PO rendered, along with the field list on the right-hand side of the screen. Your fields will have green check marks next to them.
   1. Click **"Next"** at the bottom left of the screen to begin training your form processing model.

    :::image type="content" source="../media/next-to-train.png" alt-text="A screenshot of an analyzed purchase order with the 'Next' button highlighted.":::

1. The **Model summary** page opens.
   1. Review the information for your model.
   1. Click **"Train."**

    :::image type="content" source="../media/train-po-model.png" alt-text="A screenshot of the model summary page with the 'Train' button highlighted.":::

1. The model begins training.
   - A dialog box opens telling you that the model is training and that it may take several minutes.
   - It is okay to close the window and return later, if necessary. However, with the limited number of training documents you used, the model will finish training quickly.
1. When training finishes, AI Builder will display a message **"Training complete."**
1. Click **"Go to Details page."**

    :::image type="content" source="../media/go-to-details.png" alt-text="A screenshot of the 'Training complete' dialog box with the 'Go to Details page' button highlighted.":::

1. The **Details page** opens with a banner across the top saying that your model hasn't been published and therefore, cannot be used in apps or flows.
   1. To publish your model, click **"Publish"** at the bottom of the Training document box.

    :::image type="content" source="../media/model-not-published.png" alt-text="A screenshot of the 'Details page' with the statement 'Your model isn't published yet. Publish it to use it in apps and flows', the model status, and the 'Publish' button highlighted." lightbox="../media/model-not-published.png":::

1. When the model finishes publishing, the page refreshes.
   1. The status beneath the model name now reads **"Published."**
   1. The model is published under Power Apps on the right-hand side of the screen, and you can click in to read documentation about the model.

:::image type="content" source="../media/published-use-model.png" alt-text="A screenshot of the 'Details page' showing the model is published and the 'Use Model' button is highlighted." lightbox="../media/published-use-model.png":::
