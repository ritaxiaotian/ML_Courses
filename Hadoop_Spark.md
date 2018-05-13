# 1. Udemy The Ultimate Hands-On Hadoop - Tame your Big Data! 

https://www.udemy.com/the-ultimate-hands-on-hadoop-tame-your-big-data/learn/v4/overview

## Section 1 Learn all the buzzwords and install hadoop

#### 1.1 Introduction and install hadoop on your desktop

1. Install VirtualBox

Ubuntu 16.04 ("Xenial")  i386 |  AMD64

i386 refers to the 32-bit edition and amd64 (or x86_64) refers to the 64-bit edition for Intel and AMD processors. 

2. hortonworks.com/sandbox

3. Import Hortonworks Docker Sandbox into VM -- It's a pre-installed Hadoop environment

4. download movie data from https://grouplens.org/

5. run Docker Sandbox: maria_dev; maria_dev

http://127.0.0.1:8888/#

6. Use Hive to operate on u.data & u.item

**Not really on a relational database. The tool Hive let us interact with our data on Hadoop as if it were a relational database.**

#### 1.2 Hadoop overview and history

**What is Hadoop**: an **open source software platform** for **distributed storage** and **distributed processing** of very **large data sets** on **computer clusters** built from commodity hardware" -- Hortonworks

**Hadoop History: **

    1. Google published GFS (distributed storage) and MapReduce == spark (distributed process) papers in 2003-2004

    https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf

    2. Yahoo! was building "Nutch", an open source web search engine at the same time

    3. Hadoop was primarily driven by Doug Cutting and Torn White in 2006

    4. It's been evolving ever since...
    

**Why Hardood:**

1. Data is too darn big

2. Vertical scaling doesn't cut it

    disk seek times
    
    hardware failures
    
    processing times
    
3. Horizontal scaling is linear

4. Hadoop: it's not just for batch processing anymore

#### 1.3 overview of the Hadoop Ecosystem

World of Hadoop: Query Engines. Core HadoopEcosystem, External Data storage

Hadoop built-in sections:
 
**HDFS: Hadoop Distributed File System (Distributed data storage)**
 
**YARN: Yet another resource negotiator:** 

    Data processing starts to come into play
    
    manage the resources on the computing cluster
    
    Which nodes are available for extra work, etc.
    
**MapReduce: High level programming model that allows you to process your data across an entire cluster**

    mappers: transform your data in parallel across your entir computing cluster in a very efficient manner
    
    reducers: aggregate that data together
    
**Others:

**Pig: write simple scripts that look a lot like SQL in some cases that allow you to chain together queries and get complex answers but without actually writing Python or Java code.

**Hive: Taking SQL queried and making this distributed data that is just really sitting on your file system somewhere look like a SQL database

**Apache Ambari: sits on top of everything, gives your a view of your cluster and lets you visualize what's running on your cluster , what systems are using how much resources and also has some views in it that allow you to actually do things like execute hive queried or import databases into hive or execute Pig queries and things like that.

**MESOS: Alternative to YARN, solve same problems in the same way

**SPARK: One of the most exciting technique in Hadoop system. Same level of mapreduce. Write Spark script in Python or Java or Scala.Scala being prefered. Fast and powerful!!

    Handle SQL queries
    
    Do ML across an entire cluster of information
    
    Handle streaming data in real time

**TEZ: use some of the same techniques as SPARK notably with something that is called a directed acyclic graph and this gives Tez a leg up on what map reduce does. Used in conjunction with Hive to accelerate it.

**HBASE: NoSQL database: a very very fast database meant for very large transaction rates. It's appropriate for example for hitting from a web application, hitting from a website doing all types of transaction. So HBase can actually expose the data that's stored on your cluster and maybe that data was transformed in some way by spark or mapreduce.

**Apache Storm: process streaming data from censors and web logs in real time. == Spark streaming

**oozie: way of scheduling jobs on your cluster

**Zookeeper: tech for coordinating things on your computer, across clusters

**Data Ingesting: Tying your Hadoop database into a relational database: sqoop, flume: transform web logs in real time, kafka: data ingestion

**External data storage: MySQL, cassandra, mongoDB

**Query Engines: Apache Drill: write SQL queries to work in NoSQL environment, Hue, Phoenix, presto, apache zeppelin


#### 1.4 Tips for using this course

http://sundog-education.com/hadoop-materials/

## Section 2 Using Hadoop's Core: HDFS and MapReduce

#### 5 HDFS: What it is, and how it works

The Hadoop distributed File system

        1. Handle big files
        
        2. By breaking them into blogs
        
        3. stored across several commodity computers
  
The Hadoop distributed File system Architecture: name nodes and data nodes

Reading a file: client node, name node, data node

1. Backup Metadata: 

2.Secondary Namenode: maintains merged copy of edit log you can restore from

3.HDFS Federation: Each namenode manages a specific namespace volume

4.HDFS High Availability

**5.Using HDFS: 1. UI(Ambarl) 2. Command-line Interface 3. HTTP/HDFS Proxies 4. Java interface 5. NFS Gateway**

#### 6. Install the MovieLens dataset into HDFS using Ambarl

http://127.0.0.1:8080/#/main/view/FILES/auto_files_instance

#### 7. Install the MovieLens dataset into HDFS using the command line (ssh on Linux, putty on Windows)

