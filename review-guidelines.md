# Code Review Guidelines

*A non exhaustive list of thing which should be highlighted during a code review*

Please, do not hesitate to contribute, just open a pull request ;)

---

## Highlight
1. [code](#code)
1. [function](#function) 
1. [table](#table)
1. [commit](#commit)


## Code
 * which does not follow our standards  
 * breaking an existing homogeneity
 * which is not checking what it could be automatically and easily 
 * where error are kept quiet
 
    *eg. without log*
 * which does not follow the Open/Close principle
  
    *eg. a code which postpone some use case handling w /out making their future add easy*
 * accumulating a lot of data in memory, with potential "out of memory" issue. VS batch / stream processing
 * which does not split the unit process in a batch processing

**[⬆ Top](#highlight)**

## Function
  * too long or complex, because it gonna obviously become bigger 
  
    *Which does not respect the Single Responsibility Principle. Handling several responsibilities*
  * with multiple types returned
  
    *eg. a function returning either a Foo object instance or a list of Foo objects instances*
  * with parameters names semantically poor
  
    *Eg. data, value, id, code, argv, …*
  * with a poor documentation :
    * Just one line splitting the function name
    * an array as param without a structure example
    * an array as returned value without a structure example

**[⬆ Top](#highlight)**

## Table 
* whose name does not reflect the entity of one occurence
* in which identifiers (`_id`, `_code`) are not in first positions of columns list
* without this columns: `updated_on`, `inserted_on`, `inserted_by`
* badly normalized
* with foreign keys whose names are not the same in the origin table
* with column name not reflecting enough that the value comes from outside of our system

    *eg. `payment.psp_authorization_id` rather than `payment.authorization_id`*
* crated in the wrong DB
* created with the MyIsam engine. (Conccurency issue, transaction )
* with a column 
    * numeric where an `enum` could be more intelligible
    * or inversely an `enum` col with only two val where a `bool` could be useful
    * a `bool` col which could rather be usefully replaced by a richer content w/ a cardinality > 2
      
       *eg. a date `enabled_on` rather than a bool `enabled`*
    * containing complex/structured data such as json or xml
    * which would need comment (visible with `DESC` or `SHOW CREATE TABLE` statement)  

**[⬆ Top](#highlight)**

## A commit
* which is not as unitary as it could be
* not enough commented
* which does not make the code cleaner than we found it 

**[⬆ Top](#highlight)**

*To be continued...*
