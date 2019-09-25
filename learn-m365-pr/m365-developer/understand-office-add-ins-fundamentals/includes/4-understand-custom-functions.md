Office Add-ins enable you to create custom JavaScript or TypeScript functions that can be accessed like native or built-in Excel functions.

![Custom function being activated in Excel](../media/sphere-volume.gif)

*Custom function*

## Components of a custom function

Like other types of Office Add-ins, a custom function add-in has two main components:

- Manifest (XML) for configuration
- Webpage (HTML, JavaScript) for functionality

### Manifest

To configure an add-in as a custom function, the key settings in the manifest are:

- `Host` is "Workbook"
- `ExtensionPoint` is "CustomFunctions"

### Webpage

The .html file is primarily to load the custom functions runtime as there's no add-in UI to render. You define the custom function code in the .js or .ts file.

## Where can you use custom functions?

Custom functions are available in Excel on the following platforms.

- Windows (version 1904 or later, connected to an Office 365 subscription)
- Mac (version 16.24 or later, connected to an Office 365 subscription)
- web browser