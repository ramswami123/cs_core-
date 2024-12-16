# Database Management System (DBMS) Concepts

This document provides an overview of fundamental DBMS concepts.

## Core Concepts

### ACID Properties

ACID properties ensure reliable processing of database transactions:

1.  **Atomicity:** All operations within a transaction are completed successfully, or the entire transaction is rolled back.
    *   Example: A bank transfer requires both debit and credit operations to succeed. If one fails, neither is applied.

2.  **Consistency:** A transaction brings the database from one valid state to another, maintaining all predefined rules and constraints.
    *   Example: Updating account balances must maintain the total balance before and after the transaction.

3.  **Isolation:** Transactions execute independently of each other. Intermediate states are invisible to other transactions.
    *   Example: Two transactions updating the same account must execute sequentially to ensure accurate results.

4.  **Durability:** Once a transaction is committed, it persists even in the event of a system failure.
    *   Example: A completed bank transfer is permanent, even if the system crashes.

### Key Terms

*   **Consistency (Constraints):** Database transactions modify data only according to defined rules (constraints, cascades, triggers).
*   **Checkpoint:** A point in time when the database is in a consistent state with all transactions committed. Used for recovery (log-based recovery).
*   **Redundancy:** Unnecessary data duplication due to poor design, lack of normalization, or intentional replication for backups.
*   **Transparent DBMS:** Hides the physical storage structure from users.
*   **RDBMS (Relational Database Management System):** Stores data in structured tables (rows and columns). Examples: MySQL, PostgreSQL, Oracle.

### Data Models

Conceptual tools for describing data, relationships, semantics, and constraints:

*   **Hierarchical:** Tree-like structure (single parent, multiple children).
*   **Network:** More complex relationships (multiple parents and children).
*   **Relational:** Uses tables (relations), rows (tuples), and columns (attributes).
*   **Entity-Relationship (ER Model):** Diagrams representing entities, attributes, and relationships.

### Data Abstraction Levels

*   **Physical:** How data is physically stored.
*   **Logical:** Structure and relationships of data.
*   **View:** Customized data view for specific users.

## Data Languages

*   **DDL (Data Definition Language):** Defines the database structure. Commands: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME`.
*   **DML (Data Manipulation Language):** Manipulates data. Commands: `SELECT`, `UPDATE`, `INSERT`, `DELETE`. Types: Procedural and Non-Procedural.
*   **DCL (Data Control Language):** Controls user access. Commands: `GRANT`, `REVOKE`.
*   **TCL (Transaction Control Language):** Manages transactions. Commands: `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

## DML Execution Flow

1.  **Parsing:**
    *   **Syntax Analysis:** Checks for syntax errors.
    *   **Semantic Analysis:** Checks for existence and access rights.
2.  **Query Optimization:** Finds the most efficient execution plan.
3.  **Execution Plan Generation.**
4.  **Query Execution Engine.**
5.  **Transaction Management:** Ensures ACID properties.

## Relational Algebra and Query Optimization

*   **Relational Algebra:** A procedural query language operating on relations.
*   **Query Optimization:** Finding the lowest-cost execution plan.

## Durability (Checkpointing)

Ensures committed transactions persist after system failures (achieved by checkpointing).

## Data Integrity and Normalization

*   **Functional Dependency:** Describes relationships between attributes to ensure data integrity and reduce redundancy.
*   **Normalization:** Minimizes redundancy and dependency by dividing tables and defining relationships. Normal forms: 1NF, 2NF, 3NF, BCNF.
*   **Denormalization:** Improves performance by adding redundant data to avoid complex joins.

## Database Components

*   **Entity:** A set of attributes.
*   **Entity Type:** A collection of entities with the same attributes (e.g., Student with student\_id, department, course).
*   **Attribute:** A characteristic of an entity.
*   **Non-prime Attribute:** An attribute not part of any candidate key.

### Key Concepts

*   **Composite Key:** A key composed of multiple attributes.
*   **Super Key:** A set of attributes that uniquely identifies a tuple.
*   **Candidate Key:** A minimal super key.
*   **Primary Key:** A chosen candidate key for unique identification (cannot be NULL, should not change).
*   **Foreign Key:** A field referencing the primary key of another table.

## Normal Forms

*   **1NF:** Atomic column values, unique records. Example: Separate phone numbers into individual rows.
*   **2NF:** Eliminates partial dependency (non-key attributes depend on the entire composite key).
*   **3NF:** Eliminates transitive dependency (non-key attributes depend only on the primary key).
*   **BCNF:** A stricter 3NF; for every dependency A → B, A is a super key.

## Locking

*   **Shared Lock:** Allows concurrent reads.
*   **Exclusive Lock:** Used for write operations, preventing concurrent access.

## Intension vs. Extension

*   **Intension (Schema):** Database structure (tables, columns, data types). Static.
*   **Extension (State/Instance):** Actual data stored in the database. Dynamic.

## Scaling

| Feature        | Vertical Scaling                      | Horizontal Scaling                       |
|----------------|---------------------------------------|-----------------------------------------|
| Approach       | Adding more power to a single machine | Adding more machines to the pool        |
| Implementation | Easier                                | More complex                            |
| Scalability    | Limited by hardware                   | Virtually unlimited                     |
| Cost           | Can be expensive                       | Can be cost-effective                     |
| Fault Tolerance| Limited                                | High                                     |

## Sharding

Dividing a large database into smaller shards for improved performance and scalability. Methods:

1.  Range-Based
2.  Hashed
3.  Directory
4.  Geo

## Indexing

A data structure for faster data retrieval. Types:

1.  **Primary Indexing:** Uses the primary key.
    *   Sparse: References some primary key values.
    *   Dense: References every primary key value.
2.  **Secondary Indexing:** Indexes chunks of sparse index references.
3.  **Cluster Indexing:** Indexes a combination of columns.
4.  **Ordered Index:** Sorted indices.

**Cautions:** Potential for fragmentation and slower write operations.

## B-Trees and B+ Trees

Data structures used for indexing.

*   **B-Tree (m-order):**
    *   `m` child pointers, `m-1` keys per node.
    *   Non-leaf nodes can store data.
    *   Minimum children per node (except root): `ceil(m/2)`.
    *   Root node can have min 2 children
    *   All leaf nodes at the same level (bottom-up implementation).
*   **B+ Tree:**
    *   All data pointers are at leaf nodes.
    *   Leaf nodes are linked as a list.
