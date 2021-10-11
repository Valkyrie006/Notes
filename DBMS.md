# Introduction to DBMS
- ***Data*** is a collection of a distinct small unit of information
- ***Database*** is an organized collection of data, so that it can be easily accessed and manage
- ***Database Management System (DBMS)*** is a software for storing and retrieving users’ data while considering appropriate security measures
- DBMS vs File System
    - In DBMS user not required to write procedure
    - DBMS gives an abstract view of data that hides the details
    - DBMS provides a crash recovery and protection mechanism
    - DBMS Efficient
    - DBMS concurrent access of data is there using locking
- Architecture
    1. Two Tier Architecture
        - Client Application(Presentation layer (application interface) and Application layer (logical operations)) -> Database (Server)
    2. Three Tier Architecture
        - Presentation Layer (Client tier) -> Application Layer (Business(Server) tier) -> Database Layer (Data tier)
- ***Instance*** : Collection of the information stored in the database at that particular moment
- ***Schema*** : Logical Representation/Design of database
- Three Schema Architecture (Data Abstraction)
    1. View Level or External Schema - Tells the application about how the data should be shown to the user
    2. Conceptual Level or Logical Level - Tells how the data is actually stored and structured
    3. Physical Level or Internal Schema - Tells us that where data is actually stored

    ![Three Level Schema](/assets/DBMS/Introduction_3LevelSchema.jpg)

- Data Independence
    - Property of DBMS that helps you to change the Database schema at one level of a database system without requiring to change the schema at the next higher level
    - Types
        1. Logical Data Independence
            - Ability to change the conceptual level without changing view level
        2. Physical Data Independence
            - Modification in the Physical level should not result in any changes in the Logical or View levels

# Relational Database Management Systems (RDBMS)
- Data is stored in terms of rows(Tables) and Relational DBMS as its based on Relational Model

### Keys
- Attribute or a set of attributes that help to uniquely identify a tuple (or row) in a relation (or table)
- Types of Keys
    1. Primary Key
        - Column or group of columns in a table that uniquely identify every row in that table
        - A table cannot have more than one primary key
        - Every row must have a non-NULL primary key
        - Value in a primary key column can never be modified or updated if any foreign key refers to that primary key
    2. Alternate Key
        - Column or group of columns in a table that uniquely identify every row in that table.
        - All the keys which are not primary key are called an Alternate Key
    3. Candidate Key
        - Set of attributes that uniquely identify tuples in a table
    4. Foreign Key 
        - Column that creates a relationship between two tables. It acts as a cross-reference between two tables as it references the primary key of same/another table
        - Referential integrity
            - Rule defines that a foreign key have a matching primary key. Reference from a table to another table should be valid
            - Foreign Key maintains referential integrity 
            - Referenced Table (Primary Key)
                1. Insert - No violation
                2. Delete - May cause violation
                          - We can do On DELETE Cascade (delete from both table)
                3. Update - May cause Violation
            - Referencing Table (Foreign Key)
                1. Insert - Violation
                2. Delete - No violation
                3. Update - May cause violation
    5. Super Key
        - Group of single or multiple keys which identifies rows in a table. A Super key may have additional attributes that are not needed for unique identification
        - All super keys can’t be candidate keys but its reverse is true
        
![Keys Ex1](/assets/DBMS/Keys_Ex1.png)

### ER Diagram
- Used to define the data elements and relationship for a specified system
- Components of ER Diagram
    1. Entity
        - Object or component of data
        - Represented as rectangle in an ER diagram
        - Weak Entity
            - An entity that cannot be uniquely identified by its own attributes and relies on the relationship with other entity
            - Represented by a double rectangle
            - For example – a bank account cannot be uniquely identified without knowing the bank to which the account belongs, so bank account is a weak entity
    2. Attributes
        - Describes the property of an entity
        - Represented as Oval in an ER diagram
        - Types of Attributes
            1. Key attribute
                - Can uniquely identify an entity from an entity set
                - Represented by oval same as other attributes however the text of key attribute is underlined
                - For example, student roll number can uniquely identify a student from a set of students
            2. Composite attribute 
            - An attribute that is a combination of other attributes
            - For example, In student entity, the student address is a composite attribute as an address is composed of other attributes such as pin code, state, country
            3. Multivalued attribute
                - Attribute that can hold multiple values 
                - Represented with double ovals in an ER Diagram
                - For example – A person can have more than one phone numbers so the phone number attribute is multivalued
            4. Derived attribute
                - Attribute is one whose value is dynamic and derived from another attribute
                - Represented by dashed oval in an ER Diagram
                - For example – Person age is a derived attribute as it changes over time and can be derived from another attribute (Date of birth)
    3. Relationship
        - Shows the relationship among entities
        - Represented by diamond shape
        - Types of Relationship
            1. One to One Relationship
                - When a single instance of an entity is associated with a single instance of another entity
                - For example, a person has only one passport and a passport is given to one person
            2. One to Many Relationship
                - When a single instance of an entity is associated with more than one instances of another entity
                - For example – a customer can place many orders but a order cannot be placed by many customers.
            3. Many to One Relationship
                - When more than one instances of an entity is associated with a single instance of another entity
                - For example – many students can study in a single college but a student cannot study in many colleges at the same time

            4. Many to Many Relationship
                - When more than one instances of an entity is associated with more than one instances of another entity
                - For example, a student can be assigned to many projects and a project can be assigned to many students
    
