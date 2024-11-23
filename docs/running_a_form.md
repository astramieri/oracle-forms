# Running a Form Application

The URL to invoke an Oracle Form application has the following format:

    https://<host>:<port>/forms/frmservlet[?<parameters>]

where:

- ```ports```
    - 9001 default for WebLogic Server (used for testing from Forms Builder)
    - 8888 default for Oracle HTTP Server (used commonly for production)
- ```parameters``` (separated by ```&```)
    - ```form=<form_name>.fmx```
    - ```userid=<user_name>/<pass_word>@<db_name>```
    - ```buffer_record=NO```
    - ```debug_message=NO```

## Starting a runtime session

Starting a runtime session involves the following steps:
1. The user accesses the URL that indicates that a Forms application should be run
2. The Oracle HTTP Server (OHS) or the Oracle WebLogic Server (WLS) receives an HTTP request from the browser client and contacts the Forms Servlet
3. The Forms Servlet dynamically creates an HTML page containing all the information to start the Forms session
4. The OHS or the WLS downloads a generic applet to the client after checking that it has not already been downloaded
5. The client applet contacts the Forms Listener Servlet to start the session
6. The Forms Listener Servlet starts an instance of the Forms Runtime Engine on the Forms Server (middle tier)
7. The Forms Listener Servlet establishes a connection with the Forms Runtime Engine, which connects to the database if needed and loads application executable files
8. The Forms applet displays the user interface of the application in the main window of the user’s Web browser
9. The Forms Listener Servlet, working through HTTP Server or WebLogic Server, manages communication between the Forms applet and the Forms Runtime Engine