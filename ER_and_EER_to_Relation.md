### Simplified Steps for ER-to-Relational Mapping with Examples

#### **Step 1: Mapping Regular Entity Types**
- **Goal**: Convert each entity type in the ER model into a table (relation) in the relational database.
- **What to do**:
  - For each regular (strong) entity type (e.g., Employee, Department), create a table.
  - Include all the simple attributes of the entity in the table (e.g., Employee Name, Employee Age).
  - If the entity has a composite attribute (like Name with First Name, Last Name), only include the simple components (First Name, Last Name).
  - Choose one attribute (or set of attributes if composite) to be the **primary key** (a unique identifier for each row).
  - If the entity has multiple possible unique identifiers (keys), keep track of them for future use.

**Example**:  
For the **Employee** entity type with attributes Ssn, Name, Address, create a table `EMPLOYEE(Ssn, First_Name, Last_Name, Address)` where Ssn is the primary key.

#### **Step 2: Mapping Weak Entity Types**
- **Goal**: Map weak entities (those that rely on another entity) to a table.
- **What to do**:
  - Create a table for the weak entity.
  - Add the simple attributes of the weak entity.
  - Include a **foreign key** (a reference to another table's primary key) to link the weak entity to its "owner" entity.
  - Use a combination of the foreign key and the weak entity's unique attribute as the primary key.

**Example**:  
For the **Dependent** weak entity type, which depends on **Employee**, create a `DEPENDENT(Essn, Dependent_name)` where `Essn` is the foreign key referring to Employee (Ssn). The primary key is the combination of `Essn` and `Dependent_name`.

#### **Step 3: Mapping 1:1 Relationship Types**
- **Goal**: Map one-to-one (1:1) relationships between entities to a relational table.
- **What to do**:
  - Choose one entity to hold the relationship.
  - Add a foreign key in this table that refers to the other entity's primary key.
  - Include any attributes of the relationship in the table.
  - Choose the entity with total participation (must always be in the relationship) to avoid too many NULL values.

**Example**:  
For a **Manages** 1:1 relationship between **Employee** and **Department**, add a foreign key `Mgr_ssn` in `DEPARTMENT` that refers to `Ssn` in `EMPLOYEE`. Also, add the `Mgr_start_date` to `DEPARTMENT`.

#### **Step 4: Mapping 1:N Relationship Types**
- **Goal**: Map one-to-many (1:N) relationships where one entity can be related to multiple other entities.
- **What to do**:
  - Add a foreign key in the table representing the "many" side (N-side).
  - This foreign key refers to the primary key of the "one" side (1-side).
  - Include any relationship attributes in the "many" side table.

**Example**:  
For a **Works_For** 1:N relationship between **Employee** and **Department**, add a foreign key `Dno` in `EMPLOYEE` that refers to `Dnumber` in `DEPARTMENT`.

#### **Step 5: Mapping M:N Relationship Types**
- **Goal**: Map many-to-many (M:N) relationships between entities to a new table.
- **What to do**:
  - Create a new table for the M:N relationship.
  - Add foreign keys that refer to the primary keys of both participating entities.
  - Include any attributes of the relationship in this table.
  - The primary key is usually the combination of both foreign keys.

**Example**:  
For a **Works_On** M:N relationship between **Employee** and **Project**, create a table `WORKS_ON(Essn, Pno, Hours)` where `Essn` refers to `EMPLOYEE(Ssn)` and `Pno` refers to `PROJECT(Pnumber)`. The primary key is the combination of `Essn` and `Pno`.

#### **Step 6: Mapping Multivalued Attributes**
- **Goal**: Map attributes that can take multiple values for a single entity.
- **What to do**:
  - Create a new table for each multivalued attribute.
  - Include the multivalued attribute and the primary key of the entity it belongs to.
  - The primary key is the combination of the multivalued attribute and the entity's primary key.

**Example**:  
For the **Department** entity with a multivalued attribute **Location**, create a table `DEPT_LOCATIONS(Dnumber, Dlocation)` where `Dnumber` refers to `DEPARTMENT(Dnumber)`. The primary key is the combination of `Dnumber` and `Dlocation`.

#### **Step 7: Mapping N-ary Relationship Types**
- **Goal**: Map relationships involving more than two entities.
- **What to do**:
  - Create a new table for the relationship.
  - Add foreign keys that refer to the primary keys of all participating entities.
  - The primary key is usually the combination of all foreign keys unless there's a cardinality constraint.

**Example**:  
For a ternary relationship **Supply** between **Supplier**, **Part**, and **Project**, create a table `SUPPLY(Sname, Part_no, Proj_name)` where each foreign key refers to `SUPPLIER(Sname)`, `PART(Part_no)`, and `PROJECT(Proj_name)`. The primary key is the combination of all three foreign keys.

----

### Steps for EER to Relaional Schema

#### Step 8: Options for Mapping Specialization or Generalization

In database design, "specialization" and "generalization" are methods used when dealing with categories of data that have common characteristics but also some unique properties. There are different ways to map these structures into relational tables, and these are the options for doing so:

**Option 8A: Multiple Relations - Superclass and Subclasses**
- You create one table for the superclass (general category) and separate tables for each subclass (specific categories).
- Example: If you have a general entity called `Vehicle` and two specific entities `Car` and `Truck`, you would create a `Vehicle` table and separate `Car` and `Truck` tables.

**Option 8B: Multiple Relations - Subclass Relations Only**
- Only create tables for the subclasses and add the attributes from the superclass to these tables. This works when every instance of the superclass must also belong to a subclass.
- Example: If every `Vehicle` must be either a `Car` or `Truck`, only the `Car` and `Truck` tables would exist, and they would include the general vehicle information (like `VehicleID`).

**Option 8C: Single Relation with One Type Attribute**
- You create just one table, and add a new attribute that indicates which subclass each record belongs to.
- Example: A `Vehicle` table with a `Type` column that stores whether the vehicle is a `Car` or `Truck`.

**Option 8D: Single Relation with Multiple Type Attributes**
- You create one table with a separate column for each subclass, where each column holds a `True/False` value indicating whether the record belongs to that subclass.
- Example: A `Vehicle` table with two columns: `IsCar` and `IsTruck`, where only one of these would be `True` for each record.


#### Step 9: Mapping of Union Types (Categories)

A "union type" or "category" is used when multiple classes share certain properties, but each class might have a different key (primary identifier). Here’s how to map union types:

- **Create a new table**: You create a new table that corresponds to the union category and give it a new key attribute, called a "surrogate key."
- Example: If you have an `Owner` category that can refer to either a `Person` or a `Company` (which have different types of keys), you create an `Owner` table with a new key called `OwnerId`. This table will store information relevant to both `Person` and `Company`, using `OwnerId` to uniquely identify each entry. 

These steps help in organizing data from different types into a consistent relational format.