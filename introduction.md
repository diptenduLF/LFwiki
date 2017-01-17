### The Engineering of a Web Development Framework

# Introduction

**1. Background**

* About web development frameworks


>A web development framework supports and helps the developers to build and manage web applications, web services and websites. The main design aspect of these types of frameworks is to reduce the overhead for performing common activities during the web development. A good web development framework should allow the developers and designers to give more priority and time on building the functionality of their websites rather than wasting their time to handle the common and familiar features of any web site. Most of the known issues should be handled by writing very few lines of codes (Reference [ 20 ]). As these codes are not related to the functionality of the web site rather than handling the common issues. An appropriate framework can save a significant amount of time to build a web site. Also the framework should be easily customizable, the learning time should be less, and the performance should be good and should be easily maintainable (Reference [ 18 ]).

* Motivation for the LearnITy Framework (LF)

>LearnITy Framework (going forward we will call it as LF) is a high-level framework for developing web based software using Java. LF is one declarative programming based web framework. In Declarative programming developers expresses the application's logic i.e. what they want to do without describing the way to do it i.e. how to do. In this type of programming developers give much concentration on the problem domain rather than the way of its accomplishment. LF is inspired by IBM‘s AUIML (Reference [ 27 ]) concept. Abstract User Interface Markup Language (AUML) is a way to help the developers to provide a solution of problem which is independent of the platform. The vocabulary of AUML is based on XML (Reference [ 26 ]). The objective of LF is to build a generic framework which will provide a higher level abstraction for developing web-based applications. Now a day, most difficult part of the web development is to be familiar with the framework. Then the next difficult part is to build the basic architecture of the web site. Any error in the architecture may be fatal for the whole website. If the architecture is built by junior developers then there is a great chance for this. In LF, developers can concentrate on the problem domain from the beginning rather than concentrating on the architecture. LF provides higher level abstraction for developing web-based applications which increases the productively and will reduce the burden from developers. It minimizes the html/java script code for designing the UI (Reference [ 5 ]). Developers need to declare the UI components then where they will lay in the screen, what will be the content and what will be their behavior. (Reference [ 21 ]) All of these are directly related to the application or the functionality of the web site. This information will be processed and stored to display on the screen when it is requested. The development cycle is much faster (Reference [ 24 ]). It is very easy to move the application development platform from one system to another. As it is XML based so it is English like language and very easy for the developers to learn the language. LF provides many complex components which are very frequently required. Also it provides additional functionality on the existing HTML component. It reduces the development time subsequently.

* A brief tutorial of the LF
  * Overview-
> The basic building block of an application built on top of LF is xml. In addition user may write POJO classes for performing complex server side operations, java script for client side complex operations and css for custom styling. Any application which is built using LF is considered to be a collection of interfaces represented using XML. LF has an admin section from where we can upload the xmls. This xml will be validated, parsed and stored in appropriate places. It also generates the mark up and stores. LF has the following major components–

        *  Manifest–
> Every application which built on top of LF contains a manifest xml. Before creating any interface xml we need to map it with the manifest. It contains the title of the interface, the file name of the interface zip and the type of interface  `<?xml version="1.0" encoding="UTF-8"?>
<manifest id="MSMELMS" title="MSMELMS" xmlns="http://learnityframework.org/">
<interface id="HelloWorld" title="Hello World" type="Interface" zip="HelloWorld.zip"/>
</manifest>`
  
       * Interface Role – 
