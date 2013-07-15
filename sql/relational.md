

# Relational databases


---

## The relational database

Relational databases are very popular (and a commercial success)

1. flexible and reliable for data representation and manipulation 
2. based on the relational model (solid theory)

Centered on *relations* (~ *entities*)
   - bidimensional tables
   - rows (tuples) and columns (attributes)


---

## Relation

Entity to be represented in the database

* tuple (row) &rarr; instances of the entity
* attributes (columns) &rarr; properties of the entity

Name       | Surname    | Birthdate  | Gender | Marital status |
-----------|------------|------------|--------|----------------|
Aldo	   | Fabrizi    | 20-10-1988 |	male  | unmarried      |
Romeo      | Spena      | 18-05-1960 |  male  | married        |
Caterina   | Caselli    | 30-07-1976 | female | divorced       |
Claudia    | Pandolfi   | 10-12-1978 | female | widow          |

**Entity**
Table: People 
Fields: (Name, Surname, Birthdate, Gender Marital status)
{: .smaller}

---

## Primary key
     
* Distinguish tuples from each other
* Set of attributes that identify *unambiguously* a tuple
* There may be multiple sets of unambiguous attributes (*candidate keys*)
* Primary keys can not take NULL as value (*entity integrity*)

---

## Attributes

* Attributes: name (column name) and domain
* Domain: values that an attribute can take
    - character
{: .smaller}
    - numeric
{: .smaller} 
    - male/female (=/1, binary)
{: .smaller}
    - date (e.g. born after 1990)
{: .smaller}
    - etc ...
{: .smaller}

&iexcl;Domains must be atomic!
 
---

## Related tables

Non-atomic domain

    People (Name, Surname, Birthdate, Gender, 
    Marital status, Children)

Two tables (relations)

    People (*Person_number, Name, Surname, Birthdate, 
    Gender, Marital status, Children)

    Children (*Person_number, Name, Surname, Age, 
    Gender)

---

## Related tables

- Tables *People* and *Children*
- *Link*: attribute (field) "Person_number"
- *Primary key* in People
- *Foreign key* in Children

Values in the *Foreign key* must correspond to values in the *Primary key* of the related table (*referential integrity*)

Operations are possible on relations

---

## Relational algebra

* SELECTION: returns a subset of tuples (attributes unchanged)
* PROJECTION: returns a subset of attributes
* CARTESIAN PRODUCT: each tuple in the first table is matched with each tuple of the second table
* JOIN: tuples in two tables are matched based on the value of one (or more) of their attributes 
* UNION: tuples of compatible (same attributes) tables are combined
* MINUS: difference between compatible tables
* INTERSECT: common tuples in compatible tables

---

## Tables: People & Children


Number | Name       | Surname    | Birthdate  | Gender | Marital status 
-------|------------|------------|------------|--------|----------------
  1    |  Aldo	    | Fabrizi    | 20-10-1988 |	 male  | unmarried      
  2    | Romeo      | Spena      | 18-05-1960 |  male  | married        
  3    | Caterina   | Caselli    | 30-07-1976 | female | divorced       
  4    | Claudia    | Pandolfi   | 10-12-1978 | female | widow          

&nbsp;

Number | Name       | Surname    | Age  | Gender 
-------|------------|------------|------|--------
  2    | Francesco  | Spena      | 6    | male   
  2    | Sara       | Spena      | 8    | female 


---

## Selection & Projection

    SELECT (People) Gender="female"


Number | Name       | Surname    | Birthdate  | Gender | Marital status 
-------|------------|------------|------------|--------|----------------
  3    | Caterina   | Caselli    | 30-07-1976 | female | divorced       
  4    | Claudia    | Pandolfi   | 10-12-1978 | female | widow          

&nbsp;
{: .small}

    PROJECT Gender (People)

&nbsp;
{: .small}

|Gender 
|--------
| male  
| male  
|female 
|female 

---

## Join

    JOIN (People, Children)
    People(Number)=Children(Number)

Number | Name       | Surname    | Birthdate  | Gender | Marital status | Name      
-------|------------|------------|------------|--------|----------------|-----------
  2    | Romeo      | Spena      | 18-05-1960 |  male  | married        | Francesco 
  2    | Romeo      | Spena      | 18-05-1960 |  male  | married        | Sara      

 Surname    | Age  | Gender 
------------|------|--------
 Spena      | 6    | male   
 Spena      | 8    | female 



Users use SQL instructions (translated into relational algebra operations)


