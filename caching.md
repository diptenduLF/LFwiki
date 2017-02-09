**1.Overview**
   >Caching is a technique that provides increased performance and scalability for Web based applications and web sites. In the early days of the World Wide Web, the Internet consisted of primarily static information. Since those early years, the Internet has changed dramatically—and continues to change as content becomes increasingly dynamic.
   
  >HTML and graphic files represent static content because they look identical each time users download them into their browsers. The Web server locates the requested files on its hard drives and pushes those files directly to the clients.

  >Dynamic content is displayed information that can change with every user request. This content is based on a set of instructions executed on the server side. When the Web server locates the requested instruction file on the local hard drive, it then runs these instructions inside web container software (often called application server) that is capable of executing those instructions. The result of running the instructions is HTML code. This dynamically created HTML is then sent to the browser for display.

  >Dynamic content puts a heavy load on the Web server since it requires immense processing power to produce dynamic results for thousands of visitors in real time. Database servers also work hard to provide the data to these Web application servers.

   >A web cache is an information technology for the temporary storage (caching) of web documents, such as HTML pages and images, to reduce bandwidth usage, server load, and perceived lag.

  >Clients (browsers) can receive frequently requested static HTML files much faster if they have been stored in a specific Web content cache. Caching allows static files to be quickly located in the cache rather than downloaded each time from the Web site. The same approach applies if consecutive requests for a particular dynamic page produce identical results. In this case, output also can be stored in a cache and set aside for future use. Rather than reproducing the HTML version for each request, the server can send the page from its cache, which avoids repetitive work and saves processor cycles for more productive work.

  >Server side caching technique improves performance and scalability by executing only necessary code on the Web application server or in the required database. Once the HTML has been saved to the Web content cache, the web server detects subsequent requests to the same dynamic page, intercepts the requests, and immediately responds with the cached output.

  >The LF supports server side caching as an integral part of the framework. Currently the entire page is cached with provision for selective caching of data grids. The details are given below.

