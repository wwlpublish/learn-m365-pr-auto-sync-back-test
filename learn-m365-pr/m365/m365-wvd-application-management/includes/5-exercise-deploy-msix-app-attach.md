As a senior administrator working for Contoso, you've been asked to adopt the application delivery method and to use the MSIX app attach in your Windows Virtual Desktop environment.

## Exercise: Use MSIX app attach in Windows Virtual Desktop

You decide to implement MSIX app attach delivery of the new applications in your Windows Virtual Desktop.

In this exercise, you'll add and test apps deployed by using MSIX app attach.
You will:

- Add MSIX app attach in Windows Virtual Desktop
- Publish MSIX app attach to desktop application group (DAG)
- Assign users to an app group
- Publish MSIX app attach to RemoteApp group (RAG)
- Test the MSIX app attach

> [!NOTE]
> To complete the Exercise unit, you need to have an active Azure subscription and run Windows Virtual Desktop Environment.
> You can identify all the prerequisites for this exercise in the fourth unit of this module, **Manage MSIX app attach**.

### Task 1: Add MSIX app attach in Windows Virtual Desktop

1. Open the Azure portal, and in **Search resources, services and docs (G+I)**, enter and then select Windows Virtual Desktop.
2. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Host pools**.
3. On the **Windows Virtual Desktop | Host pools** page, select the desired host pool.
4. On the **_your host pool_** page in the navigation menu on the left side, from the **Manage** section, select **MSIX packages**.
5. On the **_your host pool_ | MSIX packages** page from the toolbar, select **+ Add**.
6. On the **Add MSIX package** window in the **MSIX image path** field, add the UNC path of your MSIX image.

>[!NOTE]

>If you're storing MSIX image in Azure Files, refer to the fourth unit in this module, **Manage MSIX app attach**, to retrieve the UNC path from the URL location of the MSIX image.

7. After you add the UNC path of your MSIX image, provide the following information:

|||
|---|---|
|**MSIX image path**|UNC path of the MSIX image|
|**MSIX package**|MSIX package, loaded from the MSIX image|
|**Package applications**|MSIX applications loaded from MSIX package|
|**Display name**|Enter a descriptive name |
|**Version**|Retrieved from the MSIX package|
|**Registration type**|**On-demand**|
|**State**|**Active**|

:::image type="content" source="../media/04-Screenshot-of-Add-MSIX-package-in-WVD.PNG" alt-text="Screenshot of MSIX package in WVD." border="true":::

8. Select **Add** to add the MSIX image into the host pool.

### Task 2: Publish MSIX app attach to desktop application group (DAG)

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, select the desired application group.
3. On the application group page, in the navigation menu, in the **Manage** section, select **Applications**.
4. On the **_your application group_ | Applications** page from the toolbar, select **+ Add**.
5. On the **Add application** windows, provide the following information:

|||
| --- | --- |
|**Application source**|MSIX package|
|**MSIX package**|Select one of the MSIX packages|
|**Application name**|Enter a descriptive name|
|**Display name**|Enter a descriptive name|
|**Description**|Provide a descriptive name for the MSIX package|

:::image type="content" source="../media/05-Screenshot-of-add-app-application-group.PNG" alt-text="Screenshot of adding an MSIX package in Application Group." border="true":::

6. Select **Save** to add the MSIX image in the application group.

### Task 3: Assign users to an app group

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, select the desired application group.
3. On the application group page, in the navigation menu, in the **Manage** section, select **Assignments**.
4. On the **_your application group_ | Assignments** page, from the toolbar, select **+ Add**.
5. On the **Select Azure AD users or user groups** page, select your users or groups, and then select **Select**.

### Task 4: Publish MSIX app attach to RemoteApp group (RAG)

1. On the **Windows Virtual Desktop** page, in the navigation menu on the left side, select **Application groups**.
2. On the **Windows Virtual Desktop | Application groups** page, from the toolbar, select **+ Add**.
3. On the **Create an application group**, in **Basics**, provide the following information:

|||
| --- | --- |
|**Subscription**|Select your Azure subscription.|
|**Resource Group**|Select your existing resource group that contains your host pool.|
|**Location**|Region will be automatically selected from the location of the host pool.|
|**Application group type**|RemoteApp|
|**Application group name**|Provide a descriptive name such as **ContosoApps**.|

4. Select **Next: Applications >**.
5. On the **Applications** tab, select **+ Add applications**, and in the **Add application** grid, provide the following information:

|||
|---|---|
|**Application source**|MSIX package|
|**MSIX package**|Select one of the packages that you add into your host pool.|
|**MSIX application**|Select one of the MSIX applications|
|**Application name**|Provide a descriptive name.|
|**Display name**|Provide a descriptive name.|
|**Description**|Provide a description of the application.|
|**Icon path**|You can add a path to your custom icon.|
|**Icon index**|Add an index of the icon.|
|**Show in web feed**|Yes|

6. Select **Save** to add application, and then select **Next: Assignments >**.
7. On the **Assignment** tab, select **+ Add Azure AD users or user groups**, then select one or multiple users or groups from Azure AD, and then choose **Select**.
8. Select **Next: Workspace >**.
9. On the **Workspace** tab, select **Yes** for **Register application group** and then from the **Register application group** drop-down menu, select one of the RemoteApp groups.
10. Select **Next: Tags >**.
11. On the **Tags** tab, provide a **Name** and **Value** for the tags and select **Next: Review + create >**.
12. Once the validation completes, select **Create** to finish creating the RemoteApp group.
13. Wait for the deployment to complete.

### Task 5: Test the MSIX app attach

1. From any computer, open a browser and then open the remote desktop web client by using the following URL [https://rdweb.wvd.microsoft.com/arm/webclient/index.html](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).
2. Sign in with the credentials of the user which has been assigned access to application group that contains MSIX app attach.
3. Select the **SessionDesktop** icon and sign in with the credentials of the user.

> [!NOTE]

> You might be prompted with a security warning to "Allow local resources." Select which local resources you want to allow the remote computer to access and then select **Allow**.

4. After you remotely access the virtual machine, open the **Start** menu, and notice the shortcut of the published app.
5. Close the Remote Desktop session.

:::image type="content" source="../media/05-Screenshot-of-Edge-Dev.PNG" alt-text="Screenshot of published MSIX app attach" border="true":::
