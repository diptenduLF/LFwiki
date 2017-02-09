**1. Architecture**
 >LF is one declarative programming based framework and inspired by IBM‘s AUIML concept. Declarative programming is actually made for any kind of developers, who are not even well versed with Software Programming Languages. It is often English language based and follows some pre-defined structure in XML, hence easy to use as well. LF is a high-level framework for developing web based software using Java. It is not developed for any particular application domain. The objective is to build a generic framework which will provide a higher level abstraction for developing web-based applications. It will help to increase the productively and will reduce the burden from application developers.
Any application which is built using LF is considered to be a collection of interfaces represented using XML.
The architecture of LF –
 

 >The components which are marked in grey are application‘s component whereas the components which are marked in light gray are framework components(Reference [ 6]. The flow is-
 1. Developer creates the application schema in the application database
 2. Then he uploads the manifest, interface role and interface from the core admin module. The markup is created from the uploaded interface.
 3. User invokes the PortalServlet with an interface Id - www.ip:port/contextpath/servlet/interfaceenginev2.PortalServlet?IID=interfaceId from the Browser
 4. The PortalServlet front controller finds the appropriate markup from framework database which was created in step (ii) and serves it to the browser.
 5. The markup contains references to other resources such as Image files, JS files, CSS files, etc. that are served by other Front Controllers such as ResourceImage, ResourceJS and Resource CSS. They use the Framework database.
 6. The Javascript served by the ResourceJS front controller (or Javascript that was already present in the HTML markup served in step (ii) may contain Developer defined AJAX calls.
 7. The AJAX calls are executed with the help of the DWR servlet that routes the calls to the Developer Defined POJOS.
 8. The Developer defined POJOs may read from or write to the Application Database.
 9. The result of the AJAX calls returned by the POJOs are passed to the Developer defined JavaScript call back functions.
 10. The call back functions may update the browser screen (DOM).
 11. The generated markup served in step (iv) above may also contain AJAX calls (these are not defined by the developer) that are handled the same way. These calls refer to Framework defined POJOs that are deployed in the Application Server along with developer defined POJOs. In some cases the generated markup also contains generated JavaScript code including functions that are used as callbacks.
 12.The Framework defined POJOs refer to both the Application database as well as framework database.

  * Basic components
    * Manifest – Entry point of an interface in the application
    * Interface Role – To establish the relationship between application‘s user role and the different parts of interface xml.
    * Interface – The main component. This is to build the web page and performing different operations.
    * Interface Fragment – Same as Interface. The basic difference is fragment can only create a part of a web page where the interface is responsible for creating the main page.
    * Theme – This is responsible for creating the overall styling of an application.
    * Application Template - This is used for loading the common java script and css files. It can also provide the default values for different parts of interface/interface fragment xml
    * POJOs – This is responsible for complex server side operations which are requested by any of the interface.
  
  **Manifest**
 >This is the entry point of any interface in the application. Previously the manifest can only be uploaded. In this reengineering we made it possible to enter the manifest details from the screen itself. Manifest entry was optional previously. But now it is changed to make it mandatory. It means that interface entry has to be associated with the manifest before the interface can be uploaded through the application. Application will not allow uploading any interface if it is not associated with the manifest.Parent tag of manifest.xml is <manifest>. This tag has two attributes. The id attribute is an identifier of the interface collection and the title is the string that will be displayed in the paginated grid of ‗Interface Management‘ screen of coreadmin. <manifest> can have any number of <interface/> child tags. Each of them is the entry point of an individual interface. Value of the title attribute shows up in the Interface Management grid of coreadmin and the type attribute can be ‗Interface‘/‘InterfaceFragment‘. Zip attribute contains the name of the interface archive zip file.
The example of a manifest.xml file -`<?xml version="1.0" encoding="UTF-8"?>
<manifest id="MSMELMS" title="MSMELMS" xmlns="http://learnityframework.org/">
<interface id="LoginPage" title="LMS LoginPage" type="Interface" zip="LoginPage.zip"/>
<interface id="LMSPortal" title="LMS Portal"
type="Interface" zip="LMSPortal.zip"/>
<interface id="PortalUnit" title="Unit Grid on LMS Portal"
type="InterfaceFragment" zip="PortalUnit.zip"/>
<interface id="PortalForum" title="Forum Grid on LMS Portal"
type="InterfaceFragment" zip="PortalForum.zip"/><interface id="Forum" title="LMS Forum"
type="Interface" zip="Forum.zip"/>
</manifest>`

 **InterfaceRole -**
   >InterfaceRole is another configuration file which contains information of mapping of application roles with the interface. This generates different html snippet for same interface depending upon the role. Without an entry of the interface xml in this file will fail to generate any corresponding html snippet for that interface. This is mandatory for any interface xml. Roles are subsets of actions or functions of a system. For example, in Learning Management System there are different roles like student, teacher, HOD, Principle etc. Student can see only his own report card but the same page can contain a drop down for the HOD who can view all the students result in his department whereas the principle can view the result of all students. In LF one interface is enough for this. Only three different mappings will be present for the same xml in InterfaceRole.
In InterfaceRole we need to define the roles & the work of that role. We need to define which interface will be accessible under which role. Also, since a single interface may have multiple interface components (layout, content, behavior, etc.) of the same type; for each accessible interface, we need to specify the id of the interface components that are accessible for that particular role.
In the below example we have defined three roles called 'Default', ‗Student‘, ‗HOD‘.
‗Default‘ means everyone will get access to ‗LoginPage‘. The ‗HOD‘ will get access to ‗UserCreation‘. ‗Student‘ and ‗HOD‘ both will get access to ‗Viewresult‘ but the style, behavior will be different.`<?xml version="1.0" encoding="UTF-8"?>
<roles xmlns="http://learnityframework.org/">
<role id="DEFAULT">
<interface id="LoginPage">
<layout id="Loginlayout"/>
<content id="Logincontent"/>
<style id="Loginstyle"/>
<behaviour id="Loginbehaviour"/>
</interface>
</role>
<role id="STUDENT">
<interface id="ViewResult">
<layout id="ViewResultStudentLay"/>
<content id="ViewResultStudentCont"/>
<style id="ViewResultStudentStyle"/>
<behaviour id="ViewResultStudentBeha"/>
</interface>
</role>
<role id="HOD">
<interface id="ViewResult">
<layout id="ViewResultHODLay"/>
<content id="ViewResultHODCont"/>
<style id="ViewResultHODStyle"/>
<behaviour id="ViewResultHODBeha"/>
</interface>
<interface id="UserCreation">
<layout id="usercreationlay"/>
<content id="usercreationcontent"/>
<style id="UserCreationStyle"/>
<behaviour id="usercreationbehaviour"/>
</interface>
</role>
<roles>`

 **Interfaces and fragments –**
   This is the basic building block of an application in the LF. It contains different parts –
   * Interface
     
      >This is the parent of this interface. It will hold the 'id', 'name' & the 'type' of the interface. 'id' of each interface/interface fragment has to unique. The 'type' specifies whether it is an interface or fragment.`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"
id="LoginPage" title="LoginPage" type="Interface">`
    
    * configuration
   
       >This section contains the configuration related data. The application template id, theme id, role check is required or not etc. Details of this are described in below.
`<configuration createsession="true" checkrole="false" TemplateID="Bootstrap"></configuration>`
  
    * structure
     
      >In the Structure section every UI component need to be defined which will be present in the corresponding HTML snippet. Each UI component has a class attribute (like – label, textlink etc.) which results in corresponding HTML component. All components should have one unique id by which these components will be recognized in other sections. Details of this are described in below.
  `<structure>
<part id="accloginback" class="label"></part>
<part id="acclogincompanyname_container" class="label"></part>
<part id="acclogincompanyname" class="label"></part>
</structure>`

    * layout
   
      >The Layout section is used define the positioning of the components on the screen as well as the hierarchical parent-child relationship among the components. Under the 'layout' section we need to define the position of all the components, which we have defined under the 'structure' section. Details of this are described in below.
  `<layout id="Loginlayout">
<part id="accloginback"></part>
<part id="acclogincompanyname_container" parent_id="accloginback" height="60px"></part>
<part id="acclogincompanyname" parent_id="acclogincompanyname_container"></part>
</layout>`

    * content
      
      >The content section holds the static content of different elements. For example, the values of a text label. Details of this are described in below.
 `<content id="Logincontent"><part id="accfislabel" value="Learner Portal" valuetype="inline"></part>
</content>`

   * style
  
     >The Style section is used define the visual attributes of the components on the screen such as spacing, color, alignment, etc. The syntax for defining styling information is same as the syntax for defining styles in cascading style sheets. External CSS files may also be used. Details of this are described in below.
  `<style id="Loginstyle">
<part id="acclogincompanyname_container" value="row row-padding text-center" valuetype="reference"></part>
<part id="acclogincompanyname" value="col-md-12 text-center"
valuetype="reference"></part>
<part id="acclogincompanyname" value="[CDATA[text-align:center;font-family:times;font-weight:normal;font-size:25px;color:black;]]" valuetype="inline"></part>
</style>`
   
    * behaviour
   
      >The 'behaviour' section is used to define the behavior of the components against various events occurring on the screen. For example if we want the 'Login' button to perform a task when the user clicks it, then we need to define how it will perform the task under this 'behaviour' section. Details of this are described in below.
  `<behaviour id="Loginbehaviour">
<part id="accsigninbutton">
<event name="onclick" type="simple" function="login_onclick"
valuetype="inline" resourceid="loginj"></event>
</part>
</behaviour>`

   * resource
   
     >The Resource section is used associate various types of external content with the interface elements. Details of this are described in below.
 `<resource><resourceitem id="msmelogo" href="msmelogo.jpg" valuetype="image"></resourceitem>
<resourceitem id="loginj" href="loginjs.js" valuetype="js"></resourceitem></resource>`
 
    * LF Part Classes –
      >Under structure section each component has a class associated with it. This defines how it will be laid down in the screen. These classes actually create different HTML components with some additional wrappers. Part class and their corresponding HTML component(Reference [ 3 ]).
 
    |Lf part Class  | HTML Component|
    | ------------- |:-------------:| 
    |image          |img            |
    |flashcomponent |object         |
    |video          |embed          |
    |textlink       |a              |           
    |label          |div            |
    |form           |form           |
    |tab            |               |
    |imagelink      |               |
    |iframe         |iframe         |
    |framecontainer |               |
    |inputtext      |input type=text|
    |submitbutton   |               |
    |checkbox       |input type=checkbox              |
    |radio          |input type=radio|
    |textarea       |textarea       |
    |combo          |select         |
    |combooption    |option         |
    |frameset       |frameset       |
    |frame          |frame          |
    |inputfile      |input type=file |
    |hidden         |input type=hidden|
    |password       |input type=password|
    |button         |button           |
    |table          |table            |
    |tablerow       |tr               |
    |tablecell      |td               |
    |applet         |applet           |
    |appletparam    |PARAM            |
    |list           |ul               |
    |listitem       |li               |
    |span           |span             |
    |DBgrid         |                 |
    |Conditionalgrid|                 |
    |tree           |                 |
    |statictree     |                 |
    |dynamictree    |                 |
    |ajaxcomponent  |                 |
    |fieldset       |fieldset         |
    |legend         |legend           |
    |formlabel      |label            |
    |formtext       |input type=text  |
    |formdate       |                 |
    |formemail      |                 |
    |formnumber     |                 |
    |formpassword   |                 |
    |DBForm         |                 |      
    

 **Theme**
  >This is responsible for overall styling of the interfaces. In this file we can define the default style of any component. If, any specific style is not applied to that component then this style will be applied to that particular component. It will help us to make every button, input etc. to use the uniform styling throughout the application.
‗title‘ is the name/id of the theme. Each theme should have unique id/name. Each ‗themeselement‘ contains a ‗class‘ attribute which corresponds to any of the LF part class. The style can be inline or can be referenced from an external css file. ‗type‘ describes this. For inline corresponding value needs to be defined in ‗property‘ attribute. For reference corresponding value needs to be defined in ‗cssclasses‘ attribute. Details of this are described in below.`<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/theme.xsd"
title="bootstrap_theme">
<themeselement class="button" type="reference"
cssclasses="btn btn-primary"></themeselement>
<themeselement class="inputtext" type="reference"
cssclasses="form-control"></themeselement>
<themeselement class="password" type="reference"
cssclasses="form-control"></themeselement>
<themeselement class="textarea" type="reference"
cssclasses="form-control"></themeselement>
<themeselement class="combo" type="reference" cssclasses="form-control"></themeselement>
</theme>`
 
 **Application Templates**
  >The purpose of template is to globally set up for configuration section, element structure section and it also embed all external resources like js, css in a page. This defines the default value for different attributes of different class along with it also defines the default theme name, default cache etc.
It is also responsible for fetching the global js and css files. It also specifies the order and position of those files. The ‗application-default‘ contains one ‗configuration-section‘ and any number of ‗class‘ sections. ‗configuration-section‘ contains the default value of configuration part of interface xml. The ‗class‘ part contains the default values of attributes of different sections. ‗framework-asset-delivery‘ contains the resource files i.e. css and js file paths which will be added in the corresponding HTML of the interface which is using this template. It also contains the sequence in which the files will be delivered and the location of the files in the HTML. Details of this are described in below.`<application-template xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/application_template.xsd"
title="Bootstrap" UIframework="bootstrap" BlockUItimeout="1000">
<application-defaults><configuration-section>
<attribute name="ThemeID" defaultvalue="bootstrap_theme"></attribute>
<attribute name="createsession" defaultvalue="false"></attribute>
<attribute name="checkrole" defaultvalue="true"></attribute>
</configuration-section>
<class name="inputtext">
<section name="structure">
<attribute name="size" defaultvalue="20"></attribute>
</section>
</class>
</application-defaults>
<framework-asset-delivery><framework-asset-delivery>
<asset type="js" deliverymode="URIPath" pagelocation="BOH"
deliverysequence="1" filename="jquery-2.2.0.js" assetpath="../coreadmin/resource/jQuery/" />
<asset type="js" deliverymode="URIPath" pagelocation="BOH"
deliverysequence="2" filename="grid.locale-en.js" assetpath="../coreadmin/resource/jQgrid/i18n/" />
</framework-asset-delivery>
</application-template>`

 **POJOs**
   >The POJOs are required for the complex server side operations. For each POJO a separate entry need to be given in the dwr.xml. Each of the functions which are defined in the POJO can be called from the interface xml.`public class Portal
{
public static final SimpleLogger log = new SimpleLogger(Portal.class, true);
public String setUserInfo() {
String html = "";
WebContext wctx1 = WebContextFactory.get();
javax.servlet.http.HttpSession mysession = wctx1.getSession();
String user_id = (String) mysession.getAttribute("user_id");
String loginno= DataBaseLayer.getLoginWelcome3(user_id);
String createdate= DataBaseLayer.getLoginWelcome4(user_id);
String systemaccessuser=DataBaseLayer.systemaccess(user_id);html="<table border=\"0\" cellpadding=\"2\" cellspacing=\"1\" width=\"100%\"><tr><td style=\"text-align:left;color:blue;font-weight:normal;font-family:verdana;font-size:8pt;\">Account created: </td><td style=\"text-align:left;color:black;font-weight:normal;font-family:verdana;font-size:8pt;\">"+createdate+"</td></tr><tr><td style=\"text-align:left;color:blue;font-weight:normal;font-family:verdana;font-size:8pt;\">No of times system accessed: </td><td style=\"text-align:left;color:black;font-weight:normal;font-family:verdana;font-size:8pt;\">"+loginno+"</td></tr><tr><td style=\"text-align:left;color:blue;font-weight:normal;font-family:verdana;font-size:8pt;\">Total time system accessed: </td><td style=\"text-align:left;color:black;font-weight:normal;font-family:verdana;font-size:8pt;\">"+systemaccessuser+"</td></tr></table>";
return html;}}`

* Deployment
 
   >LF comes as a WAR file. It currently supports apache tomcat as a web server and MySQL as the database. The WAR file needs to be deployed in the tomcat web server to start using this framework. The framework schema needs to be executed in the database.
  * Overview
    
    >LF is easy to deploy and the user can start using it as soon as it is deployed. There are few configuration files are present which contains some default values, which can be changed as required.
  * Configuration parameters – The different configuration parameters are described below -
    * Portal.properties
      
      >This file contains the data source for the framework and the data source for the application. Along with that it also stores different paths for the temporary downloadable files, uploaded xmls, uploaded zips etc. It also contains a sql which provides the role of a user. This file has to be in classpath.`frameworkdatasource = jdbc/learnityDB
applicationdatasource = jdbc/learnityDB1
rolesql=select a.title from role a,user_role b where a.role_id=b.role_id and b.user_id
xml=D:\\LearnITy_resources\\temp\\xmlzip\\
themesxml=D:\\LearnITy_resources\\temp\\themesxml\\
themescss=D:\\LearnITy_resources\\temp\\themescss\\
templatexml=D:\\LearnITy_resources\\temp\\templatexml\\dwrxmlpath=D:\\LearnITy_resources\\temp\\WEB-INF\\
downloadzip=D:\\LearnITy_resources\\temp\\downloadzip\\
frameworkreportpath=D:\\\\LearnITy_resources\\\\temp\\\\report\\\\
downloadAll=D:\\LearnITy_resources\\temp\\downloadAll\\`
     * Display.properties 

       >It contains the servlet URL for displaying chart and report.`chartServletURL = interfaceenginev2.dashboard.chart3
reportServletURL = frameset`
     * Context.xml

       >This is a tomcat specific file. This holds the database connection parameters for both the framework and the applications built on top of it. The resource names and the values present against ―frameworkdatasource‖, ―applicationdatasource‖ keys in Portal.properties should be same.`<?xml version="1.0" encoding="UTF-8"?>
<Context path="/learnityLO" docBase="J:/" debug="0" reloadable="true"
crossContext="true" useHttpOnly="false">
<Resource name="jdbc/learnityDB1" auth="Container" type="javax.sql.DataSource" username="root" password="" driverClassName="com.mysql.jdbc.Driver" url="jdbc:mysql://ip:3306/learnityapplication_new?zeroDateTimeBehavior=convertToNull" removeAbandonedTimeout="10" maxWaitMillis="10000" removeAbandonedOnBorrow="true" maxTotal="1" logAbandoned="true" ></Resource>
<Resource name="jdbc/learnityDB" auth="Container" type="javax.sql.DataSource" username="root" password="" driverClassName="com.mysql.jdbc.Driver" url="jdbc:mysql://ip:3306/learnityframework?zeroDateTimeBehavior=convertToNull" removeAbandonedTimeout="10" maxWaitMillis="10000" removeAbandonedOnBorrow="true" maxTotal="1" logAbandoned="true" ></Resource>
</Context>`
     * Web.xml
       
       >The web.xml mainly contains the servlet mapping. It holds the mappings for the front controller servlets as well as core admin servlets.`<?xml version="1.0" encoding="UTF-8"?>web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance
xmlns="http://java.sun.com/xml/ns/javaee" xmlns:web=http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd
xsi:schemaLocation=http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd
id="WebApp_ID" version="3.0"
<servlet>
<servlet-name>interfaceenginev2.PortalServlet</servlet-name>
<servlet-class>interfaceenginev2.PortalServlet</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>interfaceenginev2.PortalServlet</servlet-name>
<url-pattern>/servlet/interfaceenginev2.PortalServlet</url-pattern>
</servlet-mapping>
</web-app>`
     * Dwr.xml

       >This xml contains the entry of the POJOs which serves AJAX requests. If the application need to use POJOs for supporting AJAX requests then he/she need to create an entry in this file.`<?xml version="1.0" encoding="UTF-8"?>
<dwr>
<allow>
<create creator="new" javascript="PortalEngine">
<param name="class" value="interfaceenginev2.PortalEngine"/>
</create>
</allow>
</dwr>`
  * The framework schema-

    >It contains all the data of manifest, role, interface, theme, application template i.e. all of the parts of the framework. The markup which is generated from the interface is also stored in the framework. This is the beauty of this framework. We need not to deploy the application built on LF to change its screen. We can update the interface and the markup which is stored in the framework database will also be updated and the screens shall change on the next request.
  
  * The CoreAdmin app–
    
    >This is LF core application. With the help of this application Manifest, Interface Role, Application Template, Theme, Interface can be uploaded, deleted and edited. The files can be downloaded as well. Different screens are present for different type of tasks. Details of this are described in below.

  * Markup generation–
    
    >When the interface is uploaded, it goes through several level of processing. The xml is first verified against the corresponding XSD. If it is correct then it is parsed and corresponding data is stored in different tables. HTML is created from the data which is stored in different tables. Details of implementation details is present in below.

* Runtime Behaviour

  * Overview
     
    > Interface is basic building block of LF. For each page a separate interface is needs to be uploaded. For part of the page interface fragment can be used. During the interface upload a HTML is generated corresponding to the interface. The generated HTML is stored in the framework database. When an interface is invoked by its id then the corresponding HTML is returned.

  * The application schema

    >The application which is created by the help of LF may have its own schema beside the framework schema. The detail of the application schema is described in context.xml and Portal.properties file. The application schema consists of the tables‘ specific to the application. LF does not have any dependency on the application schema.

  * Front Controllers

    >There are different front controllers are present in LF which are responsible for returning the data when an interface is requested by its id. All of these front controllers are servlets.

    * Interface
 
      >The main controller which returns the corresponding HTML of an interface. This is named as ―PortalServlet‖. The request string to get any interface is something like - http://<ip>:<port>/<context_root>/servlet/interfaceenginev2.PortalServlet?IID=LoginPage. ―LoginPage‖ is the interface id which is requested.

    * JS

      >This controller is responsible for returning the js files which are present in the ―resource‖ section of an interface. The responsible controller for this is ―ResourceJS‖.
   
    * CSS -

      >This controller is responsible for returning the css files which are present in the ―resource‖ section of an interface. The responsible controller for this is ―ResourceCSS‖.

    * XMLCreator

      >This controller is mainly used for specific part classes named as ―DBGrid‖ and ―ConditionalDBGrid‖. These part classes create table by using a third party JavaScript library named as jQGrid. The data needs to feed to this third party library as XML/JSON. Here XmlCreator comes into picture. This controller returns the data to this third party library in XML format. The responsible controller is ―XmlCreator‖.

    * Query Editor

      >In DBGrid and ConditionalDBGrid the data which is displayed in the table can be edited or new data can be added as well. ―DBGridQueryEditorServlet‖ and ―DBGridQueryEditorServletForMulti‖ take this responsibility for ―DBGrid‖ and ―ConditionalDBGrid‖ respectively.
 
  * Role mapping

     >It is the part where LF and the application are coupled. In LF we can define role and can define interface xmls different parts accessibility depending upon this role. So, the role wise access details are present in the framework database. But the role of the application user is present in the application database. As this is purely application‘s data. So when the markup for a user having a specific role is fetched, somehow LF needs to know the role of the user for which the markup will be fetched. This information needs to be supplied by the developer to LF. In portal.properties file a property is present named as ―rolesql‖. The value of this property should be the query by which the role of the user can be fetched from the application database. For an example in portal.properties file and entry like this should be present –
`rolesql=select a.title from role a,user_role b where a.role_id=b.role_id and b.user_id`―PortalServlet‖ fetch the user‘s role using this sql if the role check is set true in the requested interface xml. After fetching the role it sends this data to framework database to fetch the appropriate markup.

  * AJAX support

    >Application which are created using LF are AJAX enabled. For simple operations like create/update/delete user can use the application‘s built in AJAX facilities. For complex operations user may create a POJO and provide its entry in the dwr.xml. Each of the functions which are written inside this POJO can be used to serve an AJAX request.
   
    * Use within the LF runtime implementation

      >In LF already built in AJAX support is provided. For example loading the data in the tables, edit the data or addition of the data. Also showing the data of a form or adding/editing the data are also done by AJAX requests.

    * Use in LF based web application

      >For complex operations user may need to write his own server side functions. For these, user needs to write a POJO i.e. a simple java class and need to provide the corresponding entry in the dwr.xml file. After this user can write any function in the POJO and call this function as an AJAX call from the JavaScript. For an example user wants to write authentication code when user is logging in. The part of interface xml for the same`<behaviour id="Loginbehaviour">
<part id="accsigninbutton">
<event name="onclick" type="simple" function="login_onclick"
valuetype="inline" resourceid="loginj"></event>
</part>
<part id="accloginajax">
<event name="ajax" type="simple" function="dummy" javaclass="Portal"></event>
</part>
</behaviour>
<resource>
<resourceitem id="loginj" href="loginjs.js" valuetype="js"></resourceitem>
</resource>`Here we can see, we need to add the ―Portal‖ POJO in the event as a dummy entry which helps to load the Portal through dwr.
     >The js part to call the Portal java class`function login_onclick() {
var uid=getValue("accuseridinput");
var password=getValue("accpasswordinput");
Portal.verifyUser(uid,password,function(data) {
}`
     >The entry for Portal class in dwr –`<create creator="new" javascript="Portal">
<param name="class" value="edu.ju.thesis.Portal"/>
</create>`

   * Caching

     >Caching support is provided in the LF by the various front controllers such PortalServlet. All front controllers in the LF are caching aware. If caching is enabled then the front controllers first check the cache for existence of the requested resource (e.g., interface or image) in the cache. If the resource exists in the cache then it is fetched from the cache and sent to the browser. If the resource is not found in the cache then it is written to the cache and then sent to the browser so that subsequent requests for the same resource may be served from the cache.

  
**2.Development Workflow**
      
        Step1: Create the framework database
        Step2: Decide on the names of the UI pages that are going to be created.
        Step3: Create ―manifest.xml file, listing all the interface/UI Page names in interface 
              tags and associating each interface with its zip file name
        Step4: Decide on the roles that will be available in accessing your web application
        Step5: Create ―interfacerole.xml file where each role wise available interface, page layout,
             page structure, page content and page behavior will be listed by using relevant part ids
        Step6: Design all the UI pages using interface.xml file for each page. Each page content in XML,
             JS Scripts, Images etc. need to be zipped together and zip name must match with the name 
             specified in manifest.xml file
        Step7: Configure web.xml to include servlet class names and servlet mapping
        Step8: Start Tomcat and login to the Admin page using admin URL
              e.g. http://ip:port/threatanalysis/coreadmin/, with admin user login
        Step9: Upload manifest.xml, interfacerole.xml and interface zip files in the same order. 
              Files will be validated against pre-defined XSD structures and on successful 
              validation only XML files will be parsed for getting stored on Database.
        Step10: Login to portal using proper URL and welcome page will be displayed 