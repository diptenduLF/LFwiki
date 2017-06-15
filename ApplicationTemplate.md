>The purpose of template is to globally set up for configuration section, element structure section and it also embeds all external resources like js, css in a page. Application Template in LF is one of the most important parts. It helps the user to load common resources, to provide common configurations, to provide default values for different parts. It reduces the repetitive coding. Changing some values in the application template will affect all the interfaces that are using that particular application template.

**1.Overview (difference with content templates)**
 >Sometime user may confuse the Application Template with well-known content template. But maybe there some similarities between these two but there are huge differences. The content template is something which provides same content in different web pages(Reference [ 12 ]).JSF2 provides the implementation of content templates(Reference [ 13 ]).
 
 >A template will contain ui:insert‘ and a page will contain ui:define with the same name. Then the page will inserted into the template during runtime and common parts need not be rewritten(Reference [ 10 ]).`<html xmlns="http://www.w3.org/1999/xhtml"`
`xmlns:h="http://java.sun.com/jsf/html"`
`xmlns:f="http://java.sun.com/jsf/core"`
`xmlns:ui="http://java.sun.com/jsf/facelets">`
`<f:view contentType="text/html">`
`<h:head>`
`--`
`--`
`</h:head>`
`<h:body>`
`<ui:insert name="pageName"></ui:insert>`
`</h:body>`
`</f:view>`
`</html>`

 >The page –`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"`
`"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`
`<ui:composition xmlns="http://www.w3.org/1999/xhtml"`
`xmlns:h="http://java.sun.com/jsf/html"`
`xmlns:f="http://java.sun.com/jsf/core"`
`xmlns:ui="http://java.sun.com/jsf/facelets"`
`template="/xhtml/layout/layout.xhtml">`
`<ui:define name="pageContent">`
`--`
`</ui:define>`
`</ui:composition>`

 >ui:composition indicates it is not a full page and it will be inserted within some template and template name need to be mentioned in template attribute of the same.
The difference between this two – There are no way to define default values in content template. Also, it is not possible to define the default values for different section like an attribute‘s default value in content template. The most important difference the main page is inserted in the content template i.e. the head and body are present in the content template but this is not the case for application template. Content template mostly stores the common parts of different pages whereas the application template does not store the common parts of the pages but it stores the common configuration of the pages.