xiao@MachineLearning:~$ ssh maria_dev@127.0.0.1 -p 2222

[maria_dev@sandbox-hdp ~]$ hadoop fs -ls

[maria_dev@sandbox-hdp ~]$ hadoop fs -mkdir ml-100k

[maria_dev@sandbox-hdp ~]$ hadoop fs -ls

[maria_dev@sandbox-hdp ~]$ wget http://media.sundog-soft.com/hadoop/ml-100k/u.data

[maria_dev@sandbox-hdp ~]$ hadoop fs -copyFromLocal u.data ml-100k/u.data

[maria_dev@sandbox-hdp ~]$ hadoop fs -ls ml-100k

[maria_dev@sandbox-hdp ~]$ hadoop fs -rm ml-100k/u.data

[maria_dev@sandbox-hdp ~]$ hadoop fs -rmdir ml-100k

[maria_dev@sandbox-hdp ~]$ hadoop fs -ls 

#### 8. MapReduce:what it is and how it works

Why Mapreduce

    Distributes the processing of data on your cluster

    Divides your data up into partitions that are mapped (transformed) and reduced (aggregated) by mapper and reducer functions you define.

    Resilient to failure-an apllication master monitors your mappers and reducers on each partition
    
Illustrate with an example: How many movies did each user rate in the MovieLens data set?

    1. Mapping: The mapper converts raw source data into key(user ID)/value (movies) pairs
        
        Mapper function: Extract and organize what we care about
        
        MapReduce Sorts and Groups the Mapped data ("shuffle and sort")
        
        The Reducer processes each Key's Values  

#### 9. How MapReduce distributes processing

1. Mapper 2. Shuffle and Sort 3. Reducer

How are mappers and reducers written?

Map reduce is natively Java

STREAMING allows interfacing to other languages (ie python)

Easy to parallel, trickes are used to be more efficient

#### 10. MapReduce example: Break down movie ratings by rating score

###### Writing the Mapper

    def mapper_get_ratings(self, _, line):

        (uerID, movieID, rating, timestamp) = line.split('\t')

        yield rating, 1
    
###### Wrting the reducer

    def reducer_count_ratings(self, key, values):

        yield key, sum(values)


#### 11. Troubleshooding tips: installing pip and mrjob


#### 12. Installing Python, MRjob, and nano

**ssh maria_dev@127.0.0.1 -p 2222

su root

Password: 

You are required to change your password immediately (root enforced)

Changing password for root.

(current) UNIX password: 

New password: 

Retype new password: 

[root@sandbox-hdp maria_dev]# 

[root@sandbox-hdp maria_dev]# yum install python-pip

[root@sandbox-hdp maria_dev]# pip install mrjob==0.5.11

[root@sandbox-hdp maria_dev]# yum install nano

[root@sandbox-hdp maria_dev]# wget http://media.sundog-soft.com/hadoop/ml-100k/u.data

[root@sandbox-hdp maria_dev]# wget http://media.sundog-soft.com/hadoop/RatingsBreakdown.py


[root@sandbox-hdp maria_dev]# nano RatingsBreakdown.py

#### 13. Code up the ratings histogram MapReduce job and run it

1. run locally: - python RatingsBreakdown.py u.data

2. run with Hadoop: - python RatingsBreakdown.py -r hadoop --hadoop-streaming-jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar u.data

#### 14. Rank movies by their popularity

#### 15. Check your results against mine

[root@sandbox-hdp maria_dev]# wget http://media.sundog-soft.com/hadoop/TopMovies.py


## Section 3 Programming Hadoop with Pig

#### 16. Introducing Ambari

http://127.0.0.1:8080/#/main/dashboard/metrics

#### 17. Introducing Apache Pig

**Enable you to use mapreducer without having to write map and reducer code**

Why Pig?

1. Writing mappers and reducers by hand takes a long time

2. Pig introduces Pig Latin, a scripting language that lets you use SQL-like syntax to define your map and reduce steps.

3. Highly extensible with user defined functions (UDF's)

Methods to run Pig

1. Grunt

2. Script

3. Ambari/Hue

#### 18. Example: Find the oldest movie with a 5-star rating using Pig


#### 19. Find old 5-star movies with Pig

#### 20 More Pig Latin

#### 21. Find the most rated one star movie

#### 22. Pig Challenge: Compare Your Results to Mine!

### Section 4 Programming Hadoop with Spark

#### 23. Why Spark

#### 24. The Resilient Distributed Dataset (RDD)

#### 25. Find the movie with the lowest average rating - with RDD's

#### 26.Datasets and Spark 2.0

#### 27. Find the movie with the lowest average rating -- with DataFrames

#### 28.Movie recommendations with MLLib

#### 29. Filter the lowest-rated movies by number of ratings

#### 30. Check your results against mine


### Section 5 Using relational data stores with Hadoop




### Section 6 Using non-relational data stories with Hadoop




### Section 7 Querying your data interactively




### Section 8 Managing your Cluster




### Section 9 Feeding Data to your Cluster




### Section 10 Analyzing Streams of Data




### Section 11 Designing Real-World Systems


### Section 12  Learning more



# 2. Udemy Spark and Python for Big Data with PySpark

https://www.udemy.com/spark-and-python-for-big-data-with-pyspark/learn/v4/overview


