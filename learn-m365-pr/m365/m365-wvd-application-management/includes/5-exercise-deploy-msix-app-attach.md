As a senior administrator working for Contoso, you've been asked to adopt the application delivery method and to use the MSIX app attach in your Windows Virtual Desktop environment.

## Exercise: Use MSIX app attach in Windows Virtual Desktop

You decide to implement MSIX app attach delivery of the new applications in your Windows Virtual Desktop.

In this exercise, you will add and test app deployed using MSIX app attach.
You will:

- Add MSIX app attach in Windows Virtual Desktop
- Publish MSIX app attach to desktop application group (DAG)
- Assign users to an app group
- Publish MSIX app attach to RemoteApp group (RAG)
- Test the MSIX app attach 

> [!NOTE] 
> To complete the Exercise unit, you need to have active Azure subscription and running Windows Virtual Desktop Environment.
> You can identify all the prerequsites for this exercise in the forth unit of this module **Manage MSIX app attach**

### Task 1: Add MSIX app attach in Windows Virtual Desktop

1. Open the Azure portal, and in **Search resources, services and docs (G+I)** type and then select Windows Virtual Desktop.
2. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Host pools**.
3. On the **Windows Virtual Desktop | Host pools** page, select the desired host pool.
4. On the **_your host pool_** page in the navigation menu on the left side, from the **Manage** section, select **MSIX packages**.
5. On the **_your host pool_|MSIX packages** page from the toolbar select **+ Add**.
6. On the **Add MSIX package** windows in the **MSIX image path** field add the UNC path of your MSIX image.

>[!NOTE]

>If you are storing MSIX image in Azure Files, refer to the fourth unit **Manage msix app attach** in this module, to retrieve the UNC path from the URL location of the MSIX image.

7. Once that you add UNC path of your MSIX image select the following:

|||
| --- | --- |
| **MSIX image path** | UNC path of the MSIX image |
| **MSIX package** | MSIX package, loaded from the MSIX image |
| **Package applications** | MSIX applications loaded from MSIX package. |
| **Display name** | Type descriptive name |
| **Version** | Retrieved form the MSIX package  |
| **Registration type** | **On-demand –** |
| **State** | **Active** |

:::image type="content" source="../media/04-Screenshot-of-Add-MSIX-package-in-WVD.PNG" alt-text="Screenshot of MSIX package in WVD." border="true":::

8. Select **Add** to add the MSIX image into host pool.

### Task 2: Publish MSIX app attach to desktop application group (DAG)

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, select the desired application group.
3. On the application group page, in the navigation menu, in the **Manage** section, select **Applications**.
4. On the **_your application group_|Applications** page from the toolbar select **+ Add**.
5. On the **Add application** windows select:

|||
| --- | --- |
| **Application source** | MSIX package |
| **MSIX package** | Select one of the MSIX packages |
| **Application name** | Type descriptive name |
| **Display name** | Type descriptive name |
| **Description** | Provide descriptive name for the MSIX package |

:::image type="content" source="../media/05-Screenshot-of-add-app-application-group.PNG" alt-text="Screenshot of adding an MSIX package in Application Group." border="true":::

6. Select **Save** to add the MSIX image into the application group.

### Task 3: Assign users to an app group

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, select the desired application group.
3. On the application group page, in the navigation menu, in the **Manage** section, select **Assigments**.
4. On the **_your application group_|Assigments** page from the toolbar select **+ Add**.
5. On the **Select Azure AD users or user groups** select your users or groups and then select **Select**.

### Task 4: Publish MSIX app attach to RemoteApp group (RAG)

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, from the toolbar select **+ Add**.
3. On the **Create an application group** in the **Basics** provide the following information:

|||
| --- | --- |
| Subscription | Select your Azure subscription. |
| Resource Group | Select your existing resource group that contains your host pool.|
| Location | Region will be automatically selected from the location of the host pool. |
| Application group type | RemoteApp |
| Application group name | Provide descriptive name such as **ContosoApps**. |

4. Select **Next: Applications >**
5. On the **Applications** tab, select **+ Add applications**, and in the **Add application** grid provide the following information:

|||
| --- | --- |
| Application source | MSIX package. |
| MSIX package | Select once of the packages that you add into your host pool.|
| MSIX application | Select one of the MSIX applications |
| Application name | Provide descriptive name. |
| Display name | Provide descriptive name. |
| Description | Provide description of the application. |
| Icon path | You can add path to your custom icon |
| Icon index | Add index of the icon |
| Show in web feed | Yes |

6. Select **Save** to add application and then select **Next: Assignments >**.
7. On the **Assignment** tab, select **+ Add Azure AD users or user groups** and then select one orr multiple users or groups from Azure AD.
8. Select **Next: Workspace >**.
9. On the **Workspace** tab, select **Yes** for **Register application group** and then form **Register application group** dropdown menu select one of the RAG.
10. Select **Next: Tags >**.
11. On the **Tags** tab provide **Name** and **Value** for the tags and select **Next: Review + create >**.
12. Once the validation passed select **Create** to finish creation of RemoteApp group.
13. Wait for the deployment to complete.

### Task 4: Test the MSIX app attach 

1. Open the remote desktop client and select **Subscribe**.
2. Sign in with the credential of the user which has been assigned access to application group that contain MSIX app attach.
3. Double click the **SessionDesktop** icon and sign in with the credential of the user.
4. Once you remote in the virtual machine, open start menu, and notice the shortcut of the published app.
5. Close the Remote Desktop session.

:::image type="content" source="../media/05-Screenshot-of-Edge-Dev.PNG" alt-text="Screenshot of published MSIX app attach" border="true":::

## Results

This personal exercise environment is insufficient to demonstrate the results of the exercise if it were performed in a more real-world work environment. The following video demonstrates the results you would be able to observe in a more real-world environment.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Learn/Data-Serialization-Languages/player?format=ny]
