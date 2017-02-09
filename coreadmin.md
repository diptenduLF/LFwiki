>This is the heart of LF. This application gives the power of LF to the user. The user can upload application template, theme, and interface using this. He or she can edit, update or delete the xmls. The cache can be manipulated. The roles which will be used in the application built on top of this framework can be configured.

**1.Functionality**

  >The different functionalities of this framework are distributed in different screens. Different screens are responsible for different functionality. All of them are defined in the below sections. To login to the application a user id and password is provided to the user. This is for the admin login. The Login screen –![login](https://github.com/diptenduLF/LFwiki/blob/master/images/lt%20page.png)

 >After logging to the application, user will forwarded to the home page. From here, user can navigate to any other page. The Home Page –![core admin](https://github.com/diptenduLF/LFwiki/blob/master/images/Core%20Admin%20Home%20Page.png)

* Application Template management
  >This screen is responsible for maintaining application templates. On load, this screen shows the existing application template details. The name, default value, the UI framework, UI timeout, its size and upload time is shown. Details of application templates are described in section 7.![coreadmin](https://github.com/diptenduLF/LFwiki/blob/master/images/Core%20Admin%20Application%20Template%20Page.png)
 
  >In this screen, we can upload an application template. We can upload any application template in two ways –
  * For new application template, we will select the file by clicking on Choose File button and then upload it. If we want to make it as default template then Default Value check box has to be selected.
  * For overwriting existing application template, we first need to select the existing application template by clicking on the radio button the need to select the file and upload it.
   
    >To download an existing application template, we need to select it and click on the download button. It will be downloaded as an xml file.
   
    >To delete an existing application template, we need to select it and click on the delete button. A confirmation will come, if we confirm, it will be deleted.
   
    >If we want to set any existing template as default then we need to select it and click on the Set as Default button. If any template was previously assigned as default then that will be reset .The current one will be selected as default.

    >The view button helps us for inline editing of the application template. The view button opens a pop up -![admin](https://github.com/diptenduLF/LFwiki/blob/master/images/Application%20Template%20Online%20Edit.png)

 >In this we can edit the application template and save it. We don‘t need to upload it again. This facility is provided in this version.

* Theme Management

 >This screen is responsible for maintaining themes. On load, this screen shows the existing theme details. The name, default value, size and upload time is shown. Details of themes are described in section 8.![thememanagementpage](https://github.com/diptenduLF/LFwiki/blob/master/images/Theme%20Management%20Page.png)
 
 >In this screen, we can upload a theme. We can upload any theme in two ways –
  * For new theme, we will select the file by clicking on Choose File button and then upload it. If we want to make it as default theme then Default Value check box has to be selected.
  * For overwriting existing themes, we first need to select the existing theme by clicking on the radio button the need to select the file and upload it.

 >To download an existing theme, we need to select it and click on the download button. It will be downloaded as an xml file.

 >To delete an existing theme, we need to select it and click on the delete button. A confirmation will come, if we confirm, it will be deleted.

 >If we want to set any existing theme as default then we need to select it and click on the Set as Default button. If any theme was previously assigned as default then that will be reset .The current one will be selected as default.

 >The view button helps us for inline editing of the theme. The view button opens a pop up -![onlinetheme](https://github.com/diptenduLF/LFwiki/blob/master/images/Online%20Theme%20Edit.png)
 
 >In this we can edit the theme and save it. We don‘t need to upload it again. This facility is provided in this version.

* Manifest Management

 >This is a new screen introduced in this version. Previously, manifest can only be uploaded. Now, we can add an interface in the manifest from the screen itself. We don‘t need to upload the manifest again and again.![mainfest](https://github.com/diptenduLF/LFwiki/blob/master/images/Manifest%20Landing%20Page.png)

 >This screen shows the details of the interfaces associated with the manifest. The details include interface title, interface file name and the type i.e. interface or fragments. It also shows the total number of interfaces as well. We can search to check if an interface is associated with the manifest or not. To add a new interface with the manifest, we need to click on the new button.![addmainfest](https://github.com/diptenduLF/LFwiki/blob/master/images/Add%20Manifest%20Entry.png)

 >The manifest name can be entered at the time of inserting the first interface. We need to select the type and provide the other details i.e. name, title and file name of the interface. Then we need to click on the save button to associate it with the manifest. An interface can be uploaded only after associating it with the manifest.

* Interface Role management

  >In this screen we can view, edit or associate a new interface with the existing role.![interface](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Role%20Landing%20Page.png)

  >After selecting the role from the drop down the interface drop down shows the existing interfaces which are associated with the selected role.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Role%20Selection%20of%20Role.png)

  >After selecting any interface it shows the different sections ids of the interface which are associated with the current role.![view](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Role%20Management%20View%20Interface%20on%20Role.png)

  >As we already mentioned that an interface may have more than one layout, content, style,behaviour sections. If an interface contains more than one section then in the drop down it will show more than one section and the association of the section with the role can be changed.

  >After adding an interface from the manifest screen, the second step is to associate the interface with a role. This can be done by the New button.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Role%20Management%20Add%20New%20Interface%20Role%20Association.png)

  >From the role drop down, we can select the role with which we want to associate the interface. After selecting the role, all of the available interfaces which are not associated with the currently selected role will be displayed.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Role%20Management%20Add%20New%20Interface%20Role%20Association%20On%20Role.png)

  >We need to select the interface and provide the layout, content, behaviour and style id for the current role. A same interface can be associated with different roles. The ids of different sections should be different. It may be same as well. In that case same view will come for both the roles. After providing all the details, it needs to be saved. When uploading an interface the ids which are mentioned here should be same with the different section‘s id of the interface.

* Interface Management

  >This screen provides us the functionality to manage interfaces. This screen show the details of interfaces including the interface file name, interface title, type (interface/fragment), interface size , last updated and other details. This screen also shows total number of items, total number of interfaces, and number of fragments, manifest and interface role count.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Management%20Landing%20Page.png)

  >After adding an interface from the manifest management screen the user can view that in this screen. The interface can be searched from the search box. After finding it user needs to select the interface and upload it from this screen. The interface.xml and the resource file should be zipped together with the file name provided in the manifest screen. The type will be auto selected after selecting an interface. It can be changed by the user. Wrong selection of type will prevent the upload. The inline css and js check boxes help the user to add the js or css files as inline content in the HTML. The manifest/role xml can also be uploaded. The proper type needs to be selected from the drop down. Uploading manifest/role will result in same as adding manifest/role from their respective screens. To upload all the interfaces, manifest and role xml together we need to zip the zipped interfaces, role xml and manifest xmls. Then we need to select the interface collection from the drop down and upload it.

  >The interface zip/manifest/role xml can be downloaded from this screen. The proper resource need to selected and click on download button to download it. All of the resources can be downloaded together as an interface collection by clicking on Download All button.

  >The interface can be deleted from this screen. The proper resource need to selected and click on delete button to delete it. This deletes the manifest and role association as well. The delete all will delete all of the interfaces.

  >Manifest and Interface Role can be added from their respective screens as well. But it does not update the manifest/interface role xml. To update the manifest/interface role xml we need to generate it by clicking on the appropriate buttons on this screen.

  >The Show button will display the contents of an interface. The interface needs to be selected first and then click on the Show button.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Management%20Show%20Interface%20Screen.png)

  >The interface.xml or the resource files can be separately uploaded or deleted from this screen. To upload a resource, select the resource and the select the new file and upload it. The resource can be downloaded as well. The ―View‖ button is currently only applicable for the interface.xml, css and js files. This button shows the content of the file and it can be modified from the screen itself. User does not need to upload it again and again.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Management%20Online%20Edit%20Interface.png)

* Interface Template Theme Management

  >This screen displays the interfaces and fragments with their current application template and theme. It also shows the last updated time stamp of the interface and the same for the theme and application template.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Template%20Theme%20Management%20Landing%20Page.png)

  >Uploading an interface the corresponding HTML is stored in the database. This HTML depends on the current Application Template and Theme. There can be a case that the Application Template or the Theme is changed after the interface is uploaded. But in this case the change will not be reflected in the interface as the interface is already uploaded. This screen provides us a way to overcome this problem. The last column named as Refresh required tells us that if the interface is needs to be refreshed or not. If the value of this column is Yes, this means it is not using the current Application template or Theme. We can select the interface and then refresh it to use the current template or theme. If too many interfaces need to be refreshed then we can use the Refresh All feature.

  >This screen also provides us a way to change the Application Template or Theme of an interface. For this we need to select the interface and click on the Application Template Theme Change button.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/Interface%20Template%20Theme%20Management%20Edit%20Template%20Theme%20Association.png)

  >This popup will show the current Application Template and Theme which are being used by the interface. This can be changed from the drop down. The drop downs consist of the available Application Template and Theme. We can change it and click on save.

* Role Management

  >This screen provides us the facility to create different roles which will be used by the application built on top of this framework.![role](https://github.com/diptenduLF/LFwiki/blob/master/images/Role%20Management%20Landing%20Page.png)

  >It shows the existing roles when the page loads. Selecting any of them will display the details in the below area. We can add a new role and delete an existing role as well. This role will be displayed in the Interface Role management screen.

**2.Implementation Details**

  >Backbone of every screen is a servlet. It provides the landing page and process each of the requested operations.

  >The Theme Management screen is supported by ThemesManagement java class. The backbone of Application Template management is ApplicationTemplateManagement. For managing manifest screen ManifestManagement servlet is used. The responsibility of Interface Role management is on the servlet named as InterfaceRoleManagement. Interface Management screen has two parts. First one is the landing page and second one is the pop up which opens when Show button is clicked. The base page is controlled by InterfaceManagement. The pop corresponding to the Show button is supported by ResourceInterface. The Interface Template Theme Management screen is supported by InterfaceTemplateThemeManagement java class. Role Management screen is controlled by RoleManagement servlet. CacheManagement servlet is responsible for Cache Management screen.