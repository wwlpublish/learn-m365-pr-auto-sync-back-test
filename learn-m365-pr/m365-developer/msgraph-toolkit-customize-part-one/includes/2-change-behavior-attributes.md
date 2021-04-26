Microsoft Graph Toolkit provides a list of attributes for each component that can be used for changing the behavior of the component. The attributes vary for each component and help you customize the behavior of the component according to your needs.

Suppose you're using the **People** component in your app and you would like to display only five people in the list. You can use `show-max` attribute to change the behavior of `mgt-people` and limit the number of people as shown below:

```html
<mgt-people show-max="5"></mgt-people>
```

The behavior of the People component will change, and it will only display five people in the list:   
:::image type="content" source="../media/2-people.png" alt-text="Microsoft Graph Toolkit People component behavior with show max.":::

In the next exercise, you'll learn how to use attributes to change the behavior of Microsoft Graph Toolkit components in your app.