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

