title=Database Comparison: Oracle 12c vs. Amazon DynamoDB
date=2016-12-17
author=Alex Makumbi
type=post
tags=blog
status=published
~~~~~~

You successfully applied and landed one of your biggest contracts that expects you to design, manage and scale a database for a medium size manufacturing and distribution company. Business requirements state that the database must be hosted in the cloud. After conducting research, you’ve landed on two of the most popular databases Amazon DynamoDB and Oracle 12c. 

Dynamo is Amazon’s managed NoSQL service known for its strong consistency and predictable performance. Its design feature is quite different from Oracle 12c, a Relational Database. Instead of the relational model, Dynamo uses alternate models for data management, such as key-value pairs or document storage. Comparisons of health, storage, and network connectivity between Oracle and Dynamo was a challenge since Dynamo is a managed service, meaning that Amazon Web Services provisions and running of infrastructure are handled for users. 

On the other hand, Oracle 12c is a version of the Oracle Database which can be referred to as an Oracle Relational Database Management System, an object-relational database management system. Oracle 12c is a cloud enabled database, the ‘c’ on the 12 indicates ‘cloud’. The database features include a multi-tenant option that help users bring together databases into a private or public clouds with the added capacity to share the same hardware, platform, and network making it ideal for the distribution side of the company. 

Regardless of which database should be implemented for the business, whether that is Dynamo or Oracle 12c, a database system must have scalable and robust mechanisms for its basic functions which include consistent storing, modifying, and retrieving data while efficiently handling failure detection, failure recovery, overloading handling, system monitoring among others. I find that discussing every detail of each mechanism to make a comparison between the two databases will eat up a lot of paper, and frankly would be missing the mark. Instead the discussion will focus on the three core system features used in Oracle 12c and Dynamo and compare the differences in the conclusion.

**Physical Storage Structures**

*Oracle*

Unlike NoSQL ecosystems, relational databases such as Oracle 12c have to allocate space for tablespace which are physically stored in data files. Each tablespace consists of one or more data files which mold to the host’s operating system where the database is running. The allocated disk space is formatted but contains no user data, so as the data grows space is used to allocate extents for the segment. Another distinction is that in Oracle 12c every data file is either online or offline. The administrator has ability to determine when data files are available. 

Another note is that Oracle 12c leans on control files that serve multiple important roles in the overall functionality of managed data files. They contain data files, online redo files, and others needed to open the database. Structural changes to the database are also monitored and tracked. Metadata must be accessible when the database is not open, so it is the control file’s job to provide checkpoints where instance recovery would be required to begin.

To protect against data loss, Oracle 12c maintains online redo log files so that data not yet written to data files is able to be retrieved after an instance failure. It is able to do this because server processes write every transaction synchronously to the redo log buffer. Online redo log always contains the undo data for permanent objects. Unlike Dynamo, with Oracle 12c the administrator is able to configure the database to store all undo data.

*Dynamo*

Dynamo fundamentally differs from Oracle storage system in terms of the aim of its requirements. Dynamo was created with the mindset that applications using it will always be “writeable”, and to achieve this, data store mechanisms were made to always update regardless of server failures or concurrent writes. This is a common requirement for many NoSQL ecosystems including of course Amazon applications, bringing us to another distinction. Dynamo is built for an infrastructure within a single domain where all nodes are assumed to be trusted. 

Two of the requirements that make Dynamo unique is its ability to scale incrementally and the use of vector clocks. To allow for this mechanism of scaling incrementally, its storage structures dynamically partition data over a set of nodes in the system. In particular, Dynamo’s partitioning relies on consistent hashing to distribute the load across multiple storage hosts which allows it to scale extremely fast at short amount of time. Dynamo uses vector clocks to capture events between different versions of the same object. A vector clock is essentially a list of node pairs and each clock is associated with version of every object.

**Logical Storage Structures** 

*Oracle*

Data in Oracle is stored in data block, extent, segment and tablespace; however, some of these storage hierarchy can be found inside one another. For example, a segment is a set of allocated specific database table and a table is a storage unit that contains one or more segments. Each segment belongs to one tablespace.

As we’ll find later, Dynamo’s partition settings are dynamically increased depending on the throughput. Oracle has a similar mechanism for keeping track and allocating additional storage in tablespace or retracting storage when an object no longer requires it. To achieve this, Oracle uses bitmaps in the tablespace which are aside for a bitmap. Automatic Segment Space Management method uses these bitmaps to manage space in a tablespace.

Each Oracle user is assigned a default permanent tablespace. Tablespaces control disk space allocation of data, control tablespace online and offline, perform backup and recovery and export and import application data. Temporary tablespace is also deployed when a permanent tablespace is operational, however its data lasts only for the duration of a session. They serve to improve the efficiency of space management operation.

*Dynamo*

Dynamo is a fully managed document database service running in the AWS cloud that provides very fast and predictable performance. The database is optimized to retrieve and store semi-structured data as documents, formatted in JSON or XML. 

Data in Dynamo is stored in partitions which are basically an allocated storage for a table, backed by solid-state drives and automatic replication across multiple available zones in AWS region. When a table is being created the database automatically allocates enough partitions so that the table can handle user set provisioned throughput requirements. And since Dynamo is designed to scale super-fast, increases in table’s provisioned throughput settings beyond what currently exists at a moment’s notice can allocate additional partitions.