>  Interfaces are role specific. It means we need to define that which interface i.e. the screen created from that interface is available to which all roles. This information we need to declare in interface role xml. Also an interface may look and behave differently for different roles. This means layout, style and behavior section of an interface xml is strictly related with role. We need to define this relationship in interface role xml.`<?xml version="1.0" encoding="UTF-8"?>
<roles xmlns="http://learnityframework.org/">
<role id="DEFAULT">
<interface id="HelloWorld">
<layout id="HelloWorldLayout"/>
<content id="HelloWorldContent"/>
<style id="HelloWorldStyle"/>
</interface>
</role>
</roles>`
    
       * Interface –
    > The basic building block of LF is interface xml. The parent element of interface xml contains the id, title and type.`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"
id="HelloWorld" title="Hello World" type="Interface">`
 It has seven major sections -
              
          * Configuration

       >For defining the configuration for this interface. For an example, if the screen needs to create a session or the role checking is required or not.`<configuration createsession="true" checkrole="false" ></configuration>`
     
         * Structure –
       
        >For defining the components which will be present in the screen. Each component is represented by a class which results to some specific HTML components. Each component should have a unique id. For an example, the screen may contain two divs`<structure>
<part id="MyFirstInterfacelabel" class="label"></part>
<part id="HelloWorldLabel" class="label"></part>
</structure>`

         * Layout –
       
         >For defining the components positions in the screen and the hierarchal relationship between the components. For an example, the first div will start 50px from the top and the second div will start 60px from the top and it is the child of the first div.`<layout id="HelloWorldLayout">
<part id="MyFirstInterfacelabel" height="100%" width="100%" top="50px" position="absolute"></part>
<part id="HelloWorldLabel" height="60px" width="210px" left="600px" top="250px" position="absolute" parent_id="MyFirstInterfacelabel"></part>
</layout>

         * Content – 

         >For defining the content of the components. For an example, the label of the second div will contain the text "Hello World".`<content id="HelloWorldContent">
<part id="HelloWorldLabel" value="Hello World" valuetype="inline"></part>
</content>`

         * Style –
      
         >For styling the components. For an example, the first div box will have border shadow. The first div will have specific background color.`<style id="HelloWorldStyle"> <part id="MyFirstInterfacelabel" value="[CDATA[background-color: skyblue;]]" valuetype="inline"></part>
</style>`

         * Behaviour - 

         >For defining the components reaction under certain events in the screen. For an example, the button will check the user authenticity.

         * Resource – 

          >The resource required for the current interface. For an example, the page contains some images.

  * An example: Hello World -
  >We will start with classic example of ‗Hello World‘. We will create a screen with Hello World text on it. As we explained above we need to associate the interface with the manifest. To do anything in LF, we need to login to the Admin Module of LF. The login URL - [login](http://localhost:8080/LearnITyLMSv10/coreadmin/login.html). After logging in we will go to Interface Management screen.
![interface management](https://github.com/diptenduLF/LFwiki/blob/master/images/inteface%20management%20screen.png)
  
     >As described, we need to upload manifest.xml first to associate any interface with the application built on top of LF. The manifest file is same as in the above example. We need to select the manifest from the type drop down.![mainfest xml](https://github.com/diptenduLF/LFwiki/blob/master/images/mainfest%20xml.png)




    
      >The manifest file is uploaded successfully. We can see an entry cam for ―HelloWorld‖ interface with size 0. It means the association is created but the file is not uploaded yet. Now we will upload the interfacerole.xml. We need to select the Role Xml from the type drop down. Then we will upload the interface.xml. This time we need to select interface from the same drop down. The current interface xml is just the combination of the above interface xml parts. The full file will look like –`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"
