Before you train your model, you must identify five _positive_ example documents. In other words, these documents need to be examples of benefit letters. It is also necessary to include _negative_ examples—documents that are not benefit letters. Pull those documents together in one place as a set of training files.

You and Megan identified a group of seven documents to train the new model.

:::image type="content" source="../media/training-files.png" alt-text="A screenshot of file explorer showing a folder of training files.":::

1. Begin in the content center, navigate to **Models**, and then select _Benefit change letter_.
1. Click **"Add files"** in the **Add example files column**.
1. The **"Select example files for your model"** window opens.
1. Click **"Upload"** to bring the training files into the training area.
   1. Select all of the files in the training files folder and click **"Open."**
   1. The upload will begin. It may take a moment to complete.
   1. The default content type is _'Document.'_ This training will teach SharePoint Syntex how to change that default content type from _'Document'_ to _'Benefit change letter.'_
1. When the upload finishes, click the radio button in the top-left column to select all of the documents.
   1. Click **'Add'** in the lower right-hand corner of the window.

    :::image type="content" source="../media/add-training-files.png" alt-text="A screenshot showing all training files selected in the training area with the 'Add' button highlighted.":::

1. The seven documents are now added to the training area and more key actions options become available, so you can move forward with training your model.
1. Move to the next column in line: **Classify and run training**.
   1. Click **"Train classifier."**

    :::image type="content" source="../media/train-classifier.png" alt-text="A screenshot of the models view page with the 'Classify files and run training' area highlighted." lightbox="../media/train-classifier.png":::

1. The classifier training window opens with one of the training documents automatically selected and open.
   1. You need to mark which of the example files are _positive_ examples of benefit change letters.
   1. In document view, click either **"Yes"** or **"No"** depending on whether the document displayed is a benefit change letter or not.
       1. The formatting has been stripped so SharePoint Syntex can focus in on the text.

    :::image type="content" source="../media/define-change-letter.png" alt-text="A screenshot of the classifier window showing a positive example training file with the UI buttons 'Yes' and 'No' highlighted." lightbox="../media/define-change-letter.png":::

1. Because this is a benefit change letter, click **"Yes."**
   1. The trainer labels the first document **"Positive"** as a match for benefit change letter.
   1. The trainer moves to the next file in line.

    :::image type="content" source="../media/second-letter.png" alt-text="A screenshot of the classifier window showing an example training file with the file navigation area highlighted indicating the model is training file 2 of 7." lightbox="../media/second-letter.png":::

1. Move through each of the example files in this same way until all of them have been identified as either _positive_ or _negative_.
   1. Select 'No' when a file opens that is NOT a benefit change letter.

    :::image type="content" source="../media/negative-letter-example.png" alt-text="A screenshot of the classifier window showing a negative example training file with the UI button, 'No', highlighted." lightbox="../media/negative-letter-example.png":::

1. Once you've moved through the example files, you will notice they've been labeled as _positive_–meaning the documents are benefit change letters, or _negative_–they are not benefit change letters.

    :::image type="content" source="../media/labels.png" alt-text="A screenshot of all labeled example training files.":::

## Create an explanation

Now, you must explain to the model _why_ benefit change letters are benefit change letters. For that, click **"Train."**

:::image type="content" source="../media/train-the-model.png" alt-text="A screenshot of the classifier window with the 'Train' area of the top navigation menu highlighted.":::

1. The explanations dialog box opens in the training area.
    1. Again, the first document is automatically selected and opened.  
    1. Explanations tell the model what elements go into making a benefit change letter.

    :::image type="content" source="../media/not-yet-trained.png" alt-text="A screenshot of the classifier window with the 'Explanations' area highlighted." lightbox="../media/not-yet-trained.png":::

1. Before you can train the new model, you must add a new explanation.
   1. Click **"New"**, then **"Blank."**
   1. This opens the **Create an explanation** dialog box.
   1. Name the explanation and select the explanation type from the dropdown menu.
   1. In this case, you and Megan decide to use the subject line as an explanation, so name this **"Subject."**
   1. In the dropdown list, you can chose from **"Phrase List"** and **"Proximity"**.
   1. Because the subject line of the benefit change letters is a phrase, select **"Phrase List."**
1. A new dialog box opens for **"Phrase list"** asking you to identify words, phrases, numbers, or patterns that can be used to accurately identify a benefit change letter.
   1. Each benefit change letter has the same subject line, therefore, you can use that phrase to help the model recognize benefit change letters in the rest of the Human Resources libraries.
   1. Copy and paste the phrase _"Benefit Change Notice"_ into the text box on the left.

    :::image type="content" source="../media/create-an-explanation.png" alt-text="A screenshot of the 'Create an explanation' dialog box with the Name, Explanation type, and Phrase List as well as the phrase, 'Benefit Change Notice', within the example training file highlighted." lightbox="../media/create-an-explanation.png":::

1. Click **"Save"** at the bottom of the page.
   1. Do _not_ click **"Save and Train."**
   1. Human Resources management wants to label each of the benefit change letters with the name of the insurance providers, as well. This requires defining an extractor _before_ training the model.
   1. When you click **"Save,"** the explanation dialog box closes, returning you to the classifier page.
