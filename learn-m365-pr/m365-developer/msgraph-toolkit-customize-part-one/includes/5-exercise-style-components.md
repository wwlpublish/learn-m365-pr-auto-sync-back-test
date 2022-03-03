In this exercise, you'll learn how to use custom CSS properties with Microsoft Graph Toolkit components to change the styling of your application.

## Before you start

As a prerequisite for this exercise, you'll need to complete the previous exercise:
"Change the behavior of components by using attributes."

## Style the Login component to match your branding

Let's say you want to change the appearance of the button content for the **Login** component. In **index.html**, you can use the `<style>` tag inside `<head>` to customize components.

```html
<head>
  <style>
  </style>
</head>
```

1. To customize the body of the page, add `body{}` between the `<style>` tags. Use the following CSS property inside the `body{}` selector:
    - `background-color` changes the background color of the page to `black`.
1. To customize the **Login** component, add `mgt-login{}` between the `<style>` tags. Use the following CSS properties inside the `mgt-login{}` selector:
    - `--padding` modifies the spacing inside the "user's mail" element. Define it as `30px` for equal space from top, bottom, left, and right.
    - `--button-color--hover` changes the button hover color to `grey`.
    - `--button-background-color` changes the button background color to `slategrey`.
    - `--popup-color` changes the user profile pop-up font color to `slategrey`.
1. To customize the `Agenda` component, add `mgt-agenda{}` between the `<style>` tags. Use the following CSS properties inside the `mgt-agenda{}` selector:
    - `--agenda-header-font-size` changes the font size of the agenda header to `24px`.
    - `--event-padding` modifies spacing inside the events to `20px`.
    - `--event-background-color` changes the event background color to `slategrey`.
    - `--event-box-shadow` changes the event box shadow to `grey`.

    ```html
    <head>
      <style>
        body {
          background-color:black;
        }
        mgt-login {
          --padding: 30px ;
          --button-color--hover:grey;
          --button-background-color:slategrey;
          --popup-color:slategrey;
        }
        mgt-agenda{
          --agenda-header-font-size:24px;
          --event-padding:20px;
          --event-background-color:slategrey;
          --event-box-shadow:grey;
        }
      </style>
    </head>
    ```

1. Let's add a dark global theme to the HTML page by using `class="mgt-dark"`. Open the **index.html** file, and add the following `class` attribute to the `<body>` tag.

    ```html
    <html>
      <head>
        ...
      </head>
      <body class="mgt-dark">
        ...
      </body>
    </html>
    ```

The final version of the **index.html** file will look like this example:

```html
<!DOCTYPE html>
<html>
<head>
  <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>

  <style>
    body {
      background-color:black;
    }
    mgt-login {
      --padding: 30px ;
      --button-color--hover:grey;
      --button-background-color:slategrey;
      --popup-color:slategrey;
    }
    mgt-agenda{
      --agenda-header-font-size:24px;
      --event-padding:20px;
      --event-background-color:slategrey;
      --event-box-shadow:grey;
    }
  </style>
</head>
<body class="mgt-dark">

  <mgt-msal2-provider client-id="[Your-Client-ID]"></mgt-msal2-provider>

  <mgt-login>
    <template data-type="signed-in-button-content" >
      <div>
        {{personDetails.mail}}
      </div>
    </template>
  </mgt-login>

  <mgt-agenda class="agenda"
      date="March 9, 2021"
      days="3"
      group-by-day>
  </mgt-agenda>

</body>
</html>
```

## Test your app in the browser

1. In Visual Studio Code, select the following key combination, and search for Live Server:

    - **Windows**: <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>
    - **macOS**: <kbd>COMMAND</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>

    Run Live Server to test your app.

1. Open your browser, and go to `http://localhost:3000`.
1. Sign in with your Microsoft 365 developer account. Consent to the required permissions, and select **Accept**.
1. Finally, you'll see that the components are automatically adapted to the dark theme and the signed-in button style has changed.

:::image type="content" source="../media/5-final.png" alt-text="This image shows the final version of the application.":::

Overall, the Microsoft Graph Toolkit components are flexible when it comes to customization. You can modify the way the components look by using custom CSS properties and match them with your application's branding.
