Microsoft Graph Toolkit components are highly customizable. That makes them suitable for many different solutions. If you get stuck customizing how they display data, here are a few tips to help you understand what might be wrong.

## See what data is available in the template

Microsoft Graph Toolkit components show data by using templates, as you saw earlier in this module. Each component comes with a set of predefined templates, but you can customize them to match your app.

When you customize templates, the most common issue is incorrectly referencing the data bound to the template. If you reference a nonexistent property in the template, the component won't show anything. If you don't see the data you expected, the best place to start is to examine the data bound to the template. You can do this step by adding `{{ this }}` to the template.

```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template>{{ this }}</template>
</mgt-agenda>
```

This example shows all the data bound to the template in the web app.

:::image type="content" source="../media/4-troubleshoot.png" alt-text="Screenshot that shows the result of the example.":::

If you're working with a complex dataset, examining the data directly in the browser isn't convenient. Instead, you might want to log it to the console in the browser's developer tools, where you can explore it as an object. To do that, use `{{ console.log(this) }}`.

```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template>{{ console.log(this) }}</template>
</mgt-agenda>
```

This example logs the data bound to the template in the console.

:::image type="content" source="../media/4-console.png" alt-text="Screenshot that shows the result of the console.":::

In the components' templates, you can use any JavaScript function between `{{ }}`. In this way, you aren't limited to showing the data in the browser or logging it to the console.

Another tip is that property names of the data bound to the template are case sensitive. If the data you expected to see doesn't show in the component, check that all property names are spelled correctly.

## Are you using the right template?

Some Microsoft Graph Toolkit components expose multiple templates for you to customize. You choose which template you want to use with the `data-type` attribute.

```html
<mgt-agenda date="March 9, 2021" days="3" group-by-day>
  <template data-type="event">{{ console.log(this) }}</template>
</mgt-agenda>
```

If you don't specify the `data-type` attribute, the component uses the default template.

Each template has a different data structure bound to it. When you switch between templates, you need to update the template contents to properly refer to the available dataset.

You can find which templates are available and what they expose in each component's documentation. Let's put some of these debugging techniques into practice.
