# Big Data Modeling and Management

##Introduction

###Data Ingestion

Data Ingestion deals with the policies in place that deal with the data that is entering the system. 

This includes how the data is dealt with based on data rate and errors. This is known as the **Data Ingestion Policy** this includes the way the system handles the rate of data(Ex: Whether or not to drop data records if the data rate is too high) and how to deal with erronous data entering the system.

###Data Storage

This deals with the size and architecture(Storage Hierarcy) of the storage infrastructure used in the Big Data system and the cost/performance tradeoff for the same.

###Data Quality

Data Quality is whether or not the data is sufficiently free of errors and inconsistencies. There are several reasons why Data Quality is required such as:

-  The final use case of the data(Ex: Sectors like healthcare and finance) may require a certain degree of accuracy
- Legal regulations in place requiring a certain quality of data
- Need for accurate actionable insights which lead to optimal business decisions.

### Data Operations

Broadly 2 types of Data Operations: 

- Operations on a single Data-Item that produce a sub-item(Ex: SubArray or crop on an image)
- Operation on Collections of Data Items - These can be run in a data parallel fashion for much more efficient execution

###Data Scalability

####Scaling Up(Vertical Scaling)

- Adding more processors/RAM/ Compute Capabilities to the Existing Hardware or Buying more powerful hardware
- Many operations tend to perform better with higher memory/ more cores.
- Difficult and Expensive to maintain

####Scaling Out(Horizontal Scaling)

- Addding more, possibly less powerful machines interconnected over a high speed Network.
- Parallel operations may be slower
- Easier to maintain and add the machines



The recent trend is to develop systems that are able to *Scale Out* easily and are built to be able to do the same.

### Data Security

- Data security is a must for sensitive data.
- Increased and Distributed systems pose a larger security hazard. 
- Encryption/Decryption may add a lot of Data Processing overhead to the systems. 
- This still remains a research issue till date amongst the Big Data community.

## Big Data Modeling

Data Models represent the characteristics and organization of the data in question.

###Data Model Structure

Data can be classified either **Structured Data** or **Unstructured Data**

Structured Data tends to follow a fixed pattern of data organization while unstructured data does not.

JPEG Images, MP3 Audio Files, Video Files are examples of **Unstructured Data**.

CSV Files, Database entries are examples of **Structured Data**.

###Data Model Operations

The second component of a data model is a set of operations that can be performed 

on the data. Example:

- Subsetting : Retrieve a subset of the data from a collection based on a condition
- Substructure Extraction : Retrieve a part of a structure from every data item as specified, also known as "*projection*"
- Union - Create a new collection of records given two collection of records
- Join - Combine two collections with different data structures but with a common field/parameter. Can be expensive with a large number of records

###Data Model Constraints

Constraints are logical statements which restrict the data that may be stored in a collection. 

Types of Constraints:

- Value Constraint : "Age is never -ve"
- Uniqueness Constraint : "No two products can have the same Product ID"
- Cardinality Constraint(Number of associated objects) : "A child can have no more than 2 legal parents"
- Type Constraint : "Name has to be alphabetical"
- Domain Constraint : "Month has to be any entry in {Jan, Feb….. Dec}"
- Structural Constraint : "Matrix has to be a square matrix"



### Relational Data Model

Relational Data Model is charactarized by the structure of the data that it admits into the collection of data items , the operations on the structure and the way constraints are specified.

In a record of the relational model or '*Relational Tuple*', unless otherwise stated, each of the elements are atomic and can no further be decomposed.

A relational table has a fixed structure known as a '*Schema*' which dictates the datatypes and the constraints associated with each field.



### Semi-Structured Data Model

- Unlike the Relational Data Model, instances of the Semi-Structured Model tend to have a Nested Tree Structure, which allows for '*navigational access*' to data

- Unlike a relational structure a Data Object may hold lists of items and the lengths of these can be different. Therefore the Semi-Structured Data Model is more flexible than the Relational Data Model. 
- In a Semi Structured Data Model, one can perform a query of both the schema and not just the data



### Vector Space Model

- Used to search documents for a given text in a huge collection of text-data.
- Used to compute similarity between documents
- Document Vector(**TF- IDF**) = Term Freq Matrix(**TF**)   X Inverse Document Frequencies(**IDF**)    
- Inverse Doc Frequency(Word<sub>i</sub>) = log<sub>2</sub>(Number of Documents/Occurences of Word<sub>i</sub> in all the Documents)
- **IDF** acts as a penalization factor for words that are too commonplace to be of any importance(Ex: "is", "and", etc…)
- Document search is performed by finding the distance between 2 documents in the vector space.
- Query Terms may optionally be weighted.
- Can also be used for Image Similarity Search using 'Binned Histograms' as a vector space. 



