**BIRLA INSTITUTE OF TECHNOLOGY & SCIENCE, PILANI**  
**WORK INTEGRATED LEARNING PROGRAMMES**  
**COURSE HANDSON LAB ASSIGNMENT HANDOUT**

**M.Tech**

| Course Title     | Database Systems and Applications          |
| ---------------- | ------------------------------------------ |
| **Course No(s)** | **SESAP ZC337**                            |
| **Credit Units** | **4 Credits, 24 Hours optimized delivery** |
| **Lab Session**  | **Nov-Dec 25**                             |

**Faculty:** Balachandra A, Guest Faculty, BITS Pilani (WILP) Division  
**Email:** balachandra.ananatharamaiah@wilp.bits-pilani.ac.in  
**Mob:** 9113656626 / 9480475967

---

# SOFTWARE REQUIREMENTS SPECIFICATION (SRS) DOCUMENT

## For EMPLOYEE MANAGEMENT Database System PROJECT ASSIGNMENT - DBSA

**Version:** 1.0  
**Prepared by:** Divyansh, Student ID: [Your ID]  
**Date:** November 19, 2025

---

## Contents

**1. Introduction** .......................................................................................................................................3

- 1.1 Purpose........................................................................................................................................3
- 1.2 Scope............................................................................................................................................3
- 1.3 Definitions, Acronyms, and Abbreviations ..............................................................................3
- 1.4 References ...................................................................................................................................4

**2. Overall Description** ..........................................................................................................................4

- 2.1 Product Perspective....................................................................................................................4
- 2.2 Product Functions.......................................................................................................................4
- 2.3 User Characteristics...................................................................................................................5
- 2.4 Constraints..................................................................................................................................5
- 2.5 Assumptions and Dependencies.................................................................................................5
- 2.6 Database Normalization Strategy.............................................................................................5

**3. Specific Requirements**.......................................................................................................................6

- 3.1 Functional Requirements...........................................................................................................6
- 3.2 Non-Functional Requirements ..................................................................................................8

**4. Database Design**................................................................................................................................9

- 4.1 Entity and Attribute Definitions ...............................................................................................9
- 4.2 Relational Schema (DDL) ..........................................................................................................9
- 4.3 Normalization Process................................................................................................................12
- 4.4 Advanced Joins and Analytical Views (Level 7 Optimization) ..............................................12
- 4.5 Table Definitions (Core Schema with Indexes) .....................................................................13

**5. System Features**................................................................................................................................13

- 5.1 Data Integrity..............................................................................................................................13
- 5.2 Normalization .............................................................................................................................14
- 5.3 Reporting Queries (Examples) ..................................................................................................14
- 5.4 Effective Joins (Level 7 Feature)...............................................................................................14

**6. External Interface Requirements**....................................................................................................15

**7. Validation and Verification** .............................................................................................................15

**8. Appendix** ...........................................................................................................................................16

- 8.1 Future Enhancements ................................................................................................................16
- 8.2 Document History.......................................................................................................................16

---

# 📄 SRS Document 1: Employee Management Database System

## _Formalization of Term I Prototype_

---

## 1. Introduction

### 1.1 Purpose

This Software Requirements Specification (SRS) defines the requirements for the Employee Management Database System, designed to manage employee, department, project, and dependent information with advanced normalization (up to BCNF) and optimized join operations. The document specifies all functional and non-functional requirements, database schema constraints, and user interactions. It serves as a reference for database developers and system evaluators. The system supports efficient data access, analytical queries, and integrity enforcement across interconnected entities such as employees, departments, projects, and dependents.

### 1.2 Scope

The Employee Management Database System automates data management for a company's core operations.

**Functions include:**

- Maintaining employee personal and employment details
- Tracking departmental structure and managers
- Recording projects and their associated departments
- Tracking employee participation in projects and dependents

**Database is a normalized relational system supporting:**

- Employee, department, project, and dependent management
- Recursive relationships (supervision)
- Multi-entity joins and derived reporting
- The system ensures data integrity, referential consistency, and normalization (3NF/BCNF)
- Data models optimized through BCNF to ensure minimal redundancy and fast join performance
- **Future provisions for multimodal extensions (Image/Spatial data)**

### 1.3 Definitions, Acronyms, and Abbreviations

| **Term**    | **Meaning**                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------- |
| **DBMS**    | Database Management System                                                                               |
| **SRS**     | Software Requirements Specification                                                                      |
| **DDL**     | Data Definition Language                                                                                 |
| **DML**     | Data Manipulation Language                                                                               |
| **PK**      | Primary Key                                                                                              |
| **FK**      | Foreign Key                                                                                              |
| **SQL**     | Structured Query Language                                                                                |
| **BCNF**    | Boyce-Codd Normal Form - Advanced database normalization eliminating all functional dependency anomalies |
| **CRUD**    | Create, Read, Update, Delete operations                                                                  |
| **SQLite3** | Lightweight relational database management system                                                        |
| **BLOB**    | Binary Large Object for storing multimodal data                                                          |

### 1.4 References

- **Term I Assignment Implementation Report** (DivyanshDBSA.pdf)
- **IEEE 830–1998, ISO/IEC/IEEE 29148:2018** - Systems and Software Engineering Requirements
- **Elmasri & Navathe, Fundamentals of Database Systems, 7th Ed.**
- **Database System Concepts** - Silberschatz, Korth, Sudarshan
- **SQLite Documentation** - Official SQLite3 Reference

---

## 2. Overall Description

### 2.1 Product Perspective

The Employee Management Database System is a relational database developed using SQL and runs under SQLite3 RDBMS, with full-stack implementation using React.js and Node.js.

It is a central data store for all company divisions and will be integrated with future applications such as payroll or project tracking tools. The system is designed with **provisions for multimodal extensions** including Image/Document storage (BLOB) and Spatial data capabilities.

### 2.2 Product Functions

