Before understanding the auto-commit we should know about the transcations in DBMS.

**Transactions:**

There are times when we do not want one statement to take effect before completing another one. For better understanding I will explain it with and example. Suppose a book from the library is issued to a student, we have to decrease the number of available books from a Books table and we have to increase the count of borrowed books of that student in the Student table. Then we have to insert a record in one another table in which we will mention book id, student id, and issued date. All of these records should be updated at the same time, otherwise, the data will be inconsistent. 
The way to be sure that either action occurs or neither action occurs is to use a transaction. The transaction is a set of one or more statements that are executed as a unit, so either all of the statements are executed, or none of the statements are executed.Transactions enable you to control if, and when, changes are applied to the database. It treats a single SQL statement or a group of SQL statements as one logical unit, and if any statement fails, the whole transaction fails.

**What is auto-commit?**

The auto-commit means that every update to the database is immediately made permanent. By default, JDBC uses an operation mode called auto-commit.
If your JDBC Connection is in auto-commit mode, which is by default, then every SQL statement is committed to the database upon its completion. 
If your JDBC Connection is in auto-commit mode, which is by default, then every SQL statement is committed to the database upon its completion.
If we disabled the auto-commit operation mode of the JDBC connection then changes will not be reflected in the table unless we explicitly call commit() method of the. We can also commit the changes by enabling the auto-commit mode of connection. After enabling auto-commit mode changes will get committed for every transaction automatically.

**Buffer Pool:**

All the above-mentioned text will generate one genuine question and the question is that where is the uncommitted data get stored?And the answer is the data gets stored in the SQL buffer pool.
SQL Server retrieves the data from two areas i.e. disk and memory. The disk I/O operations are slower than memory I/O.
The Buffer Pool is a place in system memory that is used for caching tables and index data pages as they are modified or read from disk. The primary purpose of the SQL buffer pool is to reduce database file I/O and improve the response time for data retrieval. In SQL Server, the data in the table is stored in pages that have a fixed size of 8 KB. Whenever there is a need for a page (read or write) the page is first read from the disk and bought to memory location. This area in SQL Server Memory is called “Buffer Pool”.Once the page is loaded in memory, all subsequent calls which need this page would be read from Buffer Pool. This will reduce the disk I/O operations.
