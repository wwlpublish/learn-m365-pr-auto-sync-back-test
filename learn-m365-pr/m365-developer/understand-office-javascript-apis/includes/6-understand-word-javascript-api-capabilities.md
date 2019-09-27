The Word JavaScript APIs give your add-ins access to Word documents. A Word add-in can manage the content, formatting, and structure of a document.

## Object model

To understand the Word APIs, you must see how the main components of a document relate to each other.

- A **Document** contains a **Body** and at least one **Section**.
- A **Body** can contain the following.
  - **Paragraph** (one or more)
  - **Table** (one or more)
  - **List** (one or more)
  - **Text**
  - Objects like images and lists
- A **Section** gives access to its body, headers, and footers.

## Key features

### Document assembly

### Templates and placeholders

### Search

You can use the APIs to search the document for text that meets your criteria. You can also scope your search to certain types of content, for example, paragraphs or tables.

The following sample searches for the text "video you" and ignores punctuation. If the text is found, the matches are bolded, highlighted in yellow, and the font color set to purple.

```js
// Run a batch operation against the Word object model.
Word.run(function (context) {

    // Queue a command to search the document and ignore punctuation.
    var searchResults = context.document.body.search('video you', {ignorePunct: true});

    // Queue a command to load the search results and get the font property values.
    context.load(searchResults, 'font');

    // Synchronize the document state by executing the queued commands,
    // and return a promise to indicate task completion.
    return context.sync().then(function () {
        console.log('Found count: ' + searchResults.items.length);

        // Queue a set of commands to change the font for each found item.
        for (var i = 0; i < searchResults.items.length; i++) {
            searchResults.items[i].font.color = 'purple';
            searchResults.items[i].font.highlightColor = '#FFFF00'; //Yellow
            searchResults.items[i].font.bold = true;
        }

        // Synchronize the document state by executing the queued commands,
        // and return a promise to indicate task completion.
        return context.sync();
    });  
})
.catch(function (error) {
    console.log('Error: ' + JSON.stringify(error));
    if (error instanceof OfficeExtension.Error) {
        console.log('Debug info: ' + JSON.stringify(error.debugInfo));
    }
});
```

## Get started developing Word add-ins

Use the yeoman generator to start developing a Word add-in. If you want to explore the APIs more, we recommend Script Lab for Word. There, you'll see numerous samples and be able to experiment with Word documents without creating an entire add-in.
