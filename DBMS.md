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
                - For example, a student can be assigned to many projects and a project can be assigned to many students.

