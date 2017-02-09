**1.Overview (Single Page applications)**
  >Few years back each request in the websites reloads the page to display the response of the request. The concept of single page applications (SPA) breaks this traditional approach. It says reloading a page is not required until and unless user refreshes manually(Reference [ 14 ]).SPA provides the experience of a website like a native desktop application. The data in the website changes as per the request but the page does not reload. It hides the server round trip from the user. The basic implementation idea is to retrieve the data by an AJAX request and load the data in the page by the JavaScript.

  >Term Single-page application applies only to websites and web applications. It simply points to the fact that navigation between different screens of the website is achieved without loading a different webpage in the browser. Classic example is Gmail - when user clicks on a message in his/her inbox, browser stays on the same webpage, but JavaScript code hides the inbox and brings the message body on the screen(Reference [ 15 ]).

**2.Related work**
  >AngularJS is a well-known JavaScript framework which provides single page application behaviour(Reference [ 16 ]).It has a concept like route provider for providing the same. It needs to be configured like -`var singlePageApp= angular.module('singlePageApp', ['ngRoute']);`
`// configure`
`singlePageApp.config(function($routeProvider) {`
`$routeProvider`
`.when('/test', {`
`templateUrl : 'pages/test.html',`
`controller : 'testController'`
`})`
`.when('/test1', {`
`templateUrl : 'pages/test1.html',`
`controller : 'test1Controller'`
`});});`

  >The AngularJS application should have a master page which would contain common data like headed, footer and a part for the different page. The code should be like -`<!-- header.html -->`
`...`
`<!-- INJECTED PAGE AREA -->`
`<div id="main">`
`<!-- angular templating -->`
`<!-- this is where page will be injected -->`
`<div ng-view></div>`
`</div>`

  >Now when a request will be made for the 'test' URL then the corresponding html page 'pages/test.html' will be returned by the route provider and this page will be injected in the '<div ng-view></div>' part. Then if another request is made for ‗test1‘ URL then ‗'pages/test1.html‘ will be returned and will be injected in the same place replacing the old page. The main page will not be reloaded, only the part of the page will be changed. From the user point of view as the page does not reload so it seems like a native app.

**3.Functionality**

  >LF provides the power of SPA through interface fragment. It is same as the interface. It has all the power which an interface has except that it cannot have a configuration section. It does not have its own head/body. It is inserted in the page which is created by some other interface xml. Some event in the parent interface loads the interface fragment. Same interface fragment can be loaded in any number of interfaces. It saves the developer from repetitive coding. An example will help to understand the concept better. The home page of a learning management system –
 
 >![interface fragment example](https://github.com/diptenduLF/LFwiki/blob/master/images/interface%20fragment%20example.png)

 >It has several tabs like – Unit, Forum, Assessment, and Notice. Now clicking on any of the tab will not reload the page. Only the content in the below box will be changed with the respective data. Clicking on forum will load the forum data in place of unit but the page will not reload. The interface fragment is defined as –`<interface xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://learnityframework.org/"
xsi:schemaLocation="http://learnityframework.org/ http://ip:port/contextroot/xsd/Interface.xsd"
id="PortalUnit" title="Unit Grid on LMS Portal" type="InterfaceFragment">`
The other sections are exactly same as of the interface.

**4.Implementation Details**

  >The part of the interface of the homepage –`<structure>`
`--`
`<part id="mainsub" class="label"></part>`
`--`
`<part id="unitlink" class="tab"></part>`
`<part id="forumlink" class="tab"></part>`
`<part id="assessmentlink" class="tab"></part>`
`<part id="noticelink" class="tab"></part>`
`</structure>`
`<layout id="Portallayout">`
`--`
`</layout>`
`<content id="Portalcontent">`
`--`
`</content>`
`<style id="Portalstyle">`
`--`
`</style>`
`<behaviour id="Portalbehaviour">`
`--`
`<part id="unitlink">`
`<event name="onclick" type="simple" function="unit_onclick" valuetype="inline" resourceid="accmainjs"></event>`
`</part>`
`<part id="forumlink">`
`<event name="onclick" type="simple" function="forum_onclick" valuetype="inline" resourceid="accmainjs"></event>`
`</part>`
`<part id="assessmentlink">`
`<event name="onclick" type="simple" function="assessment_onclick" valuetype="inline" resourceid="accmainjs"></event>`
`</part>`
`<part id="noticelink">`
`<event name="onclick" type="simple" function="notice_onclick" valuetype="inline" resourceid="accmainjs"></event>`
`</part>`
`--`
`<part id="accloginajax">`
`<event name="ajax" type="simple" function="dummy" javaclass="Portal"></event>`
`</part>`
`</behaviour>`
`<resource>`
`<resourceitem id="accmainjs" href="mainpage.js" valuetype="js"></resourceitem>`
`--`
`</resource>`
`</interface>`

  >Now, each of the tab calls different method of the mainpage.js in the behaviour section when the corresponding tab is clicked. Clicking on the ―Unit tab, unit_onclick function is called. The JavaScript code for unit_onclick function in the mainpage.js –`function unit_onclick(){`
`--`
`PortalEngine.getInterfaceFragment("LMSPortal","PortalUnit",setFragUnit);`
`}`
`function setFragUnit(vstring){`
`setFragment("mainsub",vstring);`
`--`
`}`The unit_onclick function calls a method of the LF‘s PortalEngine class. The method is named as ―getInterfaceFragment. It takes three parameters as input - the parent interface id, the child interface id and the call back function. This function returns the child interface‘s HTML if it is a fragment. This HTML is sent to the call back function as the parameter. The call back function calls the LF‘s setFragment function which is defined in the LearnityUtil.js file. This function put the html in the mentioned area. Here mainsub is the id of the element where the interface fragment‘s html needs to be inserted. This element has to be present in the parent interface. Still the implementation of interface fragment has dependency on the developer end. We will try to move it into the LF. So that user does not need to write the JavaScript codes for fetching the interface fragments.