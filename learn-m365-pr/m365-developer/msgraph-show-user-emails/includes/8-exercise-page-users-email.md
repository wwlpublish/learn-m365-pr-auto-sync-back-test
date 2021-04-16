In this exercise, you'll extend the app to let you browse through a user's emails in batches of 10 items.

## Load emails in batches of 10 items

Start by updating the `getEmails` function to load emails in batches of 10 items. The page to be loaded is passed as a parameter to the function.

1. In your code editor, open the *graph.js* file.
1. Extend the `getEmails` function's signature with the `page` argument.

    ```javascript
    async function getEmails(page) {
      // ...
    }
    ```

1. Before you build the Microsoft Graph query, define a new variable named `pageSize` and set its value to `10`.
1. Rather than calling Microsoft Graph directly, define the first portion of the query.

    ```javascript
    var query = graphClient
      .api('/me/messages')
      .select('subject,receivedDateTime')
      .orderby('receivedDateTime desc')
      .top(pageSize);
    ```

1. If a page was specified in the function and the page number is greater than one, extend the query to skip the number of items from previous pages.

    ```javascript
    if (page && page > 1) {
      query.skip(page * pageSize);
    }
    ```

1. Finish the function by executing the query and calling Microsoft Graph.

    ```javascript
    return await query.get();
    ```

1. The complete `getEmails` function should look as follows:

    ```javascript
    async function getEmails(page) {
      ensureScope('mail.read');
    
      var pageSize = 10;
    
      var query = graphClient
          .api('/me/messages')
          .select('subject,receivedDateTime')
          .orderby('receivedDateTime desc')
          .top(pageSize);
    
      if (page && page > 1) {
          query.skip((page - 1) * pageSize);
      }
    
      return await query.get();
    }
    ```

## Extend the template to allow users to page through emails

You've extended the `getEmails` function to load emails with support for paging. The next step is to show buttons that will let users browse through the paged results.

1. In your code editor, open the *index.html* file.
1. Right after the unordered list with emails, add buttons that allow users to browse through pages of emails.

    ```html
    <div id="emailsPaging" style="display: none;">
      <span id="pageNumber" style="display: none;">Page 1</span>
      <button id="emailsPagingPrevious" style="display: none;" onclick="page--; displayEmail();">&lt; Previous</button>
      <button id="emailsPagingNext" onclick="page++; displayEmail();">Next &gt;</button>
    </div>
    ```

## Page through emails

With the app updated to let users navigate through the paged results, the final step is to add functionality to handle changing pages.

1. In your code editor, open the *ui.js* file.
1. Before the `displayEmail` function, define a new variable named `page` and set its value to `1`.
1. In the `displayEmail` function, update the call to get the `getEmails` function to include the current page number.

    ```javascript
    var emails = await getEmails(page);
    ```

1. In the `displayEmail` function, at the end add information about the current page so that it's displayed and checks if there are more emails for the user to see in the UI.

    ```javascript
    var pageNumber = document.getElementById('pageNumber');
    pageNumber.style = 'display: inline';
    pageNumber.innerHTML = `Page ${page}`;
    
    // stop if there are no more emails to display
    if (page === 1 && !emails['@odata.nextLink']) {
      return;
    }
    ```

1. Show paging buttons so that users can navigate between paged data. If a user is on the first page, hide the _previous_ button. If a user is on the last page, hide the _next_ button.

    ```javascript
    var emailsPagingButtons = document.getElementById('emailsPaging');
    emailsPagingButtons.style = 'display: block';
    
    
    var previousEmailsButton = document.getElementById('emailsPagingPrevious');
    // hide previous button on the first page
    previousEmailsButton.style = `display: ${page === 1 ? 'none' : 'inline'}`;
    
    var nextEmailsButton = document.getElementById('emailsPagingNext');
    // hide next button on the last page
    nextEmailsButton.style = `display: ${!emails['@odata.nextLink'] ? 'none' : 'inline'}`;
    ```

1. The complete `displayEmail` function should look as follows:

    ```javascript
    var page = 1;
    async function displayEmail() {
      var emails = await getEmails(page);
      if (!emails || emails.value.length < 1) {
        return;
      }
    
      var displayEmailButton = document.getElementById('displayEmail');
      displayEmailButton.style = 'display: none';
    
      var emailsUl = document.getElementById('emails');
      // clear existing elements
      emailsUl.innerHTML = '';
      emails.value.forEach(email => {
        var emailLi = document.createElement('li');
        emailLi.innerText = `${email.subject} (${new Date(email.receivedDateTime).toLocaleString()})`;
        emailsUl.appendChild(emailLi);
      });
    
      var pageNumber = document.getElementById('pageNumber');
      pageNumber.style = 'display: inline';
      pageNumber.innerHTML = `Page ${page}`;
    
      // stop if there are no more emails to display
      if (page === 1 && !emails['@odata.nextLink']) {
        return;
      }
    
      var emailsPagingButtons = document.getElementById('emailsPaging');
      emailsPagingButtons.style = 'display: block';
    
      var previousEmailsButton = document.getElementById('emailsPagingPrevious');
      // hide previous button on the first page
      previousEmailsButton.style = `display: ${page === 1 ? 'none' : 'inline'}`;
      
      var nextEmailsButton = document.getElementById('emailsPagingNext');
      // hide next button on the last page
      nextEmailsButton.style = `display: ${!emails['@odata.nextLink'] ? 'none' : 'inline'}`;
    }
    ```

## Run your app

You've extended your app to show a user's emails by using Microsoft Graph in batches of 10 items and let them navigate between the paged data. Let's run the app locally.

1. Preview the web app by executing the following command in the terminal.

    ```cmd
    npm start
    ```

1. Your browser should be pointing to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. After you sign in with your account, select the **Show email** button.
1. You should see a list of the user's last 10 emails displayed in the app.
1. If there are more than 10 emails in your mailbox, you'll see buttons that allow you to view the next or previous 10 messages.
1. Stop the Node.js server by selecting Ctrl+C in the terminal window.
