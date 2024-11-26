# Creating a Forms Module

There are several ways to create a new form module:
- Use wizards
    - Data Block wizard
    - Layout wizard
- Build the module manually
- Use the template form

## Using The Wizards

After you create a new data block by using the wizards, Forms Builder automatically creates the following objects for you:
- a form **module** with a default menu 
    - basic database functionality such as querying, inserting, updating, and deleting is automatically available on the items in the base-table block when you run the new form
- a **data block** with default property values
    - the values can be modified to change the behavior of the form
- a **frame** object to arrange the items within the new data block
- an **item for each table column** included in the data block
    - each item is assigned default property values to match the underlying column specifications
- a **prompt for each item** in the data block
    - the default prompt is the name of the column
- (optional) **triggers** to validate user input 
    - if you select the *Enforce data integrity check* box
