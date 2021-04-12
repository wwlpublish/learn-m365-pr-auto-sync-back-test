Microsoft Graph Toolkit components are highly customizable. That makes them suitable for many different solutions. Should you get stuck customizing how they display data, here are a few tips that will help you understand what might be wrong.

## See what data is available in the template

Microsoft Graph Toolkit components show data using templates as you saw earlier in this module. Each component comes with a set of predefined templates, but you can customize them to match your app.

When customizing templates, the most common issue is incorrectly referencing the data bound to the template. If you reference a non-existent property in the template, the component won't show anything. Whenever you’re not seeing the data you’d expect, the best place to start is to examine the data bound to the template. You can do this, by adding `{{ this }}` to the template, for example:

```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template>{{ this }}</template>
</mgt-agenda>
```

This will show all the data bound to the template in the web app:
:::image type="content" source="../media/4-troubleshoot.png" alt-text="A screenshot that shows the result of the example":::

If you’re working with complex data set, examining the data directly in the browser isn't very convenient. Instead, you might want to log it to the console in the browser’s developer tools, where you can explore them as an object. To do that, use `{{ console.log(this) }}` instead:

```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template>{{ console.log(this) }}</template>
</mgt-agenda>
```

This will log the data bound to the template in the console:
:::image type="content" source="../media/4-console.png" alt-text="A screenshot that shows the result of the console":::

In components’ templates, between `{{ }}` you can use any JavaScript function so you’re not limited to showing the data in the browser or logging it to console.
Another tip worth mentioning is that property names of the data bound to the template are case-sensitive. If the data that you’re expecting isn't showing in the component, check that all property names are correctly spelled.

## Are you using the right template?
Some Microsoft Graph Toolkit components expose multiple templates for you to customize. You choose which template you want to use with the `data-type` attribute, for example:
```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template data-type="event">{{ console.log(this) }}</template>
</mgt-agenda>
```

If you don’t specify the `data-type` attribute, the component will use the default template.

Each template has a different data structure bound to it. When switching between templates, you'll need to update the template contents to properly refer to the available data set.

You can find which templates are available and what they expose in each component’s documentation. Let’s put some of these debugging techniques into practice.
