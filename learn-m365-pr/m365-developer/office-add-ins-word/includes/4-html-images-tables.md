In this unit, you'll learn how to work with HTML, images, and tables in Microsoft Word documents using the Office JavaScript API.

## Work with HTML in Word documents

Many developers will find it easier to interact with a Word document as HTML rather than using the Open Office XML (OOXML). Open Office XML tends to be cryptic and difficult for developers to decipher.

Office.js enables developers to write or read content in a Word document as familiar HTML. The document body, paragraphs, and ranges can all be manipulated as HTML using the `getHtml()` and `insertHtml()` methods in the Word JavaScript API.

The following code writes a block of HTML at the end of a paragraph. This same code can also be used for the document body and a range of content:

```javascript
paragraph.insertHtml('<p style="font-family: verdana;">Inserted HTML.</p><p>Another paragraph</p>', "End");
```

To retrieve the contents of a paragraph as HTML, use the `getHtml()` method as the following code demonstrates:

```javascript
const html = paragraph.getHtml();
```

## Work with images in Word documents

Images can be challenging to work with in JavaScript, but Office.js allows images to be manipulated as base64 encoded strings. Images can be inserted into the body, paragraphs, or ranges of a document. Each of these objects has an `inlinePictures` collection that developers can write to.

Office.js allows you to manipulate how images are displayed in the document through properties such as `lockAspectRatio`, `height`, and `width` among others.

The following code returns a collection of all inline pictures in the body of the document:

```javascript
const images = body.inlinePictures;
```

In the To insert an image into the body of the document, use the `insertInlinePictureFromBase64()` method, passing in the base64 string representation of the image and if the image should be added to the `Start` or `End` of the collection:

```javascript
const base64Image = "..";
context.document.body.insertInlinePictureFromBase64(base64Image, "End");
```

You can also get the base64 encoded string of an image in a document using the `getBase64ImageSrc()` as the following code demonstrates:

```javascript
const someInlinePicture = body.inlinePictures[0];
const base64 = someInlinePicture.getBase64ImageSrc();
```

Finally, you can lock the aspect ratio of an image and set the dimensions of the picture using the provided properties such as `width`:

```javascript
someInlinePicture.lockAspectRatio = true;
someInlinePicture.width = 400;
```

## Work with tables in Word documents

Office.js enables developers to insert a table relative to paragraphs, ranges, and the body of a document.

The `insertTable()` method specifies the dimensions of the table and where to insert it. Data is added to the table by passing in a two-dimensional array of values to the `insertTable()` method.

The `tables` property allows tables to be accessed and manipulated in JavaScript on the `body` and `range` objects.

> [!IMPORTANT]
> While a table can be inserted into the document relative to a paragraph, it doesn't exist within the paragraph. This differs from inline images covered in the previous section that are added to paragraphs.

The following code demonstrates how to get a reference to all the tables in the body of a document.

```javascript
const originalRange = context.document.body.tables;
```

> [!NOTE]
> While the previous code uses the `body` property on a document, the `tables` collection also exists on ranges as well.

To add a table with three columns and three rows of data, first create a two-dimensional array that contains the content and include it as one of the arguments to the `insertTable()` method.

```javascript
const tableData = [
  ["Name", "ID", "Birth City"],
  ["Bob", "434", "Chicago"],
  ["Sue", "719", "Havana"],
];
paragraph.insertTable(3, 3, "After", tableData);
```

The table object contains properties to retrieve the number of rows in a table, using the `rowCount` property, and the contents of the table, using the `values` property:

```javascript
const rows = table.rowCount;
const array2D = table.values;
```

## Summary

In this unit, you learned how to work with HTML, images, and tables in Microsoft Word documents using the Office JavaScript API.
