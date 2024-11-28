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
        - valid settings: Same Record (default), Change Record, or Change Data Block
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
        - set to ```Yes``` for a control block that contains a summary calculated item
        - cannot set to ```Yes``` for a data block
- **Database**
    - Database Data Block
        - set to ```Yes``` if the data block is based on a database object, and ```No``` if it is a control block
    - Enforce Primary Key
    - Query Allowed
    - Insert Allowed
    - Update Allowed
    - Delete Allowed
    - Query Data Source Type
        - possbile values: None, Table, Procedure, Transactional Triggers, or the ```FROM``` clause query
    - Query Data Source Name
    - Query Data Source Columns
    - Query Data Source Arguments
        - it specifies the names, data types, and values of the arguments that are to be passed to the procedure for querying data
        - it is valid only when the *Query Data Source Type* property is set to ```Procedure```