- Manage employees and departments
- Assign managers to departments
- Record projects and link them to departments
- Track which employees work on which projects
- Record employee dependents
- Generate summary and analytical queries
- **Future capability:** Store and manage employee profile photos (Image Extension)
- **Future capability:** Geographic location tracking for departments and projects (Spatial Extension)

### 2.3 User Characteristics

| **User Role**              | **Description**                                                      |
| -------------------------- | -------------------------------------------------------------------- |
| **Database Administrator** | Defines database schema, manages users, backups, system maintenance  |
| **HR Manager**             | Maintains employee, department, dependent data with full CRUD access |
| **Project Manager**        | Manages project details and employee assignments                     |
| **Employee**               | Read-only access to personal data and project assignments            |

### 2.4 Constraints

- The database must be in **Boyce-Codd Normal Form (BCNF)** or higher
- All referential integrity constraints must be enforced through FKs
- Access control must restrict schema modification to the Administrator
- Must use standard SQL DDL/DML commands
- Web-based interface for cross-platform accessibility
- SQLite3 for lightweight deployment

### 2.5 Assumptions and Dependencies

- Each employee belongs to one department
- Each department has exactly one manager
- Each project belongs to one department
- The system depends on an underlying SQL RDBMS environment
- Single organizational unit deployment
- English language interface
- Standard web browser compatibility required

### 2.6 Database Normalization Strategy

The database uses progressive normalization up to **BCNF** to:

- Ensure atomic attribute dependencies
- Eliminate redundancy and update anomalies
- Improve consistency in join-based queries (especially analytical joins)
- Maintain **future extensibility** for multimodal data types (BLOB for images, Spatial for geographic data)

---

## 3. Specific Requirements

### 3.1 Functional Requirements

| **ID**   | **Requirement Description**                                                                                                                          | **Priority** |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| **FR1**  | The system shall allow creation of new Employee records, including SSN, Name, Birth Date, Address, Sex, Salary, Department No, and Supervisor SSN.   | High         |
| **FR2**  | The system shall allow retrieval and listing of all Employees with their related Department, Supervisor, and Project Assignments.                    | High         |
| **FR3**  | The system shall allow updating Employee attributes except the primary key (SSN).                                                                    | High         |
| **FR4**  | The system shall allow deletion of an Employee only if referential constraints (e.g., dependents, assignments) permit.                               | High         |
| **FR5**  | The system shall allow creation of new Departments with Department Number, Name, Manager SSN, and Start Date.                                        | High         |
| **FR6**  | The system shall allow updating Department details, including Manager assignment.                                                                    | Medium       |
| **FR7**  | The system shall allow deletion of Departments with proper restriction checks.                                                                       | Medium       |
| **FR8**  | The system shall allow creation of Project records with Project Number, Name, Location, and owning Department Number.                                | High         |
| **FR9**  | The system shall allow updating Project details and Department assignment.                                                                           | Medium       |
| **FR10** | The system shall allow deleting Projects and automatically remove related Work Assignments.                                                          | Medium       |
| **FR11** | The system shall allow assigning an Employee to a Project with recorded weekly Hours (0–80).                                                         | High         |
| **FR12** | The system shall allow updating the Hours in a Work Assignment.                                                                                      | Medium       |
| **FR13** | The system shall allow removing an Employee–Project assignment.                                                                                      | Medium       |
| **FR14** | The system shall allow creation of Dependent records linked to Employees.                                                                            | Medium       |
| **FR15** | The system shall allow updating and deleting Dependent records.                                                                                      | Medium       |
| **FR16** | The system shall enforce referential integrity between Employees–Departments, Employees–Supervisors, Projects–Departments, and Dependents–Employees. | High         |
| **FR17** | The system shall allow execution of join queries combining Employees, Departments, Projects, Supervisors, and Dependents.                            | High         |
| **FR18** | The system shall allow displaying Employee supervisory hierarchy (recursive self-join).                                                              | Medium       |
| **FR19** | The system shall allow searching/filtering across all entity categories.                                                                             | Medium       |
| **FR20** | The system shall allow consistent CRUD operations through the React front-end with backend validation.                                               | High         |

### 3.2 Non-Functional Requirements

| **ID**    | **Category**    | **Requirement Description**                                                                                   | **Priority** |
| --------- | --------------- | ------------------------------------------------------------------------------------------------------------- | ------------ |
| **NFR1**  | Performance     | Query execution for up to 1,000 rows shall complete within 2 seconds.                                         | High         |
| **NFR2**  | Performance     | Joins involving up to 4 tables (Employee–Works_On–Project–Department) shall execute under 3 seconds.          | High         |
| **NFR3**  | Reliability     | The system shall enforce PK, FK, CHECK, and NOT NULL constraints to prevent invalid data insertion.           | High         |
| **NFR4**  | Reliability     | Delete operations shall follow cascade/restrict rules to ensure no orphan records.                            | High         |
| **NFR5**  | Security        | User input to the backend shall be validated to prevent SQL injection.                                        | High         |
| **NFR6**  | Security        | Only authorized backend endpoints may modify database records.                                                | High         |
| **NFR7**  | Maintainability | The schema shall be structured in BCNF to reduce anomalies and ease schema evolution.                         | Medium       |
| **NFR8**  | Scalability     | The system architecture (React + Node + SQLite) shall support migration to PostgreSQL/MySQL without redesign. | Medium       |
| **NFR9**  | Usability       | UI forms shall validate all inputs client-side before sending to backend.                                     | Medium       |
| **NFR10** | Availability    | The system shall ensure ACID-compliant commits via SQLite transaction support.                                | Medium       |

---

## 4. Database Design

### 4.1 Entity and Attribute Definitions

