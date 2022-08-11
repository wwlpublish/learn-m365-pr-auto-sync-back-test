Once you create a request, Priva immediately begins to look for matches to the data subject in content within your Microsoft 365 environment. Once we've identified all the items we think match your criteria, you'll see the estimate in the **Data estimate summary** card on the request's **Overview** page. The amount of data within the scope of your search will affect the length of time it takes to complete the estimate.

Your request will move automatically to the next stage of **Data retrieval**, where all the content items are gathered together for stakeholders to collaborate on reviewing the data. In some instances, we'll pause the data estimate before moving onto retrieval and notify you of next steps to take before continuing.

### Pause in data estimate

There are two reasons why a request will pause at the **Data estimate** stage:

1. When creating a request, you can choose to get an estimate first. See step 6 of [creating a custom request](/privacy/priva/subject-rights-requests-create#custom-setup-guided-process-to-choose-all-settings) for details.

2. If the estimate is projected to return a large number of items to review (over 10K items), the workflow pauses. At this point you can preview the results and decide whether to [edit your search query](/privacy/priva/subject-rights-requests-create#refining-your-search) or continue to retrieve the identified items.

When the request is paused at **Data estimate**, you'll see a card on your request's details page with summary information about the number of items, volume, their location, and a link allowing you to **View search query details**.

## View and edit search queries

To see detailed information about the request's search, select **View search query details** on the **Data estimate summary** card. A flyout pane opens which summarizes the query and shows further details about what was found. From here, you have the following options:

- Select **Preview results** to get a preview of the type of content that will be returned under the current search settings.
- Select **Edit search query** to change the search settings.

When you select **Edit search query**, you'll be led through a guided process to change or add properties to identify the data subject, change conditions, and adjust the locations you want the search to cover. Follow the instructions at [Refining your search](/privacy/priva/subject-rights-requests-create#refining-your-search) for more detailed information. You can review the final version of your new search query, then select **Save** to begin the search again.

A new estimate will be generated and the status of the request will go back to **Data estimate**. The new search may take up to 60 minutes to complete. Once it’s done, you’ll see updated results on the request’s details page.

When you're ready to proceed, select the **Retrieve data** in the upper right of your screen to advance to the data retrieval stage.

## Retrieve data

The data retrieval stage is when all the files, emails, chats, images, and other content items containing the data subject's personal data are retrieved. The items are put together in an Azure Blob Storage container for review. Data retrieval may take a few minutes or significantly longer depending on the volume of data.

When this stage is complete, the request moves automatically to the next stage of **Review data**.