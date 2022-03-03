In this exercise, you'll extend the app to let users view their last 10 emails.

## Load emails from Microsoft Graph

Start by adding a call to Microsoft Graph to load the current user's last 10 emails.

1. In your code editor, open the **graph.js** file.
1. At the end of the file, add a new async function to retrieve the 10 last emails. Load each email's subject and the date and time when it was received.

    ```javascript
    async function getEmails() {
      ensureScope('mail.read');

      return await graphClient
        .api('/me/messages')
        .select('subject,receivedDateTime')
        .orderby('receivedDateTime desc')
        .top(10)
        .get();
    }
    ```

## Add a placeholder to show emails

Next, extend the app with a button to load emails and add a placeholder to display them.

1. In your code editor, open the **index.html** file.
1. Locate the line `<h4>Welcome <span id="userName"></span></h4>` and add the following markup immediately after it:

    ```html
    <button onclick="displayEmail();" id="displayEmail">Show email</button>
    <ul id="emails"></ul>
    ```

1. Extend the content block with a button to load emails and a placeholder to display them.

    ```html
    <div id="content" style="display: none;">
      <h4>Welcome <span id="userName"></span></h4>
      <button onclick="displayEmail();" id="displayEmail">Show email</button>
      <ul id="emails"></ul>
    </div>
    ```

## Display emails in the app

The last step is to request emails by using Microsoft Graph and show them in the placeholder.

1. In your code editor, open the **ui.js** file.
1. At the end of the file, add the `displayEmail` function:

    ```javascript
    async function displayEmail() {
      var emails = await getEmails();
      if (!emails || emails.value.length < 1) {
        return;
      }

      document.getElementById('displayEmail').style = 'display: none';

      var emailsUl = document.getElementById('emails');
      emails.value.forEach(email => {
        var emailLi = document.createElement('li');
        emailLi.innerText = `${email.subject} (${new Date(email.receivedDateTime).toLocaleString()})`;
        emailsUl.appendChild(emailLi);
      });
    }
    ```

## Run your app

You've extended your app to show a user's emails by using Microsoft Graph. Let's run the app locally.

1. Preview the web app by executing the following command in the terminal.

    ```console
    npm start
    ```

1. Your browser should be pointing to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. After you sign in with your account, select the **Show email** button.
1. If you're running the app for the first time, you'll be prompted to grant the app access to your email. To continue, consent to the request.
1. You should see the last 10 emails displayed in the app.

> [!TIP]
> If you don't see any emails, make sure that emails are in the inbox of the account that you use to sign in to the app.
