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

- **Block processing**
- **Interface event**
- **Master detail**
- **Message handling**
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

The trigger type determines which type of event fires it. There are more than **100 built-in triggers**, each identified by a specific name. The name of a trigger identifies its type. All built-in trigger types are associated with an event,
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

### Trigger Scope

The scope of a trigger is determined by its position in the formobject hierarchy—that is, the type of object under which you create the trigger. 

There are 3 possible levels:
- Form level
- Block level
- Item level

Some triggers cannot be defined below a certain level.

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

In the cases of Before and After, you can fire more than one trigger of the same type due to a single event. However, you must define each trigger at a different level.