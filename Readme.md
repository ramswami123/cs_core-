
## DBMS Concepts

### Consistency
Consistency refers to the requirement that any given database transaction must change affected data only in allowed ways. This means that any data written to the database must be valid according to all defined rules, including constraints, cascades, triggers, and any combination.

### Checkpoint
A checkpoint in a Database Management System (DBMS) is a point in time when the database is in a consistent state and all transactions have been committed. Checkpoints are used for the recovery of the database after a system crash and are part of the log-based recovery system.

### Redundancy
Redundancy refers to the unnecessary duplication of data within the database. This can occur for several reasons, such as poor database design, lack of normalization, or intentional replication for backup and recovery purposes.

### Transparent DBMS
A transparent DBMS is a type of DBMS that keeps its physical structure hidden from users. Physical structure or physical storage structure refers to the memory manager of the DBMS and describes how the data is stored on disk.

### RDBMS
RDBMS stands for Relational Database Management System. It is a type of database management system (DBMS) that stores data in a structured format, using rows and columns.

### Examples of Relational Databases
- MySQL
- PostgreSQL
- Oracle Database

### Database Languages
- **Data Definition Language (DDL)**: Commands like CREATE, ALTER, DROP, TRUNCATE, RENAME, etc. These commands are used for updating the data structure.
- **Data Manipulation Language (DML)**: Commands like SELECT, UPDATE, INSERT, DELETE, etc. These commands are used for manipulating already updated data.
- **Data Control Language (DCL)**: Commands like GRANT and REVOKE. These commands are used for giving and removing user access to the database.
- **Transaction Control Language (TCL)**: Commands like COMMIT, ROLLBACK, and SAVEPOINT. These commands are used for managing transactions in the database.

### Data Model
The data model is specified as a collection of conceptual tools for describing data, data relationships, data semantics, and constraints.

### Types of Data Models
- **Hierarchical Data Model**: Organizes data in a tree-like structure, where each record has a single parent and potentially many children.
- **Network Data Model**: Similar to the hierarchical model but allows more complex relationships with multiple parent and child records.
- **Relational Data Model**: Uses tables (relations) to represent data and their relationships. Each table consists of rows (tuples) and columns (attributes).
- **Entity-Relationship Model (ER Model)**: Represents data entities, their attributes, and relationships between entities using diagrams.

### Levels of Data Abstraction
- **Physical Level**: Describes how data is stored.
- **Logical Level**: Describes what data is stored in the database and the relationships among those data.
- **View Level**: Describes only part of the entire database.

### DML (Data Manipulation Language)
- **Procedural DML**: Requires a user to specify what data is needed and how to get those data.
- **Non-Procedural DML**: Requires a user to specify what data is needed without specifying how to get those data.

### Flow of DML Commands Compilation
1. **Parsing**:
   - **Syntax Analysis**: Checks for syntax errors.
   - **Semantic Analysis**: Checks if the referenced tables and rows exist and if the user has access.
2. **Query Optimization**
3. **Execution Plan Generation**
4. **Query Execution Engine**
5. **Transaction Management**: Ensures that the transaction's ACID (Atomicity, Consistency, Isolation, Durability) properties are maintained.

### Relational Algebra
Relational Algebra is a procedural query language that contains a set of operations that take one or two relations as input and produce a new relation.

### Query Optimization
Query optimization specifies an efficient execution plan for evaluating a query that has the least estimated cost.

### Durability
Durability ensures that once a transaction has been committed, it will remain so, even in the event of a system failure. This means that all the changes made by the transaction are permanently recorded in non-volatile storage, such as a hard drive or SSD, and will survive any subsequent crashes or power failures. This is achieved by "checkpointing."

### Functional Dependency
Functional dependency describes the relationship between attributes in a relation (table) and is used to ensure data integrity and reduce redundancy.

### Normalization
Normalization is a process in database design that organizes tables to minimize redundancy and dependency. It involves dividing large tables into smaller ones and defining relationships between them.

### Denormalization
Denormalization is the process of boosting up database performance and adding redundant data, which helps to get rid of complex data. Denormalization is a part of database optimization techniques.

### Entity
An entity is a set of attributes in a database.

### Entity Type
An entity type is specified as a collection of entities having the same attributes. For example, a student has `student_id`, `department`, and `course` as its characteristics.

### Attribute
An attribute can be defined as the characteristics of the entity. Entities can be uniquely identified using the attributes.

### Non-Prime Attribute
A non-prime attribute is an attribute that does not contribute to the unique identification of a record in a table. Non-prime attributes are also known as non-key attributes.

### Composite Key
A composite key is a key that consists of two or more attributes (columns) that together uniquely identify a record in a table.

### Super Key
A super key is a set of one or more attributes (columns) in a table that can uniquely identify a tuple (row) in that table.

### Candidate Key
A candidate key is a minimal set of attributes (columns) in a table that can uniquely identify a record (row) in that table.

### Foreign Key
A foreign key is a field (or collection of fields) in one table that uniquely identifies a row of another table.

### Primary Key
A primary key is a specific type of candidate key that is chosen to uniquely identify each record in a table. The primary key cannot contain NULL values. Every record must have a value for the primary key. The values of the primary key should not change over time. Once assigned, the primary key value should remain constant.

### Normal Forms

#### First Normal Form (1NF)
- **Definition**: Ensures that each column contains atomic (indivisible) values and each record is unique.
- **Example**: A table with a column that contains a list of phone numbers should be split so that each phone number is in a separate row.

#### Second Normal Form (2NF)
- **Definition**: Eliminates partial dependency, where non-key attributes depend on part of a composite key.
- **Example**: If a table has a composite key (e.g., `StudentID` and `CourseID`), attributes like `CourseName` should depend on `CourseID` alone, not on the combination of `StudentID` and `CourseID`.

#### Third Normal Form (3NF)
- **Definition**: Eliminates transitive dependency, where non-key attributes depend on other non-key attributes.
- **Example**: If `StudentID` determines `AdvisorID`, and `AdvisorID` determines `AdvisorName`, then `AdvisorName` should not be in the same table as `StudentID`.

#### Boyce-Codd Normal Form (BCNF)
- **Definition**: A stricter version of 3NF, ensuring that for every functional dependency \( A \rightarrow B \), \( A \) is a super key.
- **Example**: If a table has a dependency where a non-prime attribute determines a prime attribute, it should be decomposed to satisfy BCNF.

### Locks

#### Shared Lock
A shared lock is required for reading a data item. When more than one transaction is allowed to read the data items, it is known as a shared lock.

#### Exclusive Lock
When any transaction is about to perform a write operation, the lock on the data item is an exclusive lock. Allowing more than one transaction to write would lead to inconsistency in the database.
