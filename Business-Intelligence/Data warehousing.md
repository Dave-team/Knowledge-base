# Data warehousing 
## Principles
- Conform dimensions: make sure that the same customer table is used accross the entire infrastructure
- Aim for long fact tables and wide dimension tables
- Think about the grain of a table and in development, ensure this grain doesn't change
- When designing a data warehouse, start simple. Use the data for a while and then the design will be more apparent. Only worry about design when a simple design doesn't work for the business or is non performant. 
- Similarly, a bus matrix excercise in the beginning has limited functionality. Instead, start by building a design for e.g. Salesforce and just build incrementally from there. 
- Materialize data depending on requirements: when performance is required or when a model is often referenced, materialize as table. Otherwise, view. 

## Purpose of Kimball 
- Storage is no longer expensive
- Organizing the data in a structured way that aligns with the business
- Conforming data to make it uniform and guarantee consistent results throughout the business 
- Making queries simple to join and understand by denormalizing the data and optimize it for reporting 

## Guidelines for fact or dimension
- When a value is used for aggregations, fact table. When a value is used to group and filter, it's a dimension. Good example here is price. 
- If a value changes frequently, it's a fact.
- If a value needs to be used accross multiple fact tables, put it in a dimension 

## Relationship cardinality
Relationship cardinality is the number of instances of an entity in relationship with another entity. There are: 
- One-to-one: one instance of the first entity corresponds to only one instance of the child or second entity (e.g. one employee has one employee ID)
- One-to-many: where there is one parent entity but it can have many children. In these cases, an entry in one table can be related to more than one entry in another table (e.g. one member can have many loans, or one department has multiple employees) 
- Many to one: there are more instances of the first entity, but it corresponds to only one instance of the second entity (e.g. multiple answers to a single survey question, or reasons why someone buys a product )
- Many-to-many: more than one instance of the first entity corresponding to more than one instance of the second entity. E.g. a patient cab have many symptoms and diagnosis and there can be many procedures that apply to each diagnoses  

## Dimensional model design process
1. Select a process you are modelling 
2. Declare the grain – ‘What is a fact row, exactly’? Generally, aim to be as atomic or fine a grain as possible. Choosing this depends both on what is needed by the business, as well as what is possible from the source system. 
2. Identify the dimensions. The grain of the fact will determine a minimal set of dimensions as you know exactly what the fact means and the facts are often related to dimensions (by product, customer, loan, etc.)  Then, you set up additional dimensions that make the fact table best suited to meet the business requirements. Dimensionsfall out of the question, “How do businesspeople describe the data that results from the business process?” We want to decorate our fact tables with a robust set of dimensions representing all possible descriptions that take on single values in the context of each measurement.
3. Identify the facts – select the metrics applicable to the business process. Each fact/metric must be true to the grain of the fact table. Facts are determined by answering the question, “What are we measuring?
4. From this, you create the bus architecture. In this, you basically want to follow a logical structure of the business. A fact table and associated dimensions are defined for each step in the chain 

## Data normalization
Normalization is the process of reducing data redundancy while maintaining data integrity. This is performed by creating relationships among tables through primary and foreign keys. Normalization procedures include 1NF (first normal form), 2NF, 3NF, etc.

Process used to organize a database into tables and columns. A table should be about a specific topic. It aims to make process of selecting, inserting, updating, deleting data more efficient and reduce data issues that might appear otherwise. Why normalize:
- Minimize duplicate data (redundancy)
- Minimize or avoid data modification issues (i.e. updates or inserts could cause you to make mistakes like forgetting to update some values. When a student’s name changes, you don’t want to update all the classes they are in). There are 3 types of anomalies that occur when a database is not normalized: 
    - Insertion – If a column doesn’t allow nulls this would be an issue
    - Update: when a row changes, we need to change all rows relating to a subject, otherwise we get inconsistent data  
    - Deletion: when we would delete delete for e.g. a department, we’d also be deleting the row for the employee 
