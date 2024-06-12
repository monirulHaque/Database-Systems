This repository contains all of my lecture contents of the course Database Systems.

------------------

**Table of Contents**


- [Course Overview](#course-overview)
  - [Tentative Marks Distribution](#tentative-marks-distribution)
  - [Consultaion](#consultaion)
- [Lecture 1](#lecture-1)
  - [Basic Definitions](#basic-definitions)
    - [Data](#data)
    - [Database](#database)
    - [Database Management System (DBMS)](#database-management-system-dbms)
    - [Database System](#database-system)
    - [Example Database](#example-database)
    - [Simplified Structure of a Database System](#simplified-structure-of-a-database-system)
  - [A Brief History](#a-brief-history)
    - [Timeline](#timeline)
  - [Faciliteis and Functionalities of DBMS](#faciliteis-and-functionalities-of-dbms)
- [Lecture 2](#lecture-2)
  - [Database Users](#database-users)
  - [When not to use a DBMS](#when-not-to-use-a-dbms)
  - [Data Models](#data-models)
  - [Database Schema vs Database State](#database-schema-vs-database-state)
  - [Three Schema Architecture](#three-schema-architecture)
    - [Internal Schema](#internal-schema)
    - [Conceptual Schema](#conceptual-schema)
    - [External Schema](#external-schema)
  - [Data Independence](#data-independence)
    - [Logical Data Independence](#logical-data-independence)
    - [Physical Data Independence](#physical-data-independence)
  - [DBMS Languages](#dbms-languages)
    - [Data Definition Language (DDL)](#data-definition-language-ddl)
      - [CREATE Command](#create-command)
      - [DROP Command](#drop-command)
      - [ALTER Command](#alter-command)
      - [TRUNCATE Command](#truncate-command)
    - [Data Manipulation Language (DML)](#data-manipulation-language-dml)
      - [SELECT Command](#select-command)
      - [INSERT Command](#insert-command)
      - [UPDATE Command](#update-command)
      - [DELETE Command](#delete-command)
    - [Data Control Language (DCL)](#data-control-language-dcl)
    - [Transaction Control Language (TCL)](#transaction-control-language-tcl)
- [Lecture 3](#lecture-3)
  - [ER Diagram](#er-diagram)
    - [ER Diagram Exampls](#er-diagram-exampls)

# Course Overview
## Tentative Marks Distribution
| Marks Distribution     | %  |
| ---------------------- | -- |
| Assignments            | 5  |
| Quiz (Best 3 out of 4) | 10 |
| Midterm                | 20 |
| Final                  | 35 |
| Lab                    | 30 |

There is no marks for attendance this semester but you must attend at least 70% of the theory classes and 90% of the lab classes to be able to sit for the exam and that the policy will be strictly maintained.

## Consultaion
Email: ext.monirul.haque@bracu.ac.bd 
![Consultation](Media/Consultation.png)

# Lecture 1
## Basic Definitions
### Data
Known facts that can be recorded and have an implicit meaning. 
Example: names, phone numbers, email addresses etc.
### Database
An organized collection of related data which is logically coherent and is built for a specific purpose. 
Example: USIS has a database which contains your ID, Phone Number, Email Address, Courses, Grades. 
### Database Management System (DBMS)
A software package/system to facilitate the creation, retrieval and maintenance of a computerized database.
Example: MySQL, Oracle, SQL Server, MongoDB, MariaDB etc. 
### Database System
The DBMS software together with the data itself. Sometimes, the applications are also included.

### Example Database
<p align = "center">
  <img src = "Media/Lecture1/lec1exdb.png">
  <img src = "Media/Lecture1/lec1dbdissect.png" width ="500">
</p>

### Simplified Structure of a Database System
<p align = "center">
  <img src = "Media/Lecture1/lec1structdb.png" width ="500">
</p>

## A Brief History
Databases have been around for centuries, with record-keeping evolving from stone tablet engravings to file cabinets to digital storage. 
<p align = "center">
  <img src = "Media/Lecture1/lec1hist1.png" width ="300"> </br>
  <i>Fig: Ancient Sumerian medical prescription database</i> </br>
  <img src = "Media/Lecture1/lec1hist2.png" width ="300"> </br>
  <i>Fig: File cabinet system, a vintage solution for database system</i>
</p>

### Timeline
- **1950's:** In the early 1950's "file" system was invented and so was "File-Based Systems". File-based systems were an early attempt to computerize the manual file cabinet systems. The limitations were unhandled data dependencies, duplication of data, limited fixed queries, no security, only one user could access the database at a time. 
<p align = "center">
  <img src = "Media/Lecture1/lec1hist3.jpg" width ="300"> </br>
  <i>Fig: File-based Systems worked mainly on IBM 350 RAMAC Disk File. Storage Capacity 3.75MB</i> </br>
</p>

- **1960's:** The first database system was integrated Data Store (IDS), developed at General Electric (GE). They were the best home electronic appliances company but they soon sold their computer division to another company as their computer division was third best in the world. The IDS database system was based on a Network Data Model. 
<p align = "center">
  <img src = "Media/Lecture1/lec1hist4.png"> </br>
  <i>Source: Professor Andy Pavlo's Slides</i> </br>
</p>
The Integrated Data Store (IDS) system, utilizing the network database model, enabled data access through multiple paths, enhancing query performance and flexibility. It eliminated data duplication by allowing records to be shared across multiple sets. However, IDS was complex, making it challenging to design, implement, and maintain. It required advanced technical skills to define records, sets, and navigate the network structure using pointers and links. Additionally, IDS lacked portability, making it difficult to transfer to different hardware, and it could not handle dynamic data evolution effectively.

Then came Information Management System (IMS) devloped at IBM following a hierarchical data model. 

<p align = "center">
  <img src = "Media/Lecture1/lec1hist5.png"> </br>
  <i>Source: https://prepinsta.com/</i> </br>
</p>

The advantages the IMS database system had over IDS were that it was easier to understand and implement. It was easier to visualize. As it maintained a tree structure, data retrieval was faster. However, It was not flexible nor adaptive to data and it was expensive to change predefined hierarchy. It also had data duplications and redundancy. Trying to reduce data duplication lead to complex tree structures with multiple parents of a single child, which would make data retrieval slower.

- 1970's: Ted Codd, mathematician researcher at IBM, saw how programmers were wasting their time rewriting IMS or Codasyl (COBOL programmers standard for IDS) programs every time database structure or layout changed. He published a paper proposing Relational Model for Database.

<p align = "center">
  <img src = "Media/Lecture1/lec1hist6.png"> </br>
  <i>Source: Professor Andy Pavlo's Slides</i> </br>
</p>

This approach eliminated almost all the problems the previous database systems had offering simplicity, data integrity, flexibility, and scalability. The data structure was logical and easy to understand. 
However, IBM didn't believe in this new approach because unlike others Ted Codd didn't implement it. It was just an idea. But Larry Ellison, a startup entrepreneur, found the idea interesting and implemented the first Relational Database Management System, Oracle, in 1977.

- **1980's:** In this era Relational Database Management System's were winning. IBM realized that they made a mistake and attempted to create Relational DBMS but failed twice. But they created a language called SEQUEL (Structured English QUEry Language) to manipulate and retrieve data stored in the relational model. SEQUEL sounded very close to QUEL which was used by the DBMS INGRES. So, the INGRES Corp. founder Stonebraker sued IBM. As a result, IBM was forced to changed the name to SQL (Structured Query Language). 
As their were so many relational DBMS were available that time, ISO called for all the query languges to standardize the best one. Stonebraker didn't like the governing body of the ISO, so he didn't submit. As a result, SQL became the standardized query language of all the Relational DBMS even though QUEL was better than SQL. Since then, the standard has been revised multiple times to include a larger set of features and incorporate common extensions making it better than QUEL gradually.
In this era Object Oriented Model was also introduced which was used in XML and JSON formats. Popular Database MongoDB follows this model.
- **1990's:** No major advancements in database systems happened in this era. Mycrosoft SQL Server and MySQL were created in this era.
- **2000's:** NoSQL Systems such as MongoDB became popular which made queries easier. 
- **2010's:** Graph Systems, Cloud System, Blockchain database... We are swimming in thousands of different database systems.

To learn more, check out Professor Pavlo's lecture https://www.youtube.com/watch?v=LWS8LEQAUVc&list=PLSE8ODhjZXjYzlLMbX3cR0sxWnRM7CLFn&index=1

## Faciliteis and Functionalities of DBMS
- A structured way to store and organize data in a logical and efficient manner.
- Efficient Data Manipulation (Insert, Update, Delete, Retrieve)
- Data Integrity Enforcement (Ensuring that data remains accurate, consistent, and reliable)
- Data Security (Control access to data and protect it from unauthorized access) 
- Concurrency Control (concurrent access to data by multiple users or applications, ensuring that data remains consistent and preventing conflicts or data corruption when multiple users try to modify the same data simultaneously.)
- Backup and Recovery
- Scalability and Performance

# Lecture 2
## Database Users
- **Actors On the Scene:** Those who actually use and control the database 
content, and those who design, develop and maintain database applications.
  - **Database administrators:** Responsible for authorizing access to the database, for coordinating and monitoring its use, acquiring software and hardware resources, controlling its use and monitoring efficiency of operations.
  - **Database designers:** Responsible to define the content, the structure, the constraints, and functions or transactions against the database. They must communicate with the end-users and understand their needs.
  - **Software Engineers:** Responsible for implementing the database and its associated applications using a dbms and other programming languages and tools.
  - **End-users:** They use the data for queries, reports and some of them update the database content.
- **Workers Behind the Scene:** Those who design and develop the DBMS 
software and related tools, and the computer systems operators. Example: The engineers who created and are maintaining MySQL, MongoDB etc.

## When not to use a DBMS
- Hardware/Security/Service of that DBMS costs more than the available budget. Example: We don't need to buy Improvado DBMS  with 2000 dollar per month when we just need a DBMS for a local e-commerce website. In that case, we can just use free DBMS like MongoDB or MySQL.
- Database is well defined, no further changes are expected and multiple user access not required.
- For temporary/short-lived data.
- In resource-constrained environments like embedded systems or IoT devices. Example: AC, projector, calculator etc.
- When the data complexity exceeds the DBMS's modeling capabilities. Example: Google Maps can not be stored in MySQL database, it's stored in a graph DBMS.
- When the data needs to be updated and accessed real time, meaning that the database stores data in JSON files which is synchronized in real-time to every client that is connected to the database. In that case we can not use relational databases like MySQL, we might have to rely on NoSQL languages such as MongoDB, Firebase etc. But the cost will be higher.
- If the database system is not able to handle the complexity of data because of modeling limitations. For example, complex genome and protein structures can not be stored in MySQL

## Data Models
A set of concepts to describe the structure of a database, the operations for manipulating these structures, and certain constraints that the database should obey.
* **Conceptual (high-level, semantic) data models**: 
These Provide concepts that are close to the way many users perceive data, meaning that these data models don't go into too much detail. These are abstract representations of the important entities/objects, attributes and relationships of the whole database. So, sometimes these are also called entity-based or object-based data models.
* **Physical (low-level, internal) data models**:
These provide concepts that describe details of how data is stored in the computer hardware(HDD/SSD/RAM) in that database system. 
* **Implementation (representational) data models**:
This type of data model is used to represent the logical part of the database. It's neither low-detailed/abstract as conceptual data models nor as detailed as the physical data models to show structure of the database on hardware. 
* **Self-Describing Data Models**:
These models combine the description of data with the data values. Example: MongoDB (the data is stored in objects that look like python dictionaries). 

## Database Schema vs Database State

| Database Schema    | Database State   |
| ---------------------- | ---------------------- |
| The description of a database including structure, data type and constraints | Snapshot of the database in a particular moment  |
| It is not changed frequently | It changes after every insertion, update and delete in the database |
| ![alt text](Media/Lecture2/database-schema.png) | ![alt text](Media/Lecture2/dbstate.png) |

## Three Schema Architecture
<p align="center">
  <img src="Media/Lecture2/threeschema.png" width=500>
</p>

### Internal Schema
Internal schema at the internal level to describe physical storage structures and access paths (e.g indexes). Typically uses a physical data model.
<p align="center">
  <img src="Media/Lecture2/threeschemaphysical.png" width=300>
</p>

### Conceptual Schema

Conceptual schema at the conceptual level to describe the structure and constraints for the whole database for a community of users. Typically uses a conceptual or an implementation data model.

<p align="center">
  <img src="Media/Lecture2/threeschemaconceptual.png" width=300>
</p>

### External Schema

External schemas at the external level to describe the various user views. It uses a conceptual data model.


<p align="center">
  <img src="Media/Lecture2/threeschemaexternal.png" width=500>
</p>

Examples source: https://www.javatpoint.com/dbms-three-schema-architecture

## Data Independence
Data Independence is the ability to change the schema at one level without impacting the schema at the next higher level. 
### Logical Data Independence
■ The capacity to change the conceptual schema without having to 
change the external schemas and their associated application 
programs.
■ Example: adding a new column that is not shown in the app or 
changing the datatype which does not change the external view.
### Physical Data Independence
■ The capacity to change the internal schema without having to 
change the conceptual schema.
■ For example, the internal schema may be changed when certain 
file structures are reorganized or new indexes are created to 
improve database performance
## DBMS Languages
DBMS Language Commands can be grouped into different categories. 
### Data Definition Language (DDL)
The SQL DDL category provides commands for defining, deleting and modifying tables in a database. We use the following commands in this category.
#### CREATE Command
To create the database or tables inside the database.
```SQL
CREATE TABLE table_name (column_name1 datatype(size), column_name2 datatype(size), column_name3 datatype(size));
```
#### DROP Command
To delete a database or a table inside the database. 
```SQL
DROP TABLE table_name; 
```
#### ALTER Command
To change the structure of the tables in the database such as changing the name of a table, adding a primary key to a table, or adding or deleting a column in a table.

```SQL
--Syntax to add a column into a table
ALTER TABLE table_name ADD (column_name datatype(size));
--Syntax to add a primary key to a table
ALTER TABLE table_name ADD primary key (column_name);
```
#### TRUNCATE Command
To remove all records from a table, which will empty the table but not delete the table itself. 
```SQL
TRUNCATE TABLE table_name;
```
### Data Manipulation Language (DML)
The SQL DML commands provide the ability to query, delete and update data in the database.  Use the following commands in this category.
#### SELECT Command
To retrieve data from tables in the database. 
```SQL
SELECT * FROM table_name;
```
#### INSERT Command
To add records of data into an existing table. 
```SQL
INSERT INTO table_name (column1, column2, column3) VALUES (value1, value2, value3);
```
#### UPDATE Command
To modify or update data contained within a table in the database. 
```SQL
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
#### DELETE Command
To delete data from a table in the database.
```SQL
DELETE FROM table_name WHERE condition;
```
### Data Control Language (DCL)
You use DCL to deal with the rights and permissions of users of a database system. You can execute SQL commands to perform different types of operations such as create and drop tables. To do this, you need to have user rights set up. This is called user privileges. This category deals with advanced functions or operations in the database. Note that this category can have a generic description of the two main commands. Use the following commands in this category:

**GRANT** Command to provide the user of the database with the privileges required to allow users to access and manipulate the database.

**REVOKE** Command to remove permissions from any user.
### Transaction Control Language (TCL)
The TCL commands are used to manage transactions in the database. These are used to manage the changes made to the data in a table by utilizing the DML commands. It also allows SQL statements to be grouped together into logical transactions. This category deals with advanced functions or operations in a database. Note that this category can have a generic description of the two main commands. Use the following commands in this category:

**COMMIT** Command to save all the work you have already done in the database. 

**ROLLBACK** Command to restore a database to the last committed state.
# Lecture 3
Relational
## ER Diagram
### ER Diagram Exampls
<details>
<summary>
<span style="font-size:1.2rem">
<b>Example 1</b> </br>
We need to create a database schema design based on the following (simplified) requirements of the COMPANY Database: </br>
<ul>
  <li> The company is organized into DEPARTMENTs. Each department has a name, number and an empyloyee who manages the department. We keep track of the start date of the department manager.</li>
  <li> A department may have several locations. Each department Each department controls a number of PROJECTs. Each project has a unique name, unique number and is located at a single location.</li>
  <li> We store each EMPLOYEE’s social security number, address, salary, sex, and birthdate.</li>
  <ul>
    <li> Each employee works for one department but may
  work on work on several projects several projects.</li>
    <li> We keep track of the number of hours per week that an employee currently works on each project.</li>
    <li> We also keep track of the direct supervisor of each employee.</li>
  </ul>
  <li> Each employee may Each employee may have a number of a number of DEPENDENTs. For each dependent, we keep track of their name, sex birthdate and relationship to the employee </li>
</ul>
</span>
</summary>
<br>
<p align="center">
  <img src="Media\Lecture3\lec3ex1.png"/>
</p>
</details>

<details>
<summary>
<span style="font-size:1.2rem">
<b>Example 2</b> </br>
We now present another example, a UNIVERSITY database, to illustrate the ER 
modeling concepts. Suppose that a database is needed to keep track of student 
enrollments in classes and students’ final grades. After analyzing the miniworld 
rules and the users’ needs, the requirements for this database were determined to be 
as follows: </br>
<ul>
<li> The university is organized into colleges (COLLEGE), and each college has a unique name (CName), a main office (COffice) and phone (CPhone), and a particular faculty member who is dean of the college. Each college administers a number of academic departments (DEPT). Each department has a unique name (DName), a unique code number (DCode), a main office (DOffice) and phone (DPhone), and a particular faculty member who chairs the department. We keep track of the start date (CStartDate) when that faculty member began chairing the department.
<li> A department offers a number of courses (COURSE), each of which has a unique course name (CoName), a unique code number (CCode), a course level (Level: this can be coded as 1 for freshman level, 2 for sophomore, 3 for junior, 4 for senior, 5 for MS level, and 6 for PhD level), a course credit hours (Credits), and a course description (CDesc). The database also keeps track of instructors (INSTRUCTOR); and each instructor has a unique identifier (Id), name (IName), office (IOffice), phone (IPhone), and rank (Rank); 
in addition, each instructor works for one primary academic department.
<li> The database will keep student data (STUDENT) and stores each student’s name (SName, composed of first name (FName), middle name (MName), last name (LName)), student id (Sid, unique for every student), address 
(Addr), phone (Phone), major code (Major), and date of birth (DoB). A student is assigned to one primary academic department. It is required to keep track of the student’s grades in each section the student has completed.
<li> Courses are offered as sections (SECTION). Each section is related to a single course and a single instructor and has a unique section identifier (SecId). A section also has a section number (SecNo: this is coded as 1, 2, 3, . . . for multiple sections offered during the same semester/year), semester (Sem), year (Year), classroom (CRoom: this is coded as a combination of building code (Bldg) and room number (RoomNo) within the building), and days/times (DaysTime: for example, ‘MWF 9am-9.50am’ or ‘TR 3.30pm-5.20pm’—restricted to only allowed days/time values). (Note: The database will keep track of all the sections offered for the past several years, in addition to the current offerings. The SecId is unique for all sections, not just the sections for a particular semester.) The database keeps track of the students in each section, and the grade is recorded when available (this is a many-to-many relationship between students and sections). A section must have at least five students.
</ul>
</span>
</summary>
<br>
<p align="center">
  <img src="Media\Lecture3\lec3ex2.PNG"/>
</p>
</details>


<details>
<summary>
<span style="font-size:1.2rem">
<b>Example 3</b> </br>
Consider the following requirements for an airline reservation system. </br>
<ul>
<li> The database represents each AIRPORT, keeping its unique AirportCode, the AIRPORT Name, and the City and State in which the AIRPORT is located.
<li> Each airline FLIGHT has a unique number, the Airline for the FLIGHT, and the Weekdays on which the FLIGHT is scheduled (for example, every day of the week except Sunday can be coded as X7).
<li> A FLIGHT is composed of one or more FLIGHT LEGs (for example, flight number
CO1223 from New York to Los Angeles may have two FLIGHT LEGs: leg 1 from New York to
Houston and leg 2 from Houston to Los Angeles). Each FLIGHT LEG has a DEPARTURE AIRPORT
and Scheduled Departure Time, and an ARRIVAL AIRPORT and Scheduled Arrival Time.
<li> A LEG INSTANCE is an instance of a FLIGHT LEG on a specific Date (for example, CO1223 leg 1 on July 30, 1989). The actual Departure and Arrival AIRPORTs and
Times are recorded for each flight leg after the flight leg has been concluded. The
Number of available seats and the AIRPLANE used in the LEG INSTANCE are also kept.
<li> The customer RESERVATIONs on each LEG INSTANCE include the Customer Name, Phone,
and Seat Number(s) for each reservation.
<li> Information on AIRPLANEs and AIRPLANE TYPEs are also kept. For each AIRPLANE
TYPE (for example, DC-10), the TypeName, manufacturing Company, and Maximum Number of Seats are kept. The AIRPORTs in which planes of this type CAN LAND are kept in the database. For each AIRPLANE, the AirplaneId, Total number of seats,
and TYPE are kept.
</ul>
</span>
</summary>
<br>
<p align="center">
  <img src="Media\Lecture3\lec3ex3.PNG"/>
</p>
</details>