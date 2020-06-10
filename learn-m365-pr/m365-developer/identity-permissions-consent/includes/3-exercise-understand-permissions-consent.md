The Microsoft identity platform implements the OAuth 2.0 authorization protocol. This protocol is a method that a third-party app can use to access web-hosted resources on behalf of a user. The web-hosted resources can define a set of permissions that can be used to implement functionality in smaller chucks.

In this exercise, you’ll learn about the different types of permissions supported by the Microsoft identity platform and the consent experience that users and admins must go through to grant permission requests to apps.

> [!NOTE]
> This exercise utilizes two different accounts in the same organization. One of the accounts, **admin@{org}.onmicrosoft.com**, is assigned the global administrator role and is used to perform management tasks in the directory such as creating the app. The other account, **adelev@{org}.onmicrosoft.com**, is not a member of the global administrator role and is used to demonstrate a typical user without administrative rights.

## Create a Node.js web application

In this first section, you'll create a web application to host a web page that will host the single page application. To do this, you'll create a Node.js web server to serve the HTML page from a web server running on your workstation as http://localhost:3007.

Open your command prompt, navigate to a directory where you want to save your work, create a new folder, and change directory into that folder.

Execute the following command to create a new Node.js application:

```shell
npm init -y
```

Install the Node.js webserver **express** and HTTP request middleware **morgan** into the application:

```shell
npm install express morgan
```

Create a new file **server.js** in the root of the folder and add the following JavaScript to it. This code will start the web server:

```js
var express = require('express');
var app = express();
var morgan = require('morgan');
var path = require('path');

var port = 3007;
app.use(morgan('dev'));

// set the front-end folder to serve public assets.
app.use(express.static('web'));

// set up our one route to the index.html file.
app.get('*', function (req, res) {
  res.sendFile(path.join(__dirname + '/index.html'));
});

// Start the server.
app.listen(port);
console.log(`Listening on port ${port}...`);
console.log('Press CTRL+C to stop the web server...');
```

## Create a web page for the user to sign in and display details

Create a new folder **web** in the current folder and add a new file **index.html** to the folder. Add the following code to the **index.html** file:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Microsoft Identity: Permissions and Consent</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/bluebird/3.5.5/bluebird.min.js"></script>
  <script src="https://alcdn.msftauth.net/lib/1.1.3/js/msal.min.js"></script>
</head>

<body>
  <div class="container">
    <div>
      <p id="WelcomeMessage">Microsoft Authentication Library For Javascript (MSAL.js) Exercise</p>
      <button id="SignIn" onclick="signIn()">Sign In</button>
      <h2>Latest messages</h2>
      <div id="messages"></div>      
    </div>
    <div>
      <pre id="json"></pre>
    </div>
  </div>
  <script>
    var msalConfig = {
      auth: {
        clientId: '{{APPLICATION_ID}}',
        authority: 'https://login.microsoftonline.com/{{DIRECTORY_ID}}',
        redirectURI: 'http://localhost:3007'
      },
      cache: {
        cacheLocation: "localStorage",
        storeAuthStateInCookie: true
      }
    };

    var graphConfig = {
      graphMeEndpoint: "https://graph.microsoft.com/v1.0/me",
      requestObj: {
        scopes: ["user.read", "mail.read"]
      }
    };

    var msalApplication = new Msal.UserAgentApplication(msalConfig);

    // init the auth handling on the page
    initPage();



    // TODO: add CODE before this line



    // TODO: add FUNCTIONS before this line


    function initPage() {
      // Browser check variables
      var ua = window.navigator.userAgent;
      var msie = ua.indexOf('MSIE ');
      var msie11 = ua.indexOf('Trident/');
      var msedge = ua.indexOf('Edge/');
      var isIE = msie > 0 || msie11 > 0;
      var isEdge = msedge > 0;

      // if you support IE, recommendation: sign in using Redirect APIs vs. popup
      // Browser check variables
      // can change this to default an experience outside browser use
      var loginType = isIE ? "REDIRECT" : "POPUP";

      // runs on page load, change config to try different login types to see what is best for your application
      switch (isIE) {
        case true:
          document.getElementById("SignIn").onclick = function () {
            msalApplication.loginRedirect(graphConfig.requestObj);
          };

          // avoid duplicate code execution on page load in case of iframe and popup window
          if (msalApplication.getAccount() && !msalApplication.isCallback(window.location.hash)) {
            updateUserInterface();
            acquireTokenRedirectAndGetUser();
          }
          break;
        case false:
          // avoid duplicate code execution on page load in case of iframe and popup window
          if (msalApplication.getAccount()) {
            updateUserInterface();
            acquireTokenPopupAndGetUser();
          }
          break;
        default:
          console.error('Please set a valid login type');
          break;
      }
    }
  </script>
