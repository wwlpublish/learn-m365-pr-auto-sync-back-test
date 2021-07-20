To help support Megan Bowen, the Human Resources admin at Contoso Electronics, you have successfully built and trained a document understanding model. The model can accurately identify and label a benefits change letter. The model can also extract the insurance provider's name from each benefits change letter and add that name to a column in the SharePoint library. So far, however, you have only applied this to training files.

Now you are now ready to show Megan, who volunteered to be the model owner for Human Resources, how to apply the new benefits change letter model to the Human Resources SharePoint libraries.

## Steps to apply the document understanding model  

1. Start or return to the Content center.
   1. From the training page, click on "Benefits change letter" in the navigation bar at the top of the page.

    ![Graphical user interface, application](../media/image060.png)

1. Notice that the final button "Apply model to libraries" is now lit up for selection.
   1. Click "Apply model."

    ![Graphical user interface, application, website, Teams](../media/image061.png)

1. The "Add benefits change letter" dialogue box opens on the right-hand side of the screen with a list of SharePoint sites.
   1. Select the SharePoint site you want to apply the model to. In this case, select Human Resources.

    ![Graphical user interface, application](../media/image063.png)

1. Now select the library where you want the model to run. In this case, you opt to use a blank "Documents" library to apply the model to. This is the fast and easy way to run a model when you have large libraries. You will apply the model the library and then mass-import your files, which will be classified and extracted by the model as the files copy into the library.
   1. Select "Documents."
   1. Click the "Add" button at the bottom of the dialogue box.

    ![Graphical user interface, application, Word](../media/image065.png)

1. If you prefer to apply the model to the existing HR Letters library, you will need to select each file, then choose "classify and extract" to run the model against the files one at a time.
1. Click "Go to the library" at the bottom of the dialogue box.
1. The empty "Documents" library opens.
   1. Note that this library has the model applied to it. You see this in the upper right-hand navigation pane in "View."
   1. Also note the column names preset in the library. These are the columns you defined when you built the model.

    ![Graphical user interface, text, application, email](../media/image067.png)

1. Upload your files.
   1. Click on "Upload" in the upper left-hand corner.
   1. Select "Files."
   1. Navigate to HR Letters.
   1. Click "Select all" to load the files into the new library where the model has been applied.
   1. The upload may take a moment to complete.
1. Initially, files copy into the library with only the "Content type" column filled in, but SharePoint Syntex goes to work evaluating each file against the model.
   1. As the model processes files, columns fill automatically.

    ![Graphical user interface, application](../media/image069.png)

1. Once processing is complete, all benefits change letters should be labeled as such in the Content Type column. Provider name will be listed, and all Benefit change letters will have a Retention label of "Confidential."
   1. You can now sort and filter by the Content Type or Provider columns.

Congratulations! You've created a document understanding model that classifies files and extracts data. You've also applied that model to a document library and had each file analyzed.