1. **EMPLOYEE**(SSN, Name, Birth_Date, Address, Sex, Salary, Supervisor_SSN, Dept_No)
2. **DEPARTMENT**(Dnumber, Dname, Location, Manager_SSN, Mgr_start_date)
3. **PROJECT**(Pnumber, Pname, Plocation, Dnum)
4. **WORKS_ON**(Essn, Pno, Hours)
5. **DEPENDENT**(ID, Essn, Dependent_name, Sex, Bdate, Relationship)

### 4.2 Relational Schema (DDL)

````sql
-- Department Entity (Created first due to FK dependencies)
CREATE TABLE DEPARTMENT (
    Dnumber INTEGER PRIMARY KEY,
    Dname VARCHAR(50) UNIQUE NOT NULL,
    Location VARCHAR(100),
    Manager_SSN VARCHAR(11) UNIQUE,
    Mgr_start_date DATE NOT NULL
);

-- Employee Entity
CREATE TABLE EMPLOYEE (
    SSN VARCHAR(11) PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Birth_Date DATE,
    Address VARCHAR(200),
    Sex CHAR(1) CHECK(Sex IN ('M','F')),
    Salary DECIMAL(10,2) CHECK(Salary > 0),
    Supervisor_SSN VARCHAR(11),
    Dept_No INTEGER,
    FOREIGN KEY (Supervisor_SSN) REFERENCES EMPLOYEE(SSN),
    FOREIGN KEY (Dept_No) REFERENCES DEPARTMENT(Dnumber)
);

-- Add Manager FK constraint after EMPLOYEE table exists
ALTER TABLE DEPARTMENT
ADD FOREIGN KEY (Manager_SSN) REFERENCES EMPLOYEE(SSN);

-- Project Entity
CREATE TABLE PROJECT (
    Pnumber INTEGER PRIMARY KEY,
    Pname VARCHAR(100) UNIQUE NOT NULL,
    Plocation VARCHAR(50),
    Dnum INTEGER,
    FOREIGN KEY (Dnum) REFERENCES DEPARTMENT(Dnumber)
);

-- Works_On/Assignment Entity
CREATE TABLE WORKS_ON (
    Essn VARCHAR(11),
    Pno INTEGER,
    Hours DECIMAL(4,1) CHECK(Hours BETWEEN 0 AND 80),
    PRIMARY KEY (Essn, Pno),
    FOREIGN KEY (Essn) REFERENCES EMPLOYEE(SSN),
    FOREIGN KEY (Pno) REFERENCES PROJECT(Pnumber)
);

-- Dependent Entity
CREATE TABLE DEPENDENT (
    ID INTEGER PRIMARY KEY AUTOINCREMENT,
    Essn VARCHAR(11),
    Dependent_name VARCHAR(50),
    Sex CHAR(1) CHECK(Sex IN ('M','F')),
    Bdate DATE,
    Relationship VARCHAR(20) CHECK(Relationship IN ('Spouse','Son','Daughter','Parent','Other')),
    FOREIGN KEY (Essn) REFERENCES EMPLOYEE(SSN) ON DELETE CASCADE
);
````

### 4.3 Normalization Process

| **Normal Form** | **Description** | **Achieved Purpose** |
|-----------------|-----------------|---------------------|
| **1NF** | Atomic attribute values; repeating groups removed | Each column contains indivisible data |
| **2NF** | Non-key attributes depend on full PK | Partial dependencies removed |
| **3NF** | Transitive dependencies removed | No non-key attribute depends on another non-key |
| **BCNF** | Every determinant is a candidate key | Functional dependencies refined |

**Result:** Each table in Employee Management DB is in **BCNF**, allowing optimal join-based query decomposition.
The EMPLOYEE–WORKS_ON–PROJECT join is lossless, maintaining full consistency.

### 4.4 Advanced Joins and Analytical Views (Level 7 Optimization)

**Example Derived Views:**

