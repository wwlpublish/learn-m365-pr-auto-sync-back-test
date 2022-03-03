In this exercise, you'll extend the app to let you load a user's emails in batches of 10 items.

## Load emails in batches of 10 items

Start by updating the `getEmails()` function to load emails in batches of 10 items. If the next set of emails to load has been defined, it's passed as the function's argument.

1. In your code editor, open the **graph.js** file.
1. Update the `getEmails()` function's signature to accept a single argument `nextLink`:

    ```javascript
    async function getEmails(nextLink) {
      // ...
    }
    ```

1. If the `nextLink` has been set, the function should pass it to the SDK to retrieve the data. If `nextLink` hasn't been set, the function should load the initial set of data. Update the `getEmails()` function by replacing the `return` statement with the following `if` statement:

    ```javascript
    if (nextLink) {
      return await graphClient
        .api(nextLink)
        .get();
    }
    else {
      return await graphClient
        .api('/me/messages')
        .select('subject,receivedDateTime')
        .orderby('receivedDateTime desc')
        .top(10)
        .get();
    }
    ```

    The updated `getEmails()` function should look as follows:

    ```javascript
    async function getEmails(nextLink) {
      ensureScope('mail.read');

      if (nextLink) {
        return await graphClient
          .api(nextLink)
          .get();
      }
      else {
        return await graphClient
          .api('/me/messages')
          .select('subject,receivedDateTime')
          .orderby('receivedDateTime desc')
          .top(10)
          .get();
      }
    }
    ```

## Extend the template to allow users to load more emails

You've extended the `getEmails()` function to load more emails. The next step is to show a button that will let users load more emails if available.

1. In your code editor, open the **index.html** file.
1. Locate the line `<ul id="emails"></ul>` and add the following code immediately after it to add a button that allows users to load more emails.

    ```html
    <div id="loadMoreContainer" style="display: none;">
      <button onclick="displayEmail();">Load more</button>
    </div>
    ```

## Load more emails

With the app updated to let users load more emails, the final step is to add functionality to handle loading more emails.

1. In your code editor, open the **ui.js** file.
1. Before the `displayEmail()` function, define a new variable named `nextLink` without assigning a value to it:

    ```javascript
    var nextLink;
    ```

1. In the `displayEmail()` function, update the call to get the `getEmails()` function to include the `nextLink`.

    ```javascript
    var emails = await getEmails(nextLink);
    ```

1. Next, after retrieving the data, get the value of the `@odata.nextLink` property. If set, it will indicate that there's more data available for users to show. Add the following code immediately after the `if` statement in the `displayEmail()` function:

    ```javascript
    nextLink = emails['@odata.nextLink'];
    ```

1. At the end of the `displayEmail()` function, after displaying the retrieved emails, scroll to the end of the page so that the user can immediately see the retrieved emails.

    ```javascript
    window.scrollTo({ top: emailsUl.scrollHeight, behavior: 'smooth' });
    ```

1. Finally, check if `nextLink` has been returned and if so, display the button to load more emails.

    Add the following code to the end of the `displayEmail()` function:

    ```javascript
    if (nextLink) {
      document.getElementById('loadMoreContainer').style = 'display: block';
    }
    ```

1. The complete `displayEmail()` function should look as follows:

    ```javascript
    var nextLink;
    async function displayEmail() {
      var emails = await getEmails(nextLink);
      if (!emails || emails.value.length < 1) {
        return;
      }
      nextLink = emails['@odata.nextLink'];

      document.getElementById('displayEmail').style = 'display: none';

      var emailsUl = document.getElementById('emails');
      emails.value.forEach(email => {
        var emailLi = document.createElement('li');
        emailLi.innerText = `${email.subject} (${new Date(email.receivedDateTime).toLocaleString()})`;
        emailsUl.appendChild(emailLi);
      });
      window.scrollTo({ top: emailsUl.scrollHeight, behavior: 'smooth' });

      if (nextLink) {
        document.getElementById('loadMoreContainer').style = 'display: block';
      }
    }
    ```

## Run your app

You've extended your app to show a user's emails by using Microsoft Graph in batches of 10 items and let them load more emails. Let's run the app locally.

1. Preview the web app by executing the following command in the terminal.

    ```console
    npm start
    ```

1. Your browser should be pointing to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. After you sign in with your account, select the **Show email** button.
1. You should see a list of the user's last 10 emails displayed in the app.
1. If there are more than 10 emails in your mailbox, you'll see a button that allows you to load the next 10 messages.
1. Stop the Node.js server by selecting <kbd>CTRL</kbd>+<kbd>C</kbd> in the terminal window.