id="HelloWorld" title="Hello World" type="Interface">
<configuration createsession="true" checkrole="false" ></configuration>
<structure>
<part id="MyFirstInterfacelabel" class="label"></part>
<part id="HelloWorldLabel" class="label"></part>
</structure>
<layout id="HelloWorldLayout">
<part id="MyFirstInterfacelabel" height="100%" width="100%" top="50px" position="absolute"></part>
<part id="HelloWorldLabel" height="60px" width="210px" left="600px" top="250px" position="absolute" parent_id="MyFirstInterfacelabel"></part>`

  
     >We need to create a folder named as ‗HelloWorld‖ and zip it with the name ―HelloWorld.zip‖ as mentioned in the manifest and upload it from the current screen.![uploaded mainfest](https://github.com/diptenduLF/LFwiki/blob/master/images/uploaded%20mainfest.png)


**2.Contributions of the Thesis**
   >The thesis is aimed to understand the LF and engineer it to make it consistent and improve it so that it becomes much easier to use.
 
 * Motivation

  >LearnITy Framework was conceptualized around the year 2007 at a private organization with the aim of making it possible for entry level developers to efficiently create web-based applications. After the initial conceptualization, the design and implementation of this framework progressed in an incremental fashion based on requirements from live projects. As a result of this growth model, less attention could be given to putting the framework on a sound engineering foundation. The work in this thesis was primarily concerned with providing that engineering foundation to the LearnITy Framework. In order to work towards this objective a number of activities were carried out including major capability enhancements, design changes, code factoring and other implementation changes, documenting the framework, as well as publishing it as an open source project. The initial work of implementation was done by the developers working for the organization where the framework was conceptualized. The period of development was up to 2009. Afterwards, other contributors worked on the framework as part of their master thesis work. This work was primarily on layout(Reference [ 1 ], [ 2 ]).

 * Design

  >The major design changes are-
 
  * Previously manifest was not mandatory. Interface could be uploaded without associating it with the manifest if it was uploaded individually. But if it was uploaded as a collection then the interface could not be uploaded without the manifest entry. This was inconsistent. Also manifest is a good design principle as it can be used as an index for the interfaces and it has the power to create two separate applications together in a single instance. This inconsistency is rectified and manifest is made mandatory for all the interfaces.

  * There was no way to view the associated interfaces with the manifest. A new screen is designed for the same.

  * Previously manifest and Role could not be added from the screen. Only their corresponding xmls could be uploaded which was not a good design. It is enhanced to allow the developer to enter role and manifest entries from the screen.

  * Previously xmls and resource files could not be edited from the screen. Developers could upload it from the respective screens. This design is changed to allow the user to edit xmls (interface, theme and application template) from the screen itself. The resource files i.e. css and JavaScript can also be edited from the screen which was not supported in the design before.

  * Change in theme and application template affects the interfaces. Previously developer needs to remember the affected interfaces name. Now this design is changed and a flag is added to mark the affected interface.

  * XMLs are the building block of an application which is built on top of LF. But there is a huge chance of errors in the XMLs. Very basic XSDs was present in LF but there was no validation mechanism present. Now all of the xmls i.e. interface, theme and application template are validated against their corresponding XSDs before getting uploaded. The XSDs are also updated.
  Important part classes which include DBGrid, ConditionalDBGrid and DBForm are restructured and upgraded.

 * Implementation

  * Making the manifest mandatory is done during the individual upload of the interface as well as during uploading the interfaces as a collection. Previously both upload were using their separate functions but were doing the same job. These functions are merged together. A common utility class is created and before calling this function a validation is added to check if the interfaces is associated with the manifest or not. If the checking fails then the upload stops and error is shown to the users.

  * Manifest Management screen is added to view the manifest entries. An interface can be associated with the manifest from this screen. This is done by clicking on the 'New' button in the same screen.

  * Interface Role can be added from the newly added 'New' button of the existing Interface Role Management screen of the core admin module.

  * Interface xml and the related resource could be viewed by selecting on the name of the interface and then clicking on the ‗Show‘ button in the Interface Management screen. In the ‗Show‘ screen a new button is added to view the xml and resource as a text file and edit them and save them online. This reduces the repeated uploading of files which saves time and increase productivity. Application Template, Theme can be viewed and edited in the same way from their respective screens.

  * Interface xml and the related resource could be viewed by selecting on the name of the interface and then clicking on the ‗Show‘ button in the Interface Management screen. In the ‗Show‘ screen a new button is added to view the xml and resource as a text file and edit them and save them online. This reduces the repeated uploading of files which saves time and increase productivity. Application Template, Theme can be viewed and edited in the same way from their respective screens

  * A new screen named as ‗Interface Template Theme Management‘ is introduced to show the name of associated theme and application template of an interface. From this screen developer can see which interface is required to be refreshed as a result of the theme or application template change.

  * At the time of uploading different xmls, the xmls are validated against their corresponding XSD in the responsible servlet. If the XSD validation succeeds then only the xmls are uploaded.

  * The DBGrid and ConditionDBGrid code is fully restructured. These are very important LF classes. It creates table with lot of features. Some of very useful features are also added like filter search, alternate coloring of rows, bootstrapping etc. DBForm class which is responsible for form validation is another very important LF class which is also restructured.

  * Famous UI framework Bootstrap is successfully implemented in the LF. An application template can be created as a bootstrap template

 * Other
 >These are only major changes except those there are lot of minor changes to upgrade the framework. Few of them are -

  * Regenerating the manifest xml.
  * Regenerating the interface role xml.
  * Download all interfaces from the interface screen.
  * Delete all interfaces from the interface screen.
  * Screens are updated to add additional column to show useful and helpful data to the developers.
  * There was no message on any of the core admin screens. Useful messages are added in all of the screens to help the developers to understand about the status of the current operation.
  * Lot of bug fixes and code restructuring is also done to improve the framework.
  * Publishing the code in github for easy versioning and open for all to learn and add values in it.