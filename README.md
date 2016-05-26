# XBS -- an PML based, model-driven application development tools & execution platform

*(Updated on February 2nd, 2016)*

## Table of content
 * [What is PML?](#WhatIsPML) 
 * [PML vs UML?](#PMLvsUML)
 * [What is XBS?](#WhatXBS)
 * [Architecture Advantages](#Advantages)
 * [Screen Shots](#ScreenShots)
 * [Want to give it a try?](#demo)

## <a name="WhatIsPML"/>What is PML?
PML is graphic process-oriented software modeling language. The mindset of PML is: software system or applications can be modeled with a set of collaborated and relative independent processes. A structured process can be further modeled by sub processes, so on and so forth. 

PML uses one diagram to model all behaviors of a software process: control-flows, message(object)-flows and event-flows. PML process node has one Input port (it is also process starting point), multiple inlet/outlet Call ports, inlet/outlet Event ports, and Outcome ports. Where, Input and Outcome ports are control-flow edges; Call ports are bi-direction message-flow edges; Event ports are unidirectional message-flow edges. PML integrates modeling of UI together with back-end processes.

PML models are directly executable, by PML execution engine. Because PML application is modular, PML execution environment could provides off-the-shelf functionalities to application, such as process based profiling; fail-over and load-balancing at process granularity; dynamic on/off logging of a process's input/outcome (without coding it); single instance a process across the whole system; specific a power machine to run the cpu-hog processes; computing resources allocation, etc. 

The following is the PML's UML meta model diagram:
<img src="https://github.com/KenXBS/XBS/blob/master/images/PML%20XML%20class%20diagram.png" width="800" />

The following is an application sample, a web sign-on process diagram:
<img src="https://github.com/KenXBS/XBS/blob/master/screenshot/Sample%20Login%20process.png" width="800" />

The diagram shows a process which involves both UI and server-side components. The process starts with <<initExtJS>> node, which initializes a JavaScript framework on browser. If it's succeeded, it shows a login form where user keys in user's credentials. When user clicks on 'sign on' button, the process will be routed to the server-side 'auth' process, to authenticate user's credentials. The Auth process may end up with three possibilities,
success, failed, or blocked (two many failures). According to its outcome, process will be routed to different corresponding following process, either show a message or open user's desktop. The following is the top application diagram:
<img src="https://github.com/KenXBS/XBS/blob/master/screenshot/web%20app%20demo.png" width="800" />
When the web application starts, it starts the <<serverend>> process at server-side, which keeps running and provides services (e.g. authentication) to other processes. Note, there is no raw Ajax to code. Communications between node to node, including UI to back-end are handled by PML execution platform. 

## <a name="PMLvsUML" />PML vs UML
PML and UML are both Object-Oriented graphic modeling language. But they bear different modeling idea. UML uses an Unified way (i.e. class-based) to model all kinds of software entities, data or behaviors. PML, in the opposite, applies different modeling semantics for different type of software objects. For example, for application data, use class-based modeling, same as UML does; for application behaviors, PML provides a specific set of graphic symbols or notations. According to PML's thought, application has behaviors, behaviors manipulate data. PML is used to model things, e.g. data, processes, events, roles, transactions, etc. And UML is to model program. 

Another significant difference of UML and PML is: UML is code-generation and PML is directly execution on models. PML through its execution platform to provide off-the-shelf functionalities to its applications.  

The follow is a table to list the various difference of UML and PML:
<table><tbody>
<tr>
	<th>PML</th>
	<th>UML</th>
</tr>
<tr>
	<td>Modeling different things in different manner. </td>
	<td>One set of modeling notations for everything. </td>
</tr>
<tr>
	<td>One diagram one process. All behaviors of a process is modeled within one diagram.</td>
	<td>Has a few type of diagrams, some are only for control-flows, some only for message-flows. some only for event-flows. To model event a simple process, need a couple diagrams. To get a whole picture of behaviors of a process, need put those puzzle pieces together. Harder to model, review and debug</td>
</tr>
<tr>
	<td>UI and back-end process can model together and consistently.</td>
	<td>UML is developing UI modeling spec. Wondering how can be used together with back-end process modeling?</td>
</tr>
<tr>
	<td>Encourage collaboration from all kinds of project stakeholders, as PML model diagram is intuitive.</td>
	<td>Not intuitive for non-programmers.</td>
</tr>
<tr>
	<td>PML models are interface-based and self-contained. PML encourages to make each model more generic and be reused in source or binary form. For example, it's easy to develop a domain specific model library. </td>
	<td>XML behavior diagram is hardly (or not straightforward) to be reused.</td>
</tr>
<tr>
	<td>No decision node. PML process model supports multiple outcomes. Control flow routes based on the outcome of a process directly. No hassles of encoding and decoding of outcomes.</td>
	<td>UML Activity node has only one outcome edge. Developers have to merge (encode) from multiple outcomes to one, at end of sub activity, and after, decode back from one outcome and recover to multiple outcomes, to be able to route.</td>
</tr>
<tr>
	<td>Direct-execution on models. WYSIWYG(what you see is what you get). Its execution environment can provide off-the-shelf functionalities to application, like cluster environment, fail-over and load-balancing, hot swap, dynamic profiling and tracing, dynamic computing resources allocation, etc. All those can be done in flexible granularity, in unit of model. </td>
	<td>Code generation. Modeling information lost in final executable. No way to provide useful functionalities to application based on application models.</td>
</tr>

</tbody></table>


## <a name="WhatIsXBS" /> What is XBS?

XBS is a PML based model-driven application development tools and application execution environment. XBS is also a RAD (Rapid Application Development) environment.

<img src="https://github.com/KenXBS/XBS/blob/master/images/xbs%20architecture%20diagram.jpg" width="800"/>


It provides: 

  * <font color="blue">IDE</font>. XBS IDE is a PML based graphical modeling tools, to model data, processes, events, roles, transactions, resources, 
etc. Meanwhile, the IDE provides programming environment to implement UI and Code logics, with various programming languages, like Java, C/C++, C#, Java Script etc. In addition, XBS IDE provides a <font color="blue">test harness 
infrastructure</font> to facility QA processes. It can help with both unit test of each model, and integration test, to make sure it covers all 
the code paths.

  * <font color="blue">Application execution engine</font>. It's a single-machine application execution engine. That's API based, so it can be embedded into customer applications. The engine can run different type of applications, like web/desktop application, web service or back-ground jobs.


  * <font color="blue">Clustered Application Server (CAS)</font>. It provides a clustered computing environment and a web based cluster management console.  XBS CAS can run multiple and various types of applications. Through cluster manager, administrator can remotely configure, monitor, load-balance, diagnostic application executions, at module granularity.


## <a name="Advantages" />Architecture advantages

As shown in Figure [#Architecture_Diagram], XBS application is modular and physically made up by a set of loosely coupled modules. Each module can be individually 
deployed on servers in a heterogeneous <font color="blue">computer farm</font> environment. Blessed by that architecture, XBS brings significant 
advantages for application development and execution:

  * <font color="blue">Highly scale-able</font>.  At design time, XBS application scales smoothly and easily from an initial project to a full 
enterprise-wide program. At runtime,  XBS application throughout can be easily scaled up by adding more application servers and deploying more 
instances of bottle-necking modules. XBS does load-balancing between them. 

  * <font color="blue">Highly available</font>. Because XBS does fail-over and load balancing among instances of modules, application servers can be 
shut down with zero application down time.

  * <font color="blue">Highly reliable</font>. XBS application is transaction protected.
  
  * <font color="blue">Highly customize-able and expandable and support template programming</font>. Application can purposely design some modules to 
be customized by application consumers. They can also re-implement some module to extend the application's functionality. One module can be big as a 
sub-system. XBS developers can make *templates* for vertical applications, such as a telecom or healthcare framework that includes pre-defined 
processes, rules, dashboards and user screens that need only to be customized for use.

  * <font color="blue">Highly flexible</font> with IT environment. XBS application is develop once and fit all. XBS application can be deployed onto 
from single machine to a large size of server farm environment, without code change. Application can be configured at module level on a specific 
machine or network. For example, resources extensively accessing modules can be deployed close to the resource (i.g. same sub-net or on the same 
machine), or computation extensive modules to a CPU-powerful machine,  to obtain most optimized performance.

  * <font color="blue">Highly dynamic and lower cost of ownership</font>. Except Code nodes, most of application logic is modeled by graphical tools 
and transformed to execution by XBS. That accelerates the life-cycle of application development. XBS application is agility and dynamic. XBS modules is 
well-encapsulated and reusable. Application processes can be easily revised (by simply re-linking modules or nodes), to response ever-changing 
requirement. XBS application can employ XBS event facilitates to be self-tuned also. 

  * <font color="blue">XBS IDE is visualized and easy to use.</font> For program coding, there is not XBS proprietary programming language or script 
to learn. XBS 'Code' nodes can be coded using different existing programming languages, to meet development team's skill sets, or by mandatory 
requirement to interface with legacy system (e.g. only C/C++ API available). Calls between nodes are handled by XBS run time. They can be easily 
changed between synchronized and a-synchronized. So, for example, to XBS developer, Java node calls C/C++ node in the same way of calling a Java node, 
there is no need JNI programming effort. UI codes can use any web UI frameworks, jQuery, Extjs, Mootools, etc. UI designer has flexible to build 
multiple set of nodes for different kind of devices, e.g. web browser or Mobile device. And they are sharing the same set of code nodes. In addition, 
UI designers can work on UI nodes and meanwhile, programmers work on code nodes. XBS has zero learning curve for experienced developers. There is no 
'XBS script or XBS language" such thing.

  * <font color="blue">Effective project management.</font> Since application is split into modules and nodes, project manager can balance the work 
load to team members at more granularity. It's also easier and more accurate for project manager to measure risk and effort; estimate project size, 
complexity and progress; set mile stone and collaborates with QA team.  

  * <font color="blue">XBS IDE is visualized and intuitive.</font> It makes possible for other project stakeholders (business analyzer or architects) 
to use the IDE, to design, review and analyze the application processes. On the other hand, coders use the IDE to implement application module's 
nodes, using their favorite programming languages. IDE provides native programming language environment for coding. XBS provides code assistance and 
syntax check. Any interface changes will be captured in code. That make sure node's implementation and interface are always synced.
   
  * <font color="blue">XBS application server provides rich off-the-shelf features </font>to facilitate application run-time. Those are most demanding 
features for large enterprise class applications, like fail-over, load balance, distributed transaction, cross-server communication, task scheduler, 
event trap etc. That would significantly reduce application development effort, and time to market.
 
  * <font color="blue">XBS also provides a centralized web-based admin console</font> for application execution. It is used to deploy, configure, 
schedule, on/off, monitor and trouble shooting, analyze application execution. [#XBS_admin_console]

  * <font color="blue">XBS applications are cloud ready,</font> due to XBS provided centralized management capability. XBS run time is good candidate 
for application cloud hosting. XBS application can be run (wholly or partially) on Cloud, and be managed by application owner from remote.


## <a name="ScreenShots"></a>Screen Shots
### A typical application module
_The following screen shot exhibits a typical application logic flow: initialize some required system components (e.g. authentication process), show user a 
log on page, it calls 'authentication' module/process to validate user according to user typed credentials. If 'success', it get user type from 
authentication module and then return to XBS engine. XBS engine, as design, opens corresponding window according to user type. If 'failed', it return 
'Exception' outcome with error message to XBS (or you can easily add a UI node to show the message to user.)_

<img src="https://github.com/KenXBS/XBS/blob/master/images/main_module.png" width="1024"/>


### The 'Auth' module
_The following screen shot shows the 'authentication' module of the above application. It's started by 'init' node of the above main module. It, in 
turn, starts authentication db and ready for two external calls: DoAuth and GetUserInfo. The module is long time process and designed to provide 
services to other process. It also generate an OUT event when 'auth db' got problem. The event is delivered to other processes as designed._

<img src="https://github.com/KenXBS/XBS/blob/master/images/auth.png" width="500" />


### Connection Configure
_The following screen shot depicts the connection configure window. Node's inputs can be configured to be some from last node's outputs, some from 
module data, or hard-coded value._

<img src="https://github.com/KenXBS/XBS/blob/master/images/property_config.png" width="500" />


### App main module in expanded view
_The following screen shot shows the same application module as the above one, with its login module expanded in-line. That should be convenient for 
application processes review. _

<img src="https://github.com/KenXBS/XBS/blob/master/images/app_main_large.png" width="500" />


### XBS admin console
_The follow is a screen shot of XBS Admin Console (It self is a web application developed with XBS framework). On the left panel, it shows the lists 
of application modules and all the application servers. Each module has a deployment number. If more than 2, means the module is deployed on multiple 
workers and therefore, it has fail-over and load balancing. If it's "1", the module may become single failure point. The right side of window exhibits 
the monitor/profile tab. It provides valuable application execution statistics data: the usage of module instance pool, number of calls and average 
execution time for each module and its nodes, etc._

<img src="https://github.com/KenXBS/XBS/blob/master/images/XBSAdminConsole_screenshot.png" width="800" />


### Demo: a three-page wizard module

<img src="https://github.com/KenXBS/XBS/blob/master/images/3pagewizard.png" width="500" />


### Screen shot: The 'Main' module of XBS Cluster Management Console
_XBS Cluster Management Console itself is a XBS application. The following is the screen shot of its 'main' module._

<img src="https://github.com/KenXBS/XBS/blob/master/images/XBS%20Server%20module.png" width="800" />


## <a name="demo" />Give it a try? 
I setup a XBS development environment on a test machine. I also create a couple of demo XBS applications: one is a desktop UI application, one is 
non-UI application (calculate PI) and one is a web application (url is 'http://localhost:5555/test' )

You may log onto the machine with [http://www.teamviewer.com/en/index.aspx TeamViewer]. Partner Id is '426124994' and password is 'xbstrial'.

You may browser/modify those demo applications, and run them using Eclipse's 'Debug' menu.

If you should have any difficulties, you can contact me at: liu_xiao_kang@hotmail.com