</body>
</html>
```

> [!NOTE]
> The remainder of this exercise instructs you to add code to this **index.html** file. Pay close attention where you add the code using the using the two `TODO:` comments for placement.

Add the following function to the **index.html** file immediately before the `// TODO: add FUNCTIONS before this line` comment that will configure the welcome message for the page:

```js
function updateWelcomeMessageAndSigninControl() {
  // update welcome message
  var divWelcome = document.getElementById('WelcomeMessage');
  divWelcome.innerHTML = `Welcome <strong>${msalApplication.getAccount().name}</strong> &lt;${msalApplication.getAccount().userName}&gt; to Microsoft Graph API`;

  // update signin/out button
  var loginbutton = document.getElementById('SignIn');
  loginbutton.innerHTML = 'Sign Out';
  loginbutton.setAttribute('onclick', 'signOut();');
}
```

Next, add the following functions to **index.html** immediately before the `// TODO: add FUNCTIONS before this line` comment. These functions request an access token from Microsoft identity and submit a request to Microsoft Graph for the current user's last 10 emails. The function `acquireTokenPopupAndGetUserEmails()` uses the popup approach that works for all modern browsers while the `acquireTokenRedirectAndGetUserEmails()` function uses the redirect approach that is suitable for Internet Explorer:

```js
function acquireTokenPopupAndGetUserEmails() {
  // try to get token silently without logging in (ie: from token cache)
  msalApplication.acquireTokenSilent(graphConfig.requestObj)
    .then(function (tokenResponse) {
      // request email messages from Microsoft Graph
      getMessagesFromMSGraph(graphConfig.graphMeEndpoint +'/messages?$top=10&$select=subject', tokenResponse.accessToken, graphAPICallback);
    }).catch(function (error) {
      console.log(error);
      if (requiresInteraction(error.errorCode)) {
        // unable to get token silently, so log the user in interactively (ie: display popup)
        msalApplication.acquireTokenPopup(graphConfig.requestObj).then(function (tokenResponse) {
          // request email messages from Microsoft Graph
          getMessagesFromMSGraph(graphConfig.graphMeEndpoint +'/messages?$top=10&$select=subject', tokenResponse.accessToken, graphAPICallback);
        }).catch(function (error) {
          console.log(error);
        });
      }
    });
}

function acquireTokenRedirectAndGetUserEmails() {
  // try to get token silently without logging in (ie: from token cache)
  msalApplication.acquireTokenSilent(graphConfig.requestObj).then(function (tokenResponse) {
    getMessagesFromMSGraph(graphConfig.graphMeEndpoint +'/messages?$top=10&$select=subject', tokenResponse.accessToken, graphAPICallback);
  }).catch(function (error) {
    console.log(error);
    // unable to get token silently, so log the user in interactively (ie: display popup)
    if (requiresInteraction(error.errorCode)) {
      msalApplication.acquireTokenRedirect(graphConfig.requestObj);
    }
  });
}

// Check the error code for the error returned to determine if interactive login required
function requiresInteraction(errorCode) {
  if (!errorCode || !errorCode.length) {
    return false;
  }
  return errorCode === "consent_required" ||
          errorCode === "interaction_required" ||
          errorCode === "login_required";
}
```

These functions first attempt to retrieve the access token silently from the currently signed in user. If the user needs to sign in, the functions will trigger either the popup or redirect authentication process.

The redirect approach to authenticating requires an extra step. The MSAL application on the page needs to see if the current page was requested based on a redirect from Azure AD. If so, it needs to process information in the URL request provided by Azure AD.

