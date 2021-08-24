Teams templates are pre-built definitions of a team's structure designed around a business need or project. You can use Teams templates to quickly create rich collaboration spaces with channels for different topics and preinstall apps to pull in mission-critical content and services. Teams templates provide a predefined team structure that can help you easily create consistent teams across your organization.

## The types of team templates

There are two type of team templates. 
* **Base template**

    Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the store and team properties that are not yet supported individually in Teams templates.

    Once a base template type is defined, you can extend or override these special templates with additional properties that you'd like to specify. But some base template types contain properties that can't be overridden. For the available base template types, see [base template types](https://docs.microsoft.com/microsoftteams/get-started-with-teams-templates?azure-portal=true#team-template-capabilities).

* **Custom template**

    Besides the team templates created by Microsoft, you can create your own template in the Teams admin center.

## Teams template capabilities

Most properties in a team are included and supported by templates. The following table provides a quick summary of what's included and what's not included in Teams templates.

| **Team properties supported by Teams templates** | **Team properties not yet supported by Teams templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Base template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Autofavorite channel | |
| Installed app | |
| Pinned tabs | |

> [!NOTE]
> Teams templates currently don't support creating private channels. Private channel creation isn't included in template definitions.


## Create a custom template
You can create a template from scratch, an existing team or team template that can be saved and modified to meet your particular organizational needs.

1. Log in to the Teams admin center.

2. In the left navigation, expand **Teams** > **Team templates**.

3. Select **+ Add**.

    ‎:::image type="content" source="../media/team-templates-new.png" alt-text="An image of the Team templates dialog with Add highlighted.":::

‎
4. In the **Team templates** section, select a way to create the template.

- Create a brand new template
- Use an existing team as a template
- Start with an existing team template

    ‎‎:::image type="content" source="../media/create-template.png" alt-text="Select a starting point for your new template":::  


5. In the **Template settings** section, complete the following fields and then select **Next**:
    - Template name
    - Template short and long descriptions
    - Locale visibility  

6. Add or modify any channels or apps that your team needs.

7. Select **Submit** when completed.

## Manage templates policies

Manage the team templates that your end users see by creating templates policies in the admin center. Within each template policy, you can designate which templates are shown or hidden. Assign different users to different template policies so that your users view only the subset of team templates specified.

### Create template policies 

1. Sign in to the Teams admin center.
2. Expand **Teams** > **Templates policies**.
3. Select **Add**.
4. In the **Templates Policies Settings** section, complete the following fields:

    - Templates Policy name
    - Templates Policy short description

5. In the **Viewable Templates** table, select the templates you want to hide and select **Hide**.

    You can see the templates you've selected to hide in the **Hidden Templates** table.

6. To unhide certain templates, scroll to the **Hidden templates** table.

7. Select the templates to unhide, and then select **Show**.

   The selected templates will appear in your **Viewable templates** table.

8. Select **Save**.

   Your new template policy is displayed in the **Templates Policies** list.

### Assign users to the template policies

Users assigned to a policy will only be able to view the viewable templates within that policy.

1. From **Templates Policies**, select a policy, and then select **Manage users**.
2. Type the users to assign to this policy.
3. Select **Apply**.

