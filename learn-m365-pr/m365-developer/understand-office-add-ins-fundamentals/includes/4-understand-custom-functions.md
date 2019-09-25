Office Add-ins enable you to create custom JavaScript or TypeScript functions that can be accessed like built-in Excel functions such as SUM().

![Custom function being activated in Excel](../media/sphere-volume.gif)

*Custom function*

## Components of a custom function

Like task panes and other types of Office Add-ins, a custom function add-in has two main components:

- Manifest (XML) for configuration
- Webpage (HTML, JavaScript) for functionality

### Manifest

To configure an add-in as a custom function, the key areas in the manifest are:

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

The webpage HTML loads the custom functions runtime, which then runs your custom functions written in JavaScript or TypeScript. The custom functions runtime doesn't have a UI, so there's nothing for the webpage to display.

```html
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/custom-functions-runtime.js" type="text/javascript"></script>
```

Typically custom functions are combined with a task pane in the same add-in. So often you should include a second webpage in your project that loads the task pane to handle user interaction in Excel.

## Where can you use custom functions?

Custom functions are available in Excel on the following platforms.

- Windows (connected to an Office 365 subscription)
- Mac (connected to an Office 365 subscription)
- Web browser
