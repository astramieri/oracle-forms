# Triggers

A trigger is a PL/SQL program unit that is executed (fired) due to an event. 

Forms Builder defines a vast range of events for which you can fire a trigger:
- Query-related events
- Data entry and validation
- Logical or physical navigation
- Operator interaction with items in the form
- Internal events in the form
- Errors and messages

Events cause the activation or firing of certain trigger types.

**Note**. Database events that occur on behalf of a form can fire certain triggers, but these database triggers are different from Forms Builder triggers.

## Grouping Triggers into Categories

Triggers may be grouped into functional categories:

- **Block Processing**
- **Interface Event**
- **Master Detail**
- **Message Handling**
- **Navigational**
- **Query Time**
- **Transactional**
- **Validation**

Triggers may be grouped into categories based on name:

- **When-Event**
- **On-Event**
- **Pre-Event**
- **Post-Event**
- **Key**

## Trigger Components

There are 3 main components to consider when you design a trigger in Forms Builder:
- **Type**
- **Code**
- **Scope**

### Trigger Type

The trigger type determines which type of event fires it. There are **more than 100 built-in triggers**, each identified by a specific name. The name of a trigger identifies its type. All built-in trigger types are associated with an event,
and their names always contain a hyphen (-).

Forms Builder supports **user-named triggers** as well as the standard built-in triggers. A usernamed trigger is one that is named by the designer. These triggers fire only if called by another trigger or program unit using built-in code features.

### Trigger Code

The code of the trigger defines the actions for the trigger to perform when it is fired. 

Statements in a trigger and can include:
- SQL statements that are legal in a PL/SQL block
- Standard PL/SQL constructs (assignments, control statements, etc.)
- Calls to user-named subprograms (procedures and functions) in the form, a library, or the database
- Calls to built-in subprograms and package subprograms
    
Although you can include SQL statements in a trigger, keep in mind the following rules:
- ```INSERT```, ```UPDATE```, and ```DELETE``` statements can be placed in transactional triggers
- ```COMMIT```, ```ROLLBACK```, and ```SAVEPOINT``` should not be included directly as SQL trigger statements

**Note.** If your trigger code does not require defined variables, you do not need to include the ```BEGIN``` and ```END``` keywords; they are added implicitly.

### Trigger Scope

The scope of a trigger is determined by its position in the form object hierarchy. 

There are 3 possible levels:
- Form level
- Block level
- Item level

Some triggers cannot be defined below a certain level.

*A mistake often made by inexperienced Forms developers is to define a trigger at the wrong scope. For example, if you want a message to display when the cursor is placed on an item, you should code a When-New-Item-Instance trigger at the item level for that item. If you mistakenly put the trigger at the block or form level, the trigger will fire whenever the operator navigates to any item in the block or form.*

## Trigger Execution Hierarchy

When there is more than one trigger of the same type, Forms by default fires the trigger most specific to the cursor location. However, you can alter the firing sequence of a trigger by setting the Execution Hierarchy trigger property.

Execution Hierarchy (EH) is a trigger property that specifies how the current trigger code should execute if there is a trigger with the same name defined at a higher level in the object hierarchy. Setting EH for form-level triggers has no effect because there is no higher-level trigger. 

Settings for Execution Hierarchy are the following:
- Override (default)
    - Only the trigger that is most specific to the cursor location fires
- After
    - The trigger fires after firing the same trigger, if any, at the next highest level
- Before
    - The trigger fires before firing the same trigger, if any, at the next highest level

In the cases of *Before* and *After*, you can fire more than one trigger of the same type due to a single event. However, you must define each trigger at a different level.

## PL/SQL Editor

Things to remember about the PL/SQL Editor:

- New or changed text in triggers remains uncompiled until you click *Compile*
- Compiling triggers that contain SQL requires connection to the database
- All uncompiled triggers are compiled when the form module is compiled
- The *Block* and *Item* pop-up lists do not change the current trigger scope but they enable you to switch to another trigger

## Forms Builder Variables

Forms Builder generally accepts two types of variables for storing values:
- PL/SQL variables
    - These must be declared in a ```DECLARE``` section, and remain available until the end of the declaring block
    - They are not prefixed by a colon (:)
- Forms Builder variables
    - These are the variable types maintained by the Forms Builder
    - These are seen by PL/SQL as external variables, and **require a colon (:) prefix** to distinguish them from PL/SQL objects (except when the name is passed as a character string to a subprogram)

### Forms Builder Variables

| Variable Type | Scope | Use |
| - | - | - |
| Item (text, list, check box, etc.) | Presentation and user interaction | ```:block_name.item_name``` |  
| Global variable | Sessionwide character variable | ```:GLOBAL.variable_name``` |
| System variable | Form status and control | ```:SYSTEM.variable_name``` | 
| Parameter | Passing values in and out of module | ```:PARAMETER.name``` |

**Note**. The contents of system variables are in uppercase.

You can use the ```DEFAULT_VALUE``` built-in to assign a value to a global variable. Forms Builder creates the global variable if it does not exist. If the value of the indicated variable is not null, ```DEFAULT_VALUE``` does nothing.

    DEFAULT_VALUE('ITALY','GLOBAL.country');

You can use the ```ERASE``` built-in to remove a global variable.

## Built-in Subprograms

Forms Builder provides a set of predefined subprograms as part of the product. These
subprograms are defined within built-in packages as either a procedure or function.

Forms Builder built-in subprograms belong to one of the following:
- **Standard Extensions** package
    - Contains hundreds of core Forms built-ins that are integrated into the Standard PL/SQL command set in Forms Builder
    - You can call them directly, without any package prefix
    - E.g.: ```EXECUTE_QUERY```
- **Other Forms Builder** packages
    - Subprograms in other built-in packages provide functionality related to a particular supported feature
    - These require the package name as a prefix when called
    - E.g.: ```ORA_JAVA.CLEAR_EXCEPTION```

### Limits of Use

You can call built-ins in any trigger or user-named subprogram in which you use PL/SQL. However, some built-ins provide functionality that is not allowed in certain trigger types. 

Built-ins are, therefore, divided into 2 groups:
- **Unrestricted built-ins**
    - They do not affect logical or physical navigation and can be called from any trigger, or from any subprogram
- **Restricted built-ins**
    - They affect navigation in your form, either external screen navigation, or internal navigation 
    - You can call these built-ins only from triggers while no internal navigation occurs

**Note.** Calling a restricted built-in from a navigational trigger compiles successfully but causes a run-time error.