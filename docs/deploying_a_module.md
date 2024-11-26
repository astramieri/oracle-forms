# Deploying a Forms Module

For production applications you usually deploy the module to a middle-tier machine. This machine may be running on a different platform; if so, you need to recompile the module after you transfer it to the middle tier.

You can use an FTP utility to move the ```*.fmb``` and other needed files to the middle-tier machine, into a directory specified in ```FORMS_PATH```. If the platform is the same as your development platform, you can move the ```*.fmx``` and other executable files there as well. If it is a different platform, you can invoke the Forms Compiler on the middle tier to recompile the module files.

After the executables have been placed on the middle tier, you can invoke the application in a browser, using a URL that points to the Forms Servlet on the middle-tier Web server.