### Normalization
- Database design technique that reduces data redundancy and eliminates undesirable characteristics like Insertion, Update and Deletion Anomalies
- Types of Anomalies
    ![Normalization Anomalies Example](/assets/DBMS/Normalization_Anomalies_Example.png)
    1. Data redundancy
        - When two or more rows or columns have the same value or repetitive value leading to unnecessary utilization of the memory
        - Example - There are two students in the above table, 'James' and 'Ritchie Rich', whose records are repetitive when we enter a new CourseID. Hence it repeats the studRegistration, StudName and address attributes
    2. Insert Anomaly
        - When some attributes or data items are to be inserted into the database without existence of other attributes
        - For example, In the Student table, if we want to insert a new courseID, we need to wait until the student enrolled in a course. In this way, it is difficult to insert new record in the table. Hence, it is called insertion anomalies.
    3. Update Anomalies
        - When duplicate data is updated only in one place and not in all instances. Hence, it makes our data or table inconsistent state. 
        - For example, suppose there is a student 'James' who belongs to Student table. If we want to update the course in the Student, we need to update the same in the course table; otherwise, the data can be inconsistent. And it reflects the changes in a table with updated values where some of them will not.
    4. Delete Anomalies
        - When some records are lost or deleted from the database table due to the deletion of other records
        - For example, if we want to remove Trent Bolt from the Student table, it also removes his address, course and other details from the Student table. Therefore, we can say that deleting some attributes can remove other attributes of the database table
- Functional Dependency 
    - Relationship that exists between two attributes
    -  Left side of FD is known as a determinant, right side of FD is known as a dependent
    - Example: A->B, A is determinant, B is dependent
    - Types of FD
        1. Trivial Functional Dependency
            - X->Y is a trivial functional dependency if Y is a subset of X
            - Example: A->A
        2. Non-Trivial Functional Dependency
            - When A->B holds true where B is not a subset of A
    - Properties of FD
        1. Reflexivity: If Y is a subset of X then, X->Y
        2. Augmentation: If X->Y, then XZ->YZ
        3. Transitive: If X->Y and Y->Z, then X->Z
        4. Union: If X->Y and X->Z, then X->YZ
        5. Decomposition: If X->YZ, then X->Y and X->Z
        6. PseudoTransitivity: If X->Y and WY->Z, then WX->Z
        7. Composition: If X->Y and Z->W, then XZ->YW
- Partial Dependency
    - Non-prime attribute is functionally dependent on part of a candidate key
    - Example: let's start with R{ABCD}, and the functional dependencies AB->CD and A->C. The only candidate key for R is AB. C and D are a non-prime attributes. C is functionally dependent on A. A is part of a candidate key. That's a partial dependency.
- Lossless Decomposition
    - If there natural join results in original relation R
    - No loss of information
- Lossy Decomposition
    - If there natural join does not result in original relation R
- Closure of Attribute Set
    - Set of all those attributes which can be functionally determined from an attribute set
    - Closure of attribute set {X} is denoted as {X}<sup>+</sup>
    - Find closure of attribute set
        1. Add attributes contained in attribute set for which closure is being calculated to result set
        2. Recursively add attributes to result set which can be functionally determined from attributes already contained in result set
    - Example
    ![Closure Example](/assets/DBMS/Normalization_Closure_Example.png)
    - Finding Super Key
        - If closure result of an attribute set contains all attributes of relation, then that attribute set is called as a super key of that relation
        - Example - Closure of attribute A is the entire relation schema. Thus, attribute A is a super key for that relation
    -Finding Candidate Key
        - If there exists no subset of an attribute set whose closure contains all attributes of the relation, then that attribute set is called as a candidate key of that relation
        - Example - No subset of attribute A contains all attributes of the relation. Thus, attribute A is also a candidate key for that relation
    - ***Prime Key***: Attribute which is part of one of candidate key
