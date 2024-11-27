# Oracle Forms Builder

Oracle Forms Builder is a **productive development environment** for building enterprise-class, scalable database applications for the Web. 

Oracle Forms Builder provides a set of tools that enable business developers to easily and quickly construct sophisticated database forms and
business logic with a minimum effort.

Oracle Forms Builder uses **powerful declarative capabilities** to rapidly create applications from database definitions that leverage the tight integration with the Oracle database. The toolset leverages Java technology, promotes reuse, and is designed to allow developers to declaratively build rich user interfaces. 

Developer productivity is further increased through a single integrated development environment that enables distributed debugging across all tiers, utilizing the same PL/SQL language for both server and client.

## Modes of Operation

Forms Builder has 2 main modes of operation: 
- **Enter-Query mode**
    - to enter search criteria for a database query
    - keystrokes are interpreted as *search criteria* for retrieving restricted data
- **Normal mode**
    - to insert and alter records in the database
    - keystrokes are interpreted as either the entering of new records or the altering of existing ones

**NOTE.** The third mode of operation, **Query mode**, occurs while Forms is processing a query; the user cannot interact with the form while this query processing is taking place.

## Retrieving Data 

There are two general types of queries:
- **unrestricted**: the equivalent of selecting all the rows for all the represented columns from the base table for the queried data block
- **restricted**: the equivalent of selecting a restricted set of rows for all the represented columns from the base table for the queried data block

You can use any one of the following methods to perform a restricted query:
- matching values
- matching patterns (wildcards)
- a *Query/Where dialog box* for user entry of SQL predicates

**Note**. To improve security, Forms 10.1.2.0.2 introduced a new run-time environment variable, ```FORMS_RESTRICT_ENTER_QUERY```, that is initially set to ```TRUE```, which makes it impossible to invoke the *Query/Where dialog box*. 