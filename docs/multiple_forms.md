# Multiple Forms Applications

Oracle Forms applications rarely consist of a single form document.

You can design forms to appear in separate windows, so the user can work with several forms concurrently in a session (when forms are invoked by the ```OPEN_FORM``` built-in). Users can then navigate between visible blocks of different forms, much as they can in a single form.

You can design forms for a Forms Runtime session according to the following conditions:
- Forms share the same database session or open their own separate sessions
- Database transactions are continued across forms or ended before control is passed to another form
    - The commit sequence starts from the current form and follows the opening order of forms
- Forms Builder provides the same menus across the application or each form provides its own separate menus when it becomes the active form

Each form runs within the same Forms Runtime session, and Forms remembers the form that invoked each additional form. This chain of control is used when you exit a form or commit transactions.

There are several methods to exchange data between forms, and code can also be shared. The following objects are available to provide information to all open forms: 
- Global variables
- Global record groups
- PL/SQL variables

![Multiple Forms Application](../images/multiple_forms.png)

## Benefits of Multiple Form Applications

Separating your application into multiple forms offers the following benefits:
- Logic modularity
- Network performance and scalability
- Debugging

## Opening a Form with ```OPEN_FORM```

You can use the ```OPEN_FORM``` built-in to start another form module from the one that is already active. This is a restricted procedure and cannot be called in Enter Query mode. ```OPEN_FORM``` enables you to start another form in a modeless window so the user can work in other running forms at the same time.

    OPEN_FORM('form_name', activate_mode, session_mode, data_mode, paramlist);

Sintax:
- ```form_name```
    - file name of the executable module (without the ```.FMX``` suffix)
- ```activate_mode```
    - either ```ACTIVATE``` (default) or ```NO_ACTIVATE```
- ```session_mode```
    - either ```NO_SESSION``` (default) or ```SESSION```
- ```data_mode```
    - either ```NO_SHARE_LIBRARY_DATA``` (default) or ```SHARE_LIBRARY_DATA```
- ```paramlist```
    - either the name (within quotation marks) or internal ID of a parameter list

**Note**. There are two other built-ins that can call another form (```CALL_FORM``` or ```NEW_FORM```).

### Conditional Opening

The ```OPEN_FORM``` built-in enables you to start up several instances of the same form. To prevent this, the application can perform appropriate tests, such as using the ```FIND_FORM``` built-in.

    IF ID_NULL(FIND_FORM('form_name')) THEN
        OPEN_FORM('form_name');
    ELSE
        GO_FORM('form_name');
    END IF;

## Closing a Form with ```EXIT_FORM```

When a form is closed, Forms checks to see whether there are any uncommitted changes. If there are, the user is prompted with the standard alert:

    Do you want to save the changes you have made?

If you are closing a form with ```EXIT_FORM```, the default functionality is the same as described above. You can, however, make the decision to commit (save) or roll back through the ```EXIT_FORM``` built-in, so the user is not asked.

    EXIT_FORM(commit_mode);

Sintax:
- ```commit_mode```
    - ```ASK_COMMIT``` (the default) gives the decision to the user
    - ```DO_COMMIT``` posts and commits changes across all forms for the current transaction
    - ```NO_COMMIT``` validates and rolls back uncommitted changes in the current form
    - ```NO_VALIDATE``` is the same as NO_COMMIT, but without validation