# Data Blocks and Frames

There are 3 ways to modify properties of Forms Builder objects:
- Reentrant Wizards
- Layout Editor *(if the object appears on a canvas)*
- Property Palette
    - properties are grouped under functional headings or nodes

## Property Palette

Each form object has various types of properties. Properties are manipulated differently, depending on the property type.

Each property in a Property Palette has an icon to its left:
- **circle**: specifies that the property value is the default value
- **square**: specifies that the property values has been changed from the default
- **arrow**: specifies that the property values is inherited
- **arrow with a cross**: specifies that the property value was inherited but has been overriden 

## Visual Attributes

Visual Attribute is another object that you can create in the Object Navigator. Visual Attributes are the font, color, and pattern properties that you set for form and menu objects. 

## Data Block Properties

Each data block has several properties. These properties are divided into groups.

- **Navigation**
    - Navigation Style
        - valid settings: *Same Record* (default), *Change Record*, or *Change Data Block*
    - Previous/Next Navigation Data Block
- **Records**
    - Current Record Visual Attribute Group
        - Visual Attribute used to highlight the current record in the data block
    - Number of Records Displayed
    - Query Array Size
        - it specifies the maximum number of records that Forms should
fetch from the database at one time
        - when set to 0, this property defaults to the *Number of Records Displayed*
    - Number of Records Buffered
        - minimum amount of buffer space retained for holding queried records in the data block
    - Query All Records
        - it specifies whether all the records matching the query criteria should be fetched when a query is executed
        - it is necessary to support the *Calculated Field* feature
    - Record Orientation
        - it determines the orientation of records in the data block (horizontal or vertical)
    - Single Record 
        - it specifies that the control block should always contain one record
        - set to *Yes* for a control block that contains a summary calculated item
        - cannot set to *Yes* for a data block
- **Database**
    - Database Data Block
        - set to *Yes* if the data block is based on a database object
        - set to *No* if it is a control block
    - Enforce Primary Key
    - Query Allowed
    - Insert Allowed
    - Update Allowed
    - Delete Allowed
    - Query Data Source Type
        - possbile values: *None*, *Table*, *Procedure*, *Transactional Triggers*, or the *FROM clause* query
    - Query Data Source Name
    - Query Data Source Columns
    - Query Data Source Arguments
        - it specifies the names, data types, and values of the arguments that are to be passed to the procedure for querying data
        - it is valid only when the *Query Data Source Type* property is set to *Procedure*
    - Optimizer Hint
    - Locking Mode/KeyMode
    - Update Changed Columns Only
        - set to *No* (by default) so that all columns are included in the default UPDATE statement
    - Enforce Column Security
    - Maximum Query Time
        - it provides the option to abort a query when the elapsed time
of the query exceeds the value of this property
    - Maximum Records Fetched
        - it provides the option to abort a query when the number
of records fetched exceeds the value of this property
    - ```WHERE``` Clause
        - this clause is automatically appended (```AND```) with any conditions supplied by the operator in Enter Query mode
    - ```ORDER BY``` Clause
        - the operator can alter this order by using the Query/Where dialog box at run time
- **Scroll Bar**
    - Show Scroll Bar
    - Scroll Bar Canvas/Tab Page
    - Scroll Bar Orientation
    - Scroll Bar X/Y Position
    - Scroll Bar Width/Length

## Frame Properties

The selections that you make in the Layout Wizard when creating a data block are recorded as properties of the resulting layout frame object. You can change frame properties to modify the arrangements of items within a data block.

- **Layout Data Block**
    - it specifies the name of the data block with which the frame is
associated
    - the items within this data block are arranged within the frame
    - a data block can be associated with only one frame
- **Update Layout**
    - it specifies when the frame layout is updated
    - valid settings: *Automatically*, *Manually*, or *Locked*
- **Layout Style**
    - it specifies the layout style for the items withing the frame
    - valid settings: *Form* or *Tabular*
- **Distance Between Records**
    - it specifies the pysical distance with which to separate records
- **X/Y Position**
    - it specifies the x and y coordinates of the frame’s position on the canvas
- **Width/Height**
    - it specifies the width and height of the frame

**Note**. You can arrange a frame as well as the objects within it manually in the Layout Editor.

### Copying Properties

You can copy the properties and values from the Property Palette to a buffer, so that they can be applied (pasted) to other objects in your design session.

It is possible to copy the property settings of an object to objects of different types. In this case, properties that do not apply to the target object are ignored.

### Property Classes

When you display a list of properties (from either one object or a combination of objects) in the Property Palette, the list of property names and associated values can be saved for future application to other objects. This is known as a **Property Class**, which is a Forms Builder object in its own right.

Objects can inherit some of their properties from a linked property class, so their properties change automatically if the associated properties are changed in the property class.

## Control Block

A **Control Block** is a block that is not associated with any database, and its items do not relate to any columns within any database table. This means that Forms does not perform an automatic query when the operator issues an Enter Query or Execute Query command, nor does it issue an automatic Insert, Update, or Delete for the block when the operator saves changes to the database.

Because there are no database columns on which to base control block items, a control block has no items until you manually add them later.