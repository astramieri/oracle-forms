# Oracle Forms Executables

Oracle Forms includes the following two executables (components):
- **Forms Builder**
    - it is the application-building component of Oracle Forms
    - it is used to design and store the definitions of form, menu, and library
documents
- **Forms Compiler**
    - it reads the definition of module and creates an executable run file

## Invoking Forms Builder

    FRMBLD [my_form] [my_user/my_pass@my_database]

## Testing a Form Application

Because Forms applications are Web based, it is not possible to run them directly from the command line. Instead, they are invoked by entering a URL, directed to Forms Services, in a browser.

The files used at run time must already have been compiled by the Forms Compiler component. These files must reside on the middle-tier machine in a directory accessible to the Forms Runtime Engine (in ```FORMS_PATH```).

To test a Form application, Forms Services can be accessed directly from Forms Builder by configuring specific preferences.


