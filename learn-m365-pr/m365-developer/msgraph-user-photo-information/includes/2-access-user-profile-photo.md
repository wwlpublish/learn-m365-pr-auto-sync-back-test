Now that you've identified the need to display a salesperson photo in your application, let's pause for a moment and understand why you need Microsoft Graph to access this information.

Your profile photo is an image of who you are. It's a personal branding that allows people to instantly associate a name with a face and make it easier for people to know who they're interacting with in an application.

A profile photo can be of a user, a group, or an Outlook contact in the Microsoft 365 ecosystem. Profile photos are used effectively in components such as:

- Sign in control
- People picker
- Permission mechanism of files
- Organizational charts
- Chat messages

The challenge is to uniformly display a profile photo across the application, because the Microsoft 365 ecosystem has multiple sources for profile photos. Your organization might even have a separate system to store profile images of users or contacts.

Microsoft Graph simplifies these challenges and gives you an instant solution for storing and retrieving a unique profile photo.

Here's an example of a Microsoft Graph API endpoint to get a signed-in user's photo:

```http
GET https://graph.microsoft.com/v1.0/me/photo/$value
```

This endpoint gives you the image blob object that can be rendered in your application. To display the image on a webpage, you create an in-memory object from the image blob object and make it the source of an image element.

If you want to retrieve the metadata of the photo for a signed-in user, you can use the following request:

```http
GET https://graph.microsoft.com/v1.0/me/photo
```

The Microsoft Graph endpoints aren't limited to the signed-in user's photo. You can securely retrieve the photo of users, groups, or contacts.
