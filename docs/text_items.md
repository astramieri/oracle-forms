# Text Items

A **Text Item** is an interface object with which you can query, insert, update, and delete data. A text item usually corresponds to a column in the database table. 

When an item is first created, its default type is text.

You can create a text item by doing one of the following:
- converting an existing item into a text item
- using the *Text Item tool* in the Layout Editor
- using the *Create icon* in the Object Navigator
- using the wizards

**Note**. To display an item at run time, **you must assign the item to a canvas** in the Property Palette.

## Text Item Properties

The properties of an item are divided into several groups.

- **General**
    - Item Type
- **Physical**
    - Visibile
    - Canvas
        - it determines the canvas on which the item is displayed. 
        - if left unspecified, the item is said to be a *Null* canvas item, and will not display at run time or in the Layout Editor
    - X and Y Position
    - Width and Height
- **Records**
    - Current Record Visual Attribute Group 
    - Distance Between Records
    - Number of Items Displayed
- **Visual Attributes**
- **Prompt**
    - it specifies the text label that is associated with an item
- **Data**
    - Data Type
    - Data Length Semantics
    - Maximum Length
    - Format Mask
- **Values**
    - Required
    - Lowest/Highest Allowed Value
    - Initial Value
        - the default value assigned to an item whenever a record is created
        - it can be set to select from a sequence
        - it must be compatible with the item data type
    - Copy Value from Item
        - it specifies the source of the value that Forms uses to populate the item
        - when you define a master-detail relation, Forms sets this property automatically on the foreign key items in the detail block
        - the text item should disable input (otherwise, the user can violate the foreign key relationship!)
    - Synchronize with Item
- **Navigation**
    - Keyboard Navigable
        - it determines whether you can navigate to an item during default navigation with the function keys or menu items and place focus on it
    - Previous Navigation Item
    - Next Navigation Item
- **Database**
    - Database Item
    - Query/Insert/Update Allowed
    - Query Length
    - Case Insensitive Query
- **Functional**
    - Enabled
    - Conceal Data
        - it hides characters that the operator types into the text item
    - Multi-Line
- **Help**
    - Hint
    - Display Hint Automatically
    - Tooltip

**Note.** An item that has the Visual Attribute Group property set to *DEFAULT*, or that has individual attribute settings left unspecified, inherits those settings from the canvas to which it is assigned.

**Note.** When you create an item in a data block, Forms Builder assumes that the item is a data item, sets its Database Item property to Yes, and automatically includes it in any ```SELECT```, ```UPDATE```, and ```INSERT``` statements issued to the database. If an item that you are creating is a control item, you must explicitly set its Database Item property to No.

## Text Item Initial Value

You can use any one of the following values to issue an initial item value whenever a new record is created:
- **raw value**
    - e.g. ```34```, ```ITALY```
- **system variabile**
    - current application server operating system date/time
        - e.g. ```$$DATE$$```
        - e.g. ```$$DATETIME$$```
        - e.g. ```$$TIME$$```
    - current database date/time
        - e.g. ```$$DBDATE$$```
        - e.g. ```$$DBDATETIME$$```
        - e.g. ```$$DBTIME$$```
- **global variable**
    - e.g. ```:GLOBAL.CUSTOMER_ID```
- **form parameter**
    - e.g. ```:PARAMETER.SALES_REP_ID```
- **form item**
    - e.g. ```:ORDERS.ORDER_ID```
- **sequence** 
    - e.g. ```:SEQUENCE.ORDERS_SEQ.NEXTVAL```