Moving forward with our discussion on logical storage structures, it is important to understand how data is handled under Dynamo’s key/value interface. Tables usually have a partition key only or a partition key and sort key. Dynamo handles the two slightly differently to optimize efficiency. Under a partition key only table, the key has to be referenced when writing and reading items. A table with partition key and sort key similar to partition key, only now items are grouped and ordered by sort key value.

**Data processing**  

*Oracle*

Oracle being a Relational Database Management System adheres to Structured Query Language which provides the interface. All operations of the data in Oracle are performed using SQL statements. For instance, SQL statement could be used to create tables, query, and modify data in tables. A procedural extension named PL/SQL embedded with Oracle database allows developers to use all Oracle Database SQL statements, functions and data types. What is unique about this procedural extension is its ability to provide control to the flow of SQL program, variables and deployment of error-handling procedures. 

*Dynamo*

As noted earlier, Dynamo relies on provisioned throughput model to process data. A user is able specify read and writes via documents, such as JSON, XML declaring number of input operations that a table is expected to achieve. A user is also able to declare consistency characteristics for each read request within an application. The number of input operations can be determined by Item size, expected read and write request rates, has local or global secondary indexes etc.

Oracle 12c has a domain-specific language to query data, however Dynamo provides access with a simple application programming interface to create, read, update and delete data. Dynamo also has batch operations for reading and writing multiple items/rows across multiple tables. Another feature available is an atomic item and attribute operation, which basically allows for updating, adding, deleting and item only if a certain value is present or not present.

Dynamo’s impressive capabilities of taking in large amounts of data at a given notice means that it should also be able to read millions of data efficiently. To achieve this, Dynamo and many NoSQL databases support scan capabilities to address large-scale analytical processing. Dynamo’s Query API, filters and parallel scanning could be applied to narrow down result set.

**Metrics Comparison**

**Data model**

> Oracle 12c
>> Oracle’s relational structure organizes data into tables, which consist of rows and columns. The schema defines the tables, columns, indexes, relationships between tables, and other database elements.

> Amazon DynamoDB
>> A partition key is used to retrieve values, column sets, or semi-structured JSON, XML or other documents containing related item attributes.

-----

**Performance**

> Oracle 12c
>> Performance is generally dependent on the disk subsystem. Optimization of queries, indexes, and table structure is required to achieve peak performance.

> Amazon DynamoDB
>> The performance is generally a function of the underlying hardware cluster size, network latency, and the calling application.

-----

**Scale**

> Oracle 12c
>> Oracle’s structure makeup makes it easiest to scale up with faster hardware.

> Amazon DynamoDB
>> Dynamo was designed with the purpose of scaling out using distributed clusters of low-cost hardware to increase throughput without increasing latency.

-----

**APIs**

> Oracle 12c
>> Structured Query Language (SQL) is used to store and retrieve data requests. Queries are parsed and executed by relational database management systems (RDBMS).

> Amazon DynamoDB
>> It is easy to retrieve and store data structures with object-based APIs. Partition keys let applications look up key-value pairs, column sets, or semi-structured documents.

-----

**Data Storage**

> Oracle 12c
>> Partitions. 

> Amazon DynamoDB
>> Automatic Segment Space Management (ASSM) is used in conjunction with bitmaps.

-----

**Conclusion**

Amazon Dynamo and Oracle 12c are all excellent databases because they are capable of scaling extremely fast in a short amount of time. Deciding on what database to implement for a business setting ultimately depends on the type of data you’ll be storing, the volume of data, among others. Each database has its strength and weaknesses. While conducting research, I found that a user willing to be hands on might consider working with Oracle 12c. With Oracle, you have to provide your own hardware, for example to allocate disk space used to create room for the segments. You also have control over whether the database is online or offline, determining when data files are available. Dynamo removes you from having to think about how to set up the infrastructure because the database’s ecosystem is handled by Amazon Web Services.

Each database handles instance failure different as well, I found that Oracle automatically maintains processes to write every transaction synchronously to the redo log buffer so that data not yet written to data files can be retrieved. Dynamo was designed with the expectation that failures are going to occur, so the database is constantly anticipating these anomalies, as a result, data store mechanisms were made to also update regardless of server failure. In this sense, each database handles these basic but critical functions. So in a sense both databases are similar in that they have the capabilities to handle instance failure. 

Another similarity to point out is that both databases are capable of scaling extremely fast in a short amount of time, though each accomplishes this in its own unique way. We know that data is stored in partitions in Dynamo, so when a large amount of data is stored partition settings dynamically increase. And for Oracle, an Automatic Segment Space Management (ASSM) is used in conjunction with bitmaps to manage space in tablespace. In a sense, ASSM functions similar to partition settings in that storage is able to be automatically fluctuate to accommodate incoming flows of data.

In conclusion, determining which database to use boils down to your business requirements and expectations of how data should be stored, modified or gathered. I would be remised if I did not end the discussion by mentioning one obvious distinction, which is that Oracle is a relational database management system and adheres to Structured Query Language. On the other hand, as we’ve touch on quite a bit is that Dynamo a NoSQL database relying on a provisioned throughput model to process data via documents, such as JSON and XML.

 


 

