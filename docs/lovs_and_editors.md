# LOVs and Editors

LOVs and Editors are objects in a form module that you can associate with text items to enhance input. Each opens its own window when activated at run time. LOVs enable users to choose a value from a static or dynamic list, while Editors provide a larger area for text entry with search and replace capability. 

LOVs and Editors are defined at the form level, which means that you can use them to support text items in any block of the form module.

## LOVs

An LOV is a scrollable pop-up window that enables a user to pick the value of an item from a multicolumn dynamic list. The user can reduce the lines displayed in the list by simple automatic reduction techniques, or by search strings. Each line in an LOV can present several field values, with column headings above.

LOVs have the following qualities:
- Dynamic
    - the list entries can change to reflect changes in the source data.
- Independent
    - the designer can invoke an LOV from any text item, or from outside a text item if called programmatically
- Flexible
    - you can use the same LOV to support several items
- Efficient
    - you can design LOVs to reuse data already loaded into the form, instead of accessing the database for every call
    - this is useful where data is relatively static

When you build an LOV, consider the following objects:
- **Record group**
    - a Forms Builder object that is used to store the array of values that are presented by an LOV
- **LOV**
    - the list itself, which presents one or more column values from the supporting record group in the LOV window
- **Text items**
    - the main text item that you attach to an LOV is usually one that the LOV returns a value to You can call the LOV from this item to provide possible values for it
    - a single LOV can return values to several items

### Record Groups

A record group is a column-and-row structure stored within Forms Runtime memory and is similar to the structure of a database table. It holds records that can be reused by other text items, therefore reducing repeated access to external data.

Record groups can be designed to contain static values. Alternatively, they can be populated programmatically at run time or, most commonly, populated by a SQL query.

**Note**. Because LOVs and record groups are separate objects, you can create multiple LOVs based on the same record group.