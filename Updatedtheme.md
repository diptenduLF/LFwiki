**1.Overview**
   >Creating a unifying theme for a webpage is one of the most important steps in designing a website. The purpose of the website should be reflected from its UI design. The look should be consistent and span across the entire website. So, a theme should be designed by keeping in mind that what the web site is all about. Only themes lend a consistent look and feel to different component. Theme changes the design of the website. Changing the theme changes how the site looks on the front-end, i.e. what a visitor sees when they browse to the site on the web.


**2.Functionality**

   >LF provides a simple way for theming the website. ThemeManagement screen in the CoreAdmin application help for managing theme. Please go through section 10.1.2 for more details. From this screen we can upload, modify, delete and edit theme xmls. A basic theme.xml looks like –`<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
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

  >In this file we can define the default style of any component. If, any specific style is not applied to that component then this style will be applied to that particular component. It will help us to make every button, input etc. to use the uniform styling throughout the application. The different element of the theme xml -
 
  * theme – It is the parent element of this xml. This element contains the title of the theme. Theme title should be unique. Two themes cannot have the same title.
  * themeselement – This is the child of theme. theme contains any number of themeselement. Each themeselement contains the styling for a LF class. The different attributes of themeselement –
   * class - It specifies the LF class for which the styling will be applied.
   * type – The type specifies the type of styling which will be applied on this element. It can have two values – reference and inline. If the type is set as reference then it means the value is the css class (class attribute) name of the corresponding HTML element. If the type is set as inline then the value will be set as the style (style attribute) of the element.
   * cssclasses – This attribute will be read if the type is set as reference. The value of this attribute will be set in the class attribute of the element.
   * property - This attribute will be read if the type is set as reference. The value of this attribute will be set in the style attribute of the element.

  >The style section is used to define the visual attributes of an interface using CSS syntax. There are two ways of providing 
 **style attributes** : (i)via reference-here a CSS class name is provided, (ii) inline-here the style attributes are defined within the <style> section itself. In the example below a part with id “userid_container” is given a CSS class with named "FlexRowContainer1" . This class needs to be defined in a CSS file that needs to be uploaded along with interface.xml. For the part id "accsigninbuttoncontainer"  the style is defined inline using the CDATA mechanism of xml; in this case no external CSS file is required.`<style id="Loginstyle">`
`<part id="userid_container" value="FlexRowContainer1" valuetype="reference" resourceid="logincss"></part>`
`<part id="accsigninbuttoncontainer"  value=""[CDATA[height: 100%;background-color:#F0FDA6;min-height:min-content]]" valuetype="inline"></part>`
`</style>`

   >The markup generated for the above style definitions is given below.`<link href="./interfaceenginev2.ResourceCss?resource_id=logincss&amp;interface_id=LoginPage" rel="stylesheet" type="text/css">`

  >The above code is generated to load the CSS file “login.css” mentioned in the resource section of the interface.xml. This file contains the definition of the class “FlexRowContainer1”.`FlexRowContainer1`
`{`
	`display: flex;`
    `flex-direction: column;`
    `flex-direction: column;`
    `background-color: lightblue;`
	`padding-top:0.5em;`
	`padding-bottom:0.5em;`
	`align-items: center;`
	`align-content: center;`
`}`

  > This Class is referred in the generated markup for the div with id "userid_container" `<div class="FlexRowContainer1" id="userid_container" tabindex="">`
`</div>`

 >For the div id "accsigninbuttoncontainer" the markup generated uses the style attribute to define the style inline.`<div id="accsigninbuttoncontainer" style="height: 100%;background-color:#F0FDA6;min-height:min-content" tabindex=""> `
`</div>`

 > The above mechanism is used to style individual interfaces. If a developer wishes to give consistent style to all the interfaces then the mechanism of themes need to be used.  Creating a unifying theme for the various screens is one of the most important steps in designing a website or web-based application. Changing the theme changes how each screen of the site or application looks on the front-end, i.e. what a user sees when they browse to the site on the web.




  >So, the theme is responsible for overall styling of the interfaces. In this file we can define the default style of any component. If, any specific style is not applied to that component then this style will be applied to that particular component. Now theme can be applied to an interface in three different ways.

 * Interface Configuration section – Theme can be mentioned in the interface‘s configuration section. This provides us the power to use a different theme for a particular interface. This theme selection has the highest priority with respect to the two other theme selection.`<configuration ThemeID="Bootstrap"></configuration>`
   
   > A theme with the title Bootstrap should be present.
 * Application Template – Theme can be configured in the application template as well. This makes it sure that the interfaces which use a particular ApplicationTemplate also use the same theme. If for any interface the theme id is specified in the configuration section then that will have the higher priority on this.`<configuration-section>
<attribute name="ThemeID" defaultvalue="bootstrap_theme"></attribute>
<attribute name="createsession" defaultvalue="false"></attribute>
<attribute name="checkrole" defaultvalue="true"></attribute>
</configuration-section>`
  > Each interface.xml may refer to a theme using the themeID attribute. Theme can be mentioned in the interface‘s “configuration” section. This provides us the power to use a different theme for a particular interface. `<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"xmlns="http://learnityframework.org/"`
	`xsi:schemaLocation="http://learnityframework.org/ http://localhost:8080/learnitymsme/xsd/Interface.xsd"`
	`id="LMSPortal" title="LMS Portal" type="Interface">`
       `<configuration themeID=”bootstrap_theme”></configuration>`

 * Default Theme – We can specify a default theme in the ThemeManagement screen. If we don‘t specify any theme in the application template or the interface is not using any application template and no theme is mentioned in the interface as well then the default theme is used.

   >The login page interface.xml contains bootstrap template. This template uses the bootstrap theme. The button in the login interface xml does not contain any special styling. But the theme xml contains the styling for a button as –`<themeselement class="button" type="reference"
cssclasses="btn btn-primary"></themeselement>`

    
   >This is a bootstrap css specific class which mainly colours a button as blue. It result the login page button as blue and all of the pages which will use this template their button will have the same styling. The bootstrap css (Reference [ 40 ]) which contains the styling is loaded by the application template.

   
   >The login page looks like –![login](https://github.com/diptenduLF/LFwiki/blob/master/images/login%20page(cssclass%20using).png)

   >The markup generated for the above screen is given below-
`<link href="../coreadmin/resource/bootstrap/css/bootstrap.css" rel="stylesheet" type="text/css">`
`<link href="../coreadmin/resource/bootstrap/css/bootstrap-theme.css" rel="stylesheet" type="text/css">`
 
   >The above code is generated since the bootstrap template is used with the login interface xml and this template includes the above CSS files.
`<div id="accsigninbuttonbutton"> `
`<input class="btn btn-primary" id="accsigninbutton" name="accsigninbutton" onclick="login_onclick()" type="button" value="Sign In">`
`</div>`

   >The above markup is generated based on the themeselement definition for part class “button”;since this interface includes a part of class button so the CSS classes “btn” and “btn-primary” are added to the HTML ‘input’ tag  of type ‘button’.

   >Now, we will change the bootstrap theme from theme management –![bootstrap theme](https://github.com/diptenduLF/LFwiki/blob/master/images/bootstrap_theme.png)

   > We changed the button style from  cssclasses="btn btn-primary" to “inline” property. Then we need to refresh this from  “InterfaceTemplateThemeManagement” screen. 
`<themeselement class="button" type="inline" `
 `property="position: relative; margin-top: 30px; margin-bottom: 30px; left: 50%; transform: translate(-50%, 0);font-family: inherit;color: red;`
		  `background: white; outline: none; border: none;padding: 5px 15px;font-size: 1.3em;font-weight: 400;border-radius: 3px;box-shadow: 0px 0px 10px rgba(51, 51, 51, 0.4);`
  `cursor: pointer; transition: all 0.15s ease-in-out;"></themeselement>"></themeselement>`
 This will change the already created HTML of interface to the new HTML which will use the new css classes. 
Then we need to refresh this from InterfaceTemplateThemeManagement screen.![in](https://github.com/diptenduLF/LFwiki/blob/master/images/in.png)

   >This will change the already created HTML of interface to the new HTML which will use the new property.
    This will result to the new screen –![login](https://github.com/diptenduLF/LFwiki/blob/master/images/login.png)

   >This changes the button style without changing anything in the corresponding interface xml. It shows how theme impacts the overall styling of the webpage. The overall styling can be controlled and easily changed by the theme within a minute.`<div id="accsigninbuttonbutton">`
`<input id="accsigninbutton" name="accsigninbutton" onclick="login_onclick()" style="position: relative;margin-top: 30px;margin-bottom: 30px;left: 50%;transform: translate(-50%, 0);font-family: inherit;color: red; background: white;outline: none;border: none;padding: 5px 15px;font-size: 1.3em;font-weight: 400;border-radius: 3px;box-shadow: 0px 0px 10px rgba(51, 51, 51, 0.4); cursor: pointer;transition: all 0.15s ease-in-out;" type="button" value="Sign In">`
`</div>`

   >The above markup is generated based on the themeselement definition for part class “button” ; since this interface includes a part of class button so the CSS style attribute is added   to the HTML ‘input’ tag of type ‘button’.


**3.Implementation Details**
    
   >Theme implementation can be divided into two parts –
   
   * Theme Management Screen
   >The ThemeManagement screen is supported by ThemesManagement servlet. When a theme xml is uploaded that time the ThemesManagement servlet took the responsibility to do the necessary steps. It first validates the xml against theme.xsd. If the validation succeeds then the theme xml is parsed and it checks if the theme already exists or not. It checks this against the theme title. If the theme already exists then it deletes the old one and inserts the new theme in the database.
    
   * Apply Theme during Markup Generation
   >During markup generation of a interface.xml the theme is selected in the following way-
    
   > **ThemeID**attribute of configuration section of interface.xml is checked. If it is present and corresponding theme is also present then that is used.
   > **If ThemeID** is not present or the theme which is mentioned in ThemeID is not present then it checks if any application template is being used by the interface or not. If application template is used and it holds some default value for theme then that theme is used.
   > If no theme is selected on the above two steps then it checks for default theme. A theme can be set as default from the ThemeManagement screen. If default theme is present then that is used otherwise no theme is used.

  >ThemeEngine is the helper class which is responsible for executing the above mentioned algorithm to choose the theme for an interface. This is done during the markup generation of an interface in the DisplayEngine class.