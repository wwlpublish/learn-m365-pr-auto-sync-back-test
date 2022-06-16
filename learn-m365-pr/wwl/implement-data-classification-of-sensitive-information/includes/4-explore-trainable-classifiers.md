Classifying and labeling content so it can be protected and handled properly is the starting place for the information protection discipline. Microsoft 365 has three ways to classify content:

 -  **Manually**. Manual classification requires human judgment and action. Users and admins apply them to content as they encounter it. You can use either the pre-existing labels and sensitive information types or use custom created ones. You can then protect the content and manage its disposition.
 -  **Automated pattern-matching**. This category of classification mechanisms includes finding content by:
     -  Keywords or metadata values (keyword query language).
     -  Using previously identified patterns of sensitive information like social security, credit card, or bank account numbers.
     -  Recognizing an item because it's a variation on a template (document finger printing, which is covered in a later unit in this training).
     -  Using the presence of exact strings exact data match.
 -  **Trainable classifiers**. A Microsoft 365 trainable classifier is a tool that an organization can "train" to recognize various types of content. Microsoft 365 includes an extensive list of pre-defined classifiers. Organizations can also create their own custom classifiers. Classifiers can be trained by giving them samples to look at. Once a classifier is trained, the organization can use it to identify items for application of Office sensitivity labels, Communications compliance policies, and retention label policies.

This unit examines the use of trainable classifiers.

### Trainable classifiers

Creating a custom trainable classifier first involves giving it samples that are manually picked and positively match the category. Then, after the trainable classifier tool has processed those samples, you test the classifiers' ability to predict by giving it a mix of positive and negative samples. This unit examines how to create and train a custom classifier. It also examines how to improve the performance of custom trainable classifiers and pre-trained classifiers over their lifetime through retraining.

This classification method is well suited to content that isn't easily identified by either the manual or automated pattern-matching methods. This method of classification is more about using a classifier to identify an item based on what the item is, not by elements that are in the item (pattern matching). A classifier learns how to identify a type of content by looking at hundreds of examples of the content you're interested in classifying.

> [!NOTE]
> You can view the trainable classifiers in the Content explorer tool by expanding Trainable Classifiers in the filters panel. The trainable classifiers will automatically display the number of incidents found in SharePoint, Teams, and OneDrive, without requiring any labeling. If you don't want to use this feature, you must file a request with Microsoft Support to disable out-of-the-box classification. Doing so will disable the scanning of your sensitive and labeled content before you create labeling policies.

Classifiers are available to use as a condition for:

 -  Office auto-labeling with sensitivity labels
 -  Auto-apply retention label policy based on a condition
 -  Communication compliance

> [!NOTE]
> Classifiers only work with items that aren't encrypted.

There are two types of trainable classifiers:

 -  **Pre-trained classifiers**. Microsoft has created and pre-trained multiple classifiers that you can start using without training them. These classifiers will appear with the status of **Ready to use**.
 -  **Custom trainable classifiers**. If an organization has classification needs that extend beyond what the pre-trained classifiers cover, it can create and train its own classifiers.

These classifier types are examined in the following sections.

#### Pre-trained classifiers

Microsoft 365 comes with multiple pre-trained classifiers:

 -  **Adult, Racy, and Gory**. Detects images of these types. The images must be between 50 kilobytes (KB) and 4 megabytes (MB) in size. They must also be greater than 50 x 50 pixels in height x width dimensions. Scanning and detection are supported for Exchange Online email messages and Microsoft Teams channels and chats.
 -  **Agreements**. This classifier detects content related to legal agreements. For example, statements of work, loan and lease agreements, and employment and non-compete agreements.
 -  **Customer Complaints**. The customer complaints classifier detects feedback and complaints made about your organization's products or services. This classifier can help you meet regulatory requirements on the detection and triage of complaints, like the Consumer Financial Protection Bureau and Food and Drug Administration requirements.
 -  **Discrimination**. This classifier detects explicit discriminatory language and is sensitive to discriminatory language against the African American/Black communities when compared to other communities.
 -  **Finance**. This classifier detects content in corporate finance, accounting, economy, banking, and investment categories.
 -  **Harassment**. This classifier detects a specific category of offensive language text items related to offensive conduct targeting one or multiple individuals based on the following traits: race, ethnicity, religion, national origin, gender, sexual orientation, age, disability.
 -  **Healthcare**. This classifier detects content in medical and healthcare administration aspects. For example, medical services, diagnoses, treatment, claims, and so on.
 -  **Human Resources (HR)**. This classifier detects content in human resources related categories. For example, recruitment, interviewing, hiring, training, evaluating, warning, and termination.
 -  **Intellectual Property (IP)**. This classifier detects content in Intellectual Property related categories such as trade secrets and similar confidential information.
 -  **Information Technology (IT)**. This classifier detects content in Information Technology and Cybersecurity categories. For example, network settings, information security, hardware, and software.
 -  **Legal Affairs**. This classifier detects content in legal affairs-related categories. For example, litigation, legal process, legal obligation, legal terminology, law, and legislation.
 -  **Procurement**. This classifier detects content in categories of bidding, quoting, purchasing, and paying for supply of goods and services.
 -  **Profanity**. This classifier detects a specific category of offensive language text items that contain expressions that embarrass most people.
 -  **Resumes**. This classifier detects docx, .pdf, .rtf, and .txt items that are textual accounts of an applicant's personal, educational, professional qualifications, work experience, and other personally identifying information.
 -  **Source Code**. This classifier detects items that contain a set of instructions and statements written in the top 25 used computer programming languages on GitHub: ActionScript, C, C\#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script.
    
        > [!NOTE]
        > The Source Code classifier is trained to detect when the bulk of the text is source code. It doesn't detect source code text that's interspersed with plain text.
 -  **Tax**. This classifier detects Tax relation content such as tax planning, tax forms, tax filing, tax regulations.
 -  **Threat**. This classifier detects a specific category of offensive language text items related to threats to commit violence or do physical harm or damage to a person or property.

