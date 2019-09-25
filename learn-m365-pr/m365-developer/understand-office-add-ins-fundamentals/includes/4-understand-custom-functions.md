Office Add-ins enable you to create custom JavaScript or TypeScript functions that can be accessed like native or built-in Excel functions.

![Custom function being activated in Excel](../media/sphere-volume.gif)

*Custom function*

## Components of a custom function

Like other types of Office Add-ins, a custom function add-in has two main components:

- Manifest (XML) for configuration
- Webpage (HTML, JavaScript) for functionality

### Manifest

To configure an add-in as a custom function, the key settings in the manifest are:

```xml
<OfficeApp
  ...
  xsi:type="TaskPaneApp">
   ...
  <Hosts>
    <Host Name="Workbook"/>
  </Hosts>
   ...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/taskpaneappversionoverrides" xsi:type="VersionOverridesV1_0">
    <Hosts>
      <Host xsi:type="Workbook">
        <AllFormFactors>
          <ExtensionPoint xsi:type="CustomFunctions">
            ...
          </ExtensionPoint>
        </AllFormFactors>
      </Host>
    </Hosts>
   ...
  </VersionOverrides>
</OfficeApp>
```

### Webpage

You define the custom function code in a .js or .ts file. The .html file is primarily to load the custom functions runtime as there's no add-in UI to render.

```html
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/custom-functions-runtime.js" type="text/javascript"></script>
```

## Where can you use custom functions?

Custom functions are available in Excel on the following platforms.

- Windows (version 1904 or later, connected to an Office 365 subscription)
- Mac (version 16.24 or later, connected to an Office 365 subscription)
- web browser
