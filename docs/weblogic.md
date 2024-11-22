# Oracle WebLogic Server

Oracle WebLogic Server is a scalable, enterprise-ready Java Platform, Enterprise Edition (Java EE) application server. 

The WebLogic Server infrastructure supports the deployment of many types of distributed applications and it is an ideal foundation for building applications based on Service-Oriented Architecture (SOA).

WebLogic Server can define multiple environments called **domains**. 

Each domain consists of:
- one **Administration Server** 
- one (or more) **Managed Servers** 

Depending on the components that are installed, you may also have an Oracle DB instance, and possibly a metadata repository if the installed components require one.

![Oracle WebLogic Domains](../images/weblogic_domains.png)

## Oracle WebLogic & Forms Applications

A managed server is a WebLogic Server instance that runs deployed applications. When you install and configure Oracle Forms, a managed server is created named ```WLS_FORMS```. 

In order to run a form, you first must start this managed server. You can start a managed server even if the Administration Server (needed for configuring Forms Services) is not running.

WebLogic Server provides a servlet container that is ideally suited to run Forms applications. The servlet container calls the servlet’s methods and provides services that the servlet needs when running.

When a request for a Forms application is routed to WebLogic Server, WebLogic Server performs the following actions:
- if an instance of the servlet does not exist, it loads the servlet class, then instantiates and initializes an instance of the servlet class
- it invokes the servlet, passing request and response objects
    - the request object contains information about the client, request parameters, and HTTP headers
    - the response object returns the servlet’s output to the client