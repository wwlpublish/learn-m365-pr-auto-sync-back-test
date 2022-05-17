Depending on an organization's needs, it can use the following methods to provision user accounts:

 -  **Microsoft 365 admin center.** This portal provides a simple web interface for individually creating and managing users. It's also available as an app for mobile devices or tables as Microsoft 365 admin app.
 -  **Import multiple users.** This option provides a method for the bulk importation of multiple users into the Microsoft 365 admin center through a comma-separated value (CSV) file.
 -  **Windows PowerShell.** This cmdlet-based and script-based interface can be used to create and manage single and multiple users.
 -  **Directory synchronization.** This option requires an organization to provision and manage users by synchronizing Microsoft 365 with an on-premises directory service such as Active Directory. The Azure AD Connect tool can be used to synchronize on-premises Active Directory objects with Azure AD in Microsoft 365.

The most common and easiest way to create user accounts in non-directory synchronized environments is to use the Microsoft 365 admin center or the Microsoft 365 admin app. More advanced methods such as importing multiple users or Windows PowerShell are normally used for mass-imports, or if an automated script was run for user creation. In environments where directory synchronization is implemented, an organization can't use the Microsoft 365 admin center or Windows PowerShell for user creation. It must instead use the local tools available in its Active Directory.

### Creating users with the Microsoft 365 admin center

Using the Microsoft 365 admin center is the simplest method for creating one or more user accounts. To create a user, following these steps:

1.  Sign in to Microsoft 365 admin center.
2.  On the **Microsoft 365 admin center**, in the left-hand navigation pane, select the **Users** group and then select **Active users.**
3.  On the **Active users** page, select **Add a user**. This action will start a wizard that walks you through the steps necessary to add the user information.
4.  On the **Set up the basics** page, enter the required user and password information. Verify you select the correct domain for the Username.
5.  On the **Assign product licenses** page, select the product license(s) that should be assigned to the user.
6.  On the **Optional settings** page, select the role(s) you want to assign to this user.
7.  On the **Review and finish** page, review the information you entered. If necessary, correct any information that was entered incorrectly. When all information is correct, select the **Finish adding** button to add the user account.

### Creating users with the Import multiple users option

The **Add multiple users** option in the Microsoft 365 admin center can be used to add large numbers of users in one operation by using a comma-separated values (CSV) file. Microsoft 365 provides an empty template and a sample CSV file to make the process easier. A text-editing tool such as Notepad or Microsoft Excel can be used to edit these files. To create users by using bulk import, you should complete the following steps:

1.  In the Microsoft 365 admin center, on the **Active users** page, select **Add multiple users**.
2.  Browse to the CSV file that contains your users.
3.  The verification result informs you if any errors are in your file. If there are errors, you can view the results in the linked log file.
4.  On the **Set user options** page, set the new users’ sign-in status, location, and licenses.
5.  On the **View your results** page, specify who should receive the email of the results. It's recommended that you include your own email address so that you can provide the temporary passwords to your new users.

### Creating users with Windows PowerShell

Some enterprise administrators prefer to use Windows PowerShell rather than the Microsoft 365 admin center to complete user administrative functions. After installing and connecting to the Azure Active Directory PowerShell module, you can use the **New-AzureADUser** cmdlet to create a user account in Microsoft 365.

```
New-AzureADUser -UserPrincipalName username@domainname –DisplayName “Firstname Lastname” –FirstName “Firstname” –LastName “Lastname”
```

For example, the following cmdlet creates a user account for Patti Fernandez:

```
New-AzureADUser –UserPrincipalName PattiF@Adatum.onmicrosoft.com –DisplayName “Patti Fernandez” – FirstName “Patti” –LastName “Fernandez”
```

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Create a user account for Adatum's Enterprise Administrator](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M2-L1-E2-T1/index.html?azure-portal=true).

This simulation guides you through the steps to create a Microsoft 365 user account and assign it the Global Administrator role. This demonstration is centered around the fictitious Adatum Corporation. You'll create a user account for the equally fictitious Holly Dickson, who is Adatum's new Enterprise Administrator. You'll then assign Holly the Microsoft 365 Global Administrator role.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”