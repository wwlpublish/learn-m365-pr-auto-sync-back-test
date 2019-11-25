As you build your add-in, you have many UI design factors to consider. The Office UI Fabric provides elements that adhere to Office branding so your add-in looks like a natural extension of Office. **Note**: Using UI Fabric is optional but recommended.

## About UI Fabric

Office UI Fabric has two (2) main areas:

1. Fabric Core - Provides basic elements like font, icons, and color
1. Fabric React components - Includes Fabric Core elements and adds input, navigation, and notification components, among others

### Fabric Core

Fabric Core provides basic design elements that reflect or sync with Office branding.

To start using Fabric Core, reference the CSS in your HTML page, as shown in the following code.

```html
<link rel="stylesheet" href="https://static2.sharepointonline.com/files/fabric/office-ui-fabric-core/9.6.1/css/fabric.min.css">
```

You can then use Fabric icons, fonts, and colors. The following example shows how you can include an extra-large table icon in the Office application's primary theme color.

```html
<i class="ms-Icon ms-font-xl ms-Icon--Table ms-fontColor-themePrimary"></i>
```

### Fabric components

Fabric React provides UX components for input, navigation, notification, and other categories. It builds on and includes Fabric Core.

Recommended components you can use in your add-in are as follows:

- Breadcrumb
- Button
- Checkbox
- ChoiceGroup
- Dropdown
- Label
- List
- Pivot
- TextField
- Toggle

> [!TIP]
> You can use the Yeoman generator for Office Add-ins to create a project that references Fabric React. An available project type is `Office Add-in Task Pane project using React framework`.
