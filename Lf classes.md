**1.Overview**
    
   >LF part classes are the most important component of the framework. It creates different HTML components in the screen with some additional wrappers. This helps the developer to create difficult components/behavior much easily. For an example, part class DBGrid helps the user to create table much more easily. Table is one of the most important components of any traditional website. Handling pagination, sorting, filtering and fixed headers are the nightmare of the developers. DBGrid handles almost all of the known issues of table. Similarly form validation is another vital thing in any website. The data in the form must be checked for avoiding obvious error conditions. This is also made very much easy with DBForm class. Also, it provides us complex HTML structures like tree. This part classes are defined in the structure section of an interface.xml. In the structure section there can be any number of part elements. Each part element must contain a class attribute and an id attribute. This id attribute helps us to refer this element in to the other sections of the interface. This id creates the id attribute of the corresponding HTML element of the part class.
`<structure>
<part id="accloginback" class="label"></part>
<part id="acclogincompanyname_container" class="label"></part>
<part id="acclogincompanyname" class="label"></part>
</structure>`
    
    Few important classes are(Reference [ 4 ])-
 * Label
   
   >Class label is used to create a div tag. This is used to create a division or a section in an HTML document. It also helps us to group block-elements.
 
 * Span
   
   >Class span is used to create a span tag. This is used to group inline-elements in a document. The class provides no visual change by itself. It provides us a way to add a hook to a part of a text or a part of a document.
The main difference between this two classes are ―label‖ should be used to wrap sections of a document, while ―span should be used to wrap small portions of text, images, etc. The default nature of ―label class is block where the default nature of span is float.
                         
 * Button

   >To create a button the page we need to use ―button‖ class. It has two attributes
  * Type
  * name
 * Input Text

  >To create a text field for getting input from user one needs to use ―inputtext‖. It has the following attributes –
  * tabindex – The number of tab which will take the cursor to this field
  * name – name of the input field
  * maxLength – maximum length of the input text
  * size – size of the input text box
  * autocomplete – set the browser autocomplete "on" or "off"
 * Input Password

  >To create a password field for getting input from user one needs to use ―password‖. It has the following attributes –
  * tabindex – The number of tab which will take the cursor to this field
  * name – name of the input field
  * maxLength – maximum length of the input text
  * size – size of the input text box
 * Image

  > To add an image in the screen user needs to use the image class. To use an image, we have to add that image in the resource section in the interface.xml, and the id of the resourceitem has to be included in the value in the content tag and mention the valuetype property as reference.
  * Example of all of the above mentioned classes –
    `<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`