**2.Functionality**
    
   
   **2.1 Structure of an Application Template:**
     
   >The Template file is a zip file that contains the template xml and all the resources that are using in the   template.
   > Here is an example of template file structure:

 ![zip file](https://github.com/diptenduLF/LFwiki/blob/master/images/image.png)

   **2.2 Overview of Application Template Xml:**
   >LF provides a simple way for provide common configuration through Application template. ―ApplicationTemplate‖ screen in the CoreAdmin application help for managing application templates. Please go through section 10.1.1 for more details. From this screen we can upload, modify, delete and edit application template xmls. A basic application template xml looks like –`<application-template xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`
	`xmlns="http://learnityframework.org/"`
	`xsi:schemaLocation="http://learnityframework.org/ http://localhost:8080/learnitymsme/xsd/application_template.xsd"`
	`title="Aparna"> `
	`<application-defaults>`
		`<configuration-section>`
			`<attribute name="ThemeID" defaultvalue="bootstrap_theme"></attribute>`
			`<attribute name="createsession" defaultvalue="false"></attribute>`
			`<attribute name="checkrole" defaultvalue="true"></attribute>`
		`</configuration-section>`
`<class name="inputtext">`
			`<section name="structure">`
				`<attribute name="size" defaultvalue="20"></attribute>`
			`</section>`
		`</class>`
		`<class name="DBgrid">`
			`<section name="structure">`
				`<attribute name="CustomEditButton" defaultvalue="false"></attribute>`
				`<attribute name="resetSearchOnClose" defaultvalue="false"></attribute>`
				`<attribute name="width" defaultvalue="735"></attribute>`
				`<attribute name="height" defaultvalue="250"></attribute>`
			`</section>`
		`</class>`
		`<class name="Conditionalgrid">`
			`<section name="structure">`
				`<attribute name="CustomEditButton" defaultvalue="false"></attribute>`
				`<attribute name="resetSearchOnClose" defaultvalue="false"></attribute>`
			`</section>`
		`</class>`
	`</application-defaults>`
	`<framework-asset-delivery>`
		`<asset type="js" deliverymode="CDN" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.2.0/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="2" filename="grid.locale-en.js" assetpath="../coreadmin/resource/jQgrid/i18n/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="3" filename="jquery.jqGrid.min.js" assetpath="../coreadmin/resource/jQgrid/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="4" filename="jquery-ui.js" assetpath="../coreadmin/resource/jquery-ui/" />`
`<asset type="css" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="5" filename="jquery-ui.css" assetpath="../coreadmin/resource/jquery-ui/" />`
		`<asset type="css" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="6" filename="jquery-ui.structure.css" assetpath="../coreadmin/resource/jquery-ui/" />`
		`<asset type="css" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="7" filename="jquery-ui.theme.css" assetpath="../coreadmin/resource/jquery-ui/" />`
                        `<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="8" filename="engine.js" assetpath="../dwr/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="9" filename="util.js" assetpath="../dwr/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="10" filename="PortalEngine.js" assetpath="../dwr/interface/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="11" filename="LearnityUtil.js" assetpath="../coreadmin/js/" />`
                        `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="12" filename="main2.css" assetpath="../coreadmin/css/"/>`
`<asset type="js" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="13" filename="jquery.validate.js" assetpath="../coreadmin/resource/validate/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="14" filename="jquery.blockUI.js" assetpath="../coreadmin/resource/block/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="EOB"`
			`deliverysequence="15" filename="jquery.alphanumeric.js" assetpath="../coreadmin/js/" />`
`<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
		`deliverysequence="16" filename="bootstrap.css" assetpath="../coreadmin/resource/bootstrap/css/" />`
                  `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="17" filename="bootstrap-theme.css" assetpath="../coreadmin/resource/bootstrap/css/" />`
                          `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="18" filename="ui.multiselect.css" assetpath="../coreadmin/themes/" />`
		   `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
	                   `deliverysequence="19" filename="main.css" assetpath="../coreadmin/css/" />`
                     `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="20" filename="learnity1_main.css" assetpath="../coreadmin/css/" />`
                       `<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="21" filename="bootstrap.js" assetpath="../coreadmin/resource/bootstrap/js/" />`
`<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="23" filename="ui.jqgrid-bootstrap.css" assetpath="../coreadmin/resource/jQgrid/" />`
		`<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="24" filename="ui.jqgrid-bootstrap-ui.css"`
			`assetpath="../coreadmin/resource/jQgrid/" />`
                         `<asset type="css" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="25" filename="ui.custom-bootstrap-ui.css"`
			`assetpath="../coreadmin/resource/app/" />`
                         `<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
		`deliverysequence="26" filename="jquery.dynatree.js" assetpath="../coreadmin/resource/dynatree/" />`
                          `<asset type="css" deliverymode="Inline" pagelocation="BOH"`
			`deliverysequence="27" filename="ui.dynatree.css"`
			`assetpath="../coreadmin/resource/dynatree/skin-vista/" />`
              `</framework-asset-delivery>`
`</application-template>`




		


   **2.3 Functionality With Application Template Xml:**

   >In this file we can define the default values of any component. The different element of the template xml -
  
  * application-template – It is the parent element of this xml. This element contains the title of the template. Template title should be unique. Two templates cannot have the same title. It also contains an attribute named as UIframework. Currently two types of templates are supported bootstrap and jQuery. If any template is mentioned as bootstrap then bootstrap related configurations are happened in the generated HTML for the interface that is using the bootstrap template.
     Application Template Xml has two sections-
     *  Application Defaults
     * Asset Delivery

    **Application Default:**
    >`<application-defaults>`
		`<configuration-section>`
			`<attribute name="ThemeID" defaultvalue="bootstrap_theme"></attribute>`
			`<attribute name="createsession" defaultvalue="false"></attribute>`
			`<attribute name="checkrole" defaultvalue="true"></attribute>`
		`</configuration-section>`
		`<class name="inputtext">`
			`<section name="structure">`
				`<attribute name="size" defaultvalue="20"></attribute>`
			`</section>`
		`</class>`
	`</application-defaults>`


     * configuration-section – It can have only one configuration section. It holds any number of attribute elements. The attribute element contains two attributes- name and defaultvalue. The name attribute can have the following values –
       * ThemeID
       * Enable_Caching
       * CacheName
       * CacheDynamicJS
       * CacheDynamicCSS
       * CacheDynamicImage
       * createsession
       * checkrole
     >These are actually the configuration section properties of the interface xml. The default values of the configuration property can be defined in this section. For an example if the name is ―ThemeID‖ then the corresponding default value holds the default theme for the interfaces that are using this application template.
    * class –

    >Any number of class elements can be defined under application-template. The class element contains a name attribute and any number of section elements. The name attribute corresponds to any available part class i.e. LF class. This section defines the default values for the different attributes of a class. For an example –`<class name="DBgrid">`
`<section name="structure">`
`<attribute name="CustomEditButton" defaultvalue="false"></attribute>`
`<attribute name="resetSearchOnClose" defaultvalue="false"></attribute>`
`<attribute name="width" defaultvalue="735"></attribute>`
`<attribute name="height" defaultvalue="250"></attribute>`
`</section>`
`</class>`
   
    >So, the section element contains any number of attribute element. The name attribute of the section element contains the name of the section for which the attribute will have the default value. The name attribute in the attribute element contains the name of the part class attribute and the defaultvalue contains the default value. In the above example, if any class use this template and uses a DBGrid class then its default width would be 735 and default height would be 250 and it will not reset the table after search pop up is closed as the resetSearchOnClose is made as false. But these values can be overwritten in the interface xml.

   
    **Asset-delivery**
    >`<framework-asset-delivery>`
		`<asset type="js" deliverymode="CDN" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.2.0/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="2" filename="grid.locale-en.js" assetpath="../coreadmin/resource/jQgrid/i18n/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="3" filename="jquery.jqGrid.min.js" assetpath="../coreadmin/resource/jQgrid/" />`
		`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="4" filename="jquery-ui.js" assetpath="../coreadmin/resource/jquery-ui/" />`
`</framework-asset-delivery>`

    >This contains the common js and css files. It is made of any number of asset elements. The asset element contains the following attributes-
     * type – It can be js or css. This denotes which type of asset it is.
     * deliverymode – It can be ―URIPath‖, ―Inline‖ or ―Dynamic‖. First one tells that the resource will be loaded as a link. It creates a static link in the markup. The second one tells that the resource will be embedded in the markup. The third one tells that the resource will be served via a servlet. So it cannot be cached in the browser.
     * pagelocation – It can be ―BOB‖, ―EOB‖, ―BOH‖, ―EOH‖. The first one tells that resource will be added at the beginning of the body. The second one tells that the resource will be added at the end of the body. The third one tells that resource will be added at the beginning of the head. The fourth one tells that the resource will be added at the end of the head.
     * deliverysequence – It tells the sequence in which the resource will be added in the page. The dependent resource should have larger sequence number than the resource on which it depends.
     * filename –name of the asset file with extension
     * assetpath – the path of the asset.
    >During code generation the definition in the framework in the asset  delivery section are used to generate the asset loading namely <script> and <link>. For example the template xml given above leads to the generation of following HTML markup-`<head>`
	`<META http-equiv="Content-Type" content="text/html; charset=UTF-8"> `
	`<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.2.0/jquery.js" type="text/javascript"></script><script src="../coreadmin/resource/jQgrid/i18n/grid.locale-en.js" type="text/javascript"></script><script src="../coreadmin/resource/jQgrid/jquery.jqGrid.min.js" type="text/javascript"></script><script src="../coreadmin/resource/jquery-ui/jquery-ui.js" type="text/javascript"></script>type="text/javascript"></script> `
	`….</head>	`

  **2.4 Code Generation**
  >Using the Delivery mode of the asset Delivery their different markup is generated---

   >Using “URIPath” delivery mode of asset file "jquery.js".`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="../coreadmin/js/js/" />`
    The Markup is generated of this:`<script src="coreadmin/js/js/jquery.js" type="text/javascript"></script>`
   
   >Using “Inline” delivery mode of asset file "jquery.js":`<asset type="js" deliverymode="Inline" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="../coreadmin/js/js/" />`
    The Markup is generated of this in the body of the LoginPage:`(function( factory ) {`
	`if ( typeof define === "function" && define.amd ) {`
`…………………………………………}`

   >Using “Dynamic” delivery mode of assetfile "jquery.js":`<asset type="js" deliverymode="Inline" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="../coreadmin/js/js/" />`
    The Markup is generated of this:`<script src="./interfaceenginev2.AssetJs?template_id=58 &amp;file_name=jquery.js" type="text/javascript"></script>`

  >Using “CDN” delivery mode of assetfile "jquery.js":`asset type="js" deliverymode="CDN" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.2.0/" />`
   The Markup is generated of this:`<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.2.0/jquery.js" type="text/javascript"></script>`

 >Using the pagelocation of the asset Delivery their different markup is generated---

  >Using “BOH” pagelocation of assetfile "jquery.js":`<asset type="js" deliverymode="URIPath" pagelocation="BOH"`
			`deliverysequence="1" filename="jquery.js" assetpath="../coreadmin/js/js/" />`
   The Markup is generated of this:`<head> `
	`<META http-equiv="Content-Type" content="text/html; charset=UTF-8"> `
	`<script src="coreadmin/js/js/jquery.js" type="text/javascript">`
`……..</head>`

  >Using “EOB” pagelocation of assetfile "jquery.js":

  **2.5 Definition Section**

>Template can be defined in two ways –

  * Interface Configuration section – Template can be mentioned in the interface‘s configuration section. This provides us the power to use a separate template for a particular interface. This template selection has the highest priority.`<configuration TemplateID =" GridTreeNew "></configuration>`
  * Default Theme – We can specify a default template in the ApplicationTemplateManagement screen. If we don‘t specify any template in the interface then the default template is used.

>The user creation page interface.xml contains GridTreeNew template. This is a non-bootstrap template. So it does not use bootstrap properties. The corresponding grid also does not use bootstrap grid. The page with jQuery grid looks like-

>![user acnt admnstratn](https://github.com/diptenduLF/LFwiki/blob/master/images/user%20acnt%20administration.png)

>Now, we will change the template from ―InterfaceManagement‖ screen–

>![interface management](https://github.com/diptenduLF/LFwiki/blob/master/images/interface%20management.png)

>We changed the template now we will go to the screen again to view it –

>![management](https://github.com/diptenduLF/LFwiki/blob/master/images/interface%20management2.png)

>We can see the grid is using the bootstrap now and the button is also using bootstrap styling. The css and js files are also changed. So with the use of a template gives us the strength to control the interfaces from a central place. Any change in the template will affect all of the interfaces using that template.

**3.Implementation Details**

  >Template implementation can be divided into three parts –

  * Application Template Management Screen

   >The Application Template Management screen is supported by ApplicationTemplateManagement servlet. When a template xml is uploaded that time the ApplicationTemplateManagement servlet took the responsibility to do the necessary steps. It first validates the xml against application_template.xsd. If the validation succeeds then the template xml is parsed and it checks if the template already exists or not. It checks this against the template title. If the template already exists then it deletes the old one and inserts the new template in the database.

  * Resource Application Template Screen

   >The “Resource Application Template” screen or under the Show button screen of the zip file is supported by “ResourceApplicationTemplate” servlet. It contains two fields one for all the resources and another for the template xml.   
This screen is responsible for maintaining application templates and all assets or resources. We first select an application template and click on the show button.


  * Apply Template during Markup Generation
    >During mark-up generation of an interface.xml the template is selected in the following way-
   * TemplateID attribute of configuration section of interface.xml is checked. If it is present and corresponding template is also present then that is used.
   * If no template is selected on the above step then it checks for default template. A template can be set as default from the ApplicationTemplateManagement screen. If default template is present then that is used otherwise no template is used.

   >In the DisplayEngine class the default values of the configuration section and for different part classes are fetched and applied during markup generation. If any part class has a value for a specific attribute then that is used otherwise it checks the template. If any default value is present for that attribute for that specific part class then that is used.