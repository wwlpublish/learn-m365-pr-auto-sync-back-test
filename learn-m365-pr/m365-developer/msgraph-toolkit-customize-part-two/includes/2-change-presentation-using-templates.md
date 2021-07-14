Microsoft Graph Toolkit provides support for creating custom templates that can change how data is displayed by components.

Suppose you're planning to build a web application to show upcoming events to the signed-in user. For this project, instead of using the default Microsoft Graph Toolkit Login component experience, you want to modify the signed-in button that shows the user's profile.

You can use the Login component's templating to easily change the presentation of the signed-in user's profile. You can also choose the specific data to display, such as the user's display name, given name, job title, mail, or phone number.

To add templating to Microsoft Graph Toolkit components, you can use the `<template>` HTML element. For example, you can add templating to the Login component.

```html
<mgt-login>
	<template> 
	</template>
</mgt-login>
```

## Define a part of the component you want to template

Multiple data parts are available to template for each component. You can define the part you want to template by using the `data-type` attribute on the `<template>` element. For example, if you want to template the signed-in button part in the Login component, add a `data-type` attribute with a value of `signed-in-button-content`.

```html
<mgt-login>
	<template data-type=”signed-in-button-content”> 
	</template>
</mgt-login>
```

## Select the data to bind to a template

The templates for Microsoft Graph Toolkit components help you select and display specific data context in your app. Now that you've defined `signed-in-button-content` as the data-type value of the template, suppose you want to display the user's first name in the signed-in button.

The Login component passes a `{personDetails}` object to the component at runtime. The `{personDetails}` object provides all the details about the user. You can use the `{personDetails}` object in the template to display any user data you want. For example, to display the user's given name, add `{personDetails.givenName}` in the template.

```html
<mgt-login>
    <template data-type=”signed-in-button-content”> 
        <div>{{personDetails.givenName}}</div>
    </template>
</mgt-login>
```

> [!Tip]
>To see what data is available in the template, enter `{{ this }}`. This step shows you the whole object bound to the template. If the `{personDetails.givenName}` value is Megan, the button content looks like the following example.

>:::image type="content" source="../media/2-tip.png" alt-text="Screenshot that shows Microsoft Graph Toolkit components with templates.":::

In the next exercise, you'll learn how to use templates with Microsoft Graph Toolkit components to modify the presentation of data.
