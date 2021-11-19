Address lists are used to group recipient objects based on an LDAP query for specific user attributes. You can use address lists to sort the GAL into multiple views, which makes it easier to locate recipients. This feature is especially helpful for large or highly segmented organizations.

You can configure address lists with recipient filters that determine which objects belong in each address list. Address lists are evaluated every time a mail-enabled account is modified to determine the address lists on which it should appear.

There are two types of recipient filters:

 -  **Pre-canned.** A commonly used Exchange filter that you can use to meet various recipient-filtering criteria for creating address lists. For example, using pre-canned filters, you can determine the scope of recipients and add conditional filtering based on properties such as company, department, and state or region.
 -  **Custom.** If pre-canned filters don't meet your needs for creating address lists, you can create a custom filter by using the RecipientFilter parameter. For example, you can use the Filter parameter to filter information about users whose title contains the word "manager”.

The following examples describe when and how address lists are used:

 -  **Custom address lists.** Consider an organization that has two large divisions and a single Exchange organization. One division, named Fourth Coffee, imports and sells coffee beans. The other division, Contoso, Ltd., underwrites insurance policies. Because of the different nature of each business, the employees rarely communicate with each other. To make it easier for employees to find recipients who exist only in their division, you can create two new custom address lists, one for Fourth Coffee and one for Contoso, Ltd. When employees search for recipients in their division, these custom address lists allow them to select only the address list that is specific to their division. However, if an employee is unsure about the division in which the recipient exists, the employee can search within the GAL that contains all recipients in both divisions.
 -  **Hierarchical address lists.** You can use subcategories of address lists, which are known as hierarchical address lists. For example, you can create an address list that contains all recipients in Vancouver and another address list that contains all Seattle recipients. You can also create another list that's titled Research and Development. This list will be within the Vancouver address list, and it will contain all employees who work in Vancouver’s Research and Development department. This design allows employees to easily find the information they need.

When creating address lists, you should consider the following recommendations:

 -  Address lists should make it easier for users to find recipients. As such, you should avoid creating so many address lists that users can't decide which list to use.
 -  Use a naming convention and location hierarchy for your address lists so users can easily determine which recipients are included in the list.
 -  Remind users that they can find anyone in their organization by using the GAL.

**Additional reading.** For more information, see [Address lists in Exchange Online](/exchange/address-books/address-lists/address-lists?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.