### Graph Data Model

Graph data model bears not just the properties and attributes(Nodes Data) of entities but also their connectedness(Edges) to other objects

The various operations one can perform using graph models are:

- Optimal Path Operation : 
- Finding Densely connected cluster/subgraph withing a graph('**Communities**')
- Detection of Connected Components of a graph



## Working with Big Data

###Streaming Data

A **Data Stream** is a constant feed of data flowing in from a given source that needs to be processed almost immediately after its generated. It can be a possibly unbounded sequence of data-items or records that may or may not be correllated. Each data-item has a time stamp and may be geo-tagged.

*Example*: Monitoring and detection of potential failures in an IoT System or set of connected sensors.

Streaming Data Systems have the following characteristics: 

- Only one chance to look at and process the data.(One record at a time / Short Time window)

- Have to deal with high velocity and size of the incoming Big Data in near realtime.

- Processing components subscribe to the stream non-interactively

- Independent Computations

  

**Data at Rest** refers to mostly static data from one or more sources collected *prior* to the actual analyis of the data. Processing of this type of data is known as *Batch Processing*. 

**Data in Motion** refers to the way data is analyzed as it is generated.  Processing of this type of data is known as *Stream Processing*. Size of the data is unbounded and hence iterative/looping algorithms are not feasible.



#### Stream Processing

- Compute one or a small window of data-items at a time
- Fast turnaround and simple computations
- No interaction with the data source

Most real world applications use a hybrid of Stream and Batch Processing where initially data is processed real time but then pushed to a batch processing system. 

However Streaming Data poses several challenges due to which it has to be handled and processed in a different way.

- Size and frequency of incoming data can be very unpredictable.( Ex: Incoming tweets may increase during sporting events) 

- Changes can be periodic or sporadic

- May have to deal with dropped / missing data or even no data at a given point in time.

- Require fast algorithms

  

###Data Lakes

A Data Lake is a part of a big data infrastructure that allows several Data Streams to flow in and be collected and processed.We can think of it as a massive storage depository with huge processing power and ability to handle a very large number of concurrence, data management and analytical tasks. 

Each data object is stored in a flat file system with unique identifiers as a BLOB(Binary Large OBject) and tagged with some metadata.

Data Lakes works as follows:

1. Load Data from source.
2. Store as raw data in the data lake. 
3. Applications can freely read from the data lake and add their own desired structure(**Schema on Read**)

Data Lakes can potentially support all kinds of applications and users as they store a wide variety and range of data.

### Data Warehouse 

A Data Warehouse is a component of Big Data infrastructure that stores data for a particular use in a given structured format. 
Data is stored in a hierarchical file system with some structure.

Data Warehouses works as follows:

1. Load Data from source.
2. Data is transformed into a specific structure and then written(**Schema on Write**)
3. Applications that wish to use the data need to know this structure to access this data.



## Big Data Management

#### Advantages of DBMS

- Declarative Query Languages can be used (Only need to mention *what* to be fetched and not *how*)
- Data Independence(Isolate applications from DBMS Implementation)
- System automatically finds efficient ways of fulfilling queries.
- Implementation of Transactional Safety and Failure recovery.(In built systems to maintain Data Integrity and Security during Transactions)
- Conflict Free concurrent acces



#### Parallel DBMS:

- Improves Performance through parallel implementations
- Often allows data replication
- Allows data redundancy



#### Distributed DBMS:

- Network of independently running connected DBMS systems that are communicating with each other.
- Each instance may not have the entire schema but may be aware of part the schema of their neighbours. 
- Can pass queries or parts of the query to its neighbours.



### From DBMS to BDMS

#### Desirable Characteristics of BDMS

- A Flexible, semi-structured model
- Should support a wide variety of data types and allow many operations on the same
- A full query language that is ATLEAST as powerful as *SQL*
- An efficient parallel query runtime that can run on multiple machines
- Wide range of query sizes
- Ability to support continuous data ingestion and streaming data.
- Ability to scale gracefully to support large volumes of data and efficiently utilize machines on the cluster to fulfill these data requirements
- Simple operational management even for large clusters spanning geographical locations.



####ACID and BASE Properties

In traditional DBMS Systems, we talk about the **ACID** Properties for transactional security. But in BDMS Systems,ACID properties are difficult to maintain, hence these properties are relaxed to a certain extent and replaced with **BASE** Properties:

