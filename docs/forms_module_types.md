# Forms Module Types

A Forms application consists or many modules (or files).

A module is a major component of your application and is the basis for storage and ownership. A module owns the objects that it contains.

A Forms module can be of the following types:
- **Form**
    - it is the main component of an application
    - it presents the objects and data that users can see or interact with
- **Menu**
    - it consists of a hierarchy of menus, each with selectable items
    - a default menu with all basic operations is provided for every form 
    - it can be used with multiple forms
- **PL/SQL Library**
    - it is a collection of PL/SQL program units whose code can be referenced and called from other modules
- **Object Library**
    - it is a collection of form objects that you can use in other
modules

## Note

A form module can be run independently, but menu modules, PL/SQL libraries, and object libraries are functional only when attached to or included in a form module.