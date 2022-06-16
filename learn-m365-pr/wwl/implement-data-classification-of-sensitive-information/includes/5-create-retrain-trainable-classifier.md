A Microsoft 365 trainable classifier is a tool that an organization can "train" to recognize various types of content. The organization can do so by giving the tool different samples of data to look at. Once a classifier has been trained - that is, once it's been initially created - an organization can continue to "retrain" it to improve its precision in identifying various types of data classifications.

This unit examines how to create a trainable classifier, and how to retrain an existing classifier.

### How to create a trainable classifier

Complete the following steps to create, test, and publish a custom trainable classifier:

1.  Collect between 50-500 seed content items. These content items must be samples only. They must also strongly represent the type of content you want the trainable classifier to positively identify as being in the classification category.
    
    > [!IMPORTANT]
    > You should verify the items in your seed set are strong examples of the category. The trainable classifier initially builds its model based on what you seed it with. The classifier assumes all seed samples are strong positives. It has no way of knowing if a sample is a weak or negative match to the category.
2.  Place the seed content in a SharePoint Online folder that's dedicated to holding **the seed content only**. Make note of the site, library, and folder URL.
    
    > [!TIP]
    > If you create a new site and folder for your seed data, allow at least an hour for that location to be indexed before creating the trainable classifier that will use that seed data.
3.  Sign in to the **Microsoft Purview compliance** portal with either compliance admin or security admin role access. Then select **Data classification** on the navigation pane.
4.  On the **Data classification** page, select the **Trainable classifiers** tab.
5.  On the **Trainable classifiers** tab, select **Create trainable classifier** on the menu bar.
6.  Fill in appropriate values for the **Name** and **Description** fields of the category of items you want this trainable classifier to identify.
7.  Select the SharePoint Online site, library, and folder URL for the seed content site from step 2. Select **Add**.
8.  Review the settings and select **Create trainable classifier**.
9.  It can take up to 24 hours for the trainable classifier to process the seed data and build a prediction model. The classifier status is **In progress** while it processes the seed data. When the classifier is finished processing the seed data, the status changes to **Need test items**.
10. Once the classifier has finished processing the seed data, select the classifier to view its details page.
    
    :::image type="content" source="../media/classifier-trainable-ready-to-test-detail-d5631f36.png" alt-text="Screenshot of the details page that's displayed after selecting the classifier you created.":::
    
11. Collect at least 200 test content items for best results (10,000 maximum). These items should be a mix of items that are strong positives, strong negatives, and some that are a little less obvious in their nature.
12. Place the test content in a SharePoint Online folder that's dedicated to holding **the test content only**. Make note of the SharePoint Online site, library, and folder URL.
    
    > [!TIP]
    > If you create a new site and folder for your test data, allow at least an hour for that location to be indexed before creating the trainable classifier that will use that seed data.
13. Select **Add items to test**.
14. Select the SharePoint Online site, library, and folder URL for the test content site from step 12. Select **Add**.
15. Complete the wizard by selecting **Done**. Your trainable classifier will take up to an hour to process the test files.
16. When the trainable classifier is done processing your test files, the status on the details page will change to **Ready to review**. If you want to increase the test sample size, select **Add items to test** and allow the trainable classifier to process the extra items.
    
    :::image type="content" source="../media/classifier-trainable-ready-to-review-detail-f54c85b3.png" alt-text="Screenshot of the training process page in which you'll review items to generate classifier accuracy.":::
    
17. Select the **Tested items to review** tab to review the items.
18. Microsoft 365 will present 30 items at a time. Review each item. A dialog box will appear for each item asking whether you agree with its assessment of the item. The following screenshot displays the **We predict this item is "Relevant". Do you agree?** assessment. You can respond by selecting either **Yes, No,** or **Not sure, skip to next item**. The model's accuracy is automatically updated after every 30 items.
    
    :::image type="content" source="../media/classifier-trainable-review-detail-390cd433.png" alt-text="Screenshot of the review item page that asks whether you agree with its assessment of the test item.":::
    
19. Review ***at least*** 200 items. Once the accuracy score is stabilized, the **Publish** option will become available and the classifier status will change to **Ready to use**.
    
    :::image type="content" source="../media/classifier-trainable-review-ready-to-publish-7e67cb66.png" alt-text="Screenshot of the review item page that indicates the classifier is ready to use.":::
    
