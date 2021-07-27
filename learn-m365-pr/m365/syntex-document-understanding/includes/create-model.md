Before applying document understanding models, they need to be created within the content center that was created during SharePoint Syntex setup.

Megan Bowen, a Human Resource administrative assistant at Contoso Electronics, volunteered to act as the document understanding model owner and build and apply models since she is familiar with the documents and the libraries.  

Here, you'll learn how to instruct Megan and other model owners how to build document understanding models.

:::image type="content" source="../media/home-page.png" alt-text="Screenshot of the Contoso Electronics Human Resources SharePoint page." lightbox="../media/home-page.png":::

Megan and her managers have identified a library of letters to begin building their document understanding model.  

:::image type="content" source="../media/hr-letters-highlighted.png" alt-text="Screenshot of the Contoso Electronics Human Resources SharePoint page with the HR Letters library highlighted on the top navigation menu." lightbox="../media/hr-letters-highlighted.png":::

Megan opens the HR Letters library, which contains documents of various types. Megan and her team want to identify which documents are letters notifying Contoso Electronics employees of benefit changes. Given the healthcare data contained in those letters, Contoso Electronics has an obligation to retain them for seven years. Yet, looking through the library, nothing distinguishes these sensitive notification documents from any other document. To know which letters must be retained and which are safe to delete, Megan must open each document.  

:::image type="content" source="../media/hr-letters-library.png" alt-text="Screenshot of the Contoso Electronics HR Letters library and its contents." lightbox="../media/hr-letters-library.png":::

Human Resources would like to use a document understanding model to automatically identify which documents are benefit notification letters, and then classify them appropriately. First you'll help Megan define a document understanding model and then you'll show her how to create the model by following these steps.

1. Start in the content center. This is the place for creating and training document understanding models, and then applying those models to document libraries.
1. Select **"Models."**

    :::image type="content" source="../media/content-center-models.png" alt-text="Screenshot of the Contoso Electronics content center with the Models tab highlighted in the top navigation menu." lightbox="../media/content-center-models.png":::

1. The **Create a Model** page opens.
   1. The **"Create a Model"** button appears.
   1. You can see a list of models that have been created previously by other model owners.  

    :::image type="content" source="../media/hc-hr-content-center.png" alt-text="A screenshot of the model wizard and a list of previously created models in the SharePoint Syntex content center." lightbox="../media/hc-hr-content-center.png":::

1. Select **"Create a Model"** in the upper left-hand corner of the page.
1. A **"New document understanding model"** dialog box opens on the right-hand side of the browser.  
1. Enter a name for the model. In this case, name the model "Benefit change letter."

    :::image type="content" source="../media/creating-benefit-change-letter-model.png" alt-text="A screenshot of the 'New document understanding model' dialog box.":::

1. Each model is tied to a SharePoint content type that must be defined as you create the model.
   1. Click **"Advanced Settings."**
   1. You will see two radio buttons, the first allows you to create a new content type, the second allows you to select one of the content types that already exists in your SharePoint site.
   1. Since you are defining benefit changes letters, which are a new content type, you need to create a new content type called "Benefit change letter."
      1. Click into the drop-down box for **Retention Label** and select **"Confidential."** This selection is based on the Human Resources manager's knowledge of document retention requirements.
   1. This is also where you can define and assign a retention label to the documents your model identifies.

    :::image type="content" source="../media/benefit-change-content-type-retention.png" alt-text="A screenshot of the 'Advanced settings' dialog box where a new content type is created.":::

1. Click **"Create."**
1. SharePoint Syntex brings you to the **Models page view** in the content center.  

    :::image type="content" source="../media/benefits-change-model-created.png" alt-text="A screenshot of the models view page where document understanding models are created" lightbox="../media/benefits-change-model-created.png":::

1. The page lays out the key steps you need to take with your model.
   1. **Add example files**
      1. Add files to be used for training the model to recognize benefit change letters.
      1. Include negative examples–a few documents that are _not_ benefit change letters.
   1. **Classify files and run training**
      1. Teaches the model to recognize benefit change letter, so it can analyze every document in each library it is applied to.  
      1. Classifies documents as it identifies them as a benefit change letters, applying the "Confidential" label that was selected when the model was created.
   1. **Create and train your extractors.** Extractors pull data from the letters. In this case, Human Resources would like to sort the letters based on the names of the insurance provider, which is buried in the body of the document.
   1. **Apply models to libraries**. Once the model is trained with a few example documents, you can apply it to the library or libraries of your choice.

We'll walk through each of these items step-by-step following your model creation.
