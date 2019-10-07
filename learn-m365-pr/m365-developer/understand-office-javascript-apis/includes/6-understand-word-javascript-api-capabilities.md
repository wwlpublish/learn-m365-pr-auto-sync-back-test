The Word JavaScript APIs give your add-ins access to Word documents. A Word add-in can manage the content, formatting, and structure of a document.

## Object model

To understand the Word APIs, you must see how the main components of a document relate to each other.

- A **Document** contains a **Body** and at least one **Section**.
- A **Body** can contain:
  - **Paragraph** (one or more)
  - **Table** (one or more)
  - **List** (one or more)
  - **Text**
  - Objects like images and lists
- A **Section** gives access to its body, headers, and footers.

## Key scenarios

In this section, you'll learn about a couple of key scenarios for Word APIs.

- Document assembly
- Search

> [!NOTE]
> You can apply simple formatting to an entire existing document using the Office.js APIs. However, if you wish to apply complex formatting or use rich content objects, you can use Office Open XML (OOXML) to create these effects. Examples of capabilities in OOXML include applying drop shadows to text or pictures, coercing text boxes into shapes, and inserting Excel charts as live charts in Word documents. Because this is a more advanced skill, we will not cover this subject in its entirety but mention it for developers who are familiar with OOXML.

### Work with document text

Word add-ins use the `Office.onReady()` event handler to start. If the add-in targets Word 2016 or later, it calls the `Word.run()` method to run Word JavaScript APIs. The add-in must pass a function to `Word.run()` that expects a context object to be passed as the parameter. The context object allows the add-in to interact with the Word document. You can use the context object to create any needed proxy objects for the Word document and load the proxies with any properties you wish to use. You can also program actions to run using those properties. As always, a `context.sync()` command then synchronizes the state between the proxy objects and objects in the Word document.

The following example shows code that inserts text after the body text of a Word document. For simplicity, this sample omits the `Office.onReady()` code and focuses on the code within a `Word.run()` code block.

```js
// Run a batch operation against the Word JavaScript API.
Word.run(function (context) {
    // Create a proxy object for the document body.
    var body = context.document.body;

    // Queue a command to load the text property of the proxy body object.
    body.load("text");

    // Queue a command to insert text into the end of the Word document body.
    body.insertText('This is text inserted after loading the body.text property',
                    Word.InsertLocation.end);

    // Synchronize the document state by executing the queued commands,
    // and return a promise to indicate task completion.
    return context.sync().then(function () {
        console.log("Body contents: " + body.text);
    });
})
```

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

To start developing a Word add-in, use:

- The Yeoman generator for Office Add-ins
- Visual Studio

If you want to explore the APIs more, the Script Lab add-in is recommended. There, you'll see numerous samples and be able to experiment with Word documents without creating an entire add-in.