```sql
-- Comprehensive Employee-Project View
CREATE VIEW EMP_PROJECT_VIEW AS
SELECT E.SSN, E.Name, D.Dname AS Department, P.Pname AS Project, W.Hours
FROM EMPLOYEE E
JOIN WORKS_ON W ON E.SSN = W.Essn
JOIN PROJECT P ON P.Pnumber = W.Pno
JOIN DEPARTMENT D ON D.Dnumber = E.Dept_No;

-- Management Hierarchy View
CREATE VIEW MANAGEMENT_HIERARCHY AS
SELECT E.SSN, E.Name AS Employee, S.Name AS Supervisor, D.Dname AS Department
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE S ON E.Supervisor_SSN = S.SSN
JOIN DEPARTMENT D ON E.Dept_No = D.Dnumber;
````

**Example Analytical Queries:**

- Q1: List total hours each employee worked per project
- Q2: Find employees supervised by a manager working on the same project
- Q3: Aggregate average salary per department
- Q4: Identify departments managing projects at multiple locations

**Performance Optimization:**

- Create indexes on all FK columns (e.g., Essn, Pno, Dept_No)
- Use materialized views for complex analytical joins
- Employ query rewriting for automatic join optimization

### 4.5 Table Definitions (Core Schema with Indexes)

```sql
-- Performance Indexes for Join Optimization
CREATE INDEX idx_employee_dept_no ON EMPLOYEE(Dept_No);
CREATE INDEX idx_employee_supervisor ON EMPLOYEE(Supervisor_SSN);
CREATE INDEX idx_works_on_essn ON WORKS_ON(Essn);
CREATE INDEX idx_works_on_pno ON WORKS_ON(Pno);
CREATE INDEX idx_project_dnum ON PROJECT(Dnum);
CREATE INDEX idx_dependent_essn ON DEPENDENT(Essn);
```

These indexes support high-performance joins in analytical workloads and ensure optimal query execution times.

---

## 5. System Features

### 5.1 Data Integrity Features

| Feature                    | Implementation                               | Benefit                                           |
| -------------------------- | -------------------------------------------- | ------------------------------------------------- |
| **Normalization**          | BCNF schema design                           | Eliminates update anomalies and data redundancy   |
| **Constraint Enforcement** | CHECK, UNIQUE, NOT NULL constraints          | Ensures data quality and business rule compliance |
| **Referential Integrity**  | Foreign key constraints with CASCADE options | Maintains relationship consistency                |
| **Transaction Support**    | ACID-compliant operations                    | Ensures data consistency during concurrent access |

### 5.2 Reporting and Query Capabilities

#### Supported Query Types

- **Employee-Department Joins**: Manager and departmental reporting
- **Project-Assignment Analysis**: Resource allocation and workload distribution
- **Hierarchical Queries**: Supervisory relationship traversal
- **Aggregate Reporting**: Salary statistics, project hours summation
- **Cross-Entity Analytics**: Multi-table complex reporting

### 5.3 Advanced Features

- **Recursive Relationships**: Employee supervisory hierarchy management
- **Composite Keys**: Multi-attribute primary keys for dependent and assignment entities
- **Temporal Data**: Manager start dates and dependent birthdates
- **Gender Constraints**: Validated enumeration values

---

## 6. External Interface Requirements

| **Interface Type** | **Description**                                                                                             |
| ------------------ | ----------------------------------------------------------------------------------------------------------- |
| **User Interface** | React.js web application with responsive design; SQL console/DBMS GUI compatibility                         |
| **Hardware**       | Standard server/workstation: 4GB RAM, Dual-core 2.0 GHz, 500MB storage, Broadband network                   |
| **Software**       | SQLite3 RDBMS, Node.js runtime (16.x+), Modern web browsers (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+) |
| **Communication**  | RESTful APIs for client-server communication; Local DB connection (JDBC/ODBC compatible)                    |

**Integration Capability:**  
Supports integration with data analytics tools (e.g., Power BI, Tableau, or SQL-based dashboards) for join-based queries and reporting.

---

## 7. Validation and Verification

### 7.1 Test Cases

| **Test ID** | **Test Category**     | **Test Description**                       | **Input**                            | **Expected Result**                               | **Priority** |
| ----------- | --------------------- | ------------------------------------------ | ------------------------------------ | ------------------------------------------------- | ------------ |
| **T1**      | Referential Integrity | Insert Employee with valid Department      | Dept_No exists in DEPARTMENT         | Insert successful                                 | High         |
| **T2**      | Referential Integrity | Insert Employee with invalid Dept_No       | Dept_No = 999 (non-existent)         | FK violation error                                | High         |
| **T3**      | Data Integrity        | Insert Employee with negative salary       | Salary = -100                        | CHECK constraint violation                        | High         |
| **T4**      | Business Logic        | Assign Employee to Project with >80 hours  | Hours = 120                          | CHECK constraint failure (Hours BETWEEN 0 AND 80) | High         |
| **T5**      | Cascade Operations    | Delete Employee who has Dependents         | Employee SSN referenced in DEPENDENT | Dependent records cascade deleted                 | High         |
| **T6**      | Complex Queries       | Execute 4-table join query                 | Employee–Works_On–Project–Department | Correct combined dataset within 3 seconds         | Medium       |
| **T7**      | Primary Key           | Insert Employee with duplicate SSN         | Existing SSN value                   | PK violation error                                | High         |
| **T8**      | Referential Integrity | Insert Dependent for non-existent Employee | SSN not found in EMPLOYEE            | FK violation error                                | Medium       |
| **T9**      | Supervisory Hierarchy | Display Employee supervisory chain         | Recursive self-join query            | Correct hierarchical display                      | Medium       |
| **T10**     | Unique Constraints    | Insert Department with duplicate name      | Existing Department name             | UNIQUE constraint violation                       | Medium       |

### 7.2 Verification Methods

| Verification Type       | Method                                      | Coverage                        |
| ----------------------- | ------------------------------------------- | ------------------------------- |
| **Schema Validation**   | DDL script execution and constraint testing | Database structure integrity    |
| **Functional Testing**  | CRUD operation validation for all entities  | Complete functionality coverage |
| **Performance Testing** | Query execution time measurement            | System performance requirements |
| **Integration Testing** | End-to-end workflow validation              | System component interaction    |

---

## 8. Appendix

### 8.1 Future Enhancements

- **Add Image Storage (BLOB)** for employee profile photos - **[IMPLEMENTED IN SRS DOCUMENT 2]**
- Add spatial attributes (e.g., project site geometry)
- Implement temporal tables for salary history tracking
- Advanced analytics and business intelligence dashboards
- Mobile application development
- Real-time data synchronization capabilities

### 8.2 Document History

| **Version** | **Date**     | **Description**                                                           |
| ----------- | ------------ | ------------------------------------------------------------------------- |
| **1.0**     | **Nov 2025** | Initial draft for normalized Employee Management DB with BCNF achievement |

---

**Compliance:**  
This enhanced SRS complies with **IEEE 830 and ISO/IEC/IEEE 29148**, including:

- Structured requirement hierarchy
- Full traceability of normalization design
- Testability of join and view operations
- Integration readiness for analytical tools

---

**Page 1 of 2**

---

---

# SOFTWARE REQUIREMENTS SPECIFICATION (SRS) DOCUMENT

## For EMPLOYEE PROFILE PHOTO EXTENSION - MULTIMODAL MODULE

**Version:** 1.0  
**Prepared by:** Divyansh, Student ID: [Your ID]  
**Date:** November 19, 2025  
**Extension Type:** Image/Document Storage (BLOB Implementation)

---

**Document Version**: 1.0  
**Last Updated**: November 19, 2025  
**Status**: Final for Term II Submission

---

**BIRLA INSTITUTE OF TECHNOLOGY & SCIENCE, PILANI**  
**WORK INTEGRATED LEARNING PROGRAMMES**  
**COURSE HANDSON LAB ASSIGNMENT HANDOUT**

**M.Tech**

| Course Title     | Database Systems and Applications          |
| ---------------- | ------------------------------------------ |
| **Course No(s)** | **SESAP ZC337**                            |
| **Credit Units** | **4 Credits, 24 Hours optimized delivery** |
| **Lab Session**  | **Nov-Dec 25**                             |

**Faculty:** Balachandra A, Guest Faculty, BITS Pilani (WILP) Division  
**Email:** balachandra.ananatharamaiah@wilp.bits-pilani.ac.in  
**Mob:** 9113656626 / 9480475967

---

# SOFTWARE REQUIREMENTS SPECIFICATION (SRS) DOCUMENT

## For EMPLOYEE PROFILE PHOTO EXTENSION - MULTIMODAL MODULE

**Version:** 1.0  
**Prepared by:** Divyansh, Student ID: [Your ID]  
**Date:** November 19, 2025  
**Extension Type:** Image/Document Storage (BLOB Implementation)

---

## Contents

**1. Introduction** .......................................................................................................................................3

- 1.1 Purpose........................................................................................................................................3
- 1.2 Scope............................................................................................................................................3
- 1.3 Extension Rationale...................................................................................................................3
- 1.4 References ...................................................................................................................................4

**2. Overall Description** ..........................................................................................................................4

- 2.1 Product Functions Extension....................................................................................................4
- 2.2 User Interaction Model.............................................................................................................4
- 2.3 Integration Strategy..................................................................................................................4
- 2.4 Constraints and Dependencies..................................................................................................5

**3. Specific Requirements**.......................................................................................................................5

- 3.1 Functional Requirements (FR-M)..............................................................................................5
- 3.2 Non-Functional Requirements (NFR-M)...................................................................................6

**4. Extended Database Design**................................................................................................................7

- 4.1 Extended EMPLOYEE Table DDL...............................................................................................7
- 4.2 Schema Integration and BCNF Compliance..............................................................................7
- 4.3 Storage Strategy and Implementation......................................................................................8
- 4.4 Multimodal Data Handling........................................................................................................8

**5. System Integration**............................................................................................................................8

- 5.1 API Endpoints.............................................................................................................................8
- 5.2 Frontend Integration..................................................................................................................9
- 5.3 Backend Integration...................................................................................................................9

**6. Validation and Verification** .............................................................................................................9

- 6.1 Image Module Test Cases..........................................................................................................9
- 6.2 Integration Test Cases...............................................................................................................10

**7. Implementation Guidelines**..............................................................................................................10

- 7.1 Development Phases..................................................................................................................10
- 7.2 Technical Implementation........................................................................................................11
- 7.3 Success Metrics.........................................................................................................................11

**8. Appendix** ...........................................................................................................................................11

- 8.1 Future Multimodal Enhancements..........................................................................................11
- 8.2 Document History.....................................................................................................................11

---

## 1. Introduction

### 1.1 Purpose

This Software Requirements Specification (SRS) defines the requirements for the **Employee Profile Photo Extension**, a multimodal module designed to extend the existing Employee Management Database System with image storage capabilities. The extension adds Employee Profile Photo functionality using BLOB data types, demonstrating advanced database features and fulfilling the multimodal provisions designed in Term I. This document specifies all functional and non-functional requirements for the image extension, database schema modifications, and integration procedures. It serves as a reference for database developers implementing multimodal data capabilities and system evaluators assessing the extension's compliance with the base system architecture.

### 1.2 Scope

The Employee Profile Photo Extension automates image management for employee identification within the company database system.

**Functions include:**

- Upload and storage of employee profile photographs
- Secure image retrieval and display operations
- File validation and size restriction enforcement
- Integration with existing Employee Management CRUD operations

**Extension is a multimodal database enhancement supporting:**

- BLOB data type implementation within existing BCNF schema
- Backward compatibility with all existing system operations
- Standard image format support (JPEG, PNG) with security validation
- **The extension maintains data integrity, referential consistency, and BCNF normalization**
- **Demonstrates practical implementation of multimodal database provisions from Term I design**

### 1.3 Extension Rationale

This implementation demonstrates the **future-ready multimodal architecture** designed in Term I, specifically utilizing the BLOB storage provisions for Image/Document data as outlined in the original system design. The extension validates the extensibility principles built into the normalized schema and provides a foundation for additional multimodal capabilities.

### 1.4 References

- **Base Employee Management System SRS Document 1** (Current submission)
- **Term I Assignment Implementation Report** (DivyanshDBSA.pdf, Section 8.2, p. 34)
- **IEEE 830–1998, ISO/IEC/IEEE 29148:2018** - Systems and Software Engineering Requirements
- **SQLite BLOB Documentation** - Official SQLite3 Binary Data Reference
- **React.js Documentation** - Component Integration Guidelines

---

## 2. Overall Description

### 2.1 Product Functions Extension

The Employee Profile Photo Extension integrates with the existing Employee Management Database System developed using React.js, Node.js, and SQLite3. It extends the base system's capabilities without modifying core functionality.

**New capabilities include:**

- Upload, store, retrieve, and display employee profile photos
- File type, size, and security validation for image uploads
- Visual employee identification through profile photos
- Efficient BLOB handling within SQLite3 architecture
- **Integration with existing Employee detail views and listing pages**

### 2.2 User Interaction Model

| **User Role**              | **Image Module Access**                                         | **Operations Permitted**                                        |
| -------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| **Database Administrator** | System-level image storage management and optimization          | Full schema modification, backup operations including BLOB data |
| **HR Manager**             | Full CRUD access to employee profile photos                     | Upload, update, delete employee photos; bulk photo management   |
| **Project Manager**        | Read-only access to view employee photos in project assignments | View photos in project team listings and reports                |
| **Employee**               | View personal profile photo; request photo updates              | Personal photo viewing; update requests through HR              |

### 2.3 Integration Strategy

The extension follows the **principle of minimal disruption** to existing system architecture:

- **Database Level:** Addition of single BLOB column to existing EMPLOYEE table
- **API Level:** New RESTful endpoints for image operations alongside existing employee endpoints
- **Frontend Level:** Enhancement of existing React components with image display and upload capabilities
- **Security Level:** Extension of existing validation framework to include file security checks

### 2.4 Constraints and Dependencies

- **Schema Constraint:** Must maintain BCNF normalization of base Employee Management schema
- **Technology Constraint:** Must integrate seamlessly with existing React.js + Node.js + SQLite3 stack
- **Performance Constraint:** Image operations must not degrade existing system performance
- **Security Constraint:** Image storage must follow same security principles as base system
- **Backward Compatibility:** All existing Employee Management operations must remain functional

---

## 3. Specific Requirements (Image Extension)

### 3.1 Functional Requirements (FR-M)

| **ID**    | **Requirement Description**                                                                  | **Priority** |
| --------- | -------------------------------------------------------------------------------------------- | ------------ |
| **FR-M1** | The system shall allow authorized users to upload an Employee profile photo.                 | High         |
| **FR-M2** | The system shall validate uploaded files to ensure they are of type JPEG or PNG.             | High         |
| **FR-M3** | The system shall store the uploaded photo as a BLOB in the EMPLOYEE table.                   | High         |
| **FR-M4** | The system shall allow updating/replacing an existing Employee profile photo.                | Medium       |
| **FR-M5** | The system shall allow displaying the stored profile photo on the Employee detail view.      | High         |
| **FR-M6** | The system shall prevent upload of files larger than the configured size limit (5 MB).       | High         |
| **FR-M7** | The backend shall sanitize file names and prevent arbitrary file access.                     | High         |
| **FR-M8** | The system shall provide fallback placeholder images when an Employee has no photo uploaded. | Medium       |

### 3.2 Non-Functional Requirements (NFR-M)

| **ID**     | **Category**    | **Requirement Description**                                                               | **Priority** |
| ---------- | --------------- | ----------------------------------------------------------------------------------------- | ------------ |
| **NFR-M1** | Performance     | Image loading should not exceed 1 second on a standard network.                           | High         |
| **NFR-M2** | Performance     | Images shall be compressed (if stored as files) to optimize load time.                    | Medium       |
| **NFR-M3** | Security        | The system shall not expose direct file paths; signed URLs or APIs shall be used.         | High         |
| **NFR-M4** | Security        | Uploaded files must be scanned/validated for MIME correctness.                            | High         |
| **NFR-M5** | Domain          | Maximum supported file size is 5 MB.                                                      | High         |
| **NFR-M6** | Domain          | Supported formats are PNG and JPEG only.                                                  | High         |
| **NFR-M7** | Maintainability | The addition of BLOBs must not require changes to existing CRUD operations.               | Medium       |
| **NFR-M8** | Scalability     | The schema should allow migration to cloud storage (AWS S3/GCP) without breaking changes. | Medium       |

---

## 4. Extended Database Design

### 4.1 Extended EMPLOYEE Table DDL

**Primary Extension:** Addition of Profile_Photo BLOB column to existing normalized schema

```sql
-- Extension DDL for Employee Management Database
-- Adds multimodal image storage capability while maintaining BCNF

