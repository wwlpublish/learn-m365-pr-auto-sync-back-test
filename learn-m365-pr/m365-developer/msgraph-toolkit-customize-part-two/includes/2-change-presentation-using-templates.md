Microsoft Graph Toolkit provides support for creating custom templates that can change how data is displayed by components.

Suppose you are planning to build a web application to show upcoming events to the signed in user. For this project, instead of using the default Microsoft Graph Toolkit **Login** component experience, you would like to modify the signed in button that shows the user’s profile. You can leverage the Login component's templating to easily change the presentation of the signed in user’s profile. You can also choose the specific data to display such as the user’s display name, given name, job title, mail, or phone number. 

To add templating to Microsoft Graph Toolkit components, you can use the `<template>` HTML element. For example, you can add templating to the **Login** component as shown below:

```html
<mgt-login>
	<template> 
	</template>
</mgt-login>
```
## Define a part of the component you want to template

There are multiple data parts available to template for each component. You can define the part you want to template by using the `data-type` attribute on the `<template>` element. For example, if you would like to template the signed in button part in the **Login** component, you can add a `data-type` attribute with a value of `signed-in-button-content` as shown 
next:

```html
<mgt-agenda>
	<template data-type=”signed-in-button-content”> 
	</template>
</mgt-agenda>
```

## Select the data to bind to a template

The templates for Microsoft Graph Toolkit components help you select and display specific data context in your app.   Suppose you would like to display the user’s first name in the signed in button. After you define `signed-in-button-content` as the data-type value of the template, the following steps will occur:  

1. The Login component will pass a `{personDetails}` object to the component at runtime. The `{personDetails}` object provides all the details about the user.
2. The `{personDetails}` object can then be used in the template to display any user data you'd like. For example, to display the user's given name, `{personDetails.givenName}` can be added in the template.

    ```html
    <mgt-login>
    	<template data-type=”signed-in-button-content”> 
    		<div>{{personDetails.givenName}}</div>
    	</template>
    </mgt-login>
    
    ```

> [!Tip]
>To see what data is available in the template, type `{{ this }}`. This will show you the whole object bound to the template. If the `{personDetails.givenName}` value is Megan, the button content will look like the following:
>:::image type="content" source="../media/2-tip.png" alt-text="A screenshot that shows how Microsoft Graph Toolkit components with templates.":::

In the next exercise, you'll learn how to use templates with Microsoft Graph Toolkit components to modify the presentation of data.