These trainable classifiers appear in the **Microsoft Purview compliance** portal. In the navigation pane, select **Data classification**. On the **Data classification** page, select the **Trainable classifiers** tab. View the classifiers with the status of **Ready to use**.

#### Custom classifiers

For some organizations, the pre-trained classifiers don't meet their data classification needs. In this situation, an organization can create and train its own classifiers. There's more work involved with creating a custom classifier, but they'll be much better tailored to an organization's needs. The high-level steps involved in creating a custom classifier include:

1.  You start creating a custom trainable classifier by feeding it examples that are definitely in the category.
2.  Once the classifier processes those examples, you test it by giving it a mix of both matching and non-matching examples.
3.  The classifier then makes predictions as to whether any given item falls into the category you're building.
4.  You then confirm its results, sorting out the true positives, true negatives, false positives, and false negatives to help increase the accuracy of its predictions.
5.  Once you're satisfied with the test results, you deploy the classifier by publishing it.

When you publish the classifier, it sorts through items in locations like SharePoint Online, Exchange, and OneDrive, and classifies the content. After you publish the classifier, you can continue to train it using a feedback process that's similar to the initial training process.

For example you could create trainable classifiers for:

 -  **Legal documents**. For example, attorney client privilege, closing sets, and statements of work.
 -  **Strategic business documents**. For example, press releases, merger and acquisition, deals, business or marketing plans, intellectual property, patents, and design docs.
 -  **Pricing information**. For example, invoices, price quotes, work orders, and bidding documents.
 -  **Financial information**. For example, organizational investments, and quarterly or annual results.

### Prepare for a custom trainable classifier

It's helpful to understand what's involved in creating a custom trainable classifier before you dive in.

#### Timeline

The following diagram displays a timeline that reflects a sample deployment of trainable classifiers.

:::image type="content" source="../media/trainable-classifier-deployment-timeline_border-ef712e6d.png" alt-text="Diagram showing the timeline for creating a sample deployment of trainable classifiers.":::


> [!TIP]
> Opt-in is required the first time for trainable classifiers. It takes 12 days for Microsoft 365 to complete a baseline evaluation of an organization's content. A global administrator will be needed to kick off the opt-in process.

#### Overall workflow

To understand more about the overall workflow of creating custom trainable classifiers, see [Process flow for creating custom trainable classifiers](/microsoft-365/compliance/classifier-learn-about?azure-portal=true).

#### Seed content

Trainable classifiers are used to independently and accurately identify an item as being in particular category of content. To create a trainable classifier, an organization must first present it with many samples of the type of content that are in the category. This feeding of samples to the trainable classifier is known as **seeding**. An organization must select the seed content that it wants to use to represent the category of content.

> [!TIP]
> You must have at least 50 positive samples, with a maximum of 500. samples. The trainable classifier will process up to the 500 most recent created samples (by file created date/time stamp). The more samples you provide, the more accurate the predictions the classifier will make.

#### Testing content

Once the trainable classifier has processed enough positive samples to build a prediction model, the organization must test the predictions the classifier makes. You should test with different data than the initial seed data you first provided. The testing should verify whether the classifier can correctly distinguish between items that match the category and items that don't. Testing should begin by selecting another, hopefully larger, set of manually selected content. This sample is known as the test sample. It should consist of samples that fall into the category and samples that don't.

Once the classifier processes this test sample, you must manually review the results. When doing so, you should verify whether each prediction is correct, incorrect, or you aren't sure. The trainable classifier will use this feedback to improve its prediction model.

> [!TIP]
> For best results, have at least 200 items in your test sample. It should include an even distribution of positive and negative matches.

### How to create a trainable classifier

Complete the following steps to create, test, and publish a custom trainable classifier:

1.  Collect between 50-500 seed content items. These content items must be only samples that strongly represent the type of content you want the trainable classifier to positively identify as being in the classification category.
    
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
