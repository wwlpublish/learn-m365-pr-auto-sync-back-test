Security groups are collections of users assigned to a group. Rights can then be assigned to these security groups, granting all users in the group access to permissions within an application.

In this unit, you’ll learn what security groups are and how you can use them within your custom apps secured with Microsoft identity.

## Manage app access with Azure AD groups

Azure Active Directory (Azure AD) lets you use groups to manage access to your cloud-based apps and your resources. Your resources can be part of the Azure AD organization, such as permissions to manage objects through roles in Azure AD, or external to the organization, such as for Software as a Service (SaaS) apps, Azure services, and SharePoint sites.

Azure AD helps you give access to your organization's resources by providing access rights to a single user or to an entire Azure AD group. Using groups lets the resource owner assign a set of access permissions to all the members of the group, instead of having to provide the rights one-by-one. The resource or directory owner can also give management rights for the member list to someone else, such as a department manager or the support department administrator, letting that person add and remove members, as needed.

The resource owner of a group can also enable users to find their own groups to join instead of explicitly assigning users to groups. Groups can be configured to automatically accept all user join requests or to require approval.

## Security groups in custom apps and APIs

Custom apps can request a user's group membership as a way to provide or restrict access to certain functionally within the app.

By default, the ID and Access tokens provided by Microsoft identity only contain basic information about the current user. Security groups the user is a member of aren't included in the tokens.

To add them to the ID token, set the `groupMembershipClaims` property to `SecurityGroup` or `All` in the manifest of the registered Azure AD app from the Azure AD admin center.

The code you will write in ASP.NET Core will add the groups to the role claim instead of the group claim, so there is one more thin you need to change. Locate the `optionalClaims` property as update it to set `accessToken` to include additional properties that will return the groups as roles:

```json
{
  ...
  "optionalClaims": {
    "accessToken": [
      {
        "name": "groups",
        "additionalProperties": ["emit_as_roles"]
      }
    ]
  }
  ...
}
```

### Code configuration

With the app registered and configured in the Azure AD admin center, the next step is to update the app's configuration.

Within the method `ConfigureServices()`, locate the line that configures the `OpenIdConnectOptions`. Update the expression to match the following code:

```csharp
services.Configure<OpenIdConnectOptions>(AzureADDefaults.OpenIdScheme, options =>
{
  options.Authority = options.Authority + "/v2.0/";
  options.TokenValidationParameters.RoleClaimType = "groups";
});
```

Notice the addition of the line for the `RoleClaimType` is set to `groups`. This is added to specify the claim that represents Groups when creating the ClaimsPrincipal in ASP.NET.

In ASP.NET, you can secure a controller so only authenticated users can access it by decorating it the method with the `[Authorize]` attribute. This attribute also supports securing the endpoint based on a security group.

After configuring the OpenID Connect middleware to use Microsoft identity as the role claim, you can specify the ID of a group to secure the controller:

```csharp
[Authorize(Roles("22222222-2222-2222-2222-222222222222"))]
public class ProductsController : Controller
{ }
```

You can also use the group information in code using the `user.IsInRole("22222222-2222-2222-2222-222222222222")` method. For example, the following code will only show the **Products** navigation link if the user is in a specific group:

```cshtml
@if (User.IsInRole("22222222-2222-2222-2222-222222222222"))
{
  <li class="nav-item">
    <a class="nav-link text-dark" asp-area="" asp-controller="Products" asp-action="Index">Products</a>
  </li>
}
```

## Summary

In this unit, you learned what security groups are and how you can use them within your custom apps secured with Microsoft identity.
