# XBS : an executable model-driven application development platform

(Updated on April 14, 2015)

## Why XBS?

 * Visually modelling application processes. Graphically design process flow, process interaction, and process lifecycle, for both UI and non-UI processes. XBS has proprietary process modeling diagram, which is not UML based. It is straightforward for people with or without programming background. It’s powerful and can replace all three UML behaviour diagrams. It can also be used as BPMN diagram. [#Screen_Shots]

 * XBS is execution model-driven development (MDD) platform. Different than code-generation MDD, XBS process diagrams are directly executed by XBS Application Server, at run time. There is no PIM, PSM, action languages, etc. as typical code-generation MDD.

 * XBS application is modularized and loosely-coupled. XBS application server provides off-the-shelf functions to applications at run-time, at module level: failover & load balance, distributed transaction, real-time tracing and execution profiling & monitor, etc. XBS provides a web console (which is developed using XBS), to manage XBS application server cluster.

 * Write once and use anywhere. Benefit from XBS loosely-coupled nature, XBS application can be deployed to any environment, from single machine to a large clustered computer farm on fly, without code change.

 
## What is XBS?

XBS is a generic application development platform, to design and execute dynamic, modular applications: from simple desktop application, web application, to large distributed enterprise system. XBS is a complete application development environment. It provides visual IDE, Application Server, application execution management console, and application unit-test framework. [#Architecture_Diagram]

XBS is a model-driven application development platform. XBS Application development cycle is straightforward: first, model application processes by using XBS graphical modeling tools. After that, to implement all the code nodes (if any) with chosen programming languages. 

XBS is an executable MDD. XBS process diagrams are executed by XBS Engine directly. In another word, ‘the model is the executable’. XBS Engine manages application models loading, remote calling, scheduling and failover, etc. Except that, application code talks to third party API directly. See the system stack diagram. [#System_Diagram]

XBS application process is modeled by a set of loosely coupled modules. XBS module is a software block which has full-featured interface: inputs, outcomes (each outcome has its own set of outputs), events (outlet & inlet) and calls (inlet and outlet). XBS interface is declarative and programming language neutral. XBS module, in turn, is modeled by (functional and code) nodes, sub modules, shared modules and edges, using XBS proprietary process modeling diagram, which can substitute all three URL behaviour diagrams: sequence, stat chat, and activity diagram .  See [#Screen_Shots]

XBS application is loosely coupled. It’s ‘loosely’ at runtime. That makes possible to distribute processes to multiple servers on fly. On the other hand, it’s ‘coupled’ at design time. Even a large enterprise system (with multiple web portals, web services and a bunch of backend jobs) can be developed as one XBS project and based on one set of modules; UI and server-side logics are modeled together in one project (even one module). That is different from loose-coupled SOA based applications, which is developed as multiple applications and become harder and harder to manage when system grows. For XBS, a Web Service is just a remotely executed module. On the other hand, an XBS module can be deployed as a Web Service to provide services to third party application.

XBS modules can be individually deployed, configured, executed among XBS application servers. XBS application can be very flexible to fit in various hardware environments. It can be deployed on from single machine to a large computer farm, without any code change. XBS application servers also provides off-the-shelf features for distributed application, like fail over, load balancing, distributed transaction, etc. For example, using XBS application execution console (or programmatically), a module can be configured to run on a predefined server set (‘Group’ in XBS). When need more computation power, just add machines to the server set. XBS cluster will automatically balance load to added machines.

## Platform Components

  * _<font color="blue">IDE</font>. XBS IDE provides graphical application processes modeling tools, to define components, nodes, events, resources, etc. and link them together to form application processes. Meanwhile, the IDE also provides programming environment to code for 'UI' and 'Code' nodes, with various programming languages, e.g. Java, C/C++, C#, Java Script etc. In addition, XBS IDE provides a <font color="blue">test harness infrastructure</font> to facility QA processes. It can help with both unit test of each component, and integration test, to make sure it covers all the code paths. _

  * _<font color="blue">Application server</font>. XBS provides rich-featured distributed application execution environment. It provides out-of-shelf features for enterprise class applications, like <font color="blue">failover, load balancing, events processing, distributed transaction, etc. </font>XBS supports diverse types of accesses: Web/Mobile portal, Web Services and back-ground jobs (scheduled or triggered by events, e.g. to periodically clean up log, database, events trapping, etc.). Multiple applications can simultaneously run on one set of XBS runtime environment. _

  * _<font color="blue">Cluster Management Console</font>. XBS provides a web-based, centralized management console for application execution.  Administrators can be remotely and centralized to configure, monitor and troubleshooting application's execution among all the clustered application servers. Remote management makes XBS platform <font color="blue">Cloud</font> ready: XBS application can be run (wholly or partially) in Cloud, and managed remotely by its owner. _

  * _<font color="blue">Test harness platform</font> to facility unit and integration test. XBS debugger can let developer put breakpoints in the process diagram, and enable step by step debugging at graphic level._
  
# Relationships with latest IT technologies

   * <font color="blue">Event-driven</font> XBS modeling is event-enabled. XBS execution environment handles local and remote, system and application events.

  * <font color="blue">Test-driven</font> XBS provides unit & integration test framework to facility test-driven development or QA process.
  
  * <font color="blue">SOA</font> XBS is Web Service enabled. A XBS module/node can be simply a proxy to call third party web service. On the other hand, a XBS module/node can be configured to provide SOAP interface to be invoked as a web service by other application. In addition, XBS execution environment provides SOA infrastructure for applications.

  * [https://en.wikipedia.org/wiki/Grid_computing Grid Computing] XBS platform can connect to a Grid environment, to support massive distributed computing applications.

  * <font color="blue">Business Process Management (BPM)</font> XBS is an excellent BPM application development platform: XBS modeling can be used as a foundation for domain-specific modeling; XBS execution environment provides many off-the-shelf features for BPM applications, e.g. monitor, analyze, events trap, etc.
 

## Architecture advantages

As shown in Figure [#Architecture_Diagram], XBS application is made up by a set of loosely coupled components. Each components can be individually deployed on servers in a heterogeneous <font color="blue">computer farm</font> environment. Blessed by that architecture, XBS brings significant advantages for application development and execution:

  * <font color="blue">Highly scale-able</font>.  At design time, XBS application scales smoothly and easily from an initial project to a full enterprise-wide program. At runtime,  XBS application throughout can be easily scaled up by adding more application servers and deploying more instances of bottle-necking modules. XBS does load-balancing between them. 

  * <font color="blue">Highly available</font>. Because XBS does fail-over and load balancing among instances of modules, application servers can be shut down with zero application down time.

  * <font color="blue">Highly reliable</font>. XBS application is transaction protected.
  
  * <font color="blue">Highly customize-able and extendable and support template programming</font>. Application can purposely design some modules to be customized by application consumers. They can also re-implement some module to extend the application's functionality. One module can be big as a sub-system. XBS developers can make *templates* for vertical applications, such as a telecom or healthcare framework that includes pre-defined processes, rules, dashboards and user screens that need only to be customized for use.

  * <font color="blue">Highly flexible</font> with IT environment. XBS application is develop once and fit all. XBS application can be deployed onto from single machine to a large size of server farm environment, without code change. Application can be configured at module level on a specific machine or network. For example, resources extensively accessing modules can be deployed close to the resource (i.g. same sub-net or on the same machine), or computation extensive modules to a CPU-powerful machine,  to obtain most optimized performance.

  * <font color="blue">Highly dynamic and lower cost of ownership</font>. Except Code nodes, most of application logic is modeled by graphical tools and transformed to execution by XBS. That accelerates the lifecycle of application development. XBS application is agility and dynamic. XBS modules is well-encapsulated and reusable. Application processes can be easily revised (by simply re-linking modules or nodes), to response ever-changing requirement. XBS application can employ XBS event facilitates to be self-tuned also. 

  * <font color="blue">XBS IDE is visualized and easy to use.</font> For program coding, there is not XBS proprietary programming language or script to learn. XBS 'Code' nodes can be coded using different existing programming languages, to meet development team's skill sets, or by mandatory requirement to interface with legacy system (e.g. only C/C++ API available). Calls between nodes are handled by XBS run time. They can be easily changed between synchronized and asynchronized. So, for example, to XBS developer, Java node calls C/C++ node in the same way of calling a Java node, there is no need JNI programming effort. UI codes can use any web UI frameworks, jQuery, Extjs, Mootools, etc. UI designer has flexible to build multiple set of nodes for different kind of devices, e.g. web browser or Mobile device. And they are sharing the same set of code nodes. In addition, UI designers can work on UI nodes and meanwhile, programmers work on code nodes. XBS has zero learning curve for experienced developers. There is no 'XBS script or XBS language" such thing.

  * <font color="blue">Effective project management.</font> Since application is split into modules and nodes, project manager can balance the work load to team members at more granularity. It's also easier and more accurate for project manager to measure risk and effort; estimate project size, complexity and progress; set mile stone and collaborates with QA team.  

  * <font color="blue">XBS IDE is visualized and intuitive.</font> It makes possible for other project stakeholders (business analyzer or architects) to use the IDE, to design, review and analyze the application processes. On the other hand, coders use the IDE to implement application module's nodes, using their favorite programming languages. IDE provides native programming language environment for coding. XBS provides code assistance and syntax check. Any interface changes will be captured in code. That make sure node's implementation and interface are always synced.
   
  * <font color="blue">XBS application server provides rich off-the-shelf features </font>to facilitate application run-time. Those are most demanding features for large enterprise class applications, like fail-over, load balance, distributed transaction, cross-server communication, task scheduler, event trap etc. That would significantly reduce application development effort, and time to market.
 
  * <font color="blue">XBS also provides a centralized web-based admin console</font> for application execution. It is used to deploy, configure, schedule, on/off, monitor and trouble shooting, analyze application execution. [#XBS_admin_console]

  * <font color="blue">XBS applications are cloud ready,</font> due to XBS provided centralized management capability. XBS run time is good candidate for application cloud hosting. XBS application can be run (wholly or partially) on Cloud, and be managed by application owner from remote.


## Architecture Diagram
<img src="http://xbs-application-development-platform.googlecode.com/files/xbs%20architecture%20diagram.jpg" width="500" />

## Screen Shots
===1. A typical application module===
_The following screen shot exhibits a typical application logic flow: init some required system components (e.g. authentication process), show user a log on page, it calls 'authentication' module/process to validate user according to user typed credentials. If 'success', it get user type from authentication module and then return to XBS engine. XBS engine, as design, opens corresponding window according to user type. If 'failed', it return 'Exception' outcome with error message to XBS (or you can easily add a UI node to show the message to user.)_

<img src="http://https://xbs-application-development-platform.googlecode.com/svn/wiki/images/Main.png" width="500" />


===2. The 'Auth' module===
_The following screen shot shows the 'authentication' module of the above application. It's started by 'init' node of the above main module. It, in turn, starts authentication db and ready for two external calls: DoAuth and GetUserInfo. The module is long time process and designed to provide services to other process. It also generate an OUT event when auth db got problem. The event is delivered to other processes as designed._

<img src="https://xbs-application-development-platform.googlecode.com/svn/wiki/images/auth.png" width="500" />


===3. Connection Configure===
_The following screen shot depicts the connection configure window. Node's inputs can be configured to be some from last node's outputs, some from module data, or hard-coded value.

<img src="https://xbs-application-development-platform.googlecode.com/files/property%20window.PNG" width="500" />


===3. App main module in expanded view===
_The following screen shot shows the same application module as the above one, with its login module expanded in-line. That should be convenient for application processes review. _

<img src="http://xbs-application-development-platform.googlecode.com/files/app%20main%20large.PNG" width="500" />


===XBS admin console===
_The follow is a screen shot of XBS Admin Console (It self is a web application developed with XBS framework). On the left panel, it shows the lists of application modules and all the application servers. Each module has a deployment number. If more than 2, means the module is deployed on multiple workers and therefore, it has fail-over and load balancing. If it's "1", the module may become single failure point. The right side of window exhibits the monitor/profile tab. It provides valuable application execution statistics data: the usage of module instance pool, number of calls and average execution time for each module and its nodes, etc._

<img src="http://xbs-application-development-platform.googlecode.com/files/xbsadmin_monitor_highlighted.PNG" width="500" />


===Demo: a three-page wizard module===

<img src="https://xbs-adf.googlecode.com/files/wizard%20demo%20module.PNG" width="500" />


===Screen shot: The 'Main' module of XBS Cluster Management Console===
_XBS Cluster Management Console itself is a XBS application. The following is the screen shot of its 'main' module._

<img src="https://xbs-application-development-platform.googlecode.com/svn/wiki/images/XBS%20Server%20module.png" width="500" />


## Give it a try? 
I setup a XBS development environment on a test machine. I also create a couple of demo XBS applications: one is a desktop UI application, one is non-UI application (calculate PI) and one is a web application (url is 'http://localhost:5555/test' )

You may log onto the machine with [http://www.teamviewer.com/en/index.aspx TeamViewer]. Partner Id is '426124994' and password is 'xbstrial'.

You may browser/modify those demo applications, and run them using Eclipse's 'Debug' menu.

If you should have any difficulties, you can contact me at: liu_xiao_kang@hotmail.com


