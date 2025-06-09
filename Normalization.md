# DATABASE NORMALIZATION
## What is normalization?
Database normalization is the process of organizing the attributes of the database to reduce or eliminate data redundancy (having the same data but at different places).

## Why do we need Normalization?
<ul>
<li>Reduces redundancy: Redundancy is when the same information is stored multiple times, and a good way of avoiding this is by splitting data into smaller tables.</li>
<li>Improves query performance: You can perform faster query execution on smaller tables that have undergone normalization.</li>
<li>Minimizes update anomalies: With normalized tables, you can easily update data without affecting other records.</li>
<li>Enhances data integrity: It ensures that data remains consistent and accurate.</li>
</ul>

## What causes the need for normalization
If a table is not properly normalized and has data redundancy, it will not only take up extra data storage space but also make it difficult to handle and update the database.
Here are several factors that drive the need for normalization;
<ul>
<li>Insertion, deletion, and update anomalies: Any form of change in a table can lead to errors or inconsistencies in other tables if not handled carefully. These changes can either be adding new data to a database, updating the data, or deleting records, which can lead to unintended loss of data.<li>
<li>Difficulty in managing relationships: It becomes more challenging to maintain complex relationships in an unnormalized structure.</li>
<li>Other factors that drive the need for normalization are partial dependencies and transitive dependencies, in which partial dependencies can lead to data redundancy and update anomalies, and transitive dependencies can lead to data anomalies. We will be looking at how these dependencies can be dealt with to ensure database normalization in the coming sections.</li>
</ul>

## Different types of normalization
<ul>
<li>0NF —  (Not Normalized Form) requires no additional assurances except that a record has a primary key that uniquely identifies it.</li>
<li>1NF — requires that no field has a table as its value. The original definition was even more strict: that a field value is atomic (that is — not compound). As it is with current RDBMSes, and especially PostgreSQL this presents a rather challenging requirement; let’s stick with the «no table as value» form and discuss what atomic, compound and opaque mean later.<li>
For example if there are multiple branchname for a student, they must be converted to a single-valued attribute as shown:

| ID | NAME | BRANCH NAME |
|----|------|-------------|
|  1 | John | CS,Civil    |  
|  2 | Ben  | Electronics |

To
| ID | NAME | BRANCH NAME|
|----|------|------------|
| 1  | John | CS         |
| 2  | John | Civil      |
| 3  | Ben  | Electronics|



<li>2NF — requires that (for a compound primary key) no non-key attribute depends just on part of the primary key. In other words, non-key attributes must depend on the whole primary key. If such a partial dependency is identified, the table must be split, and both dependent attribute(s) and part of the primary key it depends upon moved to a separate table.</li>

To convert a table to 2NF we decompose it into two tables as given below:
Table 1
|CUSTOMER ID | PRODUCT NAME|
|------------|-------------|
| 1          | Fan         |
| 1          | Phone       |
| 2          | AC          |
| 2          | Earphones   |
| 4          | Lamp        |
| 4          | Fan         |

Table 2
|PRODUCT NAME | PRICE    |
|-------------|----------|
| Fan         | 1000     |
| Phone       | 2000     |
| AC          | 1500     |
| Earphones   | 2000     |
| Lamp        | 1000     |


<li>3NF — requires that there is no transitive dependency (through another field depending directly on the primary key) on the primary key. This means that if the values of two or more fields consistently appear together, they should be moved to a separate table, and one of them should be made a key, so that information repetition is avoided.<li>

Suppose there is a table containing the data of students as follows:

| STU_ID | STU_NAME | ZIPCODE  | STU_STATE | STU_CITY  |
|--------|----------|----------|-----------|-----------|
| 1      | Caren    | 201010   | UP        | Noida     |
| 2      | Stephanie| 07223    | US        | Boston    |
| 3      | Makena   | 60007    | US        | Chicago   |
| 4      | Adrian   | 06369    | UK        | Norwich   |
| 5      | Martin   | 462007   | MP        | Bhopal    |

To convert this into 3NF, we decompose the relation into two tables as below.
Table 1
| STU_ID | STU_NAME | ZIPCODE |
|--------|----------|---------|
| 1      | Caren    | 201010  |
| 2      | Stephanie| 07223   |
| 3      | Makena   | 60007   |
| 4      | Adrian   | 06369   |
| 5      | Martin   | 4622007 |

Table 2
| ZIPCODE | STU_STATE | STU_CITY |
|---------|-----------|----------|
| 201010  | UP        | Noida    |
| 07223   | US        | Boston   |
| 60007   | US        | Chicago  |
| 06369   | UK        | Norwich  |
| 4622007 | MP        | Bhopal   |



<li>BCNF — Boyce-Codd Normal Form aka 3.5NF is just a bit of a stronger version of 3NF; often, a table in 3NF is also compliant with BCNF.
It requires that no part of a primary key is functionally dependent on a non-key attribute. The difference is quite subtle — till now I have been talking about non-key attributes which are dependent on key attributes. Now it is the opposite way round.</li>
<li>4NF — requires that there is no multivalued dependency on non-super key attributes<li>
<li>5NF — requires that there are no joint dependencies that do not have only superkey components. In other words a table is in 5NF if it cannot be split (reduced) further into smaller tables that have different (smaller) key without losing information.<li>
<li>6NF — requires that a row must not contain more than one non-primary attribute in addition to a primary key. As impractical as this normal form might seem, it has its applications in e.g. data warehouses and very sparse schemas, but it is most efficient in so-called columnar storage engines. For typical OLTP, 6NF is not very practical and is too close for comfort to the dreaded EAV antipattern.</li>

</ul>
 
 ## Benefits of Normalization
 #### Reduces size
 Normalized data includes quantitatively more reliable and qualitatively significant information in the same space occupied by unnormalized data. The presence of quality data makes it easy to use, reduces retrieval processing time, offers up-to-date information for every member, and is cost-efficient.

 #### Efficient Database Design
 The visually comprehensible data division results in an efficient and simple database design. It reflects user-friendly properties, making it easier to maintain and optimize further per the newer requirements and changes.
#### Easy Scalabiity
With the growing business needs, the scalability of data also becomes easier. The reduced data redundancy ensures easy locating of the relevant data and subsequent upgrade of the relevant tables. It goes without impact on other unrelated aspects of the database.
#### Streamlines Data Updates
With easily accessible data and clear distinctions, the data update process is also seamless. It becomes less time-consuming and less prone to errors as the data needs to be updated in only one place. The possibility of missing out on the key information or repetition of data is removed. It also ensures data accuracy and quick retrieval.


## Disadvantages of Normalization
<ul>
<li>Normalization can result in increased performance overhead due to the need for additional join operations and the potential for slower query execution times.</li>
<li>Normalization can result in the loss of data context, as data may be split across multiple tables and require additional joins to retrieve.</li>
<li>Proper implementation of normalization requires expert knowledge of database design and the normalization process.</li>
<li>Normalization can increase the complexity of a database design, especially if the data model is not well understood or if the normalization process is not carried out correctly.</li>
</ul>

