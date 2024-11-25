# Oracle Forms Environment Variables

Oracle Forms uses some environment variables, set on the middle-tier computer, to search at run time for files such as forms, menus, and libraries.

Oracle Forms searches the following paths **in order** until the required file is found:
- the current working directory
- directories in ```FORMS_PATH```
- directories in ```ORACLE_PATH```

The preferred way to set these variables at the machine level is to set them in the **Forms environment file**.

- **Forms environment file**
    - ```default.env``` (or other file specified in the Forms configuration file)
- **Forms configuration file**
    - ```formsweb.cfg``` (or other)
    - used to specify:
        - system parameters (environment file)
        - user parameters (e.g. form and user ID)
        - settings for the Java client
        - etc.

The ```default.env``` and ```formsweb.cfg``` files are located in the subdirectory of the domain home for the Forms-managed WebLogic server.

    $DOMAIN_HOME/config/fmwconfig/servers/WLS_FORMS/applications/formsapp_12.2.1/config