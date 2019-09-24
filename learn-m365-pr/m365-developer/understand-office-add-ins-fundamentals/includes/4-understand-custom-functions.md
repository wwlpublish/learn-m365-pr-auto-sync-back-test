Office Add-ins enable you to create custom functions which are your own defined JavaScript or TypeScript functions that can be accessed like native or built-in Excel functions.

![Custom function being activated in Excel](../media/sphere-volume.gif)

*Custom function*

## Components of a custom function

Like other types of Office Add-ins, a custom function add-in has two main components:

- Manifest (XML) for configuration
- Webpage (HTML, JavaScript) for functionality

In the manifest, the key settings are that the `Host` is "Workbook" and the `ExtensionPoint` is "CustomFunctions". The .html file is primarily to load the custom functions runtime as there is no UI to render *per se*. You define the custom function itself in the .js or .ts file.