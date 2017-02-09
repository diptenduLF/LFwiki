**1.Overview**
   
   >The root element of an interface.xml file is interface. The id attribute of <interface> tag uniquely identifies an interface and it must be unique throughout the application. The case-sensitive nature of the id attribute values of interfaces provides a larger namespace to application developers. The type attribute can be ―Interface‖ or ―InterfaceFragment‖. An interface.xml file has a single configuration, structure and resource section. But it can have multiple layout, content, style and behaviour sections. Interface is validated against Interface.xsd. Failure in validation will stop it from getting uploaded(reference [ 6 ]).

 `<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"
id="LoginPage" title="LoginPage" type="Interface">`

**2.Functionality**
   
  * Interface
      
     * Configuration
     * Structure
     * Layout
     * Content
     * Style
     * Behaviour
     * Resource
  * Configuration Section
    
     >This section holds configuration related data. This is an optional section. If nothing is mentioned then the default Application Template‘s values will be considered. The following things can be configured using this section –
     * Role Checking
       
       >During the invocation of this interface if role checking is required or not can be configured by using this property. The attribute which is used for this is ―checkrole‖. The possible values are ―true‖ and ―false‖. For an example login page does not need role checking as any user should be able to access it. But for admin pages role checking is required. If role checking is required then the value is set as ―true‖ otherwise ―false‖.
     * Session Creation
      
       >This property allows us to define if this interface is required to create a server side session or not. ―createsession‖ attribute is used for this. The possible values are ―true‖ and ―false‖. For an example login page need to create a session. But for other pages session creation is not required. If it is required then the value is set as ―true‖ otherwise ―false‖.
     * Application template ID

       >This property enables us to specify the id of the application template which will be used during the markup generation from this interface. ―TemplateID‖ is the attribute used for this purpose. The value of this attribute needs to be an ID of the available templates. If the specified id does not match with any available template then it uses the default application template. It also uses default application template if nothing is mentioned in this. If no default application template is present then no template is used. The detail of the used application template is present in the generated mark up.
