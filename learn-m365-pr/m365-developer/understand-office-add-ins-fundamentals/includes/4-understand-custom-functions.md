Office Add-ins enable you to create custom JavaScript or TypeScript functions that can be accessed like built-in Excel functions such as `SUM()`.

The following image shows a custom function called `SPHEREVOLUME` being entered in Excel.

![Custom function being entered in Excel](../media/sphere-volume.gif)

*Custom function being entered in Excel*

The following code sample shows the JavaScript code for the `SPHEREVOLUME()` function shown previously.

```js
/**
 * Returns the volume of a sphere.
 * @customfunction
 * @param {number} radius
 */
function sphereVolume(radius) {
  return Math.pow(radius, 3) * 4 * Math.PI / 3;
}
```

## Where can you use custom functions?

Custom functions are available in Excel on the following platforms.

- Windows (connected to an Office 365 subscription)
- Mac (connected to an Office 365 subscription)
- Web browser

## Define the custom function add-in type

To configure an add-in to contain custom functions, the key settings in the manifest are as follows for Excel add-ins.

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
