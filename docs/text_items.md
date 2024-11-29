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

**Note.** An item that has the Visual Attribute Group property set to *DEFAULT*, or that has individual attribute settings left unspecified, inherits those settings from the canvas to which it is assigned.