During the markup generation from the interface what application template will be used depends in the below mentioned way-
        * ThemeID attribute is checked. If it is present and corresponding theme is also present then that is used.
        * If ―ThemeID‖ is not present or the theme which is mentioned in ―ThemeID‖ is not present then it checks if any application template is being used or not. If application template is used and it holds some default value for theme then that theme is used.
        * If no theme is selected on the above step then it checks for default theme. If default theme is present then that is used otherwise no theme is used.
     * Enable Cache
       
       >This property allows us to define if this interface is required to be cached in server side. ―Enable_Caching‖ attribute is used for this. The possible values are ―true‖ and ―false‖. If an interface is cached then repetitive call does not fetch it from the database rather it fetches it from the server side cache. Caching helps us to respond faster. As it does not fetch the HTML from database, the delay due to different layer access is reduced.
     * Name of the Cache

       >This property allows us to define the cache name for the interface. This is only useful if cache is enabled. ―CacheName‖ attribute is used for this purpose.
     * Caching Dynamic Java Script
 
       >This property allows us to define if the dynamic image which is present in the interface is required to be cached in server side or not. ―CacheDynamicImage attribute is used for this. The possible values are ―true and ―false. If it is cached then repetitive call does not fetch it from the database rather it fetches it from the server side cache.`<configuration createsession="true" checkrole="false" TemplateID="Bootstrap"></configuration>`
  * Structure Section

     >The Structure section is used define the complete inventory of UI parts along with their attributes. The structure consists of many "part" sections. Each "part" section is responsible for one element in the screen. Each ‗part‘ must have a UI ‗class‘ and other optional attributes. All "part" should have one unique id by which these "part" will be recognized in other sections. A part element declared in the structure section should have one and only one reference in all the other sections except configuration and resource sections, although it is not mandatory that all the part elements in a structure section will have an entry in all the optional sections. But to be generated during a call to an interface it needs to be referred in the layout section defined for the role under which it is generated. Currently most HTML UI types are supported along with higher level abstractions such as ―DBGrid‖. The important attributes of the ―part‖ element –
     * ID –
    
       >This is a mandatory attribute in the ―part‖. This helps to uniquely identify this part in different sections of the interface xml. This also generates an ―id‖ attribute for the element in the markup.
     * Class –

      >This is another mandatory attribute in the ―part―. This helps to generate the corresponding element in the screen. This ―class‖ has to be one of the LF supported class.`<structure>
<part id="accloginback" class="label"></part>
<part id="acclogincompanyname_container" class="label"></part>
<part id="acclogincompanyname" class="label"></part>
<part id="loginmain_container" class="label"></part>
<part id="acclogincompanylogo_container" class="label"></part>
<part id="acclogincompanylogo" class="image"></part>
<part id="login_container" class="label"></part>
<part id="accfislabel" class="label"></part>
<part id="accinputouter" class="label"></part>
<part id="accinputinnerheader" class="label"></part>
<part id="accsigninlogo" class="image"></part>
<part id="accinputinner" class="label"></part>
<part id="userid_container" class="label"></part>
<part id="accuseridinputlabel" class="label"></part>
<part id="accuseridinput_container" class="label"></part>
<part id="accuseridinput" class="inputtext" tabindex="1"
autocomplete="on"></part><part id="password_container" class="label"></part>
<part id="accpasswordinputlabel" class="label"></part>
<part id="accpasswordinput_container" class="label"></part>
<part id="accpasswordinput" class="password" tabindex="2"></part>
<part id="accsigninbutton_container" class="label"></part>
<part id="accsigninbutton" class="button"></part>
<part id="incorrectuser_container" class="label"></part>
<part id="incorrectuser" class="label"></part>
<part id="accportallogo_container" class="label"></part>
<part id="accportallogo" class="image"></part>
<part id="accloginajax" class="ajaxcomponent"></part>
</structure>`
  * Layout Section

    >The Layout section is used define the positioning of the UI elements on the screen as well as the hierarchical parent-child relationship among the elements. Under the 'layout' section we need to define the position of all the parts, which we have defined under the 'structure' section. An interface.xml file may have more than one layout which empowers a web application designed in this framework to provide different views for a screen (or interface) based on different roles. The different ―layout‖ section should have different ―id‖ attribute for the ―layout‖ element. An interface must have at least one layout section. The attributes of the ―part‖ element –
    * ID

     >The id of the element. The mentioned id should be present in the ―structure‖ section. If it is not present then it will result to nothing. Logically there should be one entry for each part. The attribute is ―id.
    * Width

     >This specifies the width of the element. This is optional. The attribute is ―width‖.
    * Height

     >This specifies the height of the element. This is optional. The attribute is ―height‖.
    * Left

     >This specifies the left start position of the element. This is optional. The attribute is ―left‖.
    * Top

     >This specifies the top start position of the element. This is optional. The attribute is ―top‖.
    * Position

     >This specifies the position of the element. This is optional. The attribute is ―position‖. The value can be absolute or relative.
    * Parent Element

     >This attributes helps us to specify the parent id of the current element. The parent element also should be present in the structure section. This helps us to create a hierarchical parent-child relationship among the elements. ―parent_id‖ attribute is used for this purpose.`<layout id="Loginlayout">
<part id="accloginback"></part>
<part id="acclogincompanyname_container" parent_id="accloginback" height="60px"></part>
<part id="acclogincompanyname" parent_id="acclogincompanyname_container"></part>
<part id="loginmain_container" parent_id="accloginback" height="500px"></part><part id="acclogincompanylogo_container" parent_id="loginmain_container"></part>
<part id="acclogincompanylogo" parent_id="acclogincompanylogo_container"></part>
<part id="login_container" parent_id="loginmain_container"></part>
<part id="accfislabel" parent_id="login_container"></part>
<part id="accinputouter" parent_id="login_container"></part>
<part id="accinputinnerheader" parent_id="accinputouter"></part>
<part id="accsigninlogo" parent_id="accinputinnerheader"></part>
<part id="accinputinner" parent_id="accinputouter"></part>
<part id="userid_container" parent_id="accinputinner"></part>
<part id="accuseridinputlabel" parent_id="userid_container"></part>
<part id="accuseridinput_container" parent_id="userid_container"></part>
<part id="accuseridinput" parent_id="accuseridinput_container"></part>
<part id="password_container" parent_id="accinputinner"></part>
<part id="accpasswordinputlabel" parent_id="password_container"></part>
<part id="accpasswordinput_container" parent_id="password_container"></part>
<part id="accpasswordinput" parent_id="accpasswordinput_container"></part><part id="accsigninbutton_container" parent_id="accinputinner"></part>
<part id="accsigninbutton" parent_id="accsigninbutton_container"></part>
<part id="incorrectuser_container" parent_id="accinputinner"></part>
<part id="incorrectuser" parent_id="incorrectuser_container"></part>
<part id="accportallogo_container" parent_id="accloginback"
height="60px"></part>
<part id="accportallogo" parent_id="accportallogo_container"></part>
<part id="accloginajax" parent_id="accloginback"></part>
</layout>`
  * Content Section
    >Content section is used for poring text, HTML chunks, images, animations as appropriate into the part elements. The simplest is to insert text inside a part element. Some HTML code can also be inserted in a part element as XML character data. External content files may be referenced. An interface.xml file may have more than one ―content‖ which empowers a web application designed in this framework to provide different contents for a screen (or interface) based on different roles. The different ―content‖ section should have different ―id attribute for the ―content‖ element. The attributes of the ―part‖ element –
     * ID – 
      
        >The id of the element. The mentioned id should be present in the ―structure‖ section. If it is not present then it will result to nothing. The attribute is ―id.
     * Value-

       >The value of the content. It can be a text or can be an external file name as well. The attribute is ―value.
     * Value Type –

      >This attribute defines the type of value which is defined in ―value‖. It can be –
       * inline – This specifies the value which is specified in ―value‖ attribute is the actual one.
       * reference – This specifies the value which is specified in the ―value‖ attribute is the ―id of a ―resourceitem defined in ―resource section.
       * fixed – This specifies that it is the values of a drop down element (LF class name is ―combo). The values for the combo defined under ―combooption element.
       * cdata – This specifies that this element holds some html value. This value will be provided as a data in ―part element. The attribute is ―valuetype.
     * Default Select Label-

       >This attribute provides the default label of a drop down. When a page containing a drop down element first loads, then this label will be shown. The attribute is ―choose_one_label‖.
     * Show Default Select –

       >This attribute defines if the drop down will have a default or not. By default it is true. The attribute is ―show_choose_one.
     * Default Select Value -

      >This attribute provides the default value of a drop down. When a page containing a drop down element first loads, then this value will be preselected. The attribute is ―choose_one_value‖.
     * Location of the content –

      >This attribute defines where the content will be shown. For an example if the location is set as ―end and the corresponding part class is ―label (which generates HTML div) then the content will be generated after all the child elements(as defined in layout section) under this part class. The attribute is ―contentlocation. Possible values are ―start or ―end. Default value is ―start.
     * Combo Options –
    
      >This element corresponds to <option> tag in HTML. They are used to mark-up every single item in a drop-down list. Combo options are sensibly not cataloged as a structure class, since they neither need positional information nor involves in a parent-child relationship with any of the part elements with a structure class other than combos. So they need not have an entry in structure section as well as in layout section. They are only seen in the content section of interface.xml files enclosed in a content-entry for a part element belongs to combo structure class as<combooption> tags. Here the value type of the content entry is ‗fixed‘. It can be one or more. The element for this is ―combooption. It has two attributes –
        * label – It defines the label of the drop down element.
        * value – It defines the corresponding value of a label.
       `<content id="Logincontent">
<part id="accportallogo" value="portallogo" valuetype="reference"></part>
<part id="accsigninlogo" value="signin" valuetype="reference"></part>
<part id="acclogincompanylogo" value="msmelogo" valuetype="reference"></part>
<part id="acclogincompanyname" value="MSME TOOLROOM KOLKATA eUNIVERSITY" valuetype="inline"></part>
<part id="accfislabel" value="Learner Portal" valuetype="inline"></part>
<part id="accuseridinputlabel" value="User ID" valuetype="inline"></part>
<part id="accpasswordinputlabel" value="Password" valuetype="inline"></part>
<part id="accsigninbutton" value="Sign In" valuetype="inline"></part>
<part id=”elmLabel" valuetype=”cdata”>
<![CDATA[Select Article : ]]>
</part>
<part id="elmArticleSelector" valuetype="fixed">
<combooption name="0" value="Choose One" />
<combooption name="1" value="Peeper" />
<combooption name="2" value="Pressure Cooker" />
<combooption name="3" value="Basmati Rice" />
</part>
</content>`
 
  * Style Section
 
     >This section is responsible for the appearance of an interface. This is a place where we define styling information for part elements of various structure classes if required. Font, color, alignment etc. are specified with a style entry for these elements. The syntax for defining styling information is same as the syntax for defining styles in cascading style sheet. Actually, most of the part elements of an interface are translated to an HTML tag or a combination of HTML tags. The style definition of a part element generates either an inline style (style definition in the style attribute of an HTML tag) or adopts the style from an external css file (files with a .css extension containing style definitions attached to an HTML document with the help of a link tag) depending upon the way in which style is defined. An element can have both inline and external style definitions, and if it does, the resulting style will conform to cascading style sheet rules i.e. inline style will override the external style in case of a duplicate definition. Positional and dimensional information (i.e. width, height, top, left, position etc.) of a part element may also be defined using style entry, but it is convenient tweaking position co-ordinates and dimension in the way we have them in layout section. Inline style definitions are embedded in an attribute of ―part‖ xml tag of type CDATA. An interface.xml file may have more than one ―style‖ which provides a web application designer the power to display a screen differently depending on different roles. The different ―style‖ section should have different ―id‖ attribute for the ―content‖ element. The attributes of the ―part‖ element –
     * ID –
  
       >The id of the element. The mentioned id should be present in the ―structure‖ section. If it is not present then it will result to nothing. The attribute is ―id‖. This element will be styled.
     * Value –

       >The value of the content. It can be a cdata for example ―[CDATA[background-color: whitesmoke; border: 1px solid silver;]]‖ or can be an external css file‘s class name as well. The attribute is ―value‖.
     * Value Type –

       >This attribute defines the type of value which is defined in ―value‖. It can be –
       * inline – This specifies the value which is specified in ―value‖ attribute will be added as inline style.
       * reference – This specifies the value which is specified in the ―value‖ attribute will be added as a ―class‖ attribute to the HTML element having the same ―id‖. The css file containing the style of this ―class‖ should be present in the resource section as type ―css‖ or it can be in the application template as well.
     * Resource File ID –
   
      >For ―reference‖ style, this attributes indicate the resource file. The attribute is ―resourceid‖. It should be same as with one of the ―id‖ of a ―resourceitem‖ defined in ―resource‖ section having the ―type‖ as ―css‖. It can be omitted as well if the css file is mentioned in the Application Template.`<style id="Loginstyle">`