20. Select the **Publish** option to publish the classifier.
21. Once the classifier is published, it will be available as a condition in:
     -  [Office auto-labeling with sensitivity labels](/microsoft-365/compliance/apply-sensitivity-label-automatically?azure-portal=true)
     -  [Auto-apply retention label policy based on a condition](/microsoft-365/compliance/apply-retention-labels-automatically?azure-portal=true)
     -  [Communication compliance](/microsoft-365/compliance/communication-compliance?azure-portal=true)

### How to retrain a classifier

As an organization uses its custom trainable classifiers, it may want to increase the precision of the classifications the classifiers are making. You increase precision by evaluating the quality of the "match" and "not a match" classifications made by the classifier. After you make 30 evaluations for a classifier, it takes that feedback and automatically retrains itself.

An organization can improve the accuracy of custom trainable classifiers by providing feedback on the accuracy of the classifications they performed. This process is called retraining.

> [!NOTE]
> Pre-trained classifiers that were provided with your Microsoft 365 tenant can't be retrained.

The following diagram shows the workflow process for retraining a trainable classifier.<br>

:::image type="content" source="../media/classifier-retraining-workflow-1b724701.png" alt-text="Diagram showing the workflow process involved with retraining a trainable classifier.":::


Custom trainable classifiers are retrained in the **Data classification** feature in the **Microsoft Purview compliance** portal. Organizations should complete the following steps to retrain a classifier:

1.  In the **Microsoft Purview compliance** portal, select **Data classification** on the navigation pane.
2.  On the **Data classification** page, select the **Content explorer** tab.
3.  Under the **Filter on labels, info types, or categories** list, expand **Trainable classifiers**.
    
    > [!IMPORTANT]
    > It can take up to eight days for aggregated items to appear under the trainable classifiers heading.
4.  Select the trainable classifier you want to retrain.
    
    > [!NOTE]
    > If an item has an entry in the **Retention label** column, it means the item was classified as a match. If an item doesn't have an entry in the **Retention label** column, it means it was classified as a close match. You can improve the classifier precision the most by providing feedback on close match items.
5.  Choose an item and open it.
    
    > [!TIP]
    > Feedback can be provided on multiple items simultaneously. You can do so by selecting all items and then selecting **Improve classification** in the menu bar.
6.  Select **Provide feedback**.
7.  In the **Detailed feedback** pane, if the item is a true positive, select **Match**. If the item is a false positive, which means it was incorrectly included in the category, select **Not a match**.
8.  If there's another classifier that would be more appropriate for the item, you can choose it from the **Suggest other trainable classifiers** list. Doing so will trigger the other classifier to evaluate the item.
9.  Select **Send feedback** to send your evaluation of the "match" and "not a match" classifications. You can also suggest other items for this trainable classifier. When you've provided 30 instances of feedback to a classifier, it will automatically start the retraining process. Retraining can take from one to four hours. Classifiers can only be retrained twice per day.
    
    > [!IMPORTANT]
    > This information goes to the classifier in your tenant. It doesn't go back to Microsoft.
10. Select the **Trainable classifiers** tab.
11. The classifier that was used in your Communications compliance policy will appear under the **Retraining** heading.
    
    :::image type="content" source="../media/classifier-retraining-ac900701.png" alt-text="Screenshot of the Trainable classifiers tab on the Data classification page showing the list of Retraining classifiers.":::
    
12. Once retraining completes, choose the classifier to open the retraining overview.
    
    :::image type="content" source="../media/classifier-retraining-overview-3e9a1617.png" alt-text="Screenshot of the Retraining Overview tab showing feedback on a data classifier once retraining of the classifier has completed.":::
    
13. Review the recommended action and the prediction comparisons of the retrained and currently published versions of the classifier.
14. If you satisfied with the results of the retraining, select **Republish**.
15. If you aren't satisfied with the results of the retraining, you can choose to provide more feedback to the classifier in the **Content explorer** tab and start another retraining cycle. Or, you can choose to do nothing, in which case the currently published version of the classifier will continue to be used.