ALTER TABLE EMPLOYEE
ADD COLUMN Profile_Photo BLOB;

-- Optional: Add metadata columns for enhanced image management
-- ALTER TABLE EMPLOYEE
-- ADD COLUMN Photo_Upload_Date DATETIME DEFAULT CURRENT_TIMESTAMP;
-- ALTER TABLE EMPLOYEE
-- ADD COLUMN Photo_File_Size INTEGER;
-- ALTER TABLE EMPLOYEE
-- ADD COLUMN Photo_MIME_Type VARCHAR(50);
```

### 4.2 Schema Integration and BCNF Compliance

The image extension maintains **full BCNF compliance** of the existing Employee Management schema:

```sql
-- Complete Extended EMPLOYEE Schema (BCNF Maintained)
EMPLOYEE (
    SSN VARCHAR(11) PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Birth_Date DATE,
    Address VARCHAR(200),
    Sex CHAR(1) CHECK(Sex IN ('M','F')),
    Salary DECIMAL(10,2) CHECK(Salary > 0),
    Dept_No INTEGER REFERENCES DEPARTMENT(Dnumber),
    Supervisor_SSN VARCHAR(11) REFERENCES EMPLOYEE(SSN),
    Profile_Photo BLOB  -- NEW: Image storage capability
);
```

**BCNF Verification:**

- Profile_Photo depends solely on SSN (primary key)
- No new functional dependencies introduced
- All existing dependencies remain valid
- Extension preserves all referential integrity constraints

### 4.3 Storage Strategy and Implementation

| **Approach**          | **Implementation**                          | **Advantages**                                                | **Trade-offs**                                          | **Selected** |
| --------------------- | ------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------- | ------------ |
| **BLOB Storage**      | Direct binary storage in SQLite             | Simple backup, transaction consistency, referential integrity | Database size growth, memory usage                      | ✅ **YES**   |
| **File Path Storage** | Store file paths, images in filesystem      | Smaller database size, easier file management                 | Complex backup procedures, broken referential integrity | ❌ No        |
| **Hybrid Approach**   | Small images in BLOB, large images as files | Balanced performance and storage                              | Increased complexity                                    | ❌ No        |

**Selected Approach Justification:** **BLOB Storage** demonstrates the multimodal BLOB provisions from Term I design and maintains the integrity principles of the normalized database system.

### 4.4 Multimodal Data Handling

**Data Type Specifications:**

- **Storage Format:** SQLite BLOB (Binary Large Object)
- **Maximum Size:** 5 MB per image (application-enforced)
- **Supported Formats:** JPEG, PNG (MIME validation enforced)
- **Compression:** Client-side compression recommended before upload
- **Retrieval Method:** Base64 encoding for web display or direct binary transfer

---

## 5. System Integration

### 5.1 API Endpoints

| **Endpoint**               | **Method** | **Function**             | **Request Body**                    | **Response**                                     | **Status Codes**   |
| -------------------------- | ---------- | ------------------------ | ----------------------------------- | ------------------------------------------------ | ------------------ |
| `/api/employees/:id/photo` | **GET**    | Retrieve employee photo  | None                                | Binary image data or placeholder                 | 200, 404, 500      |
| `/api/employees/:id/photo` | **POST**   | Upload new profile photo | multipart/form-data with image file | `{"success": true, "message": "Photo uploaded"}` | 201, 400, 413, 422 |
| `/api/employees/:id/photo` | **PUT**    | Update existing photo    | multipart/form-data with image file | `{"success": true, "message": "Photo updated"}`  | 200, 400, 404, 413 |
| `/api/employees/:id/photo` | **DELETE** | Remove profile photo     | None                                | `{"success": true, "message": "Photo deleted"}`  | 200, 404, 500      |

**API Integration with Base System:**

- Photo endpoints extend existing `/api/employees` API structure
- Consistent authentication and authorization with base employee endpoints
- Error handling follows same patterns as base system
- Request/response format maintains API consistency

### 5.2 Frontend Integration

**React Component Extensions:**

| **Component**        | **Enhancement**                                           | **Integration Point**                    |
| -------------------- | --------------------------------------------------------- | ---------------------------------------- |
| **EmployeeCard**     | Display thumbnail profile photos (64x64px)                | Employee listing pages, search results   |
| **EmployeeDetails**  | Full-size photo display (200x200px) with upload interface | Employee detail view, profile management |
| **PhotoUpload**      | Drag-and-drop image upload with preview and validation    | Employee creation/edit forms             |
| **ImageValidator**   | Client-side file validation (type, size) before upload    | All photo upload interfaces              |
| **PhotoPlaceholder** | Default avatar display when no photo exists               | All employee display contexts            |

**UI Integration Strategy:**

- **Non-intrusive Design:** Photo features integrate seamlessly without disrupting existing UI flow
- **Progressive Enhancement:** System functions normally even if image features fail
- **Responsive Design:** Photo displays adapt to mobile and desktop viewports
- **Accessibility:** Alt text and screen reader support for all image elements

### 5.3 Backend Integration

**Node.js Integration Points:**

```javascript
// Example integration with existing Employee controller
const employeeController = {
  // Existing methods remain unchanged
  getEmployee: async (req, res) => {
    /* existing code */
  },
  createEmployee: async (req, res) => {
    /* existing code */
  },
  updateEmployee: async (req, res) => {
    /* existing code */
  },

  // New photo-specific methods
  getEmployeePhoto: async (req, res) => {
    // BLOB retrieval and binary response
  },
  uploadEmployeePhoto: async (req, res) => {
    // File validation, BLOB storage
  },
};
```

**Database Integration:**

- **Connection Reuse:** Photo operations use existing SQLite connection pool
- **Transaction Management:** Photo uploads participate in existing transaction framework
- **Error Handling:** Photo errors integrate with existing error middleware
- **Logging:** Photo operations logged through existing system logger

---

## 6. Validation and Verification (Image Extension)

### 6.1 Image Module Test Cases

| **Test ID** | **Test Category**    | **Test Description**           | **Input**                              | **Expected Result**                         | **Priority** |
| ----------- | -------------------- | ------------------------------ | -------------------------------------- | ------------------------------------------- | ------------ |
| **T-M1**    | File Size Validation | Upload file >5MB               | 6 MB JPEG image                        | Upload rejected with size limit error       | High         |
| **T-M2**    | File Type Validation | Upload invalid format          | PDF file disguised as image            | Upload rejected with format error           | High         |
| **T-M3**    | Successful Upload    | Upload valid image             | 200 KB JPEG image                      | Image stored successfully in BLOB           | High         |
| **T-M4**    | Image Retrieval      | Retrieve existing photo        | GET /api/employees/123/photo           | Image displays correctly                    | High         |
| **T-M5**    | Missing Image        | Retrieve non-existent photo    | GET /api/employees/999/photo           | Placeholder image returned                  | Medium       |
| **T-M6**    | Photo Replacement    | Replace existing image         | Upload new image for existing employee | Old BLOB replaced with new image            | Medium       |
| **T-M7**    | Security Validation  | MIME type spoofing attempt     | Malicious file with image extension    | Upload blocked by MIME validation           | High         |
| **T-M8**    | Performance Test     | Load employee list with photos | 50 employees with profile photos       | All images load within 1-second requirement | Medium       |

### 6.2 Integration Test Cases

| **Test ID** | **Test Description**                                           | **Expected Result**                       |
| ----------- | -------------------------------------------------------------- | ----------------------------------------- |
| **T-I1**    | Existing CRUD operations remain functional after BLOB addition | All original functionality unaffected     |
| **T-I2**    | Database backup includes BLOB data                             | Complete system restore with images       |
| **T-I3**    | Employee deletion cascades properly with image data            | BLOB data cleaned up with employee record |

---

## 7. Implementation Guidelines

### 7.1 Development Phases

| **Phase**   | **Deliverable**                                   | **Timeline** | **Dependencies**                             | **Success Criteria**                                  |
| ----------- | ------------------------------------------------- | ------------ | -------------------------------------------- | ----------------------------------------------------- |
| **Phase 1** | Extended DDL and BLOB storage implementation      | Week 1       | Base Employee schema validated               | EMPLOYEE table successfully extended, BCNF maintained |
| **Phase 2** | Backend API development for image operations      | Week 2       | Phase 1 complete, Node.js environment ready  | All photo endpoints functional, validation working    |
| **Phase 3** | Frontend integration and upload interface         | Week 3       | Phase 2 complete, React.js environment ready | Photo upload/display components integrated            |
| **Phase 4** | Testing, validation, and performance optimization | Week 4       | Phases 1-3 complete                          | All test cases pass, performance targets met          |

### 7.2 Technical Implementation

**Phase 1: Database Extension**

```sql
-- Step 1: Backup existing database
.backup employee_mgmt_backup.db