`<part id="acclogincompanyname_container" value="row row-padding text-center" valuetype="reference"></part><part id="acclogincompanyname" value="col-md-12 text-center"`
`valuetype="reference"></part>`
`<part id="acclogincompanyname" value="[CDATA[text-align:center;font-family:times;font-weight:normal;font-size:25px;color:black;]]" valuetype="inline"></part>`
`<part id="loginmain_container" value="row" valuetype="reference"></part>`
`<part id="loginmain_container" value="[CDATA[background-color: #6BB8EF;]]" valuetype="inline"></part>`
`<part id="acclogincompanylogo_container" value="col-md-6 text-center" valuetype="reference"></part>`
`<part id="acclogincompanylogo_container" value="[CDATA[padding-top: 175px;]]" valuetype="inline"></part>`
`<part id="login_container" value="col-md-5" valuetype="reference"></part>`
`<part id="login_container"`
`value="[CDATA[margin-top: 125px;border: 1px solid black;border-radius:5px; background-color: #F7F7F7;]]"`
`valuetype="inline"></part>`
`<part id="accfislabel" value="col-md-12 row-padding" valuetype="reference"></part>`
`<part id="accinputinnerheader" value="col-md-12 row-padding"`
`valuetype="reference"></part><part id="accinputinner" value="form-group form-horizontal col-md-12" valuetype="reference"></part>`
`<part id="userid_container" value="row row-padding" valuetype="reference"></part>`
`<part id="accuseridinputlabel" value="col-md-2 control-label"`
`valuetype="reference"></part>`
`<part id="accuseridinput_container" value="col-md-8" valuetype="reference"></part>`
`<part id="password_container" value="row row-padding" valuetype="reference"></part>`
`<part id="accpasswordinputlabel" value="col-md-2 control-label"`
`valuetype="reference"></part>`
`<part id="accpasswordinput_container" value="col-md-8" valuetype="reference"></part>`
`<part id="accsigninbutton_container" value="row row-padding text-right col-md-10" valuetype="reference"></part>`
`<part id="incorrectuser_container" value="row row-padding text-center col-md-10" valuetype="reference"></part>`
`<part id="accportallogo_container" value="row row-padding text-center" valuetype="reference"></part>`
`<part id="accpasswordinput" value="form-control" valuetype="reference"></part>`
`<part id="accuseridinput" value="form-control" valuetype="reference"></part>`
`<part id="accsigninbutton" value="btn btn-primary" valuetype="reference"></part></style>`
  * Behaviour Section

   >To perform some task under any event happening on screen then that needs to be defined under behaviour section. For an example if we need a button to perform some tasks when the user clicks it, then we need to define how it will perform the task under this 'behaviour' section. All DOM events may be used in this section. External JS files may also be used to define the body of the functions. An interface.xml file may have more than one ―behaviour‖ which provides a web application designer the power to act a screen differently depending on different roles. The different ―behaviour‖ section should have different ―id‖ attribute for the ―behaviour‖ element. This section contains ―part‖ elements behaviors. ―part‖ element has an ―id‖ attribute and the behaviors of a part element are defined by one or more ―event‖ elements under it. The mentioned id of the ―part‖ element should be present in the ―structure‖ section. If it is not present then it will result to nothing. The event will be applied on the element which has the mentioned ―id‖. The attributes of the ―event‖ element –
    * Value type –
 
     >It defines the type of function. It can be inline or it can be referenced from an external file. It can have two values-
     * inline – This specifies the value will be added as a JavaScript function for the event specified in the ―event attribute. Unlike other sections, ―inline can reference to external JavaScript as well but it cannot reference to any other external resource for this event.
     * reference – This specifies the event can reference some external files as well. It only supports two special events – ―invokeurl and ―openurl.
     * jsevent – This specifies the event is an inline js.
    * Name –
     
     >This can be any DOM event. For an example if it is ―onclick then the mentioned operation will be performed when the element is clicked. The attribute is ―name. Except the existing dom element there are some special event are also present in the LF.
      * invokeurl – This event can invoke a URL. For ―reference type the URL can be an external HTML which needs to be specified in the ―resource section. The ―resourceId for this resource needs to be provided in the ―value attribute. For ―inline type it cannot reference an external file, the URL needs to be given fully in the value attribute.
      * openurl – This is same as the ―invokeurl, only difference is that we can specify the target where the URL will be opened. The target needs to be specified in the ―target attribute.
      * domready – This event will be called when the dom is ready.
    * Function –

     >This defines the operation when the mentioned event is performed on the element. It can be an inline JavaScript or can be an external js function as well. The attribute is ―function.
    * Parameter –
      
     >The parameters which will be passed when the function is called. Multiple parameters are separated by comma. The attribute is ―parameter.
    * Resource File ID –

     >This attributes indicate the resource file. The attribute is ―resourceid. It should be same as with one of the ―id of a ―resourceitem defined in ―resource section having the ―type as ―js. It can be omitted as well if the js file is mentioned in the Application Template.
    * Java Class –

     >If the event is AJAX then this contains the class name which serves the AJAX request. This class must be defined in the dwr.xml file. The attribute is ―javaclass.
    * Callback –
   
     >If the AJAX needs any call back function to be called after the AJAX request completes then that needs to be defined here.
    * Target –

     >It is described in the ―openurl section.

    `<behaviour id="Loginbehaviour">
<part id="accpasswordinput">
<event name="onkeypress" function="checkEnter" valuetype="inline" parameter="event" resourceid="loginj" ></event>
</part>
<part id="accsigninbutton">
<event name="onclick" function="login_onclick" valuetype="inline" resourceid="loginj"></event>
</part>
<part id="accloginajax">
<event name="ajax" function="dummy" javaclass="Portal"></event>
</part></behaviour>`
  * Resource section

    >The Resource section is used for associating various types of external content with the interface elements. There can be only one resource section in an interface.xml. The resource section is responsible for loading the external files which are referenced from ―content, ―style or ―behaviour section. If a resource item is present in the resource section but not used in any of the previously mentioned three parts then that resource will not be loaded. Resource section holds ―image and ―html for content section, ―css for style section and ―js for ―behaviour section. It contains one or more resource items which are mentioned as ―resourceitem element. This element has the following attributes –
    * ID –
 
      >This is name or value of the resource item. With the help of this attribute it is referenced from different sections. The attribute used is ―id.
    * Full Name – 

       >The full name (with extension) of the resource. The attribute is ―href.
    * Type-

      >The type of the resource. ―valuetype‖ is used for this. It can have the following values –
       * image – This type of resource are referenced from ―content‖ section.
       * js – This type of resource are referenced from ―behavior‖ section.
       * css – This type of resource are referenced from ―style‖ section.
       * html – This type of resource are referenced from ―content‖ section.
        
     >The resources must be uploaded with the interface as a single zip file.`<resource>
<resourceitem id="portallogo" href="LearnITy-Portal.gif" valuetype="image"></resourceitem>
<resourceitem id="signin" href="SignIn.gif" valuetype="image"></resourceitem>
<resourceitem id="msmelogo" href="msmelogo.jpg" valuetype="image"></resourceitem>
<resourceitem id="loginj" href="loginjs.js" valuetype="js"></resourceitem>
</resource>`With the interface.xml, "LearnITy-Portal.gif", "SignIn.gif", "msmelogo.jpg" and "loginjs.js" should be zipped and uploaded from the interface management screen. Please go to section 10 for more details of the core admin screens.

**3.Implementation details**

   >The code and functionality are vastly restructured in these sections. When a XML or a zip is uploaded then the following this are happened –
     
      1. After uploading the file the corresponding servlet sends it to a helper class named as ―LayoutUploader.
      2. If a zip is uploaded then it unzips first and stores the files in the local disk.
      3. It then checks if it is an interface or fragment, depending upon this it sends it to their 
        respective handler functions.
      4. The interface.xml is verified by the XSD named as interface.xsd.
       If the verification succeeds then the XML is parsed.
      5. The parsed data is stored in the different tables
      6. After these another helper class is called named as ―DisplayEngine.
           This is responsible for creating the actual HTML.
      7. This class has a huge responsibility. Depending upon the parent child relationships 
    it calls a function to generate the html of corresponding part class in recursive manner.
      8. In the process of generation of the HTML the corresponding HTML element is created from the LF classes.
      9. The style, behavior sections are also handled properly.
     10. The resources are added in the HTML.
     11. After the HTML creation is done the corresponding HTML is stored in the database against the interface id. Whenever a request is made for this interface the corresponding HTML is returned.