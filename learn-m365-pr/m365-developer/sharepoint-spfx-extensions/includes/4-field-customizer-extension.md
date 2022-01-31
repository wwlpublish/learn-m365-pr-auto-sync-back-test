In this unit, you'll learn about another type of SharePoint Framework extension that enables customization of columns in SharePoint lists: field customizers.

## Overview

A SharePoint Framework field customizer extension enables developers to customize the rendering of a field in a SharePoint list view. These extensions are similar to the SharePoint classic experience customizations of client-side rendering (CSR) and JSLink. The classic mode customizations of CSR and JSLink don't work in the modern experience and field customizers will only work in the modern experience.

A field customizer enables a developer to define through code how a specific column should be rendered when a user views a SharePoint list in the grid-view format in the modern experience. The following scenarios are some example use cases for field customizers:

- display a picture or illustration in a field instead of text
- make renderings interactive
- add React component to a field rendering.

![Screenshot of the field customizer](../media/05-field-customizer-test.png)

## Field customizer class

The implementation of a field customizer is similar to the other SharePoint Framework extension options.

An interface is used to define the public properties that can be set as inputs on the extension.

```typescript
export interface IPercentCompleteFieldCustomizerProperties {
  yellowMinLimit?: string;
}
```

The extension is implemented in a class that extends the `BaseFieldCustomizer` class. This class contains three methods you can override:

The `onInit()` method returns a `Promise` object and can be used to do any initialization code that needs to be completed before rendering the field customizer. Once the returned promise resolves, the SharePoint Framework will call the `onRenderCell()` method.

The `onRenderCell()` method receives a single parameter of type `IFieldCustomizerCellEventParameters` that developers can use to obtain the value of the field for the current list item and modify the contents of the cell associated with the field.

The last method, `onDisposeCell()`, is called by the SharePoint Framework when the field is removed from the page. You should use this method to clean up any references or handlers you've setup in either the `onInit()` or `onRenderCell()` methods.

```typescript
export default class PercentCompleteFieldCustomizer
  extends BaseFieldCustomizer<IPercentCompleteFieldCustomizerProperties> {

    @override
    public onInit(): Promise<void> { }

    @override
    public onRenderCell(event: IFieldCustomizerCellEventParameters): void { }

    @override
    public onDisposeCell(event: IFieldCustomizerCellEventParameters): void { }
}
```

## Field customizer deployment as site columns

Field customizers are deployed to SharePoint as new site columns. To associate a field customizer with a site column defined with the declarative option using the `<Field>` element, set the `ClientSideComponentId` property to the unique ID of the field customizer component define in its manifest file. SharePoint will load the installed field customizer on the page when a list containing the site column is displayed on the page.

> [!IMPORTANT]
> You must ensure that the field customer is installed in a site wherever the site column is used.

Developers can set the public properties on the field customizer using the `ClientSideComponentProperties` property on the site column's `<Field>` element. The value of this property should be set to an XML encoded JSON string of the properties.

You can also add a field customizer to site column programmatically by setting properties `ClientSideComponentId` and `ClientSideComponentProperties` are available on the `Field` object.

## Debugging and testing extensions

Now let's look at how you can debug and test SharePoint Framework field customizer extensions. The SharePoint workbench doesn't support testing extensions. However, you can still build and host extensions projects locally while debugging and testing in a remote SharePoint site.

To test a field customizer extension, you include special query string parameters to the URL of a live SharePoint modern page, list, or library. These parameters instruct SharePoint to do the following things:

- load the SharePoint Framework on the page if it isn't already present
- the location of the **manifest.js** file from the local web server that tells SharePoint what custom components can be put on the page
- which component the SharePoint Framework should load and put on the page
- additional properties specific to each component

The Yeoman generator for the SharePoint Framework simplifies this process fo you by creating a configuration that the **gulp serve** task uses to create the debugging URL. These settings are defined in the **./config/serve.json** file.

When SharePoint receives the request with these query string parameters, it will first prompt the user to confirm they want to load debugging scripts. SharePoint does this same technique could be used in a phishing attack. So, you should only load the debugging scripts if you're sure you started the request.

When testing a field customizer using the query string option, take note of the `InternalFieldName` property in the **serve.json** file. You must update that property to match the name of the column's internal name property that you want to map the field customizer to during testing.

For example, the following excerpt from the **serve.json** file will attach the extension to the column with an internal field name `InternalFieldName`:

```json
"helloFieldCustomizer": {
  "pageUrl": "https://contoso.sharepoint.com/sites/mySite/SitePages/myPage.aspx",
  "fieldCustomizers": {
    "InternalFieldName": {
      "id": "a50d3e32-b8e7-44ad-94ad-eb5be4a5d007",
      "properties": {
        "sampleText": "Value"
      }
    }
  }
}
```

To attach the extension to a field named `PercentComplete`, change the `InternalFieldName` property to the new field name:

```json
"helloFieldCustomizer": {
  "pageUrl": "https://contoso.sharepoint.com/sites/mySite/SitePages/myPage.aspx",
  "fieldCustomizers": {
    "PercentComplete": {
      "id": "a50d3e32-b8e7-44ad-94ad-eb5be4a5d007",
      "properties": {
        "sampleText": "Value"
      }
    }
  }
}
```

## Summary

In this unit, you learned about another type of SharePoint Framework extension that enables customization of columns in SharePoint lists: field customizers.