-- Step 2: Add BLOB column
ALTER TABLE EMPLOYEE ADD COLUMN Profile_Photo BLOB;

-- Step 3: Verify schema integrity
PRAGMA table_info(EMPLOYEE);
```

**Phase 2: Backend Implementation**

```javascript
// Image upload middleware with validation
const multer = require("multer");
const upload = multer({
  limits: { fileSize: 5 * 1024 * 1024 }, // 5MB limit
  fileFilter: (req, file, cb) => {
    const allowedTypes = ["image/jpeg", "image/png"];
    cb(null, allowedTypes.includes(file.mimetype));
  },
});

// Photo upload endpoint
app.post(
  "/api/employees/:id/photo",
  authenticate,
  upload.single("photo"),
  async (req, res) => {
    try {
      const { id } = req.params;
      const imageBuffer = req.file.buffer;

      // Store BLOB in database
      await db.run("UPDATE EMPLOYEE SET Profile_Photo = ? WHERE SSN = ?", [
        imageBuffer,
        id,
      ]);

      res.status(201).json({
        success: true,
        message: "Photo uploaded successfully",
      });
    } catch (error) {
      res.status(500).json({ error: error.message });
    }
  }
);
```

**Phase 3: Frontend Implementation**

```jsx
// Photo upload component
const PhotoUpload = ({ employeeId, onUploadSuccess }) => {
  const [uploading, setUploading] = useState(false);

  const handleFileUpload = async (file) => {
    setUploading(true);
    const formData = new FormData();
    formData.append("photo", file);

    try {
      const response = await fetch(`/api/employees/${employeeId}/photo`, {
        method: "POST",
        body: formData,
        headers: {
          Authorization: `Bearer ${localStorage.getItem("token")}`,
        },
      });

      if (response.ok) {
        onUploadSuccess();
      }
    } catch (error) {
      console.error("Upload failed:", error);
    } finally {
      setUploading(false);
    }
  };

  return (
    <div className="photo-upload">
      <input
        type="file"
        accept="image/jpeg,image/png"
        onChange={(e) => handleFileUpload(e.target.files[0])}
        disabled={uploading}
      />
      {uploading && <div>Uploading...</div>}
    </div>
  );
};
```

### 7.3 Success Metrics

| **Metric**              | **Target**                            | **Measurement Method**               | **Acceptance Criteria**                                   |
| ----------------------- | ------------------------------------- | ------------------------------------ | --------------------------------------------------------- |
| **Upload Success Rate** | >99% for valid files                  | Automated testing with sample images | All valid JPEG/PNG files under 5MB upload successfully    |
| **Image Load Time**     | <1 second average                     | Performance monitoring in browser    | Photo display completes within 1s on standard connection  |
| **Storage Efficiency**  | <5MB average per employee             | Database size monitoring             | Photo storage remains within size constraints             |
| **System Performance**  | No degradation in existing operations | Before/after performance comparison  | Employee CRUD operations maintain original response times |
| **User Satisfaction**   | >90% positive feedback                | User acceptance testing              | Users find photo features intuitive and helpful           |

---

## 8. Appendix

### 8.1 Future Multimodal Enhancements

**Immediate Extensions (Next Phase):**

- **Document Storage:** Extend BLOB capability to store employee documents (resumes, certificates)
- **Spatial Data Integration:** Add geographic coordinates for employee work locations
- **Audio Notes:** Voice annotations for employee profiles
- **Video Profiles:** Short video introductions for remote team members

**Advanced Multimodal Features:**

- **AI-Powered Image Analysis:** Automatic photo quality assessment and optimization
- **Facial Recognition Integration:** Secure access control using employee photos
- **Mobile Photo Capture:** Direct upload from mobile devices with camera integration
- **Bulk Photo Import:** Mass upload capabilities for HR onboarding processes

**System Evolution Path:**

- **Cloud Storage Migration:** Transition from BLOB to cloud storage (AWS S3, Azure Blob) while maintaining API consistency
- **Content Delivery Network:** Implement CDN for global photo access optimization
- **Image Processing Pipeline:** Automated resizing, format conversion, and compression
- **Backup and Archival:** Specialized backup strategies for large multimodal datasets

### 8.2 Document History

| **Version** | **Date**     | **Description**                                                                                                       | **Author** |
| ----------- | ------------ | --------------------------------------------------------------------------------------------------------------------- | ---------- |
| **1.0**     | **Nov 2025** | Initial SRS for Employee Profile Photo Extension - BLOB implementation demonstrating multimodal database capabilities | Divyansh   |

---

**Compliance Statement:**  
This multimodal extension SRS complies with **IEEE 830 and ISO/IEC/IEEE 29148**, including:

- **Complete requirement specification** for multimodal database extension
- **Full integration documentation** with base Employee Management System
- **Comprehensive testing strategy** for BLOB data handling
- **Implementation roadmap** with measurable success criteria
- **Future extensibility planning** for additional multimodal capabilities

**Technical Achievement:**  
This extension successfully demonstrates the **practical implementation of multimodal database provisions** designed in Term I, validating the forward-thinking architecture of the base Employee Management System and establishing a foundation for advanced database capabilities.

---

**Page 2 of 2**

---

## 🎯 **Term II Submission Summary**

### ✅ **Deliverables Complete:**

1. **SRS Document 1**: Formalized Term I Employee Management System
2. **SRS Document 2**: Image Extension requirements and design
3. **Implementation Ready**: Complete technical specifications for demo development

### 📋 **Next Steps for Implementation:**

1. Execute DDL extension for EMPLOYEE table
2. Develop backend image handling APIs
3. Integrate frontend photo upload/display components
4. Conduct comprehensive testing as specified
5. Prepare demonstration of multimodal capabilities

---