Add the following function immediately before the `// TODO: add FUNCTIONS before this line` comment:

```js
function authRedirectCallBack(error, response) {
  if (error) {
    console.log(error);
  } else {
    if (response.tokenType === "access_token") {
      getUserFromMSGraph(graphConfig.graphMeEndpoint, response.accessToken, graphAPICallback);
    } else {
      console.log("token type is:" + response.tokenType);
    }
  }
}
```

Add the following function immediately before the `// TODO: add CODE before this line` comment:

```js
msalApplication.handleRedirectCallback(authRedirectCallBack);
```

Once the user is authenticated, the code can submit a request to Microsoft Graph for the current user's information. The two `acquireToken*()` functions pass the access token acquired from Azure AD to the function:

Add the following function immediately before the `// TODO: add FUNCTIONS before this line` comment:

```js
function getMessagesFromMSGraph(endpoint, accessToken, callback) {
  var xmlHttp = new XMLHttpRequest();
  xmlHttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200)
      callback(JSON.parse(this.responseText));
  }
  xmlHttp.open("GET", endpoint, true);
  xmlHttp.setRequestHeader('Authorization', 'Bearer ' + accessToken);
  xmlHttp.send();
}

function graphAPICallback(data) {
  var htmlBody = '';
  data.value.forEach(message => {
    htmlBody += `<li>${message.subject}</li>`;
  });
  document.getElementById("messages").innerHTML = `<ul>${htmlBody}</ul>`;
}
```

Finally, add the following two functions to implement a sign in and sign out capability for the button on the page:

Add the following function immediately before the `// TODO: add FUNCTIONS before this line` comment:

```js
function signIn() {
  msalApplication.loginPopup(graphConfig.requestObj)
    .then(function (loginResponse) {
      updateWelcomeMessageAndSigninControl();
      acquireTokenPopupAndGetUserEmails();
    }).catch(function (error) {
      console.log(error);
    });
}

function signOut() {
  msalApplication.logout();
}
```

## Create an Azure AD application

The web page you created will submit a request to Microsoft Graph to retrieve the user's emails. All requests to Microsoft Graph must include an access token as proof of the user's identity and that they have the necessary permissions to call Microsoft Graph. To obtain an access token, you must create an Azure AD application.