- **B**asic **A**vailability - System guarantees a response irrespective of response type/status.

- **S**oft state - State of system is very likely to change and at a given point of time the state of the system is known as *Soft*

- **E**ventual consistency - Eventually, if the system stops receiving input, every component will become consistent. *Eventually*. 



#### CAP Theorem

This theory states that a **Network Partitioned** BDMS Cannot simultaneously provide all of the following:

- Consistency
- Availability
- Partition Failure Tolerance



#### Redis - In Memory Key-Value store

- **Redis** is not a full blown DBMS however it's intended use case is to use in-memory storage to make common data structures accessible to the users.

- Data Structures supported: Strings, Hashes, Lists, Sets, Sorted Sets

- Redis string can be binary and can be upto 512 megabytes in size
- Keys may have an internal structure and an expiry after which the data is removed from the memory cache as memory is expensive
- Values corresponding to a key can also be a collection of items(Such as a list or a set). Redis compresses these lists to be able to store in memory efficiently by using *ZipLists*.
- **Partitioning** in Redis: 
  - Range Partitioning: Records are split into ranges and partitioned accordingly on different machines(Ex: Records 1- 10,000 on Machine 1, etc..)
  - Hash Partitioning: Records are partitioned using the hash function of the Key(Ex: Key = 152, 152 mod 10 = 2, so record goes to Machine 2, etc..)
- **Replication** in Redis:
  - Redis accomplishes replication using Master-Slave Replication
  - Clients write to the master node and master node replicates to the slaves
  - Clients read from the slaves to scale up the read performance.
  - The replication processes are synchronous, that is that slaves do not get replicated data, it locks them with each other. However  the replication process does ensure that they're consistent with each other

####Aerospike - A new generation Key Value Store

- Distributed NoSQL DB and KV Store.
- Aerospike can interoperate with Hadoop based systems, Legacy DBs or even Realtime DBs.
- Allows applications to serve its users using fast lookups and hence allows high availability of data.
- Typically uses an SSD for persistence storage to allow fast I/O and retrieval
- Data Types: Scalar Values, Lists, maps, geospatial(Lat/Lng), large objects
- KV Store Operations: Allows user to perform Geospatial query(Ex: point-in-polygon: Is a given point within a given polygon, *distance*: List of points within 5km)
- Aerospike also provides a declerative query language(AQL), an SQL like language(Ex: SELECT name, age FROM users.profiles)
- Aerospike ensures ACID Properties:
  - Consistency:
    - Immediate Consistency provided by using *Synchronous Writes*
    - Eventual Consistency can be achieved by making use of various mechanisms provided by Aerospike to relax Immediate consistency on clusters and bypass some of the consistency checks
  - Durability:
    - Achieved by storing data on Flash Storage on every node
    - Data is also replicated across nodes in the same cluster and also in remote clusters
  - Reduced Network Partitioning:
    - The above properties may seem to contradict the **CAP Theorem** however that only holds for Partitioned Systems. 
    - Aerospike tries to minimize the partitioning of data by ensuring the master nodes know exactly where the all the other nodes are and replication is happening properly even when new nodes are joining the network.

#### AsterixDB - DBMS for Semistructured Data

The below declerations correspond to the type creation for User and Tweets for Twitter message JSON Data.

```
create dataverse LittleTwitterDemo;
create type TwitterUserType as open {
 screen-name: string,
 lang: string,
 friends_count: int32,
 statuses_count: int32,
 id: int32,
 followers_count: int32
}
create type TweetMessageType as closed {
 tweetid: string,
 user: TwitterUserType,
 geo: point?,
 created_at: datetime,
 referred-topics: {{ string }},
 text: string
}
create dataset TweetMessages(TweetMessageType)
primary key tweetid;
```



- The **?** in the point decleration indicates an optional type

- If you notice, there are two different declerations: **open** and **closed**
  - **open** means the actual data can have more attributes than specified. 
  - **closed** on the other hand means it has to have the same attributes



- **create dataset** asks the system to create a dataset with the specified type



**Querying in AsterixDB**

- AsterixDB provides it's own native query language(**AQL**) and also supports other languages(Hive, XQuery, Hadoop MR Jobs, SQL++(coming up) )
- AsterixDB converts queries in other languages into a set of low level operations like select and join before passing it to its query processing engine.



**AsterixDB on a Cluster**