- Simplify queries 
- Ensure accurate data
- Optimize queries for speed


- 1NF—Eliminate repeating groups. Make a separate table for each set of attributes (in essence, this is creating an entity). Identify a primary key for each table that uniquely identifies each row. If you cannot define a primary key, then you have not split up the tables into the sets of related attributes creating an entity, and you need to repeat this step. E.g. you can’t have Customer1 and Customer2 in a table. In the first normal form, your table will have a primiary key that uniquely identifies each row in the table
- 2NF—Eliminate redundant data stored in different entities. If an attribute depends on anything other than the primary key (could be a compound key), then remove it as a separate table. In the second form, every single column describes something about the thing describing the primary key. If it doesn’t the other data should sit in its own table. At the end of the second normal form, every table serves a single purpose. E.g. a table about customers shouldn’t include which employee the customer interacted with. Instead, the employee data will go into a different table. What happens here is that each seperate attribute will have its own table and primiary key. The way to combine that data then is to store the foreign keys in the main tables that match the primiary keys in the other attributes table (e.g. student table has course ID. Then the course table has a Teacher ID. Sometimes we have many to many relationships – a student can have multiple subjects and a subject can have multiple students. To solve for this, we use a joining table: (student ID, subject ID). This table consists purely of foreign keys – one to the student table and one to the subject table. 
- 3NF—Eliminate non-key interdependencies. If you have defined the primary key and the keys within that, then all the attributes in that entity need to be related to that key. For example, if you have customer or product, you can only have attributes that are related to the customer or the product within the entity. Otherwise, remove them and put them into a separate table, as they are most likely separate entities. With these steps completed, you have defined a 3NF schema. Example: you can’t have a table with a person ID, BodyMassIndex and a flag for whether they are overweight or not. Being overweight is depending on the BodyMassIndex. Similarly, a city depends on a postcode. In this case, you can have a table with customerID, post code and then a seperate table with a column for post code and the accompanying city. 


## Fact table grain
Every measure has a grain, which is a level of detail in the measurement. Fact tables record measurements in time of a process. 
With fact tables, always stay true to the grain: the business definition of what a single fact table record represents. After the grain is declared, list the dimensional foreign keys the exists at that grain. You always build up from the lowest possible grain – i.e. you store raw data rather than only aggregated data. There are three types of grain:
- Transaction grain: measurement taken at single instant: one row per transaction. As a transaction happens, extensive context about it is captured. This context creates lots of detail in the dimension tables, so we expect a lot of them. Once we insert a row in a transaction table it is rarely, if ever, revisited.
- Periodic Snapshot Grain: e.g. for showing financial transactions in a month – it is a summarized view. They have a guarantee that records will appear even if there weren’t any transactions 
- Accumulating Snapshot Grain: this is used to measure what happened in a predictable process that has a well defined beginning and end (e.g. order processing). Records get overwritten as the process progresses from beginning to end. I think this is an example of the application process – someone might start the application but continue only at another time. Future actions make us come back to the data and update it 

## Fact table measure types 
There are three types of measures stored in the facts:
- Additive: measure that can be added across all dimensions, like amount or revenue
- Semi additive: measures that can be added across some dimensions, but not all. Example: bank account balance: we can’t just add up 12 months of account balance and get their current total – you’d have to average the amounts. However, you could calculate the total balance at any one point across all customers. 
- Non additive: these can’t be added across any dimensions: unit prices, ratios: these are numbers but aren’t supposed to ever be added 

## Slowly changing dimensions
Sometimes our dimensions change. E.g. a product can change or we need to fix an error in the data. Because the changes arrive unexpectedly, and not frequently, we call these slowly changing dimensions (SCDs). Three types of SCD:
- Type 0: filling once. This is the case when we look at for example data tables – a dim_date never really gets updated
- Type 1: Overwrite. E.g. we had the wrong city of a customer in our customer table. To correct the error, we can overwrite the change. Type 1 changes are used when we correct errors and for when conscious decision is made not to track history. In this case, we don’t modify the key relating to the dimension changed. 
- Type 2: add a new dimension record. E.g. when a customer actually moves to somewhere new. So we create a new record for the customer with the new changes. In this case, we create a new surrogate key. Include an effective date, expiry data, and whether the row is currently in use flag. This type is used when we need to track history and it’s often the best approach to tracking slowly changing dimensions. 
- Type 3: add a new field. This is applicable when an attribute can actually have multiple values. E.g. a pen in a store can be assigned to household category or art supplies. This SCD is never really used – it would be applicable when you need to ability to track all facts prior to and after a change. ‘How much by our current logic vs by our previous logic?’

## Bridge tables
Bridge tables are required when there is a many to many relationship between a fact and a dim. Example: a single tweet can contain multiple hashtags (this would change the grain of the fact table) and one hashtag can be used in multiple tweets. Other example: a patient visits a doctor but during the visit, multiple diagnosis are discovered. 

Solution: bridge table. Bridge table doesn’t have a primary key: primary key is a combination of both foreign keys, one to the fact table and one to the dimension table. 

## Schemas
- Star Schema: most common. It is a fact table surrounded by multiple dimension tables (looks like a star). The dim tables are not normalized. What is recommended is using a Star Schema with flat dimension tables – this is because storage is cheap and you want to make the queries as easy as possible. 
- Snowflake schema: take the star schema, but go up in hierarchy. So there is more than one level of layer. E.g. layer 1 = dimproduct (specific bike). Layer 2: some category (e.g. mountain vs road). Layer 3: another category: another category (e.g. bikes vs water bottles). The ruling idea behind the snowflake schema is that dimension tables are completely normalized. The biggest disadvantage of the snowflake model is that it requires more complex queries with an increasing number of joins, which could decrease performance.  

## View vs stable 
Use a view when: 
- If perfromance is important: table. So anything referenced in BI tool should be a table
- Views can start to take long, especially when referencing other views. If many dependencies, table. 

## Data models
Data Modelling is the diagrammatic representation showing how the entities are related to each other. 
- Conceptual Model will be just portraying entity names and entity relationships. It’s the conceptual structure of the business data strategy as a first step in the design process 
- Logical Model will be showing up entity names, entity relationships, attributes, primary keys and foreign keys in each entity. It is used for the implementation of the DBMS
- Physical Data Model will be showing primary keys, foreign keys, table names, column names and column data types. This is the final design blueprint to be implemented 

## Why data types matter
- Data is stored in a consistent and known format
- Knowing the data type allows you to know which calculations and formulations you can use on the column.
- Data types affect storage. Some values take up more space when stored in one data type versus another
- Data types affect performance. The less time the database has to infer values or convert them the better.


## Glossary 
- Facts: measurement of business activity, e.g. business event or transaction, and it’s often numeric (and additive). Fact tables essentially describe a process. Fact tables consist of two types of columns: keys and measures. The keys are foreign keys that point to the primary keys of dimensional tables that are associated with the fact table to enable business analysis. The primary key of a fact table is often a combination of foreign keys that combined can identify a unique row in the fact table. We can create a surrogate key for the fact tables but this often has low business added value.
- Dimension: an entity that establishes the business context for the measures/facts. They define the who, what, where, and why of the dimensional model. Measures are numeric, dimensions are descriptive. A key concept in dim tables is that each row should be unique. A dimension table consists of a primary key and attributes 
- Degenerate dimension: unique identifiers that are not linked to any other dimension because the important attributes are already stored in other dimensions. Example: a purchase order, invoice numbers, etc. It might be tempting to create different dimensions, but you would soon realize you duplicate data. Best practice is to leave this in the transaction table after the dimension keys, We still leave these keys in the fact table as they link back to the operational system and if we ever need to refer to the source, this is the way to do it  
- Grain: what a single row in a fact table represents 
- Summary fact tables: aggregated fact tables to improve performance
- Factless fact tables: when we measure an event without any specific measures. E.g. student attending class: date, student, class. 
- Role playing dimensions: when a dimension is used in different business contexts. E.g. a date dimension could be linked to order, shipment and delivery date. This occurs when a fact table references a dimension multiple times as a foreign key – each time playing a logically distinct role 
- Junk dimensions: dimension that you might need at some point and want to store but you don’t really know what to do with them. A table containing junk dimensions is often called transaction profile dimension. In the junk dimension table, you want a surrogate key called junk_id
- Conformed dimension: dimension that can be used across multiple data marts to ensure similar definitions. Conformed dimensions should sit in a ‘core’ schema that then can be queried by all marts analysts (only change this if the security settings require it 
- Conformed facts: numeric values that have the same business and mathematical interpretations so they can be compared and computed against each other consistently. 
- 3NF is a modelling technique where data is fully normalized. This is often used in backend processes that often involve adding or updating records. 
- Data mart: how the tables in a data warehouse are organized - often by team. This is helpful for security (giving people access only to what they need) and for general organization 
- Primary key: unique identifiers (one or more columns) whose data contained within it is used to uniquely identify each row in a table. A primary key needs to be unique, not NULL, and a table can only have one primary key.  
- Alternate key: any of the candidate keys that are not the primary key
- Candidate keys: any field in the table that could be used as a primary key as its unique. 
- Foreign key: column that contains the primary key of another table in the database. We use foreign keys and primary keys to connect rows in two different tables. One table's foreign key holds the value of another table's primary key. Unlike primary keys, foreign keys do not need to be unique and can be NULL.
- Surrogate keys is a key made up purely for the purpose of being the primary key. It has no value to business or real world – e.g. an address can get an address key. A person has a membered. This is the recommended way of setting up keys. 
- Unique key: attribute in the table which is unique. It can be used to identify a row but it may not be the primary key. 
- Natural key: an attributed that exists in the real world or is used by the business and can uniquely identify a row. E.g.: social security number.
- Composite key is a primary key made up of more than one attribute / column. This is often done when a natural key doesn’t fulfill the uniqueness requirement. E.g. address can be unique by combining street number, street name, city and postal code. The combination of these would be a composite key. 
- Bus matrix: visualization of conformed dimensions and facts. By data mart as rows, we identify which conformed dimensions need to be part of that data mart. 
- Galaxy schema: representation of multiple fact tables with their dim tables 
- Dimensional modelling: we create star schemas with the fact table as the central table that measures business activity (often numeric). The fact table is then surrounded with dimension tables that provide context to the fact (grain is unique by instance)
- Views: pre-built queries that users can use in their own database queries. Views themselves don’t store data (and thus also don’t require additional storage), but you can query them like a table. Disadvantages of a view is that each time a view is called, the entire query that sits behind it is run
- Materialized view: When a view is materialized, it can actually store records. However, with a materialized view, when the underlying tables are updated, the materialized views are not updated (a materialized view once upon a time). A materialized view is a view that stores the results of the view’s query. Whenever you query the materialized view, it returns the data stored with the view itself. It doesn’t run the view’s query against the underlying tables. It’s a lot like a table. Materialized views improve the efficiency of a query
- Denormalisation is the process of converting a series of normalised tables into tables that are not normalisaed. This is done to prepare data for a data warehouse where the goal is to efficiently read the data 
 
### Data modelling 
![Relationship notations](https://user-images.githubusercontent.com/28791247/93707760-3d5da680-fb29-11ea-8cae-bb475536107d.png)

![Galaxy schema](https://user-images.githubusercontent.com/28791247/93707804-6bdb8180-fb29-11ea-9040-5b4ff92f27d9.png)