Open a browser and navigate to the [Azure Active Directory admin center](https://aad.portal.azure.com). Sign in using a **Work or School Account** that has global administrator rights to the tenancy.

Select **Azure Active Directory** in the left-hand navigation.

Then select **Manage > App registrations** in the left-hand navigation.

  ![Screenshot of the App registrations](../media/azure-ad-portal-home.png)

On the **App registrations** page, select **New registration**.

  ![Screenshot of App Registrations page](../media/azure-ad-portal-new-app-00.png)

On the **Register an application** page, set the values as follows:

- **Name**: Identity Exercise 01
- **Supported account types**: Accounts in this organizational directory only (Single tenant)
- **Redirect URI**: Web = http://localhost:3007

    ![Screenshot of the Register an application page](../media/03-azure-ad-portal-new-app-01.png)

Select **Register** to create the application.

On the **Identity Exercise 01** page, copy the values **Application (client) ID** and **Directory (tenant) ID**; you'll need these values later in this exercise.

  ![Screenshot of the application ID of the new app registration](../media/03-azure-ad-portal-new-app-details-01.png)

On the **Identity Exercise 01** page, select the **1 web, 0 public client** link under the **Redirect URIs**.

Locate the section **Implicit grant** and select both **Access tokens** and **ID tokens**. This tells Azure AD to return these tokens the authenticated user if requested.

Select **Save** in the top menu to save your changes.

### Add permissions to the Azure AD app

Select **API Permissions** from the left-hand navigation, and then select **Add a permission**:

  ![Screenshot of the Configured Permissions page in Azure AD](../media/03-azure-ad-portal-new-app-permissions-01.png)

On the **Request API Permissions** page, select **Microsoft APIs**, **Microsoft Graph**, and then select **Delegated permissions**:

  ![Screenshot of selecting Microsoft Graph Delegated permissions](../media/03-azure-ad-portal-new-app-permissions-02.png)

In the search box in the **Select permissions** section, enter **Mail.R**, select the permission **Mail.Read** permission, and then select **Add permissions**.

  ![Screenshot of selecting Microsoft Graph Delegated permissions](../media/03-azure-ad-portal-new-app-permissions-03.png)

## Update the web page with the Azure AD application details

The last step is to configure the web page to use the Azure AD application.

Locate the `var msalConfig = {}` code in the **index.html** file. The `auth` object contains three properties you need to set as follows:

- `clientId`: set to the Azure AD application's ID
- `authority`: set to **https://login.microsoftonline.com/{{DIRECTORY_ID}}**, replacing the **{{DIRECTORY_ID}}** with the Azure AD directory ID of the Azure AD application
- `redirectURI`: set to the Azure AD application's redirect URI: **http://localhost:3007**

## Test the web application

To test the web page, first start the local web server. In the command prompt, execute the following command from the root of the project:

```shell
node server.js
```

Next, open a browser where you are not signed-in to Office 365 and navigate to **http://localhost:3007**. The page initially contains a default welcome message and sign in button.

![Screenshot of the default web page for an anonymous user](../media/03-test-01.png)

Select the **Sign In** button.

Depending on the browser, you're using, a popup window will load or the page will redirect to the Azure AD sign in prompt.

Sign in using a **Work or School Account** with a user *who isn't assigned* the global administrator role. On the next screen, **don't select** the **Accept** button. Instead, examine the dialog:

![Screenshot of Azure AD popup sign-in experience](../media/03-test-02.png)

This screenshot demonstrates the *user consent experience* in Microsoft identity.

Notice the permissions are all specific to the current user. Each of the permissions includes "you" or "your" as they related to the type of data and permission requested. Each of these permissions requested is delegated permissions. Delegated permissions are those which a user can grant to an app so that the app can act on behalf of the user.

For a user to grant an app delegated permissions, the user must have those same permissions. In other words, if the user doesn't have permissions to do something, they can't grant the permission to the app.

In this scenario, each user will need to grant the application permission before the app can obtain the permission and act on behalf of the user.

Close the browser and open a new instance so that you can sign-in again.

Navigate to **http://localhost:3007** again and select the **Sign In** button. This time, sign-in with a user *who is assigned* the global administrator role. Notice the difference in the consent dialog:

![Screenshot of Azure AD popup sign-in experience](../media/03-test-03.png)

There's one significant difference to take notice of. First, because you signed in using an administrator account, you have an additional option. The checkbox after the permission list enables an administrator to grant these delegated permissions to *all users* in the organization. This removes the requirement for each user to grant the permission.

Select the checkbox **Consent on behalf of your organization**. Notice how the permissions change and an additional informational message are displayed. Take special notice how the words "you" and "your" in the permissions have been replaced with "user".

![Screenshot of Azure AD popup sign-in experience](../media/03-test-04.png)

Select the **Accept** button.

Depending on the browser you're using, the popup will disappear or you'll be redirected back to the web page. When the page loads, MSAL will request an access token and request your information from Microsoft Graph. After the request complete, it will display the results on the page:

![Screenshot of the web app for an authenticated administrative user](../media/03-test-05.png)

Now try signing-in as the non-administrator user. Select the **Sign Out** button and complete the sign-out process.

Select **Sign In** and enter the credentials of the user who is not an administrator. Notice this time, you aren't prompted with the consent dialog because the administrator has already consented the permissions on behalf of everyone in the organization.

![Screenshot of the web app for an authenticated non-administrative user](../media/03-test-06.png)

You can also provide organization administrators a specific link that will take them to an admin consent experience.

In a new browser window, navigate to the following URL. Make sure you replace the `{{APPLICATION_ID}}` with the ID of the Azure AD application you created

`https://login.microsoftonline.com/common/adminconsent?client_id={{APPLICATION_ID}}&state=12345&redirect_uri=http://localhost:3007`

![Screenshot of the admin consent dialog](../media/03-test-07.png)

This experience is more targeted to an administrator as it states that the permissions requested are for an entire organization.

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console.

## Summary

In this unit, you learned about the different types of permissions supported by the Microsoft identity platform and the consent experience that users and admins must go through to grant permission requests to apps.
