Bookmarks and Q&As let you publish and promote the best possible results for high-value work searches. These answers help users easily navigate to internal sites and tools. For details about how Microsoft uses these answers to improve our internal search experience, see our [Internal search bookmarks boost productivity at Microsoft](https://www.microsoft.com/itshowcase/blog/internal-search-bookmarks-boost-productivity-at-microsoft/) blog post.

We'll cover several ways to create and publish relevant bookmarks and Q&As in this unit.

## Bookmarks

Bookmarks help people quickly find important sites and tools with just a search. Each bookmark includes a title, URL, a set of user-friendly keywords to trigger the bookmark, and a category.

:::image type="content" source="../media/m-3-u-2-all-serp-with-bookmark-answer.png" alt-text="Image showing Microsoft Search bookmark answer.":::

### Create a bookmark

1. Go to [**Bookmarks**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/bookmarks) in the [**Microsoft 365 admin center**](https://admin.microsoft.com/).
2. Select **Answers**, then **Bookmarks**.
3. Select **Add bookmark**.
4. Enter a title, URL, keywords, category, and other information. You can see a preview of the bookmark answer at the top of the panel.
5. Select **Publish** or **Save to draft**.

Publishing a bookmark immediately refreshes the search index, making it available to users right away.

### Review default and suggested bookmarks

Microsoft Search includes several default bookmarks your users may find helpful, including bookmarks for HR, benefits, and password management. To provide high-quality results to your users right away, we recommend you update and publish these default bookmarks. Just add the URL to point to the relevant intranet site. As an example, for the suggested bookmark "HR," add the URL for your HR department's intranet site and then publish.

Your users can also suggest bookmarks using the feedback links in Microsoft Search. Their recommendations will appear as suggested bookmarks.

### Recommended bookmarks and exclude URLs

To reduce the manual effort required to create bookmarks, Microsoft Search evaluates your organization's SharePoint links and recommends bookmarks. Search admins or editors can review them before publishing or set them to automatically publish. No setup is needed for recommended bookmarks; they're enabled and set to auto publish by default.

In search results, recommended bookmarks include the phrase "Suggested for you" before the URL. In the admin center, recommended bookmarks will have an Owner value of "SYSTEM."

To prevent the recommendation engine from publishing or suggesting a bookmark for a site, exclude the URL. The recommendation engine will never publish or suggest a bookmark for an excluded site or a page within an excluded site. Also, recommended bookmarks will never include URLs found in existing Published, Suggested, Scheduled, or Excluded bookmarks.

To review and publish suggested bookmarks:

1. Go to [**Bookmarks**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/bookmarks) in the [**Microsoft 365 admin center**](https://admin.microsoft.com/).
2. Select **Applied Filter: Status**.
3. Select the **Suggested** status.
4. Review the bookmark details and edit as needed. When done, select **Publish**.

To stop showing recommended bookmarks, turn the autopublish setting off in admin center. Recommended bookmarks will instead be added to the list of suggested bookmarks.

> [!Tip]
>
> Use categories to filter and organize your bookmarks.

## Q&As

Q&As let you create informative, rich-text answers for the most frequently asked questions in your organization. Like bookmarks, you create Q&As in the [Microsoft 365 admin center](https://admin.microsoft.com/). Q&As are indexed immediately when you add or update them.

:::image type="content" source="../media/m-3-u-2-all-serp-with-qna-answer.png" alt-text="Image showing Microsoft Search Q&A answer.":::

### Create a Q&A

To review and publish suggested Q&As:

1. Go to [**Q&As**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/qnas) in the [**Microsoft 365 admin center**](https://admin.microsoft.com/).
2. Select **Add question** or select a Q&A and select **Edit**.
3. As you add or edit the information, the preview automatically updates.
4. Select **Save to draft** or **Publish**.

:::image type="content" source="../media/m-3-u-2-admin-center-qna-edit-pane.png" alt-text="Image showing Microsoft Search Q&A answer edit pane and preview.":::

> [!Tip]
>
> When adding keywords, try to put yourself in the user’s mindset by imagining the words and phrases they might use while searching for the Q&A content you’re creating. As with bookmarks, you can ensure your users always find a specific result by using a reserved keyword.

## Schedule answers and conditional access

You can configure bookmarks and Q&As to only appear when certain conditions are met. For example:

* Specify countries or regions, and only users with their browser set to a targeted locale will see that result. For example, a North American help desk number only appears for users in that region.
* Specify an expiration date for a result, and it automatically disappears after the date passes.
* Specify other targets and results will only appear to members of a specific group, device type, OS, or user location. For example, make an iOS-specific Q&A appear only on iOS.

:::image type="content" source="../media/m-3-u-2-admin-center-qna-edit-pane-settings.png" alt-text="Image showing Q&A settings pane in Microsoft 365 admin center.":::
