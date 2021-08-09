Megan and the Human Resources department not only want to classify their documents appropriately within the libraries, they also want certain information extracted from the documents and displayed as columns within the library.

Now we will look at how Megan can create an extractor to pull out the information they need to be displayed.  

1. Notice another pattern in the benefit change letters just before the name of the insurance provider:

    > We are writing to inform you of a change in our insurance network participation with your insurance provider...

    This is a phrase you can use to train an extractor to identify the _name_ of the insurance provider.

1. Return to the main models page by selecting the model name, _Benefit change letter_, in the top navigation menu.

    :::image type="content" source="../media/go-back.png" alt-text="A screenshot of the classifier window with the model name highlighted.":::

1. Select **"Create extractor."**
1. A dialog box opens on the right side of the screen.
1. Name the extractor. In this case, because you're extracting the _name_ of the insurance provider, name the extractor _"Provider."_ This name will turn into a column in the SharePoint libraries filled in with all the insurance provider names once the model is applied.
1. Click **"Create."**

    :::image type="content" source="../media/new-entity-extractor.png" alt-text="A screenshot of the create extractor dialog box with a new extractor called 'Provider' being created.":::

1. You return to the training window with the training documents listed and the first one automatically selected.
   - You will train the model to recognize the insurance provider's name.
   - The model will also extract that name and label each letter with that name.
1. With your cursor, highlight the portion of the document with the insurance provider's name.
   1. Click **"Next file."**
   1. The insurance provider name you highlighted is now listed as a label for the first letter.
   1. Work through each file until you reach the negative files, or the files that are _not_ benefit change letters.
   1. For the two negative examples, check the box just above the letter that says **"No label."** This tells the extractor that these files do not match the requirements to be benefit change letters.

    :::image type="content" source="../media/provider-label.png" alt-text="A screenshot of the classifer window showing a negative example file with the 'No label' box highlighted." lightbox="../media/provider-label.png":::

1. Once all files have been either labeled or listed for no label, click "Save" in the upper right-hand corner of the screen.

    :::image type="content" source="../media/negative-example.png" alt-text="A screenshot of the classifer window showing the files with labeled extractors and a negative example file with the 'No label' box checked." lightbox="../media/negative-example.png":::

## Add an explanation

1. As before, you will need to add explanations for this extractor.
   1. In the upper left-hand title bar, click **"Train."**

    :::image type="content" source="../media/train-extractor.png" alt-text="A screenshot of the classifier window with the 'Train' tab in the top navigation menu highlighted.":::

1. Once again, the explanation dialog opens with your list of documents and the first document automatically selected for reading in the right-hand pane.
1. Click **"New"** in the explanations dialog box.
1. Select **"Blank."**

    :::image type="content" source="../media/explain-extractor.png" alt-text="A screenshot of the explanations dialog box with the 'New' button highlighted.":::

1. Name the explanation. Since you're explaining the insurance provider extractor, you can name this explanation _"Provider"_ to match the extractor.
   1. Because you will specify the text phrase leading up to the insurance provider name, select **"Phrase List"** from the dropdown list.
   1. Highlight the phrase _"your insurance provider"_ from the body of the benefit change letter training file.
   1. Copy and paste that phrase into the **Phrase list** document.
   1. You have instructed the model that this phrase is always followed by the name of the insurance provider.
1. Click **"Save and train"** in the lower left-hand corner of the dialog box.

    :::image type="content" source="../media/save-and-train-extractor.png" alt-text="A screenshot of the explanations dialog box with the 'Save and train' button highlighted.":::

1. The model will now attempt to evaluate each document in the training library against the criteria you defined in the **"Evaluation"** column.
   - You are returned to the training screen where you can watch the model work in the documents.
   - It may take a minute for the model to work through the training library.

    :::image type="content" source="../media/training-extractor.png" alt-text="A screenshot of unlabeled training files with an empty 'Evaluation' column highlighted.":::

1. When the evaluation completes, you will see the **"Evaluation"** column fill with the words **"Match"** or **"Mismatch,"** depending on how well document phrase patterns fit model definitions.

    :::image type="content" source="../media/mismatch.png" alt-text="A screenshot of labeled training files with the 'Evaluation' column highlighted showing some files evaluated as 'Match' in green and 'Mismatch' in red.":::

    In this example, you see that the second document is listed as a **"Mismatch."** This is because the insurance provider name is longer than two words.

1. Click into the mismatched letter and note that the model highlights the first two words of the insurance provider name in green, and the rest of the name in blue.  

    :::image type="content" source="../media/green-and-blue-provider-name.png" alt-text="An example of a mismatched training file with the mismatched text highlighted in both blue and green.":::

   - The blue highlight is the first part of the model you trained. You told it what the name of the insurance provider was. The green highlight is the newest explanation where you explained to the model that it should look at the text after the phrase _"your insurance provider."_ But the model doesn't know how many words past that phrase it should look.
   - You will need to add an explanation that tells the model where to stop looking.
   - To give the model the best chance of identifying an insurance provider name regardless of the name length, you need another phrase pattern to help the model capture the best data. In this case, you'll identify a phrase at the end of the insurance provider name and you've noticed that in each letter, the insurance provider name is followed by the same pattern–the company URL.  

1. To create the new explanation to help the model resolve mismatches, click **"New"** in the Explanations dialog box.
   1. Select **"Blank."**
   1. Name the new explanation. In this case, you pick _"Text after"_ since this name is only for the model and your reference.
   1. Select **"Phrase List."**
   1. Copy the phrase after the insurance provider name _"(http://"_ and paste it into the **Phrase List** text box.

    :::image type="content" source="../media/second-explanation-for-extractor.png" alt-text="A screenshot of the classifier window with the create an explanation dialog box open and the explanation, 'http://', in the phrase list highlighted." lightbox="../media/second-explanation-for-extractor.png":::

1. Click **"Save and train"** again.
   - The model will evaluate the training files again – this time with both explanations helping it identify  both the beginning and the ending of the target insurance provider names to be extracted.
   - This time, with the extra information, the model matches each training file correctly.

    :::image type="content" source="../media/match.png" alt-text="A screenshot of labeled training files showing all files evaluated as 'Match'.":::

You have successfully trained the extractor.