`xmlns="http://learnityframework.org/"`
`xsi:schemaLocation="http://learnityframework.org/ http://localhost:8080/contextroot/xsd/Interface.xsd"`
`id="LoginPage" title="LoginPage" type="Interface">`
`<configuration createsession="true" checkrole="false" TemplateID="Bootstrap"></configuration>`
`<structure>`
`<part id="accloginback" class="label"></part>`
`<part id="acclogincompanyname_container" class="label"></part>`
`<part id="acclogincompanyname" class="label"></part>`
`<part id="loginmain_container" class="label"></part>`
`<part id="acclogincompanylogo_container" class="label"></part>`
`<part id="acclogincompanylogo" class="image"></part>`
`<part id="login_container" class="label"></part>`
`<part id="accfislabel" class="label"></part>`
`<part id="accinputouter" class="label"></part>`
`<part id="accinputinnerheader" class="label"></part><part id="accsigninlogo" class="image"></part>`
`<part id="accinputinner" class="label"></part>`
`<part id="userid_container" class="label"></part>`
`<part id="accuseridinputlabel" class="label"></part>`
`<part id="accuseridinput_container" class="label"></part>`
`<part id="accuseridinput" class="inputtext" tabindex="1"`
`autocomplete="on"></part>`
`<part id="password_container" class="label"></part>`
`<part id="accpasswordinputlabel" class="label"></part>`
`<part id="accpasswordinput_container" class="label"></part>`
`<part id="accpasswordinput" class="password" tabindex="2"></part>`
`<part id="accsigninbutton_container" class="label"></part>`
`<part id="accsigninbutton" class="button"></part>`
`<part id="incorrectuser_container" class="label"></part>`
`<part id="incorrectuser" class="label"></part>`
`<part id="accportallogo_container" class="label"></part>`
`<part id="accportallogo" class="image"></part>`
`<part id="accloginajax" class="ajaxcomponent"></part></structure>`
`<layout id="Loginlayout">`
`</layout>`
`<content id="Logincontent">`
`<part id="accportallogo" value="portallogo" valuetype="reference"></part>`
`<part id="accsigninlogo" value="signin" valuetype="reference"></part>`
`<part id="acclogincompanylogo" value="msmelogo" valuetype="reference"></part>`
`<part id="acclogincompanyname" value="MSME TOOLROOM KOLKATA eUNIVERSITY" valuetype="inline"></part>`
`<part id="accfislabel" value="Learner Portal" valuetype="inline"></part>`
`<part id="accuseridinputlabel" value="User ID" valuetype="inline"></part>`
`<part id="accpasswordinputlabel" value="Password" valuetype="inline"></part>`
`<part id="accsigninbutton" value="Sign In" valuetype="inline"></part>`
`</content>`
`<style id="Loginstyle">`
`<part id="acclogincompanyname_container" value="row row-padding text-center"`
`valuetype="reference"></part><part id="acclogincompanyname" value="col-md-12 text-center"valuetype="reference"></part>`
`<part id="acclogincompanyname" value="[CDATA[text-align:center;font-family:times;font-weight:normal;font-size:25px;color:black;]]" valuetype="inline"></part>`
`<part id="loginmain_container" value="row" valuetype="reference"></part>`
`<part id="loginmain_container" value="[CDATA[background-color: #6BB8EF;]]"`
`valuetype="inline"></part>`
`<part id="acclogincompanylogo_container" value="col-md-6 text-center"`
`valuetype="reference"></part>`
`<part id="acclogincompanylogo_container" value="[CDATA[padding-top: 175px;]]"`
`valuetype="inline"></part>`
`<part id="login_container" value="col-md-5" valuetype="reference"></part>`
`<part id="login_container"`
`value="[CDATA[margin-top: 125px;border: 1px solid black;border-radius:5px; background-color: #F7F7F7;]]" valuetype="inline"></part>`
`<part id="accfislabel" value="col-md-12 row-padding" valuetype="reference"></part>`
`<part id="accinputinnerheader" value="col-md-12 row-padding"`
`valuetype="reference"></part><part id="accinputinner" value="form-group form-horizontal col-md-12"`
`valuetype="reference"></part>`
`<part id="userid_container" value="row row-padding" valuetype="reference"></part>`
`<part id="accuseridinputlabel" value="col-md-2 control-label"`
`valuetype="reference"></part>`
`<part id="accuseridinput_container" value="col-md-8" valuetype="reference"></part>`
`<part id="password_container" value="row row-padding" valuetype="reference"></part>`
`<part id="accpasswordinputlabel" value="col-md-2 control-label"`
`valuetype="reference"></part>`
`<part id="accpasswordinput_container" value="col-md-8" valuetype="reference"></part>`
`<part id="accsigninbutton_container" value="row row-padding text-right col-md-10"`
`valuetype="reference"></part><part id="incorrectuser_container" value="row row-padding text-center col-md-10"`
`valuetype="reference"></part><part id="accportallogo_container" value="row row-padding text-center"`
`valuetype="reference"></part>`
`<part id="accpasswordinput" value="form-control" valuetype="reference"></part>`
`<part id="accuseridinput" value="form-control" valuetype="reference"></part>`
`<part id="accsigninbutton" value="btn btn-primary" valuetype="reference"></part>`
`</style>`
`<behaviour id="Loginbehaviour">`
`<part id="accpasswordinput">`
`<event name="onkeypress" type="simple" function="checkEnter"`
`valuetype="inline" parameter="event" resourceid="loginj" ></event>`
`</part>`
`<part id="accsigninbutton">`
`<event name="onclick" type="simple" function="login_onclick"`
`valuetype="inline" resourceid="loginj"></event></part>`
`<part id="accloginajax">`
`<event name="ajax" type="simple" function="dummy" javaclass="Portal"></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="portallogo" href="LearnITy-Portal.gif" valuetype="image"></resourceitem>`
`<resourceitem id="signin" href="SignIn.gif" valuetype="image"></resourceitem>`
`<resourceitem id="msmelogo" href="msmelogo.jpg" valuetype="image"></resourceitem>`
`<resourceitem id="loginj" href="loginjs.js" valuetype="js"></resourceitem>`
`</resource>`
`</interface>`

  * The output screen –![login](https://github.com/diptenduLF/LFwiki/blob/master/images/login.png)
 
 * Link

  >When we want to use a text with hyper link, we have to use class as "textlink", and in the <behavior> part we have to mention the URL in the function attribute for that part id. Example of "textlink"-
  
  > `<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://learnityframework.org/" xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd" id="home" title="home" type="Interface">`
`<configuration createsession="true" checkrole="false" > </configuration>`
`<structure>`
`<part id="homemain" class="label"></part>`
`<part id="center" class="label"></part>`
`<part id="centerimage" class="image"></part>`
`<part id="GoTo" class="textlink"></part>`
`</structure>`
`<layout id="defaultlayout">`
`<part id="homemain" height="420px" width="99.5%" left="1px" top="1px" position="absolute"></part>`
`<part id="center" height="240px" width="63%" left="165px" top="2px" position="absolute" parent_id="homemain"></part>`
`<part id="centerimage" height="200px" width="99.9%" left="1px" top="34px" position="absolute" parent_id="center"></part>`
`<part id="GoTo" height="20px" width="10%" left="430px" top="280px" position="absolute" parent_id="homemain"></part>`
`</layout>`
`<content id="defaultcontent">`
`<part id="centerimage" value="companymotoimager" valuetype="reference"></part>`
`<part id="GoTo" value="Visit our site..." valuetype="inline"></part>`
`</content>`
`<style id="defaultstyle">`
`<part id="homemain" value="stylesheet1" valuetype="reference"></part>`
`<part id="center" value="[CDATA[border-style:solid;border-color:#0080FF;border-width:1px;]]" valuetype="inline"></part>`
`<part id="GoTo" value="[CDATA[border-style:solid;border-color:#0080FF;border-width:1px;font-weight:bold;font-size:11pt;text-align:center;]]" valuetype="inline"></part>`
`</style>`
`<behaviour id="defaultbehaviour">`
`<part id="GoTo">`
`<event name="onclick" type="simple" function="http://abc.com/" target="self" valuetype="inline"></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="stylesheet1" href="homestyle.css" valuetype="css"></resourceitem>`
`<resourceitem id="companymotoimager" href="LearnITy.jpg" valuetype="image"></resourceitem>`
`</resource>`
`</interface>`
  * The snapshot of the above interface –![home page](https://github.com/diptenduLF/LFwiki/blob/master/images/home.png)
   
 * List & List Item
  
   >To use unordered bullet to a text, we have to use class "list" for parent topic and use class "listitem" for their child topic. Example –
  >` <interface id="home" title="home" type="Interface">`
`<configuration createsession="true" checkrole="false" >`
`</configuration>`
`<structure>`
`<part id="homemain" class="label"></part>`
`<part id="center" class="label"></part>`
`<part id="corporate" class="list"></part>`
`<part id="corporatechild1" class="listitem"></part>`
`<part id="corporatechild2" class="listitem"></part>`
`<part id="corporatechild3" class="listitem"></part>`
`<part id="corporatechild4" class="listitem"></part>`
`<part id="GoTo" class="textlink"></part>`
`</structure>`
`<layout id="defaultlayout">`
`<part id="homemain" height="420px" width="99.5%" left="1px" top="1px" position="absolute"></part>`
`<part id="center" height="240px" width="63%" left="165px" top="2px" position="absolute" parent_id="homemain"></part>`
`<part id="GoTo" height="20px" width="10%" left="430px" top="280px" position="absolute" parent_id="homemain"></part>`
`<part id="corporate" position="absolute" parent_id="center"></part>`
`<part id="corporatechild1" parent_id="corporate"></part>`
`<part id="corporatechild2" parent_id="corporate"></part>`
`<part id="corporatechild3" parent_id="corporate"></part>`
`<part id="corporatechild4" parent_id="corporate"></part>`
`</layout>`
`<content id="defaultcontent">`
`<part id="corporate" value="Capabilities for CORPORATE" valuetype="inline"></part>`
`<part id="corporatechild1" value="Exhaustive Skill Management"`
`valuetype="inline"></part>`
`<part id="corporatechild2" value="Extensive reporting with configurable dashboards" valuetype="inline"></part>`
`<part id="corporatechild3" value="Brand and customize the LearnITy portal" valuetype="inline"></part>`
`<part id="corporatechild4" value="Track training requirements" valuetype="inline"></part>`
`<part id="GoTo" value="Visit our site..." valuetype="inline"></part>`
`</content>`
`<style id="defaultstyle">`
`<part id="homemain" value="stylesheet1" valuetype="reference"></part>`
`<part id="center" value="[CDATA[background-color: #FCFFE5;color:#006699;font-family:Verdana,Arial;border-style:solid;border-color:#0080FF;border-width:1px;]]" valuetype="inline"></part>`
`<part id="GoTo" value="[CDATA[border-style:solid;border-color:#0080FF;border-width:1px;font-weight:bold;font-size:11pt;text-align:center;]]" valuetype="inline"></part>`
`</style>`
`<behaviour id="defaultbehaviour">`
`<part id="GoTo">`
`<event name="onclick" type="simple" function="http://aunwesha.com/"`
`target="self" valuetype="inline" ></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="stylesheet1" href="homestyle.css" valuetype="css"></resourceitem>`
`</resource>`
`</interface>`
  * The snapshot of the above interface –![home](https://github.com/diptenduLF/LFwiki/blob/master/images/home2.png)

 * Text Area

   >This class is required to take lengthy user input. The corresponding partclass is "textarea".The supported attributes are –
  * tabindex – The number of tab which will take the cursor to this field.
  * name – name of the text area
  * maxLength – maximum length of the text area
  * size – size of the text area
  * rows – The number of rows(height)
  * cols – The number of columns(width)

 * Combo

  >To create a drop down, we need to use class combo in the interface.xml. The options which are to be included in the combo box, have to be mentioned in the name and value attribute of the <combooption> under <content> tag. The ―valuetype‖ for that part id is set to ―fixed‖ for static content. To use a combo box whose values are to be fetched by a select query from a database, the ―valuetype‖ of the combo class is set to be "query".
  * The example of text area and combo box –
`<interface id="home" title="home" type="Interface">`
`<configuration createsession="true" checkrole="false" >`
`</configuration>`
`<structure>`
`<part id="homemain" class="label"></part>`
`<part id="login" class="label"></part>`
`<part id="addr" class="label"></part>`
`<part id="addrtext" class="textarea" rows="2" cols="23"></part>`
`<part id="country" class="label"></part>`
`<part id="countrytext" class="combo"></part>`
`</structure>`
`<layout id="defaultlayout">`
`<part id="homemain" height="420px" width="99.5%" left="1px" top="1px" position="absolute"></part>`
`<part id="login" height="240px" width="63%" left="165px" top="2px" position="absolute" parent_id="homemain"></part>`
`<part id="addr" height="20px" width="100px" left="200px" top="15px" position="absolute" parent_id="login"></part>`
`<part id="addrtext" height="20px" width="10px" left="285px" top="15px" position="absolute" parent_id="login"></part>`
`<part id="country" height="20px" width="100px" left="200px" top="85px" position="absolute" parent_id="login"></part>`
`<part id="countrytext" height="20px" width="10px" left="285px" top="85px" position="absolute" parent_id="login"></part>`
`</layout>`
`<content id="defaultcontent">`
`<part id="addr" value="Address" valuetype="inline"></part>`
`<part id="country" value="Country" valuetype="inline"></part>`
`<part id="countrytext" valuetype="fixed">`
`<combooption name="Afghanistan" value="Afghanistan"></combooption>`
`<combooption name="Algeria" value="Albania"></combooption>`
`<combooption name="Georgia" value="Georgia"></combooption>`
`<combooption name="Germany" value="Germany"></combooption>`
`<combooption name="Ghana" value="Ghana"></combooption>`
`<combooption name="India" value="India"></combooption>`
`</part>`
`</content>`
`<style id="defaultstyle">`
`<part id="homemain" value="stylesheet1" valuetype="reference"></part>`
`<part id="login" value="[CDATA[background-color:#E6E6FF;font-size:10pt;]]" valuetype="inline"></part>`
`<part id="addr" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="country" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`</style>`
`<resource>`
`<resourceitem id="stylesheet1" href="homestyle.css" valuetype="css"></resourceitem>`
`</resource>`
`</interface>`
  * The snapshot for the above interface xml –![home](https://github.com/diptenduLF/LFwiki/blob/master/images/home3.png)
  * For fetching combo box data from database –
`<content id="scormInitializeContent">
<part id="CourseID" valuetype="query" value="select a.course_id, a.course_name from course a, course_creation_details b where a.course_id=b.course_id"></part>
</content>`

 * Form

   >This is the same as the use of form in html page. When we need to use a form in a web page, we have to use class form. The fields which have to be included in the form are the children of the form. i.e. the ―parent_id‖ of those fields is the part id of class form.
  * The example of "form" –
`<interface id="feedback" title="feedback" type="Interface">`
`<configuration createsession="true" checkrole="false" >`
`</configuration>`
`<structure>`
`<part id="feedbackmain" class="label"></part>`
`<part id="feedback" class="label"></part>`
`<part id="form1" class="form"></part>`
`<part id="visitorname" class="label"></part>`
`<part id="visitornametext" class="inputtext" size="20"></part>`
`<part id="address" class="label"></part>`
`<part id="addresstextarea" class="textarea" rows="2" cols="23"></part>`
`<part id="city" class="label"></part>`
`<part id="citytext" class="inputtext" size="20"></part>`
`<part id="state" class="label"></part>`
`<part id="statetext" class="inputtext" size="20"></part>`
`<part id="pin" class="label"></part>`
`<part id="pintext" class="inputtext" size="20"></part>`
`<part id="organisation" class="label"></part>`
`<part id="organisationtext" class="inputtext" size="20"></part>`
`<part id="designation" class="label"></part>`
`<part id="designationtext" class="inputtext" size="20"></part>`
`<part id="country" class="label"></part>`
`<part id="countrytext" class="combo"></part>`
`<part id="telno" class="label"></part>`
`<part id="telnotext" class="inputtext" size="20"></part>`
`<part id="comment" class="label"></part>`
`<part id="commenttextarea" class="textarea" size="30" rows="7" cols="65"></part>`
`<part id="submitbutton" class="button" size="20" jscontrol="custom"></part>`
`<part id="resetbutton" class="button" size="20" jscontrol="custom"></part>`
`</structure>`
`<layout id="defaultlayout">`
`<part id="feedbackmain" height="400px" width="99.5%" left="1px" top="1px" position="absolute"></part>`
`<part id="feedback" height="405px" width="77.5%" left="12.5%" top="12px" position="absolute" parent_id="feedbackmain"></part>`
`<part id="form1" parent_id="feedback"></part>`
`<part id="visitorname" height="20px" width="100px" left="10px" top="15px" position="absolute" parent_id="form1"></part>`
`<part id="visitornametext" height="20px" width="10px" left="115px" top="15px" position="absolute" parent_id="form1"></part>`
`position="absolute" parent_id="form1"></part>`
`<part id="address" height="20px" width="100px" left="52%" top="25px" position="absolute" parent_id="form1"></part>`
`<part id="addresstextarea" height="20px" width="10px" left="68%" top="15px" position="absolute" parent_id="form1"></part>`
`<part id="city" height="20px" width="100px" left="10px" top="45px" position="absolute" parent_id="form1"></part>`
`<part id="citytext" height="20px" width="10px" left="115px" top="45px" position="absolute" parent_id="form1"></part>`
`<part id="state" height="20px" width="100px" left="52%" top="75px" position="absolute" parent_id="form1"></part>`
`<part id="statetext" height="20px" width="10px" left="68%" top="75px" position="absolute" parent_id="form1"></part>`
`<part id="pin" height="20px" width="100px" left="10px" top="75px" position="absolute" parent_id="form1"></part>`
`<part id="pintext" height="20px" width="10px" left="115px" top="75px" position="absolute" parent_id="form1"></part>`
`<part id="country" height="20px" width="100px" left="52%" top="105px" position="absolute" parent_id="form1"></part>`
`<part id="countrytext" height="20px" width="10px" left="68%" top="105px" position="absolute" parent_id="form1"></part>`
`<part id="organisation" height="20px" width="100px" left="10px" top="165px" position="absolute" parent_id="form1"></part>`
`<part id="organisationtext" height="20px" width="10px" left="115px" top="165px" position="absolute" parent_id="form1"></part>`
`<part id="designation" height="20px" width="100px" left="52%" top="165px" position="absolute" parent_id="form1"></part>`
`<part id="designationtext" height="20px" width="10px" left="68%" top="165px" position="absolute" parent_id="form1"></part>`
`<part id="telno" height="20px" width="100px" left="10px" top="105px" position="absolute" parent_id="form1"></part>`
`<part id="telnotext" height="20px" width="10px" left="115px" top="105px" position="absolute" parent_id="form1"></part>`
`<part id="comment" height="20px" width="100px" left="10px" top="315px" position="absolute" parent_id="form1"></part>`
`<part id="commenttextarea" height="20px" width="10px" left="115px" top="270px" position="absolute" parent_id="form1"></part>`
`<part id="submitbutton" height="20px" width="10px" left="660px" top="310px" position="absolute" parent_id="form1"></part>`
`<part id="resetbutton" height="20px" width="10px" left="660px" top="340px" position="absolute" parent_id="form1"></part>`
`</layout>`
`<content id="defaultcontent">`
`<part id="visitorname" value="*Name" valuetype="inline"></part>`
`<part id="address" value="Address" valuetype="inline"></part>`
`<part id="city" value="City" valuetype="inline"></part>`
`<part id="state" value="State" valuetype="inline"></part>`
`<part id="pin" value="Pin" valuetype="inline"></part>`
`<part id="country" value="Country" valuetype="inline"></part>`
`<part id="countrytext" valuetype="fixed">`
`<combooption name="Afghanistan" value="Afghanistan"></combooption>`
`<combooption name="Algeria" value="Albania"></combooption>`
`<combooption name="American Samoa" value="American Samoa"></combooption>`
`<combooption name="Hungary" value="Hungary"></combooption>`
`<combooption name="Italy" value="Italy"></combooption>`
`<combooption name="Ivory Coast (Cote dIvoire)" value="Ivory Coast (Cote dIvoire)"></combooption>`
`<combooption name="India" value="India"></combooption>`
`<combooption name="Japan" value="Japan"></combooption>`
`<combooption name="Jordan" value="Jordan"></combooption>`
`</part>`
`<part id="organisation" value="Organisation" valuetype="inline"></part>`
`<part id="designation" value="Designation" valuetype="inline"></part>`
`<part id="telno" value="Telephone No." valuetype="inline"></part>`
`<part id="comment" value="Comment" valuetype="inline"></part>`
`<part id="submitbutton" value="Submit" valuetype="inline"></part>`
`<part id="resetbutton" value="Reset" valuetype="inline"></part>`
`</content>`
`<style id="defaultstyle">`
`<part id="feedbackmain" value="stylesheet1" valuetype="reference"></part>`
`<part id="visitorname" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="visitorname" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="address" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="city" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="state" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="pin" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="country" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="organisation" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="designation" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="telno" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="comment" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="howdidu" value="[CDATA[font-size:10pt;font-weight:bold;]]" valuetype="inline"></part>`
`<part id="submitbutton" value="[CDATA[background-color:#006699;color:#FFFFFF;font-size:10pt;font-weight:bold;width:90px;]]"`
`valuetype="inline"></part>`
`<part id="resetbutton" value="[CDATA[background-color:#006699;color:#FFFFFF;font-size:10pt;font-weight:bold;width:90px;]]" valuetype="inline"></part>`
`</style>`
`<behaviour id="defaultbehaviour">`
`<part id="submitbutton">`
`<event name="onclick" type="simple" function="submit_onclick" valuetype="jsevent" ></event>`
`</part>`
`<part id="resetbutton">`
`<event name="onclick" type="simple" function="formReset" valuetype="jsevent" ></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="stylesheet1" href="feedbackstyle.css" valuetype="css"></resourceitem>`
`<resourceitem id="feedbackjs" href="feedbackjs.js"`
`valuetype="js"></resourceitem>`
`</resource>`
`</interface>`
  * The result of the above xml –![feedback](https://github.com/diptenduLF/LFwiki/blob/master/images/feedbach.png)

 * iFrame

   >To use iFrame in the HTML the corresponding part class is – ―iframe‖. The possible attributes are -
  * Width – The width of the iFrame.
  * Height – The height of the iFrame
  * Frameborder – To show the frame border or not.
  * allowtransparency
  * scrolling – to allow scroll in to iFrame or not
  * background-color
  * name
  * The example-
`<interface id="home" title="home" type="Interface">`
`<configuration createsession="true" checkrole="false" >`
`</configuration>`
`<structure>`
`<part id="homemain" class="label"></part>`
`<part id="left_frame" class="iframe"></part>`
`<part id="right_frame" class="iframe"></part>`
`</structure>`
`<layout id="defaultlayout">`
`<part id="homemain" height="420px" width="99.5%" left="1px" top="1px" position="absolute"></part>`
`<part id="left_frame" height="440px" width="40%" left="1px" top="2px" scrolling="yes" position="absolute" parent_id="homemain"></part>`
`<part id="right_frame" height="440px" width="85%" left="230px" top="2px" scrolling="yes" position="absolute" parent_id="homemain"></part>`
`</layout>`
`<style id="defaultstyle">`
`<part id="homemain" value="stylesheet1" valuetype="reference"></part>`
`<part id="left_frame" value="[CDATA[border:0px solid #ff0000;]]" valuetype="inline"></part>`
`<part id="right_frame" value="[CDATA[overflow:auto;]]" valuetype="inline"></part>`
`</style>`
`<behaviour id="defaultbehaviour">`
`<part id="left_frame">`
`<event name="invokeurl" type="simple" function="http://aunwesha.com" target="left_frame" valuetype="inline" ></event>`
`</part>`
`<part id="right_frame">`
`<event name="invokeurl" type="simple" function="./interfaceengine.PortalServlet?IID=feedback" target="right_frame" valuetype="inline" ></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="stylesheet1" href="homestyle.css" valuetype="css"></resourceitem>`
`</resource>`
`</interface>`
  * The snapshot of the above example –![home](https://github.com/diptenduLF/LFwiki/blob/master/images/home4.png)
 * Tree

   >To create a tree structure we need to use the tree class. There can be two types of tree – dynamic tree and static tree. The tree is supported by jQuery framework "jquery.dynatree"(Reference [ 4 ] , [ 41 ])
  * The example -
`<interface id="DeliveryEngine" title="DeliveryEngine" type="Interface">`
`<structure>`
`<part id="deliverymain" class="label"></part>`
`<part id="deliverytop" class="label"></part>`
`<part id="poweredbylearnity" class="label"></part>`
`<part id="notebooklink" class="label"></part>`
`<part id="quitlink" class="label"></part>`
`<part id="deliverytopstrip" class="label"></part>`
`<part id="showhidetoc" class="imagelink"></part>`
`<part id="showhidetoclabel" class="textlink"></part>`
`<part id="deliverysearchlabel" class="label"></part>`
`<part id="query" class="inputtext"></part>`
`<part id="deliverysearchgo" class="button"></part>`
`<part id="showtree" class="label"></part>`
`<part id="coursename" class="label"></part>`
`<part id="treediv" class="tree" treedataremotefunction="launchcourse.treeConstruct" onselectremotefunction="f1" autocollapse="true" initialiseonload="true"></part>`
`<part id="nodeKey" class="hidden"></part>`
`<part id="deliveryIframe" class="iframe"></part>`
`<part id="ee" class="ajaxcomponent" ></part>`
`<part id="previousitem" class="imagelink" ></part>`
`<part id="topitem" class="imagelink" ></part>`
`<part id="nextitem" class="imagelink" ></part>`
`<part id="unitedit" class="button" ></part>`
`<part id="APIAdapter" class="applet" archieve="cmidatamodel.jar,lmsclient.jar,debug.jar" codebase="../html/" mayscript="true"></part>`
`<part id="maxresults" class="inputtext" size="5"></part>`
`<part id="contentsearchlabel" class="label"></part>`
`<part id="contensearchform" class="form"></part>`
`</structure>`
`<layout id="DeliveryEnginelayout">`
`<part id="deliverymain" height="100%" width="100%" left="0px" top="0px" position="absolute"></part>`
`<part id="deliverytop" height="100px" width="900px" left="0px" top="0px" position="absolute" parent_id="deliverymain"></part>`
`<part id="deliverytopstrip" height="40px" width="900px" left="0px" top="100px" position="absolute" parent_id="deliverymain"></part>`
`<part id="showhidetoc" height="30px" width="25px" left="10px" top="5px" position="absolute" parent_id="deliverytopstrip"></part>`
`<part id="showhidetoclabel" height="20px" width="70px" left="40px" top="10px" position="absolute" parent_id="deliverytopstrip"></part>`
`<part id="showtree" height="490px" width="250px" left="0px" top="140px" position="absolute" parent_id="deliverymain"></part>`
`<part id="coursename" parent_id="showtree"></part>`
`<part id="treediv" height="490px" width="250px" left="0px" top="0px" position="absolute" parent_id="showtree"></part>`
`<part id="deliveryIframe" height="490px" width="650px" left="250px" top="140px" position="absolute" parent_id="deliverymain"></part>`
`<part id="poweredbylearnity" height="40%" left="50%" top="5%" position="absolute" parent_id="deliverytop"></part>`
`<part id="notebooklink" height="20%" width="10%" left="60%" top="70%" position="absolute" parent_id="deliverytop"></part>`
`<part id="quitlink" height="20%" width="5%" left="95%" top="70%" position="absolute" parent_id="deliverytop"></part>`
`<part id="ee" parent_id="deliverymain"></part>`
`<part id="previousitem" height="28px" width="28px" left="10px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="topitem" height="28px" width="28px" left="40px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="nodeKey" parent_id="deliverymain"></part>`
`<part id="nextitem" height="28px" width="28px" left="70px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="APIAdapter" position="absolute" parent_id="deliverymain"></part>`
`<part id="contensearchform" parent_id="deliverytopstrip"></part>`
`<part id="deliverysearchgo" height="30px" width="45px" left="610px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="deliverysearchlabel" height="20px" width="50px" left="150px" top="10px" position="absolute" parent_id="contensearchform"></part>`
`<part id="query" height="40px" width="70px" left="205px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="maxresults" height="40px" width="30px" left="530px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="contentsearchlabel" height="30px" width="130px" left="400px"`
`top="5px" position="absolute" parent_id="contensearchform"></part>`
`</layout>`
`<layout id="DeliveryEnginelayoutContentEditor">`
`<part id="deliverymain" height="100%" width="100%" left="0px" top="0px" position="absolute"></part>`
`<part id="deliverytop" height="100px" width="900px" left="0px" top="0px" position="absolute" parent_id="deliverymain"></part>`
`<part id="deliverytopstrip" height="40px" width="900px" left="0px" top="100px" position="absolute" parent_id="deliverymain"></part>`
`<part id="showhidetoc" height="30px" width="25px" left="10px" top="5px" position="absolute" parent_id="deliverytopstrip"></part>`
`<part id="showhidetoclabel" height="20px" width="70px" left="40px" top="10px" position="absolute" parent_id="deliverytopstrip"></part>`
`<part id="showtree" height="490px" width="250px" left="0px" top="140px" position="absolute" parent_id="deliverymain"></part>`
`<part id="coursename" parent_id="showtree"></part>`
`<part id="treediv" height="490px" width="250px" left="0px" top="0px" position="absolute" parent_id="showtree"></part>`
`<part id="deliveryIframe" height="490px"`
`<part id="poweredbylearnity" height="40%" left="50%" top="5%" position="absolute" parent_id="deliverytop"></part>`
`<part id="notebooklink" height="20%" width="10%" left="60%" top="70%" position="absolute" parent_id="deliverytop"></part>`
`<part id="quitlink" height="20%" width="5%" left="95%" top="70%" position="absolute" parent_id="deliverytop"></part>`
`<part id="ee" parent_id="deliverymain"></part>`
`<part id="previousitem" height="28px" width="28px" left="10px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="topitem" height="28px" width="28px" left="40px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="nodeKey" parent_id="deliverymain"></part>`
`<part id="nextitem" height="28px" width="28px" left="70px" top="50%" position="absolute" parent_id="deliverytop"></part>`
`<part id="unitedit" height="60%" left="570px" top="30%" position="absolute" parent_id="deliverytop"></part>`
`<part id="APIAdapter" position="absolute" parent_id="deliverymain"></part>`
`<part id="contensearchform" parent_id="deliverytopstrip"></part>`
`<part id="deliverysearchgo" height="30px" width="45px" left="610px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="deliverysearchlabel" height="20px" width="50px" left="150px" top="10px" position="absolute" parent_id="contensearchform"></part>`
`<part id="query" height="40px" width="70px" left="205px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="maxresults" height="40px" width="30px" left="530px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`<part id="contentsearchlabel" height="30px" width="130px" left="400px" top="5px" position="absolute" parent_id="contensearchform"></part>`
`</layout>`
`<content id="DeliveryEnginecontent">`
`<part id="showhidetoc" value="hidetoc" valuetype="reference"></part>`
`<part id="showhidetoclabel" value="Hide toc" valuetype="inline"></part>`
`<part id="deliverysearchlabel" value="Search" valuetype="inline"></part>`
`<part id="deliverysearchgo" value="GO" valuetype="inline"></part>`
`<part id="poweredbylearnity" valuetype="cdata"><![CDATA[<font size="2"><b><i>Powered By</i></b><font`
`color=\"#FF0000\"><b>&nbsp;&nbsp;LearnITy&#8482;</b></font></font>]]></part>`
`<part id="notebooklink" valuetype="cdata"><![CDATA[<a href="javascript:launchNoteBook()" style="text-decoration:none"><font size="2">NoteBook</font></a>]]></part>`
`<part id="quitlink" valuetype="cdata"><![CDATA[<a href="javascript:doConfirm()" style="text-decoration:none"><font size="2">Quit</font></a>]]></part>`
`<part id="previousitem" value="previousitem" valuetype="reference"></part>`
`<part id="topitem" value="topitem" valuetype="reference"></part>`
`<part id="nextitem" value="nextitem" valuetype="reference"></part>`
`<part id="contentsearchlabel" value="Results Per Page" valuetype="inline"></part>`
`</content>`
`<content id="DeliveryEnginecontentEditor">`
`<part id="showhidetoc" value="hidetoc" valuetype="reference"></part>`
`<part id="showhidetoclabel" value="Hide toc" valuetype="inline"></part>`
`<part id="deliverysearchlabel" value="Search" valuetype="inline"></part>`
`<part id="deliverysearchgo" value="GO" valuetype="inline"></part>`
`<part id="poweredbylearnity" valuetype="cdata"><![CDATA[<font size="2"><b><i>Powered By</i></b><font color=\"#FF0000\"><b>&nbsp;&nbsp;LearnITy&#8482;</b></font></font>]]></part>`
`<part id="notebooklink" valuetype="cdata"><![CDATA[<a href="javascript:launchNoteBook()" style="text-decoration:none"><font size="2">NoteBook</font></a>]]></part>`
`<part id="quitlink" valuetype="cdata"><![CDATA[<a href="javascript:doConfirm()" style="text-decoration:none"><font size="2">Quit</font></a>]]></part>`
`<part id="previousitem" value="previousitem" valuetype="reference"></part>`
`<part id="topitem" value="topitem" valuetype="reference"></part>`
`<part id="nextitem" value="nextitem" valuetype="reference"></part>`
`<part id="unitedit" value="Edit" valuetype="inline"></part>`
`<part id="contentsearchlabel" value="Results Per Page" valuetype="inline"></part>`
`</content>`
`<style id="DeliveryEnginestyle">`
`<part id="deliverymain" value="[CDATA[background-color: #FFFFFF]]" valuetype="inline"></part>`
`<part id="deliverytop" value="[CDATA[background-color: #FFF7E5]]" valuetype="inline"></part>`
`<part id="deliverytopstrip" value="[CDATA[background-color: #6699CC]]" valuetype="inline"></part>`
`<part id="showhidetoclabel" value="[CDATA[color: #FFFFFF;text-decoration:none;font-size: 12px;]]" valuetype="inline"></part>`
`<part id="deliverysearchlabel" value="[CDATA[color: #FFFFFF;text-decoration:none;font-size: 12px;]]" valuetype="inline"></part>`
`<part id="showtree" value="[CDATA[background-color: #D6D6C0;overflow:auto]]" valuetype="inline"></part>`
`<part id="coursename" value="[CDATA[background-color: #D6D6C0]]" valuetype="inline"></part>`
`<part id="poweredbylearnity" value="[CDATA[background-color: #FFF7E5]]" valuetype="inline"></part>`
`<part id="notebooklink" value="[CDATA[background-color: #FFF7E5]]" valuetype="inline"></part>`
`<part id="quitlink" value="[CDATA[background-color: #FFF7E5]]" valuetype="inline"></part>`
`<part id="deliveryIframe" value="[CDATA[background-color: #FFFFFF]]" valuetype="inline"></part>`
`<part id="contentsearchlabel" value="[CDATA[color: #FFFFFF;text-decoration:none;font-size: 14px;]]" valuetype="inline"></part>`
`</style>`
`<behaviour id="DeliveryEnginebehaviour">`
`<part id="root">`
`<event name="onload_onclick();init()" type="simple" resourceid="deliveryjs"></event>`
`</part>`
`<part id="deliveryIframe">`
`<event name="invokeurl" type="simple" function="./interfaceengine.PortalServlet?IID=DeliveryHomePage" valuetype="inline" ></event>`
`</part>`
`<part id="previousitem">`
`<event name="onclick" type="simple" function="previousitem1" valuetype="jsevent" ></event>`
`</part>`
`<part id="topitem">`
`<event name="onclick" type="simple" function="topitem_onclick" valuetype="jsevent" ></event>`
`</part>`
`<part id="nextitem">`
`<event name="onclick" type="simple" function="nextitem1"`
`valuetype="jsevent" ></event>`
`</part>`
`<part id="nextitem">`
`<event name="onclick" type="simple" function="show_hide_toc" valuetype="jsevent" ></event>`
`</part>`
`<part id="showhidetoc">`
`<event name="onclick" type="simple" function="show_hide_toc" valuetype="jsevent" ></event>`
`</part>`
`<part id="showhidetoclabel">`
`<event name="onclick" type="simple" function="show_hide_toc" valuetype="jsevent" ></event>`
`</part>`
`<part id="deliverysearchgo">`
`<event name="onclick" type="simple" function="delivery_search_onclick" valuetype="jsevent" ></event>`
`</part>`
`<part id="APIAdapter">`
`<event name="dummy" type="simple"`
`function="org.adl.samplerte.client.APIAdapterApplet.class" valuetype="jsevent" ></event>`
`</part>`
`</behaviour>`
`<behaviour id="DeliveryEnginebehaviourContentEditor">`
`<part id="root">`
`<event name="onload_onclick();init()" type="simple" valuetype="jsevent " resourceid="deliveryjs"></event>`
`</part>`
`<part id="ee">`
`<event name="dummy" type="simple" javaclass="launchcourse" valuetype="jsevent " ></event>`
`</part>`
`<part id="deliveryIframe">`
`<event name="invokeurl" type="simple" function="./interfaceengine.PortalServlet?IID=DeliveryHomePage" valuetype="inline" ></event>`
`</part>`
`<part id="previousitem">`
`<event name="onclick" type="simple" function="previousitem1" valuetype="jsevent" ></event>`
`</part>`
`<part id="topitem">`
`<event name="onclick" type="simple" function="topitem_onclick" valuetype="jsevent" ></event>`
`</part>`
`<part id="nextitem">`
`<event name="onclick" type="simple" function="nextitem1" valuetype="jsevent" ></event>`
`</part>`
`<part id="unitedit">`
`<event name="onclick" type="simple" function="launch_editor" valuetype="jsevent" ></event>`
`</part>`
`<part id="showhidetoc">`
`<event name="onclick" type="simple" function="show_hide_toc" valuetype="jsevent" ></event>`
`</part>`
`<part id="showhidetoclabel">`
`<event name="onclick" type="simple" function="show_hide_toc" valuetype="jsevent" ></event>`
`</part>`
`<part id="deliverysearchgo">`
`<event name="onclick" type="simple" function="delivery_search_onclick" valuetype="jsevent" ></event>`
`</part>`
`<part id="APIAdapter">`
`<event name="dummy" type="simple" function="org.adl.samplerte.client.APIAdapterApplet.class" valuetype="jsevent" ></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="deliveryjs" href="deliveryjs.js" valuetype="js"></resourceitem>`
`<resourceitem id="previousitem" href="PreviousArrow.gif" valuetype="image"></resourceitem>`
`<resourceitem id="topitem" href="TOCIcon.gif" valuetype="image"></resourceitem>`
`<resourceitem id="nextitem" href="NextArrow.gif"`
`valuetype="image"></resourceitem>`
`<resourceitem id="hidetoc" href="hidetoc.gif" valuetype="image"></resourceitem>`
`<resourceitem id="treejs" href="dynatree.js" valuetype="js"></resourceitem>`
`</resource>`
`</interface>`
  * Snapshot of the above xml -![pic](https://github.com/diptenduLF/LFwiki/blob/master/images/pic.png)
  * Generating Javascript code for tree class inside source code:`function GenerateTree()
{
launchcourse.treeConstruct
(function(data){
setValue('treediv',data);
$("#treediv").dynatree({
title: "Sample",
autoCollapse: true,
keyboard: true,
onSelect: function(dtnode) {
f1(dtnode)
} });});
}
function f1(dtnode){
var url1=dtnode.data.url;
var length1=url1.length;
var s1=url1.substring(length1-4,length1);
var browserName = navigator.appName;
var browserVersion = parseInt(navigator.appVersion);
if(s1!='asmt'){
//alert(s1);
document.getElementById("deliveryIframe").src = dtnode.data.url;
$("#nodeKey").val(dtnode.data.key);
launchcourse.onselectTitle(dtnode.data.key,dtnode.data.tooltip,function(data) {
var b=data;
//alert("..."+b);
if(b=='true')
{
location.href="./interfaceengine.PortalServlet?IID=LoginPage";
}
});
}
else{
$("#nodeKey").val(dtnode.data.key);
launchcourse.getEmbeddedAssessment(dtnode.data.url,function(data){
var filename1=data[0];
var cid=data[1];
if(browserName == 'Microsoft Internet Explorer' && browserVersion >=4){
document.getElementById("deliveryIframe").src = "./learnityasmtserver.assessmentportal.embeddedasmt.Assessment?s="+filename1+"&cid="+cid+"&identifier="+dtnode.data.key;
}
else {
document.getElementById("deliveryIframe").src = "./learnityasmtserver.assessmentportal.embeddedasmt.AssessmentXHTML?s="+filename1+"&cid="+cid+"&identifier="+dtnode.data.key;
}
});
}
}
<part id="treediv" class="tree" treedataremotefunction="launchcourse.treeConstruct" onselectremotefunction="f1" autocollapse="true" initialiseonload="true"></part>`

   * Here ―launchcourse‖ is pojo class name and ―treeConstruct‖ is function name of the pojo class name. For on select event in tree links if you want to call any function please write function name, here f1 is the function name. After that whatever you want to write inside function f1, please write in a js file and define it in interface.xml file using resource tag.`<behaviour>
<part id="treeDiv">
<event name="dummy" type="simple" valuetype="jsevent" resourceid="treejs"></event>
</part>
</behaviour>
<resource>
<resourceitem id="treejs" href="dynatree.js" valuetype="js"></resourceitem>
</resource>`

  Here dynatree.js (Reference [ 41 ]) is the js file and it is defined here using resourceitem id treejs.
 
  When interface engine reads the name of the js file it finds that file and read contents from it and in generating code paste inside of function f1 in source code. autocollapse="true" means tree nodes will automatic collapse. initialiseonload="true" means GenerateTree function will call at the time of page loading otherwise write false and call GenerateTree function from anywhere else as you need.
  * Static Tree - statictree class is require to create a tree whose nodes are fixed and known to application programmer.
Code snippet -`<structure>
<part id="lex-admin-menu" class="statictree" tooltip="true" onselectremotefunction="f12" initialiseonload="true">
<treedata>
<node key="1" title="Lexicographer Admin" isFolder="true" >
<node key="1a" title="Lexicographer Load Summary" url="./interfaceengine.PortalServlet?IID=loadSummary" isFolder="false"></node>
<node key="2a" title="Lexicographer Load Management" url="./interfaceengine.PortalServlet?IID=individualLoadSummary" isFolder="false"></node>
<node key="3a" title="Lexicographer Assign Words" url="./interfaceengine.PortalServlet?IID=AssignWords" isFolder="false"></node>
<node key="4a" title="Lexicographer Auto Load Assignment" url="./interfaceengine.PortalServlet?IID=AutoLoadAssignments" isFolder="false"></node>
<node key="5a" title="Tl Lexicographer Association" url="./interfaceengine.PortalServlet?IID=TlLexAssociation" isFolder="false"></node>
<node key="6a" title="Word Completion Criteria" url="./interfaceengine.PortalServlet?IID=wordcompletioncriteria" isFolder="false"></node>
<node key="7a" title="Export Management" url="./interfaceengine.PortalServlet?IID=crawlerexport" isFolder="false"></node>
<node key="8a" title="Import Management" url="./interfaceengine.PortalServlet?IID=crawlerimport" isFolder="false"></node>
<node key="9a" title="Performance Dashboard"
url="./interfaceengine.PortalServlet?IID=performancedashboard" isFolder="false"></node>
<node key="10a" title="Browse" isFolder="true">
<node key="10a1" title="Sentence Queue" url="./interfaceengine.PortalServlet?IID=BrowseSentenceQueue" isFolder="false"></node>
<node key="10a2" title="Image Queue" url="./interfaceengine.PortalServlet?IID=BrowseImageQueue" isFolder="false"></node>
<node key="10a3" title="Video Queue" url="./interfaceengine.PortalServlet?IID=BrowseVideoQueue" isFolder="false"></node>
<node key="10a4" title="Pronunciation Queue" url="./interfaceengine.PortalServlet?IID=BrowsePronunQueue" isFolder="false"></node>
</node>
<node key="11a" title="Lex Status Export" url="./interfaceengine.PortalServlet?IID=LexStatusExport" isFolder="false"></node>
<node key="12a" title="Reports" isFolder="true">
<node key="12a1" title="View Report" url="./interfaceengine.PortalServlet?IID=Reports" isFolder="false"></node>
</node>
</node>
</treedata>
</part>
<part id="lex-tl-menu" class="statictree" lazynode="true" tooltip="true" onselectremotefunction="f12" initialiseonload="true">
<treedata>
<node key="1" title="Team Leader" isFolder="true" >
<node key="1a" title="View Unapproved Item" url="./interfaceengine.PortalServlet?IID=ViewItem" isFolder="false"></node>
<node key="1aa" title="View Approved Item" url="./interfaceengine.PortalServlet?IID=Production" isFolder="false"></node>
<node key="11a" title="View Discarded Item" url="./interfaceengine.PortalServlet?IID=ViewDiscardedItem" isFolder="false"></node>
</node>
</treedata>
</part>
</structure>
Behaviour
<behaviour id="lex-admin-behaviour">
<part id="lex-admin-menu">
<event name="dummy" type="simple" valuetype="jsevent" resourceid="treejs"/>
</part>
<part id="lex-mn-menu">
<event name=" dummy" type="simple" valuetype=" jsevent" resourceid="treejs"/>
</part>
</behaviour>
<resource>
<resourceitem id="treejs" href="tree.js" valuetype="js"/>
</resource>`
 lazynode attribute defines, if all node will create or only root node will create at the time of initialization. lazynode="true" means only root node will create at the time of initialization and after loading page, when you click a node its child nodes will be created. lazynode="false" means all node will create at the time of initialization. tooltip="true" will show tooltip of a node. ―Onselectremotefunction‖ attribute defines a function name. This function is called when a node is clicked. onselectremotefunction="f12", Here f12 is the function name. autocollapse="true" means tree nodes will automatic collapse. initialiseonload="true" means GenerateTree function will call at the time of page loading otherwise write false and call GenerateTree function from anywhere else as needed.`<resourceitem id="treejs" href="tree.js" valuetype="js"/>`

  * Here treejs.js is the js file and it is define here using resourceitem id treejs. When interface engine reads the name of the js file it finds that file and read contents from it and in generating code paste inside of function f12 in source code. In given example node Browse is one of parent the parent node and Sentence Queue, Image Queue, Video Queue all are child node of node Browse.`Write xml structure of nodes inside tag <treedata></treedata>`
Such as,`<treedata>
<node key="1" title="Team Leader" isFolder="true" >
<node key="1a" title="View Unapproved Item" url="./interfaceengine.PortalServlet?IID=ViewItem" isFolder="false"></node>
</node>
</treedata>`
   * Attribute title is the node name and key is its unique identity. Node team Leader is the parent node of node  View Unapproved Item.Generated JavaScript code inside for statictree class inside source code, when lazynode is true -`function GenerateTree()
{
$("#lex-tl-menu").dynatree({
initAjax: {url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-tl-menu&islazynode=true&tooltip=true&classname=statictree",
data: {key: "root"}
},
onActivate: function(dtnode) {
f12(dtnode);
}
,onLazyRead: function(dtnode){
dtnode.appendAjax({url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-tl-menu&islazynode=true&tooltip=true&classname=statictree",
data: {key: dtnode.data.key
}
});
}
});
}
function f12(dtnode){
document.getElementById('lex-admin-iframe').src = dtnode.data.url;
$("#lex-admin-header-page").text(dtnode.data.title);`
  * Generated JavaScript code inside for statictree class inside source code, when lazynode is false -`function GenerateTree()
{
$("#lex-mn-menu").dynatree({
initAjax: {url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-mn-menu&islazynode=&tooltip=true&classname=statictree",
data: {key: "root"}
},
onActivate: function(dtnode) {
f12(dtnode);
}
});
}
function f12(dtnode){
document.getElementById('lex-admin-iframe').src = dtnode.data.url;
$("#lex-admin-header-page").text(dtnode.data.title);
}`
  * Dynamic tree - dynamictree class is required to create a tree whose nodes will be dynamically generated from database. Interface snippet -`<structure>
<part id="lex-admin-menu" class="dynamictree" autocollapse="true" lazynode="false" tooltip="false" onselectremotefunction="f12" initialiseonload="true" parentquery="select
a.c_id,a.topic_name from admintree a,admintree_main m where a.p_id='0' and a.course_id=m.course_id and m.course_id=%course_id%" childquery="select a.c_id,a.topic_name from admintree a,admintree_main m where a.p_id=? and a.course_id=m.course_id and m.course_id=%course_id%" parameter="course_id"></part>
</structure>
<behaviour id="lex-admin-behaviour">
<part id="lex-admin-menu">
<event name="dummy" type="simple" valuetype="jsevent" resourceid="treejsadmin"/>
</part>
</behaviour>
<resource>
<resourceitem id="treejsadmin" href="tree1.js" valuetype="js"/>
</resource>`lazynode attribute defines, if all node will create or only root node will create at the time of initialization. lazynode="true" means only root node will create at the time of initialization and after loading page, when a node is clicked its child nodes will be created. lazynode="false" means all node will create at the time of initialization. tooltip="true" will show tooltip of a node. Onselectremotefunction attribute defines a function name. This function is called when a node is clicked. onselectremotefunction="f12", Here f12 is the function name.  autocollapse="true"‘ means tree nodes will automatic collapse. initialiseonload="true"‘ means GenerateTree function will call at the time of page loading otherwise write false and call GenerateTree function from anywhere else as you need.`<resourceitem id="treejsadmin" href="tree1.js" valuetype="js"/>`
  Here tree1.js is the js file and it is define here using resourceitem id treejsadmin.When interface engine reads the name of the js file it finds that file and read contents from it and in generating code paste inside of function f12 in source code. parentquery attribute defines a query to access root nodes from database. childquery attribute defines a query to access child nodes from database. parameter defines parameters of the both queries. In given example course_id is a parameter name.
  * Generated javascript code inside for dynamictree class inside source code when lazynode is true.`function GenerateTree()
{
$("#lex-tl-menu").dynatree({
initAjax: {url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-tl-menu&islazynode=true&tooltip=true&classname=statictree",
data: {key: "root"}
},
onActivate: function(dtnode) {
f12(dtnode);
}
,onLazyRead: function(dtnode){
dtnode.appendAjax(
{url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-tl-menu&islazynode=true&tooltip=true&classname=statictree",
data: {key: dtnode.data.key
}
});
}
});function f12(dtnode){
document.getElementById('lex-admin-iframe').src = dtnode.data.url;
$("#lex-admin-header-page").text(dtnode.data.title);`
  * Generated javascript code inside for dynamictree class inside source code when lazynode is false -`function GenerateTree()
{
$("#lex-mn-menu").dynatree({
initAjax: {url: "./interfaceengine.jsonWriter?interface_id=lexAdmin&part_id=lex-mn-menu&islazynode=&tooltip=true&classname=statictree",
data: {key: "root"}
},
onActivate: function(dtnode) {
f12(dtnode);
}
});
}
function f12(dtnode){
document.getElementById('lex-admin-iframe').src = dtnode.data.url;
$("#lex-admin-header-page").text(dtnode.data.title);
}`
 * Report and Report Window

   >To generate report we can use these two classes – report and reportwindow (Reference [ 4 ]). To show report on same page/frame, "report" LF class is used. To show report in a new window reportwindow will be used. We also need to add the report (.rptdesign) in rpt_file attribute in part element of content section in the interface.xml. Also we have to add the report parameters in the report_parameters tag under part element of content section. In behaviour we have to call LoadReport in function from where we need to view the report. This java script method is auto generated. We may also call this java script method from another java script method.`<interface id="TLProdictivityMetrics" title="TLProdictivityMetrics" type="Interface">`
`<configuration createsession="true" checkrole="true" />`
`<structure>`
`<part id="reportsmain" class="label" />`
`<part id="reporttypelabel" class="label" />`
`<part id="reporttype" class="combo" />`
`<part id="reportframe" class="report" />`
`<part id="showreport" class="button" />`
`<part id="accloginajax" class="ajaxcomponent" />`
`</structure>`
`<layout id="TLProdictivityMetricsLayout">`
`<part id="reportsmain" height="500px" width="768px" left="0px" top="0px" position="absolute" />`
`<part id="reporttypelabel" height="30px" width="100px" left="20px" top="20px" position="absolute" parent_id="reportsmain" />`
`<part id="reporttype" height="30px" width="150px" left="130px" top="20px" position="absolute" parent_id="reportsmain" />`
`<part id="reportframe" height="400px" width="700px" left="1px" top="50px" position="absolute" parent_id="reportsmain" />`
`<part id="showreport" height="30px" width="50px" left="160px" top="110px" position="absolute" parent_id="reportsmain" />`
`<part id="accloginajax" parent_id="reportsmain" />`
`</layout>`
`<content id="TLProdictivityMetricsContent">`
`<part id="reporttypelabel" value="Select report" valuetype="inline" />`
`<part id="reporttype" valuetype="query" value="Select u.user_id,concat(u.first_name,\' \',u.sname) from user_details u, user_role ur, role r where u.user_id=ur.user_id and ur.role_id=r.role_id and r.title=\'TEAMLEADER\'">`
`</part>`
`<part id="reportframe" viewer_type="html" rpt_file="tl_productivity_metrics.rptdesign">`
`<report_parameters>`
`<report_parameter name="tl_id" value="tl_id()" value_type="function"></report_parameter>`
`</report_parameters>`
`</part>`
`<part id="showreport" value="Show Report" valuetype="inline" />`
`</content>`
`<style id="TLProdictivityMetricsStyle">`
`<part id="reportsmain" value="[CDATA[font: 12px Arial Bold;]]" valuetype="inline"/>`
`</style>`
`<behaviour id="TLProdictivityMetricsBehaviour">`
`<part id="reporttype">`
`<event name="onchange" type="simple" function="tlselect_onchange()" valuetype="inline" resourceid=" reportsjs "/>`
`</part>`
`<part id="showreport">`
`<event name="onclick" type="simple" function="LoadReport" valuetype="jsevent"/>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="reportsjs" href="reports.js" valuetype="js"/>`
  * The generated report from the above interface after clicking the ―Show Report‖ button –![pic](https://github.com/diptenduLF/LFwiki/blob/master/images/pic2.png)
 * Chart

   >To use chart we need to use the part class chart(Reference [ 4 ]). In the structure section -`<part id="chart1" class="chart"></part>`
   * In content part we have to add all parameters for that chart in between <chartstructure></chartstructure> tag.`<part id="chart1">
<chartstructure>
<matric_title>Active User</matric_title>
<description>Active User</description>
<X_axis_query>select account_status from student_details group by account_status</X_axis_query>
<series1_query>select count(account_status) from student_details group by account_status</series1_query>
<series2_query>2</series2_query>
<series3_query>3</series3_query>
<legenddata1>User Type</legenddata1>
<legenddata2>2l</legenddata2>
<legenddata3>3l</legenddata3>
<chart_type>pie</chart_type>
<subtype>0</subtype>
<width>700</width>
<height>700</height>
<yaxis_label>Active User</yaxis_label>
<color>3</color>
<chart_dimension>TwoDimensionalwithdepth</chart_dimension>
</chartstructure>
</part>`
  * An interface.xml using the chart class –`<interface id="userChart" title="userChart" type="Interface">
<configuration createsession="true" checkrole="true" >
</configuration>
<structure>
<part id="mainpage" class="label"></part>
<part id="chart1" class="chart"></part>
<part id="Passajaxcomp" class="ajaxcomponent"></part>
</structure>
<layout id="userChartLay">
<part id="mainpage" height="100%" width="100%" left="0px" top="0px" position="absolute" > </part>
<part id="chart1" height="96%" width="96%" left="5px" top="10px" position="absolute" parent_id="mainpage"></part>
<part id="Passajaxcomp" parent_id="mainpage"></part>
</layout>
<content id="userChartCont">
<part id="chart1">
<chartstructure>
<matric_title>Active User</matric_title>
<description>Active User</description>
<X_axis_query>select account_status from student_details group by account_status</X_axis_query>
<series1_query>select count(account_status) from student_details group by account_status</series1_query>
<series2_query>2</series2_query>
<series3_query>3</series3_query>
<legenddata1>User Type</legenddata1>
<legenddata2>2l</legenddata2>
<legenddata3>3l</legenddata3>
<chart_type>pie</chart_type>
<subtype>0</subtype>
<width>700</width>
<height>700</height>
<yaxis_label>Active User</yaxis_label>
<color>3</color> <chart_dimension>TwoDimensionalwithdepth</chart_dimension>
</chartstructure>
</part>
</content>
</interface>`
  * The screen for the above interface.xml –
    
     >![pic](https://github.com/diptenduLF/LFwiki/blob/master/images/pic4.png)
     >Both the Report and Chart are using the BIRT (Business Intelligence and Reporting Tools) (Reference [ 46 ]), which is an open source Eclipse-based reporting system.
 * DBForm and its related part classes

   >This part class is used to create a form and its corresponding members inside it. The part having class DBForm can contain any number of element sections under it. The element section is same as the part section of the structure section. It contains the class name which can be any of the available part classes. It also contains an id for the element and the attributes available for the corresponding class. This class uses jQuery validation script(Reference [ 45 ]) . The DBForm specific part classes –
  * formlabel - This is label corresponding to an input element. It has a for attribute which specifies for which input element the formlabel is created.
  * formtext - It is same as inputtext class.
  * formdate – It is for date input. User can select a date from the datepicker.
  * formemail - It is for mail input. It checks if the input is email or not.
  * formnumber - It is for number input. It checks if the input is number or not.
  * formpassword - It is for password input.
  * fieldset – It is not specific no to DBForm. It creates HTML fieldset element. It holds the entire element inside it as described in the layout section.
  * submitbutton – This is same as a button which submits the form but it validates the form before submitting. On success of the validation it calls the function mentioned on the success_method attribute of the DBForm class. error_method is also present for calling a function in validation failure.

   >The DBForm helps us to validate the form which is very important before submitting any form. To use the validation feature user should use the submitbutton class to submit the form. Different types of validation properties are supported by the elements –
  
  * required and requiredmess – required attributes helps us to make the element mandatory and ―requiredmess― helps us in showing the corresponding message if the mandatory field is left blank.
  * minlength and minlengthmess - minlength attributes helps us to make the element‘s minimum length and ―minlengthmess― helps us in showing the corresponding message if the minimum length is not fulfilled.
  * maxlength and maxlengthmess - - maxlength attributes helps us to make the element‘s maximum length and ―maxlengthmess ― helps us in showing the corresponding message if the maximum length is not fulfilled.
  * equalto and equaltomess - equalto attributes helps us to check the corresponding element is equal to the mentioned element or not and ―equaltomess ― helps us in showing the corresponding error message if the condition is not fulfilled.
  * email and emailmess– email attributes make it sure that the input has to be an email and emailmess shows the corresponding error message if it is not an email.
  *numbercheck and numbermess – numbercheck attributes make it sure that the input has to be a number and numbermess shows the corresponding error message.

  >All of the validation attributes except equalto can have only two values true or false. equalto contains the id of the part with which the comparison will be made. The message attributes contains the validation message.The element also contains some special attributes for DBForm class except the part attributes-
 
  * type – The element value will be entered or auto populated. It can have two values – entered or auto.
  * insertindex – this attribute helps the insert query for fetching the elements value. Depending upon the index the paramters attribute in the insert query are replaced.
  * selectindex – this attribute helps us to populate the value in different fields. The select query output populates the values in corresponding fields depending upon the select index.
  * modifyindex - this attribute helps the modify query for fetching the elements value. Depending upon the index the paramters attribute in the modify query are replaced.
  
 >The element section also contains the queries for select, modify and insert.
An example interface –
`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`
`xmlns="http://learnityframework.org/"`
`xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"`
`id="ChangePassword" title="Change LMS Admin Password" type="Interface">`
`<configuration TemplateID="GridTreeNew"></configuration>`
`<structure>`
`<part id="mainpage" class="label"></part>`
`<part id="mainDiv" class="label"></part>`
`<part id="mess" class="label"></part>`
`<part id="changePasswordForm" class="DBForm" success_method="submitForm()">`
`<element id="changePasswordFieldSet" class="fieldset" />`
`<element id="UserId" class="formlabel" for="UserIddata" />`
`<element id="UserIddata" class="formtext" size="20" type="entered"`
`selectindex="1" />`
`<element id="OldPassword" class="formlabel" for="OldPassworddata" />`
`<element id="OldPassworddata" class="formtext" size="20"`
`tabindex="1" type="entered" selectindex="2" required="true"`
`requiredmess="Old Password is required!!" />`
`<element id="NewPassword" class="formlabel" for="NewPassworddata" />`
`<element id="NewPassworddata" class="formpassword" size="20"`
`tabindex="2" type="entered" modifyindex="1" required="true"`
`minlength="6" requiredmess="New Password is required!!"`
`minlengthmess="New Password should be 6 charecter long!!"`
`selectindex="4" />`
`<element id="RetypePassword" class="formlabel" for="RetypePassworddata" />`
`<element id="RetypePassworddata" class="formpassword" size="20"`
`tabindex="3" type="entered" required="true" requiredmess="Please retype Password!!"`
`equalto="NewPassworddata" equaltomess="Retyped password does not match!!"`
`selectindex="5" />`
`<element id="emaillabel" class="formlabel" for="emaill"></element>`
`<element id="emaill" class="formemail" size="20" tabindex="4"`
`type="entered" selectindex="3" required="true" requiredmess="Email is required!!"></element>`
`<element id="subbutton" class="submitbutton" size="20"`
`tabindex="5" />`
`<select>`
`<query id="1"`
`sql="select sp.student_id,sp.password,sd.email_id,'''','''' from student_password sp,student_details sd where sp.student_id=sd.student_id and sp.student_id=%UserIddata%"`
`parameter="UserIddata" />`
`</select>`
`<modify>`
`<query id="1"`
`sql="update student_password set password=%NewPassworddata% where student_id=%UserIddata%"`
`parameter="NewPassworddata,UserIddata" />`
`</modify>`
`</part>`
`<part id="Passajaxcomp" class="ajaxcomponent"></part>`
`</structure>`
`<layout id="ChangePasswordLay">`
`<part id="mainpage" height="100%" width="100%" left="0px" top="0px"`
`position="absolute"></part>`
`<part id="mainDiv" width="395px" left="25%" top="90px" position="absolute"`
`parent_id="mainpage"></part>`
`<part id="mess" height="50px" width="475px" left="20%" top="1px"`
`position="absolute" parent_id="mainpage"></part>`
`<part id="changePasswordForm" left="10px" top="22px" position="absolute"`
`parent_id="mainDiv"></part>`
`<part id="changePasswordFieldSet" parent_id="changePasswordForm"></part>`
`<part id="UserId" parent_id="changePasswordFieldSet"></part>`
`<part id="UserIddata" parent_id="changePasswordFieldSet"></part>`
`<part id="OldPassword" parent_id="changePasswordFieldSet"></part>`
`<part id="OldPassworddata" parent_id="changePasswordFieldSet"></part>`
`<part id="NewPassword" parent_id="changePasswordFieldSet"></part>`
`<part id="NewPassworddata" parent_id="changePasswordFieldSet"></part>`
`<part id="RetypePassword" parent_id="changePasswordFieldSet"></part>`
`<part id="RetypePassworddata" parent_id="changePasswordFieldSet"></part>`
`<part id="emaillabel" parent_id="changePasswordFieldSet"></part>`
`<part id="emaill" parent_id="changePasswordFieldSet"></part>`
`<part id="subbutton" parent_id="changePasswordFieldSet"></part>`
`<part id="Passajaxcomp" parent_id="mainpage"></part>`
`</layout>`
`<content id="ChangePasswordCont">`
`<part id="mess" value="Change Password" valuetype="inline"></part>`
`<part id="UserId" value="User Id : " valuetype="inline"></part>`
`<part id="OldPassword" value="Old Password : " valuetype="inline"></part>`
`<part id="NewPassword" value="New Password : " valuetype="inline"></part>`
`<part id="RetypePassword" value="Retype Password : " valuetype="inline"></part>`
`<part id="emaillabel" value="Email : " valuetype="inline"></part>`
`<part id="subbutton" value="SAVE" valuetype="inline"></part>`
`</content>`
`<style id="ChangePasswordstyle">`
`<part id="mainpage" value="[CDATA[background-color: #E4EBF2;]]"`
`valuetype="inline"></part>`
`<part id="mainDiv"`
`value="[CDATA[background-color: #868890;border:5px ridge white;color:white;]]"`
`valuetype="inline"></part>`
`<part id="mess"`
`value="[CDATA[font-family:Verdan;cellpadding=2;font-size:14px;font-weight:bold;color:gray;font-size:25px;text-align:center;text-decoration:underline;]]"`
`valuetype="inline"></part>`
`<part id="UserId"`
`value="[CDATA[font-family:Verdan;cellpadding=2;font-size:14px;font-weight:bold]]"`
`valuetype="inline"></part>`
`<part id="OldPassword"`
`value="[CDATA[font-family:Verdan;cellpadding=2;font-size:14px;font-weight:bold]]"`
`valuetype="inline"></part>`
`<part id="NewPassword"`
`value="[CDATA[font-family:Verdan;cellpadding=2;font-size:14px;font-weight:bold]]"`
`valuetype="inline"></part>`
`<part id="RetypePassword"`
`value="[CDATA[font-family:Verdan;cellpadding=2;font-size:14px;font-weight:bold]]"`
`valuetype="inline"></part>`
`</style>`
`<behaviour id="ChangePasswordBeha">`
`<part id="root">`
`<event name="onload" type="simple" function="onload_click"`
`valuetype="jsevent" resourceid="ChangePasswordjs"></event>`
`</part>`
`<part id="Passajaxcomp">`
`<event name="ajax" type="simple" function="dummy" javaclass="Portal"></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="ChangePasswordjs" href="ChangePassword.js"`
`valuetype="js"></resourceitem>`
`</resource>`
`</interface>`
  > The corresponding screen –![changepasswrd](https://github.com/diptenduLF/LFwiki/blob/master/images/change%20password.png)

 * DBGrid

   >DBGrid creates tables with the commonly required functionalities like pagination, sorting, fixed header, search, add, edit, delete rows etc. This class uses JQGrid framework(Reference [ 38 ], [ 39 ]).. The part having class as DBGrid may have different attributes like –
  * caption – this attribute contains the header of the table.
  * sortname – this contains the name of the column depending on which the table will be primarily sorted.
  * sortorder - default sorting order. The value can be asc or desc
  * searchOnEnter – This is for filter search. If filter search is made as true then this attribute tells if the search will start on key press or it will wait for an enter key. The value can be true or false. Default is false.
  * Gridnavbar – To switch on or off the table nav bar. The value can be true or false. Default is true.
  * Multiselect – To allow multi select rows. The value can be true or false. Default is false.
  * Rownum – The number of rows to show on a page.
  * Rowlist - To allow the user to select how many rows he/she wants to see per page.
  * Resetsearchonclose – After search is made from the pop up, if the user wants to reset when the pop up closes then the value would be true otherwise false.
  * Multiplesearch - To allow multiple searching from the search pop up.
  * Customeditbutton – To add custom edit button. By default add/edit/delete buttons are present in the navigation bar.
  * altRows – To colur alternate rows.
  * altclass – To add different classes in alteranate rows.
  * autowidth – To adjust the width of the columns automatically.
  * rownumbers – To add sequential number for each row.
  * filterToolbar – To on the filter search.

  >The part having class as DBGrid contains one or more column elements. column element is for each column. It may have different attributes like –
  
  * head – The header of the column.
  * Name – name of the column
  * index – index of the column
  * width – with of the column
  * editable – If the column is editable or not.
  * hidden – If the column will be shown to the user or not.
  * key – If the column is the key for the row or not
  * required – If the column is required when editing or adding a row.

  >Class DBGrid is used to generate simple grid that access the data from database using the query defined inside the <loadquery></loadquery> tag.
  Add, <Modify> and <Delete> actions can be done in this grid by the queries defined inside <add></add>, <modify></modify> and <delete></delete> tags respectively. Inside the above tags queries are defined in the following way –`<queries>
<query id="1" sql="[CDATA[delete from student_creation_details where student_id=%student_id%]]" parameter="student_id"></query>
</queries>`
   
  >The id will be changed depending upon the number of queries. One can add validation query before insert, edit or delete data to check whether the data is valid to insert, edit or delete respectively or not. Validation is of two types – query and custom. For query type, the validation query is defined in the following way -`<validations>
<validation type="query">
<validationquery id="1" sql="[CDATA[select student_id from student_details where student_id=%student_id% and student_id=%current_login_user_id%]]" parameter="student_id,current_login_user_id" message="You cannot delete your own account."></validationquery>
</validation>
<validation type="query">
<validationquery id="2" sql="[CDATA[select sd.student_id from student_details sd,user_role ur where sd.student_id=ur.user_id and ur.role_id=\'2\' and sd.student_id=%student_id% and %current_login_user_id%!=\'superuser\']]" parameter="student_id,current_login_user_id" message="You cannot delete other Administrator accounts."></validationquery>
</validation>
</validations>`

  >If the data is not valid, then message is returned to the user. Custom validations are given in the following way`<validations>
<validation type="custom">
<validationquery id="1" classname="edu.ju.thesis.DateValidator" message="Start Date is Less than End Date"></validationquery>
</validation>
</validations>`

  >In this type of validations one should write java file. In the above example the DateValidator class file is called from edu.ju.thesis package. This custom validation class always implements of ValidatorFunction. validateadd is for custom validation for add, validateedit is for modify and validatedelete is for delete.
There is another tag named <action></action> for add, modify or delete. If there is some other conditions for adding, editing or deleting then a java file is required. Action is written in the following way.`<action sequence="after" actionname="thesis.customGroupCourseReg" > </action>`

  >Here customGroupCourseReg class is called from thesis package. In action type the sequence attribute is of three types – before, after and replace. If sequence is before then the action class is called before the query. If sequence is after then the action class is called after the query. If replace, then action class is called replacing the query, i.e., query is not executed.
This action class is always a subclass of CustomEditAction. AddAction is for custom validation for add, EditAction is for modify and DeleteAction is for delete.
In all query there is some name is in % % and the names are written in the parameter attribute. This is for the values written in the corresponding field (textbox, textarea etc.) The name should be similar to the column name and exactly this name should be written in the parameter attribute.
There are few special events which are supported by the DBGrid. These events can be used in the behavior section for that particular part id whose class is DBGrid–
  * ondblClickRow – This event is fired on double clicking any row
  * gridComplete – This event is fired after grid is completely loaded
  * loadComplete – This event is fired after the data is loaded in the grid
 
  >The example of DBGrid in an interface-`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`
`xmlns="http://learnityframework.org/"`
`xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"`
`id="UserCreation" title="LMS User Creation" type="Interface">`
`<configuration TemplateID="GridTreeNew"></configuration>`
`<structure>`
`<part id="main" class="label"></part>`
`<part id="userimage" class="inputfile"></part>`
`<part id="image_button_container" class="label"></part>`
`<part id="ShowProfileButton_Container" class="label"></part>`
`<part id="ShowProfileButton" class="button"></part>`
`<part id="batchusermsg" class="label"></part>`
`<part id="UploadButton" class="button"></part>`
`<part id="excelimage_container" class="label"></part>`
`<part id="excelimage" class="image"></part>`
`<part id="batchuser_container" class="label"></part>`
`<part id="batchuserlabel" class="label"></part>`
`<part id="batchuser_file_container" class="label"></part>`
`<part id="batchuser" class="inputfile"></part>`
`<part id="UploadButton_container" class="label"></part>`
`<part id="UserCreationAjaxComp" class="ajaxcomponent"></part>`
`<part id="usercreationgrid" class="DBgrid" caption=" Currently Defined User(s)"`
`sortname="student_id" sortorder="desc" searchOnEnter="false">`
`<column head="User Id" name="student_id" index="1" width="105"`
`editable="true" hidden="false" key="true" required="true">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="First Name" name="a.first_name" index="2" width="125"`
`editable="true" hidden="false" key="false" required="true">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Middle Name" name="a.middle_name" index="3"`
`width="125" editable="true" hidden="false" key="false" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Last Name" name="a.sname" index="4" width="125"`
`editable="true" hidden="false" key="false" required="true">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Age" name="a.age" index="5" width="55" editable="true"`
`hidden="false" key="false" required="false">`
`<edit type="text" size="10"></edit>`
`</column>`
`<column head="Experience" name="a.experience" index="6" width="120"`
`editable="true" hidden="false" key="false" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Educational Qualification" name="a.edu_status"`
`index="7" width="150" editable="true" hidden="false" key="false"`
`required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Gender" name="a.gender" index="8" width="105"`
`editable="true" hidden="false" key="false" required="true">`
`<edit type="select" editdomaintype="fixed" value="M:Male;F:Female"></edit>`
`</column>`
`<column head="Email Id" name="a.email_id" index="9" width="105"`
`editable="true" hidden="false" key="false" required="false" custom="true"`
`custom_func="CheckEmail">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Department" name="a.department" index="10"`
`width="105" editable="true" hidden="false" key="false" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Question Preferred" name="a.question_preffered"`
`index="11" width="50" editable="true" hidden="false" key="false"`
`required="false">`
`<edit type="select" editdomaintype="fixed" value="Yes:Yes;No:No"></edit>`
`</column>`
`<column head="Media Preferred" name="a.media_preffered" index="12"`
`width="150" editable="true" hidden="false" key="false" required="false">`
`<edit type="select" editdomaintype="fixed"`
`value="Video:Video;Audio:Audio;Text:Text"></edit>`
`</column>`
`<column head="Created By" name="b.student_created_by" index="13"`
`width="150" editable="false" hidden="false" key="false" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Date of Creation" name="b.date_student_created"`
`index="14" width="155" editable="false" hidden="false" key="false"`
`required="false">`
`<edit type="date" size="30"></edit>`
`</column>`
`<column head="Password" name="c.password" index="15" width="105"`
`editable="true" hidden="false" key="false" required="true">`
`<edit type="password" size="30"></edit>`
`</column>`
`<column head="Account Status" name="a.account_stat" index="16"`
`width="155" editable="true" hidden="false" key="false" required="true">`
`<edit type="select" size="30" editdomaintype="fixed"`
`value="Active:Active;Inactive:Inactive"></edit>`
`</column>`
`<column head="Self Registration" name="a.strself" index="17"`
`width="155" editable="true" hidden="false" key="false" required="false">`
`<edit type="select" editdomaintype="fixed" value="T:True;F:False"></edit>`
`</column>`
`<column head="Qualifier" name="qualifiertext" index="18"`
`width="155" editable="false" hidden="false" edithidden="false" key="false"`
`required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="User Qualifier" name="qualifiercombo" index="19"`
`width="155" editable="true" hidden="true" edithidden="true" key="false"`
`required="false">`
`<edit type="select" size="30" editdomaintype="query"`
`value="select lqualifier,lqualifier from`
`learning_qualifier"></edit>`
`</column>`
`<loadquery`
`value="select a.student_id,a.first_name,a.middle_name,a.sname,a.age,a.experience,a.edu_status,a.gender,a.email_id,a.department,a.question_preffered,a.media_preffered,b.student_created_by,b.date_student_created,c.password,a.account_status,a.strself,a.learning_style,d.lqualifier from student_details a left join learning_qualifier d on a.learning_style=d.lqualifier,student_creation_details b,student_password c where a.student_id=b.student_id and b.student_id=c.student_id and a.student_id !=\'superuser\' "></loadquery>`
`<delete>`
`<validations>`
`<validation type="query">`
`<validationquery id="1"`
`sql="[CDATA[select student_id from student_details where student_id=%student_id% and student_id=%current_login_user_id%]]"`
`parameter="student_id,current_login_user_id" message="You cannot delete your own account."></validationquery>`
`</validation>`
`<validation type="query">`
`<validationquery id="2"`
`sql="[CDATA[select sd.student_id from student_details sd,user_role ur where sd.student_id=ur.user_id and ur.role_id=\'2\' and sd.student_id=%student_id% and %current_login_user_id%!=\'superuser\']]"`
`parameter="student_id,current_login_user_id" message="You cannot delete other Administrator accounts."></validationquery>`
`</validation>`
`</validations>`
`<queries>`
`<query id="1"`
`sql="[CDATA[delete from student_creation_details where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="2"`
`sql="[CDATA[delete from student_password where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="3"`
`sql="[CDATA[delete from student_group_association where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="4"`
`sql="[CDATA[delete from student_details where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="5"`
`sql="[CDATA[delete from usergroup_course_registration where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="6"`
`sql="[CDATA[delete from user_course_registration where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="7"`
`sql="[CDATA[delete from user_forum_association where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="8"`
`sql="[CDATA[delete from sc_user_association where user_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="9"`
`sql="[CDATA[delete from user_role where user_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`</delete>`
`<add>`
`<validations>`
`<validation type="query">`
`<validationquery id="1"`
`sql="[CDATA[select student_id from student_details where student_id=%student_id%]]"`
`parameter="student_id" message="This User already Exists."></validationquery>`
`</validation>`
`</validations>`
`<queries>`
`<query id="1"`
`sql="[CDATA[insert into student_details(student_id,first_name,middle_name,sname,account_status,email_id,department,age,gender,strself,experience,edu_status,question_preffered,media_preffered,learning_style) values(%student_id%,%a.first_name%,%a.middle_name%,%a.sname%,%a.account_stat%,%a.email_id%,%a.department%,%a.age%,%a.gender%,%a.strself%,%a.experience%,%a.edu_status%,%a.question_preffered%,%a.media_preffered%,%qualifiercombo%)]]"`
`parameter="student_id,a.first_name,a.middle_name,a.sname,a.account_stat,a.email_id,a.department,a.age,a.gender,a.strself,a.experience,a.edu_status,a.question_preffered,a.media_preffered,qualifiercombo"></query>`
`</queries>`
`<queries>`
`<query id="2"`
`sql="[CDATA[insert into student_creation_details(student_id,date_student_created,last_modification_date,student_created_by) values(%student_id%,sysdate(),sysdate(),%current_login_user_id%)]]"`
`parameter="student_id,current_login_user_id"></query>`
`</queries>`
`<queries>`
`<query id="3"`
`sql="[CDATA[insert into student_password(student_id,password) values(%student_id%,%c.password%)]]"`
`parameter="student_id,c.password"></query>`
`</queries>`
`</add>`
`<modify>`
`<queries>`
`<query id="1"`
`sql="[CDATA[update student_details set first_name=%a.first_name%,middle_name=%a.middle_name%,sname=%a.sname%,account_status=%a.account_stat%,email_id=%a.email_id%,department=%a.department%,age=%a.age%,gender=%a.gender%,strself=%a.strself%,experience=%a.experience%,edu_status=%a.edu_status%,question_preffered=%a.question_preffered%,media_preffered=%a.media_preffered%,learning_style=%qualifiercombo% where student_id=%student_id%]]"`
`parameter="a.first_name,a.middle_name,a.sname,student_id,a.account_stat,a.email_id,a.department,a.age,a.gender,a.strself,a.experience,a.edu_status,a.question_preffered,a.media_preffered qualifiercombo"></query>`
`</queries>`
`<queries>`
`<query id="2"`
`sql="[CDATA[update student_creation_details set last_modification_date=sysdate() where student_id=%student_id%]]"`
`parameter="student_id"></query>`
`</queries>`
`<queries>`
`<query id="3"`
`sql="[CDATA[update student_password set password=%c.password% where student_id=%student_id%]]"`
`parameter="c.password,student_id"></query>`
`</queries>`
`</modify>`
`</part>`
`</structure>`
`<layout id="usercreationlay">`
`<part id="main"></part>`
`<part id="usercreationgrid" height="200" width="745" parent_id="main"></part>`
`<part id="image_button_container" parent_id="main"></part>`
`<part id="ShowProfileButton_Container" parent_id="image_button_container"></part>`
`<part id="excelimage_Container" parent_id="image_button_container"></part>`
`<part id="ShowProfileButton" parent_id="ShowProfileButton_Container"></part>`
`<part id="excelimage" height="30px" width="30px" parent_id="excelimage_Container"></part>`
`<part id="batchusermsg" parent_id="main"></part>`
`<part id="batchuser_container" parent_id="main"></part>`
`<part id="batchuserlabel" parent_id="batchuser_container"></part>`
`<part id="batchuser_file_container" parent_id="batchuser_container"></part>`
`<part id="batchuser" parent_id="batchuser_file_container"></part>`
`<part id="UploadButton_container" parent_id="batchuser_container"></part>`
`<part id="UploadButton" parent_id="UploadButton_container"></part>`
`<part id="UserCreationAjaxComp" parent_id="main"></part>`
`</layout>`
`<content id="usercreationcontent">`
`<part id="ImageUploadButton" valuetype="inline" value="Upload Image"></part>`
`<part id="ShowProfileButton" valuetype="inline" value="Show Profile"></part>`
`<part id="batchusermsg" valuetype="inline"`
`value="Upload Excel to create users in batch. Click on excel image to get the Excel Format"></part>`
`<part id="batchuserlabel" valuetype="inline" value="Batch User Creation : "></part>`
`<part id="UploadButton" valuetype="inline" value="Upload"></part>`
`<part id="excelimage" valuetype="reference" value="xlimage"></part>`
`</content>`
`<style id="UserCreationStyle">`
`<part id="batchusermsg" value="[CDATA[color: #0000FF;]]"`
`valuetype="inline"></part>`
`<part id="excelimage" value="[CDATA[cursor: pointer;]]"`
`valuetype="inline"></part>`
`<part id="image_button_container" value="row row-padding"`
`valuetype="reference"></part>`
`<part id="ShowProfileButton_Container" value="col-md-8 col-xs-8"`
`valuetype="reference"></part>`
`<part id="excelimage_Container" value="col-md-4 col-xs-4"`
`valuetype="reference"></part>`
`<part id="batchusermsg" value="col-md-12 col-xs-12 row row-padding" valuetype="reference"></part>`
`<part id="batchuser_container" value="row row-padding" valuetype="reference"></part>`
`<part id="batchuserlabel" value="col-md-4 col-xs-4" valuetype="reference"></part>`
`<part id="batchuser_file_container" value="col-md-4 col-xs-4"`
`valuetype="reference"></part>`
`<part id="UploadButton_container" value="col-md-4 col-xs-4"`
`valuetype="reference"></part>`
`</style>`
`<behaviour id="usercreationbehaviour">`
`<part id="UploadButton">`
`<event name="onclick" type="simple" function="upload_onclick"`
`valuetype="jsevent" resourceid="usercreationjs"></event>`
`</part>`
`<part id="ImageUploadButton">`
`<event name="onclick" type="simple" function="imageupload_onclick"`
`valuetype="jsevent" resourceid="usercreationjs"></event>`
`</part>`
`<part id="ShowProfileButton">`
`<event name="onclick" type="simple" function="showprofile_onclick"`
`valuetype="jsevent" resourceid="usercreationjs"></event>`
`</part>`
`<part id="excelimage">`
`<event name="onclick" type="simple" function="excelimage_onclick"`
`valuetype="jsevent" resourceid="usercreationjs"></event>`
`</part>`
`<part id="UserCreationAjaxComp">`
`<event name="ajax" type="simple" function="dummy" javaclass="ladminTree"></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="usercreationjs" href="usercreation.js"`
`valuetype="js"></resourceitem>`
`<resourceitem id="xlimage" href="Excel.gif" valuetype="image" />`
`</resource>`
`</interface>`
  
  * The snapshot of the screen –![acnt](https://github.com/diptenduLF/LFwiki/blob/master/images/user%20acnt.png)
  * The snapshot with edit pop up –![accnt](https://github.com/diptenduLF/LFwiki/blob/master/images/user%20acnt2.png)

 * Conditional Db Grid

  >This class is similar with ―DBGrid‖. The only difference is that it creates a drop down depending on which the data of the table is populated. The drop down is defined by ―selector‖. It is defined in the following way –`<selector id="group_id" class="combo" contentid="GroupUserRegContent"
behaviourid="GroupUserRegBehaviour" domaintype="query"
value="select a.group_id, a.group_name from student_group a"
gridrefresh="true"></selector>`
 
  >The domaintype of selector is either ―query‖ or ―fixed‖. If the domaintype is query then the query is written in the value attribute, Otherwise the options are defined in the following way -`<selectoroption name="student_id" value="User Id"></selectoroption>
<selectoroption name="name" value="User Name"></selectoroption>
<selectoroption name="marks" value="Marks Obtained"></selectoroption>`

  >contententid and behaviourid is the id attribute of <content> and <behaviour> respectively. If the value of one selector affects the selector, then affected selector id is given to the influence attribute of the first selector. Selector id should be added to the layout.

  * The example of Conditional DB Grid -`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`
`xmlns="http://learnityframework.org/"`
`xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"`
`id="GroupUserReg" title="LMS Group User Registration" type="Interface">`
`<configuration checkrole="true" TemplateID="Bootstrap"></configuration>`
`<structure>`
`<part id="BodyDiv" class="label"></part>`
`<part id="GroupNameLabel" class="label"></part>`
`<part id="GroupUserRegGrid" class="Conditionalgrid"`
`caption="Currently Registered Users For the Above Group" sortname="student_id"`
`sortorder="desc" gridnavbar="true">`
`<selector id="group_id" class="combo" contentid="GroupUserRegContent"`
`behaviourid="GroupUserRegBehaviour" domaintype="query"`
`value="select a.group_id, a.group_name from student_group a"`
`gridrefresh="true"></selector>`
`<column head="Group Id" name="group" index="1" width="150"`
`editable="true" hidden="true" key="true" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<column head="Student Id" name="student_id" index="2" width="150"`
`editable="true" hidden="false" key="true" required="false">`
`<edit type="select" size="30" multiple="true" editdomaintype="query"`
`value="select sd.student_id,concat(sd.first_name,\' \',sd.middle_name,\' \',sd.sname) from student_details sd,user_role ur where ur.user_id=sd.student_id and ur.role_id!=2"></edit>`
`</column>`
`<column head="User Name" name="first_name" index="3" width="500"`
`editable="false" hidden="false" key="false" required="false">`
`<edit type="text" size="30"></edit>`
`</column>`
`<loadquery`
`value="select a.group_id,a.student_id,concat(b.first_name,\' \',b.middle_name,\' \',b.sname) from student_group_association a, student_details b where a.group_id=%group_id% and a.student_id=b.student_id"></loadquery>`
`<delete>`
`<queries>`
`<query id="1"`
`sql="[CDATA[delete from user_forum_association where forum_id In (select forum_id from group_forum_association where group_id=%group%) and student_id=%student_id%]]"`
`parameter="student,group"></query>`
`</queries>`
`<queries>`
`<query id="2"`
`sql="[CDATA[delete from usergroup_course_registration where student_id=%student_id% and course_id In (select course_id from group_course_registration where group_id=%group%)]]"`
`parameter="student,group"></query>`
`</queries>`
`<queries>`
`<query id="3"`
`sql="[CDATA[delete from course_learner_login_info where course_id In (select course_id from group_course_registration where group_id=%group%) and student_id=%student_id%]]"`
`parameter="student,group"></query>`
`</queries>`
`<queries>`
`<query id="4"`
`sql="[CDATA[delete from calendar_authorization where calendar_id In (select calendar_id from calendar_group_association where group_id=%group%) and student_id=%student_id%]]"`
`parameter="student,group"></query>`
`</queries>`
`<queries>`
`<query id="5"`
`sql="[CDATA[delete from student_group_association where group_id=%group% and student_id=%student_id%]]"`
`parameter="group,student"></query>`
`</queries>`
`<queries>`
`<query id="6"`
`sql="[CDATA[delete from userscoinfo where unit_id in (select unit_id from unit_group_association where group_id=%group_id) and user_id=%student_id%]]"`
`parameter="group,student"></query>`
`</queries>`
`</delete>`
`<add>`
`<queries>`
`<query id="1"`
`sql="[CDATA[insert into student_group_association values(%group_id%,%student_id%)]]"`
`parameter="group_id,student_id"></query>`
`</queries>`
`<queries>`
`<query id="2"`
`sql="[CDATA[insert into`
`userscoinfo(user_id,unit_id,sco_id,launch,prerequisites,sequence,type,lessonstatus) values(%student_id%,(select a.CourseID from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),(select a.Identifier from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),(select a.Launch from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),(select a.Prerequisites from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),(select a.Sequence from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),(select a.Type from ItemInfo a,course_group_association b where a.CourseID=b.course_id and b.group_id=%group_id%),\'Not Submitted\')]]"`
`parameter="group_id,student_id"></query>`
`</queries>`
`<queries>`
`<query id="3"`
`sql="[CDATA[Insert into usergroup_course_registration(course_id, student_id, registration_by,registration_date,access_allowed_till,total_access_time) values ((select course_id from group_course_registration where group_id=%group_id%),%student_id%,(select access_allowed_till from group_course_registration where group_id=%group_id%),(select total_access_time from group_course_registration where group_id=%group_id%))]]"`
`parameter="group_id,student_id"></query>`
`</queries>`
`<queries>`
`<query id="4"`
`sql="[CDATA[Insert into user_forum_association(forum_id, student_id, registered_by) values ((select forum_id from group_forum_association where group_id=%group_id%),%student_id%,(select registered_by from group_forum_association where group_id=%group_id%))]]"`
`parameter="group_id,student_id"></query>`
`</queries>`
`<queries>`
`<query id="5"`
`sql="[CDATA[Insert into calendar_authorization(calendar_id, student_id) values ((select calendar_id from calendar_group_association where group_id=%group_id%),%student_id%)]]"`
`parameter="group_id,student_id"></query>`
`</queries>`
`</add>`
`</part>`
`</structure>`
`<layout id="GroupUserRegLayout">`
`<part id="BodyDiv"></part>`
`<part id="GroupNameLabel" left="0px" top="10px" position="absolute"`
`parent_id="BodyDiv"></part>`
`<part id="group_id" left="115px" top="8px" position="absolute"`
`parent_id="BodyDiv"></part>`
`<part id="GroupUserRegGrid" left="0px" top="50px" position="absolute"`
`parent_id="BodyDiv"></part>`
`</layout>`
`<content id="GroupUserRegContent">`
`<part id="GroupNameLabel" value="Group Name:" valuetype="inline"></part>`
`</content>`
`<behaviour id="GroupUserRegBehaviour">`
`</behaviour>`
`</interface>`
  * The output of the above xml is –![group](https://github.com/diptenduLF/LFwiki/blob/master/images/group%20user%20reg.png)