- Types of Normal Form
    1. First Normal Form (1NF)
        - Table should not contain any multivalued attribute
        - How to get 1NF (Different processes)
            1. Convert 1 table into multiple tables
            2. Change PK to composite key of multiple columns in same table
    2. Second Normal Form (2NF)
        - Rules
            1. Should be in 1NF
            2. All non-prime attributes should be fully functional dependent on candidate key[Remove Partial Dependency](For Partial Dependency - LHS of FD is proper subset of CK AND RHS is non-prime attribute)
        - How to make 2NF (remove Partial Dependency)
            - Increase table by removing that column causing us trouble
        - Example: Prime key attributes are StudentID and ProjectID.Non-prime attributes i.e. StudentName and ProjectName should be functionally dependent on part of a candidate key, to be Partial Dependent.StudentName can be determined by StudentID, which makes relation Partial Dependent. ProjectName can be determined by ProjectID, which makes relation Partial Dependent. Therefore, the <StudentProject> relation violates the 2NF.
        ![2NF Example](/assets/DBMS/Normalization_2NF_Example.png)
    3. Third Normal Form (3NF)
        - Rules
            1. Should be in 2NF
            2. No non-primary key attribute is transitively dependent on primary key(For each FD, LHS must be CK or SK, OR RHS is a prime attribute)
        - Example: There is a transitive dependency between Bank_Code_No and Bank, because Bank_Code_No is not the primary key of this relation. To get to the third normal form (3NF), we have to put the bank name in a separate table together with the clearing number to identify it.
        ![3NF Example](/assets/DBMS/Normalization_Example_3NF.gif)
    4. Boyce-Codd Normal Form (BCNF)
        - Rules
            1. Should be in 3NF
            2. LHS of FD should be candidate key or super key
    5. Fourth Normal Form (4NF)
        - Rules
            1. Should be in BCNF
            2. No multi-valued dependency(For a dependency A → B, if for a single value of A, multiple values of B exists, then relation will be a multi-valued dependency)
    6. Fifth Normal Form (5NF)
        - Rules
            1. Should be in 4NF
            2. Not contains any lossy join dependency and joining should be lossless
        - How to make 5NF
            - Common attribute should be CK or SK of either R1 or R2 or both

### Joins
- Join statement is used to combine data or rows from two or more tables based on a common field between them
- Types of Joins ([Types of Joins](https://www.javatpoint.com/types-of-sql-join))
    1. Cross Join (Cartesian Product/Join)
        - When each row of first table is combined with each row from second table
        - If you add a WHERE clause (if table1 and table2 has a relationship), CROSS JOIN will produce same result as INNER JOIN clause
        - Syntax
            ```SQL
                SELECT * FROM [TABLE1] CROSS JOIN [TABLE2]
            ```
            OR
            ```SQL
                SELECT * FROM [TABLE1], [TABLE2]
            ```
    2. Natural Join
        - Natural Join joins two tables based on same attribute name and data-types. The resulting table will contain all the attributes of both the table but keep only one copy of each common column (Join on common column between two tables only)
        - Syntax
            ```SQL
                SELECT * FROM [TABLE1] NATURAL JOIN [TABLE2]
            ```
        - Example - [Natural Join Example](https://www.w3resource.com/sql/joins/natural-join.php)
    3. Self Join
        - Each row of table is joined with itself and all other rows depending on some conditions
        - Syntax
            ```SQL
                SELECT a.column1, b.column2
                FROM table_name a, table_name b
                WHERE some_condition;
            ```
        - Example - [Self Join Example](https://www.geeksforgeeks.org/sql-join-cartesian-join-self-join/)
    4. Inner Join
        - Used to select all matching rows or columns in both tables or as long as defined condition is valid in SQL
        - Syntax
            ```SQL
                SELECT column_1, column_2 
                FROM table_1 INNER JOIN table_2 
                ON table_1.column = table_2.column; 
            ```
        - Example [Inner Join Example](https://www.javatpoint.com/types-of-sql-join)