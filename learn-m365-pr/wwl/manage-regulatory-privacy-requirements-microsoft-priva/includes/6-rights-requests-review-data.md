After data has been collected for a subject rights request, the next stage is to review the content items, decide what items to include or exclude as part of the request, and redact information if necessary.

:::image type="content" source="../media/review-data-priva-rights-request.png" alt-text="Screenshot showing the results of a Subject Rights Request." lightbox="../media/review-data-priva-rights-request.png":::

## Tasks for completing the data review

The **Review data** stage is when collaborators examine the content items on the **Data collected** tab. A Teams channel will automatically be set up to facilitate content review by all stakeholders. See [Collaboration for data review](#collaboration-for-data-review) below for more details. The essential tasks for the data review step are outlined below.

### Import additional files

You may want to bring additional content items into the request for your data review. For example, files stored outside your organization's Microsoft 365 environment, or other items you think are relevant but weren't scoped in the search. You can import files into the **Data collected** tab of an individual request to be reviewed and worked on, along with the other items. Imported files are added to the same Azure Blob Storage container with the other content items retrieved from your search.

Follow the steps below to import files:

1. From the request details page, select **Import files** from the command bar at the top of the page.

2.  An **Import files** box will appear on the screen. Select **Choose files**, and from your file explorer view, choose one or more files to import.

3. You'll be taken back to the **Import files** box, which lists the files you chose. You can select **Choose files** again to add more items to the list. To remove any of the files, select **Clear**, which removes all files, and choose files again.

4. When all desired files are listed in the **Import files** box, select **Import**. To exit without uploading, select **Cancel import**.

When the import begins, you'll be taken back to the request's **Data collected** tab. A message above the tab indicates your upload is in progress. If there's a problem with the upload, the message will tell you and provide an option to retry.

You'll see a confirmation message above the **Data collected** tab when the import is complete.

**More details about importing files:**

- Individual file size can't exceed 4 MB. You'll see a warning message on the **Import files** box when a file's too large to upload.

- It may take up to 20 minutes before the imported files are available in the **Data collected** tab.

- If an import is already in progress for one user, the same user won't be able to upload additional files until the previous upload process finishes. Multiple users can upload files to the same request simultaneously. However, the more uploads that are in progress, the longer they'll take to complete. Status messages on the request will inform when an upload has finished and files are ready to review.

### Mark items as Include or Exclude and add notes

Review the items listed on the request's **Data collected** tab.  If you decide that the item should be included as part of the final report back to the data subject, select **Include** on the command bar across the top of the list of items. You can also select the blue **Include** button in the content review area to the right of the list of items. When you select **Include**, a flyout pane appears with an option to add notes. When you're done, select **Submit** to save the item's review status as **Include**.

If the item doesn't belong as part of the request, you can select **Exclude** on the command bar or the **Exclude** button in the content review area. Marking an item explicitly as **Exclude** is often required for internal records.

By default, only items you mark as **Include** will be included in the [final reports that are generated for the data subject](/privacy/priva/subject-rights-requests-reports).

> [!NOTE]
> If you mark an item as **Exclude**, you're required to add a note as justification for why it doesn't pertain to the subject rights request. Notes are for internal purposes and aren't included in final reports.

If the content appears to be a false positive for your search query, select **Not a match** and on the flyout pane, select **Confirm**. This action will flag the item as something that shouldn't have been detected in the search.

### Apply tags

Tags can be used to help you identify items that need further attention. Priva provides three default tags—**Follow-up**, **Delete**, and **Update**—for which you can set a description. Priva also provides two custom tags that you can name and describe.

For example, if you determine during data review that a content item doesn't need to be kept by your organization, you can apply the **Delete** tag, then export a list of all the tagged files so that you can go back and delete the identified items when you're done with the request.

The five tags that you manage in **Settings** apply to all of your subject rights requests.

**To add or remove tags:**

- Select the item from the list on the **Data collected** tab of the request.
- In the item preview area to the right of the list, select the **Apply tags** button on the bottom row. You can also select the three dots to the right of the item name and select the **Apply tags** option.
- A flyout pane appears with the list of tags. Check the box next to any of the tags you want to apply to the item. Unchecking a checked box will remove the tag.
- When you're done select **Save**, which saves your tag selections and closes the flyout pane.

**To add custom tags or update tag descriptions:**
- From the Subject Rights Requests page, select **Settings** in the upper right corner of your screen to get to your Priva settings.
- Go to the **Data review tags** page, and select the tag to input a description and, for the custom tags, a name. Learn more about [tag settings](/privacy/priva/priva-settings#data-review-tags).

**To export a list of tagged items:**
- Go to the **Data collected** page in a subject rights request.
- Above the list of items, select the **Export** command.
- An Excel file will download which shows the properties for all the items collected by the search for the request. Find the **Tags** column to identify and sort the items by tag.

### Use the Annotate command to redact text

The **Annotate** command in the content review area lets you create inline mark-ups and redact data within a content item. For example, if you need to include a file for an individual that also contains the personal information of a different data subject, you can use **Area redaction** under the Drawing button in the command bar to black out all information that doesn't pertain to the person who made the request. When your edits are complete, select **Include** to add the redacted file to the request. Annotation creates a copy of the file, which is stored in your Azure blob. The original file remains unaltered and stored in its original location.

### Enter notes about a file
To add or review notes on an item, select the item from its row and go to the **File Notes** tab in the content review area to the right. You can also use the **Add file note** option to create a new comment. To review or add notes at an overall case level, go to the main **Notes** tab above and use **Add case note**. These notes will be visible to users working on the request, but won't be included in the final report or otherwise shared with the data subject.

## Collaboration for data review

Subject Rights Request Administrators can view all requests. You can add other users to collaborate on a request, which will give them access to view that request and work with the data collected within it to help move the request to completion.

When you create a request, a dedicated Teams channel is automatically created for stakeholders to discuss the request and safely share input and contributions. The **Collaborators** tab on the request details page shows all the collaborators who can view and contribute to the request and to any associated Teams channel.

To add more collaborators, select **Add collaborator**, begin typing in the user's name, select the name once it appears, then select **Add**.

To start a Teams chat, any collaborator can select **Chat with collaborators** in the upper right of the request's details page. This action opens Teams and places you in the **General** channel for your subject rights request's Team site.

You can change the default behavior of creating Teams channels for subject rights requests by going to Priva **Settings** in the top right corner of Subject Rights Request. Select **Teams collaboration**, then uncheck the box on the page to turn off Teams capabilities for all subject rights requests.

The **Share** command in the upper right of a request's details page creates a shareable link that goes directly to the request in Priva. Give this link to collaborators so that they can access the request you've added them to.

## Complete the review

When all items have been reviewed and you've set their status as **Include**, **Exclude**, or **Not a match,** it's time to close out the review step. Any of the collaborators on a request can complete the review.

Select the **Complete review** button in the upper right corner of the request. A flyout pane will show a summary of the data and add any related notes. These notes are for internal record keeping and aren’t shared with the data subject.

Select **Complete review** on the flyout pane to finish the review step. This action prepares the request for the final stages of the process: generating reports and closing the request. Summaries of your decisions will be provided later under the **Reports** tab.