**2.Functionality**

   >The following steps are required to set up caching in the LF -

  * There is a single configuration parameter that may be used to enable or disable caching. This parameter is named InterfacingCaching and is present in the portal.properties file that is placed in the WEB-INF/classes folder. This parameter may take on the values true or false. If the value is true then caching is enabled. The caching of an interface implies not only caching of the HTML markup corresponding to the interface, but also the caching of various resources that are dynamically loaded by the HTML markup such as Images, CSS files, and JS files.

 >For caching of data grid components, there is a separate parameter GridCaching. Caching of data grids will only occur if this parameter is true.`InterfaceCaching=true
GridCaching=false`

  * The actual cache is defined using the Cache Definition screen of the CoreAdmin module.![cache](https://github.com/diptenduLF/LFwiki/blob/master/images/Cache%20Definition%20screen.png)

 >Here the following properties are used to setup the cache:
 
  Field  | Description
  ------------ | -------------
  Cache Name | The name of the cache
  Type | Either In process or Remote. Currently implementation only supports In process
  Max Elements | The maximum no. of elements that may be stored in the cache
  Overflow To Disk | Either True or False. When an element is added to a cache and it goes beyond its maximum memory size, an existing element is either deleted, if overflow to disk is False, or written to disk, if overflow is True.
  Eviction Policy | LFU/LRU/FIFO. If overflow is enabled, a check for expiry is carried out. If it is expired it is deleted; if not it is spooled. The eviction of an item from the memory store is based on this attribute.
      | Least Recently Used (LRU)—LRU is the default setting. The last-used timestamp is updated when an element is put into the cache or an element is retrieved from the cache with a get call.           
      | Least Frequently Used (LFU) —For each get call on the element the number of hits is updated. When a put call is made for a new element (and assuming that the max limit is reached for the memory store) the element with least number of hits, the Less Frequently Used element, is evicted.
      |First In First Out (FIFO) — Elements are evicted in the same order as they come in. When a put call is made for a new element (and assuming that the max limit is reached for the memory store) the element that was placed first (First-In) in the store is the candidate for eviction (First-Out).
 Disk Persistent | Either True or False. The disk store provides a thread-safe disk-spooling facility that can be used for either additional storage or persisting data through system restarts.
 Time to Live(seconds) | The maximum number of seconds an element can exist in the cache regardless of access. The element expires at this limit and will no longer be returned from the cache. The default value is 0, which means no TTL eviction takes place (infinite lifetime)
 Time to Idle(seconds) | The maximum number of seconds an element can exist in the cache without being accessed. The element expires at this limit and will no longer be returned from the cache. The default value is 0, which means no TTI eviction takes place (infinite lifetime)
 Eternal | Either True or False. When set to true, overrides timeToLive and timeToIdle so that no expiration can take place    
 Expiry Thread Interval(seconds) | Expired elements are eventually evicted to free up disk space. The element is also removed from the in-memory index of elements. One thread per cache is used to remove expired elements. This optional attribute sets the interval between runs of the expiry thread. The default value is 120 seconds. Setting this attribute to a low value can cause excessive disk-store locking and high CPU utilization.
 Disk Store Path | If the cache requires a disk store but none is configured, a default directory is used and a warning message is logged to encourage explicit configuration of the disk store path. Legal values for the path attribute are legal file system paths. For example, for Unix: /home/application/cache. The following system properties are also legal, in which case they are translated: user.home - User's home directory; user.dir- User's current working directory; java.io.tmpdir - Default temp file path. Subdirectories can be specified below the system property, for example: user.dir/one
   Default | Yes or No; whether this cache is the default cache or not. There can be only one default cache.

 >Multiple caches may be defined using the above mentioned CoreAdmin screen. Only one of them may be set as the default cache.

 >Note that even if the caches are defined using the CoreAdmin screens, caching will not work unless the InterfaceCaching attribute is set to true as mentioned above.

 
* Usage of the caches defined above by the application may be done using the following mechanisms –
  
   * Define a default cache using the mechanism mentioned above. This default cache will then be used for all caching purposes for all the interfaces.
   * Define a cache using the ApplicationTemplate mechanism-`<application-defaults>
<configuration-section>
<attribute name="cacheName" defaultvalue="AppCache"></attribute>
</configuration-section>`All interfaces associated with the above Application Template will use a cache named AppCache. This cache will have to be defined using the CoreAdmin module as mentioned above. Thus it is possible to associate a group of interfaces with a particular cache.
   * Define a cache in the Interface XML file:`<configuration cacheName="AppCache" …..></configuration>`
   * This cache will have to be defined using the CoreAdmin module as mentioned above. This mechanism enables to associate each interface with a different cache.

* Once a cache is working it is possible to perform various operations on the cache using the Cache Management screen of the CoreAdmin module.![lf cache](https://github.com/diptenduLF/LFwiki/blob/master/images/LF%20Cache%20Status.png)
  >The Refresh button is used to update the usage statistics of the cache on the screen. The Clear Cache button may be used to clear the current contents of the cache. The Shutdown Cache button may be used to shut down the cache at runtime so as to disable caching; in this case caching will not work for the interfaces associated with this cache (or all interfaces if this cache is the default cache) even if the InterfaceCaching attribute is set to true. This button thus provides a mechanism to disable caching without having to stop the Application Server and restarting it after setting the InterfaceCaching attribute to false.

**3.Implementation Details**
   >The ehcache library (http://www.ehcache.org/ ) is used in implementing caching support in the LF. The ehcache JAR is placed in the WEB-INF/lib folder.

   >Caching support is provided in the LF by the various front controllers such PortalServlet. All front controllers in the LF are caching aware. If caching is enabled then the front controllers first check the cache for existence of the requested resource (e.g., interface or image) in the cache. If the resource exists in the cache then it is fetched from the cache and sent to the browser. If the resource is not found in the cache then it is written to the cache and then sent to the browser so that subsequent requests for the same resourcemay be served from the cache. The following front controllers are cache aware -
   
   * PortalServlet
   * ResourceImage
   * ResourceJS
   * ResourceCSS
   * xmlcreator
   * DBGridQueryEditorServlet
   
   
 
>The first 4 of the above list read the IntefaceCaching configuration paremeter while the last 2 reads the GridCaching configuration parameter.

 >The comv2.aunwesha.param.CoreAdminInitHostInfo class performs various initializations for the LF and is loaded first by the Application Server (this class is a servlet defined with load-on-startup value of 1 in the web.xml). This class reads the InterfaceCaching property from the portal.properties file and sets the value in the servlet context. It also reads the name of the Default Cache (if it is defined) from the CoreAdmin database schema and also sets it in the servlet context. It then calls the InitialiseCacheDataFromTemplate function of the InterfaceCachePojo class. At the end it saves the instance of the InterfaceCachePojo to the servlet context.

  >The interfaceenginev2.InterfaceCachePojo class is used to perform cache management functions. It reads the CoreAdmin database schema and sets up the various caches using the ehcache CacheManager class. This class provides the various functions that are used by the front controllers for reading from and writing to the cache.

  >Cache key computation: Reading and writing to a cache requires a key that is used as the unique index of the value to be read or written. The various front controllers generate the appropriate key and use it when a value is to be first written to the cache or subsequently read from the cache. For pages served by the PortalServlet front controller the key is generated as a string that is the concatenation of the interface id and the user id. The user id is required since the same interface xml may be associated with different markup based on the role of the user (with the user id being mapped to a role). The ResourceImage, ResourceJS and ResourceCSS front controllers compute the cache key as a string that is the concatenation of the interface id and the resource id of the image, JS or CSS resource. The xmlcreator front controller computes the cache key as a string that is the concatenation of the interface id, part id, and the current page of the DBgrid or Conditionalgrid component. The DBGridQueryEditorServlet front controller (used for Conditionalgrids) computes the cache key as a string that is the concatenation of the interface id, part id, current page of the Conditionalgrid, and the namevaluepair of the selector (combo).

  >The 2 CoreAdmin servlets that provide support for cache definition and cache management are respectively:
   * coreadministrationv2.sysmgmt.CacheDefinition.java - This servlet calls the function coreadministrationv2.dbconnection.DatabaseLayer.addCacheDefinition for writing the cache definition to the database. The name of the Framework schema table is cache_definiton.
   * coreadministrationv2.sysmgmt.CacheManagement.java - This servlet uses the ehcache library functions to manage the cache at runtime.
   