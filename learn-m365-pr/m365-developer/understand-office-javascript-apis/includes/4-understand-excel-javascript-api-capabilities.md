The Excel JavaScript APIs give your add-ins access to Excel workbooks. An Excel add-in can edit data, format cells, create visualizations, and control the performance of the workbook.

## Object model

To understand the Excel APIs, you must see how the components of a workbook are related to one another.

- A **Workbook** contains one or more **Worksheets**.
- A **Worksheet** gives access to cells through **Range** objects.
- A **Range** represents a group of contiguous cells.
- **Ranges** are used to create and place **Tables**, **Charts**, **Shapes**, and other data visualization or organization objects.
- A **Worksheet** contains collections of those data objects that are present in the individual sheet.
- **Workbooks** contain collections of some of those data objects (such as **Tables**) for the entire **Workbook**.

## Ranges

A range is a group of contiguous cells in the workbook. The Excel JavaScript APIs typically use A1-style notation (for example, `B3` for the single cell in row B and column 3 or `C2:F4` for the cells from rows C through F and columns 2 through 4) to define ranges.

Ranges have three core properties: `values`, `formulas`, and `format`. They get or set the cell values, formulas to be evaluated, and the visual formatting of the cells.

### Range sample

The following sample shows how to create sales records. It uses `Range` objects to set the values, formulas, and formats.

```js
// A function to create sales records.
Excel.run(function (context) {
    // Get the active worksheet.
    var sheet = context.workbook.worksheets.getActiveWorksheet();

    // Create the headers and format them to stand out.
    var headers = [
        ["Product", "Quantity", "Unit Price", "Totals"]
    ];
    var headerRange = sheet.getRange("B2:E2");
    headerRange.values = headers;
    headerRange.format.fill.color = "#4472C4";
    headerRange.format.font.color = "white";

    // Create the product data rows.
    var productData = [
        ["Almonds", 6, 7.5],
        ["Coffee", 20, 34.5],
        ["Chocolate", 10, 9.56],
    ];
    var dataRange = sheet.getRange("B3:D5");
    dataRange.values = productData;

    // Create the formulas to total the amounts sold.
    var totalFormulas = [
        ["=C3 * D3"],
        ["=C4 * D4"],
        ["=C5 * D5"],
        ["=SUM(E3:E5)"]
    ];
    var totalRange = sheet.getRange("E3:E6");
    totalRange.formulas = totalFormulas;
    totalRange.format.font.bold = true;

    // Display the totals as US dollar amounts.
    totalRange.numberFormat = [["$0.00"]];

    // Send the calls to the workbook and wait for it to be updated.
    return context.sync();
});
```

![A sales record showing value rows, a formula column, and formatted headers.](../media/range-sample.png)

## Charts, tables, and other data objects

The Excel JavaScript APIs let your add-in create and manipulate the data tools within Excel. Tables and charts are two of the more commonly used objects, but the APIs support PivotTables, Shapes, Images, and other such constructs.

### Creating a table

You can create a table using a data-filled range. The APIs layer the table controls (such as filters) and formatting on top of the range.

The following sample creates a table using the ranges from the previous sample.

```js
var productTable = sheet.tables.add("B2:E5", true);
```

![A table made from the previous sales record.](../media/table-sample.png)

### Creating a chart

You can create a chart to visualize the data in a range. The Excel APIs offer dozens of chart varieties, each of which can be customized to suit your needs.

The following sample creates a simple column chart for three items.

```js
var productBarChart = sheet.charts.add(Excel.ChartType.columnStacked, sheet.getRange("B3:C5"));
```

![A column chart showing quantities of three items from the previous sales record.](../media/chart-sample.png)

## Get started developing Excel add-ins

To start developing a Word add-in, use:

- The Yeoman generator for Office Add-ins
- Visual Studio

If you want to explore the APIs more, the Script Lab add-in is recommended. There, you'll see numerous samples and be able to experiment with Excel workbooks without creating an entire add-in.