- Like many other BDMS Systems, Asterix is designed to operate on a cluster of machines
- The basic idea is to use Partition Data Parallelism
- Each data set is divided into instances of various types which can be decomposed to different machines by either range partitioning or hash partitioning.
- A runtime distributed execution engine called **Hyracks** is used for partitioned parallel execution
- **Hyracks** also breaks up the query into a number of jobs and determines which can be performed in parallel and which have to be executed stage by stage.
- This whole thing is managed by a cluster controller



**Accessing Real Time and External Data**

- Asterix can access real time data from files in a directory path(Code snippet below)

  ```
  create dataset Tweets (Tweet)
   primary key id;
  create feed TestFileFeed using localfs
  (("path"="127.0.01:///Users/adc/text/"),
  ("format"="adm"), ("type-name"="Tweet"),
  ("expression"=".*\\.adm"));
  connect feed TestFileFeed to dataset Tweets;
  ```



- Asterix can also access External data from a Real-Time API(Code snippet below)

  ```
  use dataverse feeds;
  create dataset Tweets (Tweet)
   primary key id;
  create feed TwitterFeed if not exists using "push_twitter"
   (("type-name"="Tweet"),
   ("consumer.key"=“some-key"),
   ("consumer.secret"=“some-secret"),
   ("access.token"=“some-token"),
   ("access.token.secret"=“some-token-secret"));
  connect feed TwitterFeed to dataset Tweets;
  ```

  



#### Solr - Managing Text

#####Challenges of dealing with Text Data

Some of the basic challenges that come with dealing with text involve defining exactly what a match is. Some examples of various cases of this are given below:

- Analyse / Analyze / ANALYZE (Lexical Differences and Capitalization)
- abc:def:230-39 / abcdef23039 (Structural punctuations)
- Barack Obama / Barack Hussain Obama / Barack H. Obama/etc.. (Nominal Variations)
- Mom / Mother (Synonyms)
- Dr. / Doctor (initalism)
- USA / United States of America (Abbreviations)



#####Inverted Index

- Vocabulary: A collection of all the terms present in the document or set of all documents. Can be a single term or even a collection of synonyms
- Occurence: List of information stored along with each term in the vocabulary, including which documents the term is contained in and where exactly they occur. May also store other statistics for each term like *tf-idf*, *tf*, etc..
- Inverted Index: Index which, for each term, stores atleast the ID of the document(s) for where this term occurs



#####Solr Functionality

- Solr is an Open Source enterprise search platform, the heart of which is its search functionality.However Solr does offer other functionalities as well.

- Solr can take any structured document, such as a CSV file and index each of the fields(Text, Geographic Data, Numbers, etc..) with an **Inverted Index**.
- The system designer can explicitly specify how Solr is to parse the document by configuring the Tokenizer and the Filter. 
  - **Tokenizer** decides how to split the given body of text into various discrete tokens.(Ex: Using Space, "." and "," as delimiters, etc..)
  - **Filter** decides what characters should be filtered out of the text and how to transform these tokens(Ex: Treat synonyms as the same token using a synonym file, Convert all tokens to lower case, etc..)



#### Vertica - Relational Columnar DBMS System

![Row and Column Oriented Databases](/Users/skvrahul/Library/Mobile Documents/com~apple~CloudDocs/Projects/coursera/bigdata-specialization-ucsandiego/img/row_col_db.jpg)

**Vertica** is a Columnar Database Management system that belongs to a new breed of DB Systems known as Analytical Databases.

The above diagram illustrates the difference between a *Row-Oriented* and a *Column-Oriented* Database.

##### Column Store

- Stores data column wise.
- Only uses the columns/attributes that are needed
- Tend to be much faster and uses smaller memory, even for larger data, and uses the following methods to maintain 



#####Space Efficiency in Column Store

- Columns are stored in sorted order
- Values in columns can be compressed
  - Run Length Encoding: Compress a series of repeated records into one record which stores the number of repititions(Ex: 2018, 2018, 2018, 2018, 2018, 2018    —> [2018, 6] )
  - Frame of Reference Encoding: Fix a number and store only the difference for the consecutive records(Ex: 107, 108, 109, 110  —>  [107]  0, 1, 2, 3)
- This compression saves storage space



##### Working with Vertica

- Vertica allows decleration of **Column Groups**(Set of columns from the data which are frequently accessed together). This grouping increases performance as these are frequently co-accessed.

- Update Performance is slower as Vertica internally writes to a Row Oriented Representation and then later converts it into a Column Based Representation

- Vertica, being an **Analytical Database** system, comes with an enhanced suite of Analytical Operations:

  - Statistical Functions on a window of data
  - Vertica can also act as a Data Supplier for Distributed R, a platform for high performance statistical computing.

  



















