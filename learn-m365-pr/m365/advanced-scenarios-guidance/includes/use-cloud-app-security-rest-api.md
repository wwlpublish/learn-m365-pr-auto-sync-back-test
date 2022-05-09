If you want to integrate Microsoft Defender for Cloud Apps with custom apps or web tools, you might want developers to be able to query Defender for Cloud Apps from their custom code.

In Contoso, for example, you have a mobile app that administrators use to make common changes to security settings in Azure and Microsoft 365 from any location. You'd like to be able to display alerts from Defender for Cloud Apps in this application.

Here, you'll learn how to access and change security data and settings by using the Microsoft Defender for Cloud Apps REST API.

## What is the Microsoft Defender for Cloud Apps REST API?

An Application Programming Interface (API) is a set of objects and methods that a developer can call from code to access and interact with a piece of software. Representational State Transfer (REST) APIs are interfaces that conform to a set of common requirements that make them easy to call over the internet. Web services often publish their methods and properties as REST APIs.

REST APIs usually satisfy these criteria:

- You can call them using HTTP and port 80. This criterion means REST APIs are often accessible through firewalls because port 80 is often open for web access.
- A REST API is stateless – that is, it doesn't store any state information between calls. Instead, every call includes all the information needed to communicate with the API.
- The response is in a well-known generalized text format such as JavaScript Object Notation (JSON)

The Defender for Cloud Apps REST API is a web service that you can use to call methods in Microsoft Defender for Cloud Apps. For example, you could develop a custom app that uses the REST API to obtain data on indicators of compromise and displays that information to a user. The app could also call the REST API to modify those indicators of compromise.

The Defender for Cloud Apps REST API is used by developers who write custom code that accesses and manipulates Defender for Cloud Apps objects.

## Query the Defender for Cloud Apps REST API

Queries against the REST API are usually formulated in code, however you can use the `curl` command-line tool to make requests and observe results.

A REST API call usually includes these parts:

- An operation such a `GET`, for obtaining data, or `POST`, for sending data to the service.
- An authorization token for authenticating with the service.
- A URL that specifies the data you want to see or change. The URL is in the form `https://<portal_url>/api/<endpoint>`.

To obtain the portal URL for your instance of Defender for Cloud Apps, go to the portal, select the question mark in the menu bar, and then select **About**. The portal URL is display in the About page. The endpoint depends on the information you want to query.

For example, to list all the activities defined in your Defender for Cloud Apps tenant, use a `curl` command like this:

```bash
curl -XGET -H "Authorization:Token <your_token_key>" "https://<portal_url>/api/v1/activites"
```

To get a list of continuous Cloud Discovery reports, use a `curl` command like this:

```bash
curl -XGET -H "Authorization:Token <your_token_key>" "https://<portal_url>/api/discovery/streams/"
```

To list all alerts, use a `curl` command like this:

```bash
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<portal_url>/api/v1/alerts/"
```

These commands return responses in JSON format. This format is commonly used and easy to read. For example, the alerts query response may look like this:

```json
{
  "total": 5 // total number of alerts returned
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned alerts
  ]
}
```

## Generate an authentication token

All the queries to the Microsoft Defender for Cloud Apps REST API must authenticate by including an authorization token.

> [!NOTE]
> The token is associated with the user who generated it and inherits that user's permissions and access to Microsoft Defender for Cloud Apps.

To generate this token, use these steps:

1. In the Defender for Cloud Apps portal, on the **Settings** menu, select **Security extensions > API tokens**.
1. Select **+**, and then select **Generate new token**.
1. Enter a **Token name**, reenter your password, and then select **Generate**.

   :::image type="content" source="../media/06-generate-auth-token.png" alt-text="A screenshot of the Generate new token page in the Microsoft Defender for Cloud Apps portal.":::

1. Copy and save the generated token for later use in your code or `curl` commands.

## Tuning responses by using filters

If your query returns too many results and you want to drill down into specific data, you can use filters to create a more targeted query.

For example, this `curl` command list all the alerts with high severity that relate to a policy:

```bash
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<portal_url>/api/v1/alerts/" -d '{
  "filters": {
    "source": {
      "eq": "policy"
    },
    "severity": {
      "eq": "2"
    }
  }
}'
```
