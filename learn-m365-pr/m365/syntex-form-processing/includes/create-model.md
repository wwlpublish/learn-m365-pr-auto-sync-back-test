In this unit, you will teach the accounting department how to plan for and create a form processing model to extract data from purchase orders.Currently, their purchase orders are stored in Microsoft OneDrive.To apply form processing to the existing POs and to every PO that is added to the file folder, you must make plans to import the forms to a dedicated SharePoint library.

Create a training set.

Identify and isolate a group of files to be used to train the model you create.

Five files are the recommended minimum.

Copy your files into a file folder named Training Set.

After you’ve brought over your PO examples, add at least two other files of the same type (PDF in this case) that are not purchase orders.

For this example, Statements of Work in PDF format will suffice.

Create a SharePoint document library where your purchase orders will be imported.

Click "Site Contents” in the left-hand pane of the accounting department’s SharePoint site.

![Graphical user interface, application]()

Click "New” to create a new library dedicated to purchase orders.

Select "Document Library” from the dropdown of options.

![Graphical user interface, table]()

The Create document library pane opens on the right-hand side of the screen.

Name the site – in this case "Purchase Orders."

Click "Create."

![Graphical user interface, text, application]()

This creates a new, empty document library with no columns of useful information.

![Graphical user interface, text, application]()

From within this empty SharePoint library, click on "Automate” in the upper right-hand navigation ribbon.

From the dropdown, select "AI Builder,” which opens another option box.

Select "Create a model to process forms."

A dialogue box opens on the right-hand side of the page asking you to name your new model.

The name you choose will be used as the Content Type in your new SharePoint library, so select a name that makes sense in reference to how the forms will be labeled – as purchase orders, for this example.

Type in the name.For this example, we’ll use "Purchase Order” as the name for the model.

In Advanced Settings, you have the choice between creating a new content type or selecting from a set of predefined content types available to SharePoint Syntex.For our purposes, you can leave the default "Create new” selected.

Also leave the box checked for default view of the library.Unchecking this box removes the view the model creates to show the data the model is going to extract.Without this box checked, it may look as if your model failed.

Click "Create."

![Graphical user interface, text, application, email]()

PowerApps AI Builder opens.

This transition may take a moment to complete as AI Builder creates your new model.

The AI Builder tool page opens on "Choose information to extract."

Accounting wants to see the PO number, the vendor’s name, and the total PO amount in dollars.

Click "Add."

Select "Field."

![Graphical user interface, text, application, email]()

The Field dialogue box opens, asking you to define the first field you want your AI model to extract.

In this case, name the field "PO-number."

Click "Done."

You’ll see the field added to the page.

Add another field called "Vendor Name."

Add another field called "PO-Total."

![Graphical user interface, text, application, email]()

Click "Next” button at the bottom of the page.

Train and test your model

The "Add collections of documents” page opens.

Add the training files you identified earlier.

Click "New collection."

"Add documents” appears on the page with a button beneath it.

Click the plus sign in that "Add documents” button.

![Graphical user interface, application]()

The "Collection 1” pane opens in the right-hand part of the screen.

The instructions tell you to select five or more documents with the same layout – like your collection of purchase orders.

Note that forms need to be either .JPG, .PNG, or .PDF files.

Click "Add documents."

![Graphical user interface, application, Teams]()

The "Select source” window opens with a list of data sources.

Select "Upload from local storage."

Navigate to the location of the training files.

Import all the training files.

The files will load.

Note that while we’re loading seven files, only five of them conform to the requirement of being purchase orders.

The two negative documents will be used while training your model.

Click "Add 7 documents."

![Graphical user interface, table]()

The documents will take a few minutes to upload to the environment.

When the upload completes, click "Close."

Click "Analyze” at the bottom of the screen.

![Graphical user interface, application]()

The training center will begin analyzing the documents.

This step may take a few minutes to complete.

When the analyze documents step completes, AI Builder displays a rendering of the first purchase order in the Tag documents page of the AI Builder.

A window pops up pointing out where the documents are listed in the right-hand pane of the AI Builder screen.

You can browse through the documents by clicking "Next."

To begin tagging the document fields, click the "X” in the upper right-hand corner of the window.

For our purposes, click the "X” to close the window.

![Graphical user interface, application]()

Highlight the PO Number.Click and drag to draw a dotted line box around the PO Number in your document.

![A picture containing Graphical user interface]()

When you release the mouse button, the box will solidify, and a dialogue box opens listing the three fields you defined earlier: PO-number, Vendor Name, and PO-Total.

Note that the PO Number you highlighted is now listed at the top of the dialogue box.

Select the correct field.In this case, click the radio button beside "PO-number."

![Graphical user interface, application]()

Once you make a selection, the dialogue closes, the box around the purchase order number turns green, and a green check mark appears in the field list on the right-hand side of the AI Builder screen.

![Graphical user interface, application]()

Repeat this process for the Vendor name.

Highlight the complete vendor name.

Notice that when the dialogue box opens, it contains only two field names.

Make your selection, "Vendor Name,” and check that box.

As before, the box closes, the outline around the vendor name turns green, and the green checkmark appears beside "Vendor Name” in the list of fields on the right-hand side of the page.

Scroll down in the document to "Total."

Highlight the dollar amount.

When the dialogue box opens, only "PO-Total” remains as a choice.

Click the radio button.

You’ve successfully initiated training for your form processor.

![Graphical user interface, application, table]()

Walk through each document in the same way until you reach the two .PDF files that are not purchase orders.

Note that as you move through the documents, AI Builder may automatically recognize some of your fields and automatically tag them for you.

For the documents that are not purchase orders, you will mark the defined fields as "Not available in document."

Bring up one of the training documents that is not a purchase order.

In the right-hand pane, click on the three dots to the right of each possible field name.

Select "Not available in document."

Do this for each field in each negative document.

![Graphical user interface, text, application]()

Select "Save and close” in the upper right-hand corner of the screen.

![Graphical user interface, text, application]()

AI Builder saves the Purchase Order model.

Click the model name to open the model for next steps.

![Graphical user interface, text, application]()

The training page opens with the first purchase order rendered, along with the field list on the right-hand side of the screen.Your fields will have green check marks next to them. 

Click "Next” at the bottom left of the screen to begin training your form processing model.

![A picture containing text]()

The Model summary page opens.

Review the information for your model.

Click "Train."

![Graphical user interface, application]()

The model begins training.

A dialogue box opens telling you that the model is training and that it may take several minutes.

It is okay to close the window and return later, if necessary.However, with the limited number of training documents you used, the model will finish training quickly.

When training finishes, AI Builder will display a message "Training complete."

Click "Go to Details page."

![Graphical user interface, diagram]()

The Details page opens with a banner across the top saying that your model hasn’t been published and therefore, cannot be used in apps or flows.

To publish your model, click "Publish” at the bottom of the Training document box.

![Graphical user interface, application]()

When the model finishes publishing, the page refreshes.

The status beneath "Models>Purchase Order” now reads "Published.”

Note that the model is published under Power Apps on the right-hand side of the screen, and you can click in to read documentation about the model.

![Graphical user interface, application]()
