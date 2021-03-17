Now that you have identified the need to display photo of the salesperson in your application, let’s pause for a moment and understand why you need Microsoft Graph to access this information. 

Your profile photo is an identity of who you are. It's a personal branding that allows people to instantly associate a name with a face and make it easier for people to know who they're interacting with in an application. A profile photo can be of a user, group, or an Outlook contact in the Microsoft 365 eco-system. Let’s look at some of the common components where profile photos are used effectively:

- Login control
- People picker
- Permission mechanism of files
- Org charts
- Chat messages

The challenge, however, is to uniformly display a profile photo across the application, as there are multiple sources for profile photos in the Microsoft 365 ecosystem. 

 Your organization may even have a separate system to store profile images of users or contacts as well.  

Microsoft Graph simplifies these challenges and gives you an instant solution for storing and retrieving a unique profile photo

 An example of a **Microsoft Graph API (Application Programming Interface)** end point to get a signed in user’s photo is shown next:  

```http
GET https://graph.microsoft.com/v1.0/me/photo/$value 
```
This end point will give you the image blob object that can be rendered in your application.

 To display the image on a web page, you create an in-memory object from the image blob object and make it the source of an image element.

If you would like to retrieve the metadata of the photo for a signed in user, you can use the following request:

```http
GET https://graph.microsoft.com/v1.0/me/photo
```
The Microsoft Graph endpoints are not limited to the signed in user’s photo. You can retrieve the photo of any user, group, or contact.
