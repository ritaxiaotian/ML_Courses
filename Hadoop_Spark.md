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
    
**Others:**

**Pig: write simple scripts that look a lot like SQL in some cases that allow you to chain together queries and get complex answers but without actually writing Python or Java code.**

**Hive: Taking SQL queried and making this distributed data that is just really sitting on your file system somewhere look like a SQL database**

**Apache Ambari: sits on top of everything, gives your a view of your cluster and lets you visualize what's running on your cluster , what systems are using how much resources and also has some views in it that allow you to actually do things like execute hive queried or import databases into hive or execute Pig queries and things like that.**

**MESOS: Alternative to YARN, solve same problems in the same way**

**SPARK: One of the most exciting technique in Hadoop system. Same level of mapreduce. Write Spark script in Python or Java or Scala.Scala being prefered. Fast and powerful!!**

    Handle SQL queries
    
    Do ML across an entire cluster of information
    
    Handle streaming data in real time

**TEZ: use some of the same techniques as SPARK notably with something that is called a directed acyclic graph and this gives Tez a leg up on what map reduce does. Used in conjunction with Hive to accelerate it.**

**HBASE: NoSQL database: a very very fast database meant for very large transaction rates. It's appropriate for example for hitting from a web application, hitting from a website doing all types of transaction. So HBase can actually expose the data that's stored on your cluster and maybe that data was transformed in some way by spark or mapreduce.**

**Apache Storm: process streaming data from censors and web logs in real time. == Spark streaming**

**oozie: way of scheduling jobs on your cluster**

**Zookeeper: tech for coordinating things on your computer, across clusters**

**Data Ingesting: Tying your Hadoop database into a relational database: sqoop, flume: transform web logs in real time, kafka: data ingestion**

**External data storage: MySQL, cassandra, mongoDB**

**Query Engines: Apache Drill: write SQL queries to work in NoSQL environment, Hue, Phoenix, presto, apache zeppelin**


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

Ratings = LOAD '/user/maria_dev/ml-100k/u.data' AS (userID:int, movieID:int, rating:int, ratingTime:int);

This creates a relation named "ratings" with a given schema. ( a series of tuples)

    (660,229,2,891406212)
    (412,489,4,892241344)
            ...
Use PigStorage if you need a different delimiter

    metadata = LOAD '/user/maria_dev/ml-100k/u.item' USING PigStorage('|')AS (movieID:int, movieTitle:chararray,
    releaseDate:chararray, videoRelease:chararray, imdbLink:chararray);
    
    DUMP metadata;
    
(1,Toy Story (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?Toy%20Story%20(1995))

(2,GoldenEye (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?GoldenEye%20(1995))

(3,Four Rooms (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?Four%20Rooms%20(1995))

(4,Get Shorty (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?Get%20Shorty%20(1995))

(5,Copycat (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?Copycat%20(1995))

Creating a relation from another relation; FOREACH / GENERATE

    metadata = LOAD '/user/maria_dev/ml-100k/u.item' USING PigStorage('|') AS (movieID:int, movieTitle:chararray, releaseDate:chararray, videoRelease:chararray, imdbLink:chararray);

    nameLookup = FOREACH metadata GENERATE movieID, movieTitle, ToUnixTime(ToDate(releaseDate, 'dd-MMM-yyyy')) AS releaseTime;


(1,Toy Story (1995),01-Jan-1995,,http://us.imdb.com/M/title-exact?Toy%20Story%20(1995))

to

(1,Toy Story (1995),788918400)

Group By

    ratingsByMovie = GROUP ratings BY movieID;

    DUMP ratingsByMovie;

(1,{(807,1,4,892528231),(554,1,3,876231938),(49,1,2,888068651), ... }

(2,{(429,2,3,882387599),(551,2,2,892784780),(774,2,1,888557383), ... }

    avgRatings = FOREACH ratingsByMovie GENERATE group AS movieID, AVG(ratings.rating) AS avgRating;

    DUMP avgRatings;

(1,3.8783185840707963)

(2,3.2061068702290076)

(3,3.033333333333333)

(4,3.550239234449761)

(5,3.302325581395349)

    DESCRIBE ratings;
    DESCRIBE ratingsByMovie;
    DESCRIBE avgRatings;
    ratings: {userID: int,movieID: int,rating: int,ratingTime: int}
    ratingsByMovie: {group: int,ratings: {(userID: int,movieID: int,rating: int,ratingTime: int)}}
    avgRatings: {movieID: int,avgRating: double}
    
FILTER

    fiveStarMovies = FILTER avgRatings BY avgRating > 4.0;

(12,4.385767790262173)

(22,4.151515151515151)

(23,4.1208791208791204)

(45,4.05)

JOIN

    DESCRIBE fiveStarMovies;
    DESCRIBE nameLookup;
    fiveStarsWithData = JOIN fiveStarMovies BY movieID, nameLookup BY movieID;
    DESCRIBE fiveStarsWithData;
    DUMP fiveStarsWithData;
    
fiveStarMovies: {movieID: int,avgRating: double}

nameLookup: {movieID: int,movieTitle: chararray,releaseTime: long}

fiveStarsWithData: {fiveStarMovies::movieID: int,fiveStarMovies::avgRating: double,nameLookup::movieID:int,nameLookup::movieTitle: chararray,nameLookup::releaseTime: long}

(12,4.385767790262173,12,Usual Suspects, The (1995),808358400)

(22,4.151515151515151,22,Braveheart (1995),824428800)

(23,4.1208791208791204,23,Taxi Driver (1976),824428800)

ORDER BY

    oldestFiveStarMovies = ORDER fiveStarsWithData BY nameLookup::releaseTime;
    DUMP oldestFiveStarMovies;

(493,4.15,493,Thin Man, The (1934),-1136073600)

(604,4.012345679012346,604,It Happened One Night (1934),-1136073600)

(615,4.0508474576271185,615,39 Steps, The (1935),-1104537600)

(1203,4.0476190476190474,1203,Top Hat (1935),-1104537600)


#### 19. Find old 5-star movies with Pig

Putting it all together

**run it much more quickly by running it on Tez**

#### 20 More Pig Latin

Pig Latin: Diving Deeper

Things you can do to a relation

    ■ LOAD STORE DUMP

    – STORE ratings INTO ‘outRatings’ USING PigStorage(‘:’);

    ■ FILTER DISTINCT FOREACH/GENERATE MAPREDUCE STREAM SAMPLE

    ■ JOIN COGROUP GROUP CROSS CUBE

    ■ ORDER RANK LIMIT

    ■ UNION SPLIT


Diagnostics

    ■ DESCRIBE

    ■ EXPLAIN

    ■ ILLUSTRATE

UDF’s

    ■ REGISTER

    ■ DEFINE

    ■ IMPORT

Some other functions and loaders

    ■ AVG CONCAT COUNT MAX

    ■ PigStorage

    ■ TextLoader

    ■ JsonLoader

    ■ AvroStorage

    ■ ParquetLoader

    ■ OrcStorage

    ■ HBaseStorage


#### 21. Find the most rated one star movie

Defining the problem

    ■ Find all movies with an average rating less than 2.0

    ■ Sort them by the total number of ratings

#### 22. Pig Challenge: Compare Your Results to Mine!

Hint

    ■ We used everything you need in our earlier example of finding old movies with ratings greater than 4.0

    ■ Only new thing you need is COUNT(). This lets you count up the number of items in a bag.

    – So just like you can say AVG(ratings.rating) to get the average rating from a bag of ratings

    – You can say COUNT(ratings.rating) to get the total number of ratings for a given group’s bag.

### Section 4 Programming Hadoop with Spark

#### 23. Why Spark

What is spark?

■ "A fast and general engine for large-scale data processing"

It's scalable

It's fast

■ "Run programs up to 100x faster than Hadoop MapReduce in memory, or 10x faster on disk."

■ DAG Engine (directed acyclic graph) optimizes workflows

It's hot

■ Amazon

■ Ebay: log analysis and aggregation

■ NASA JPL: Deep Space Network

■ Groupon

■ TripAdviser

■ Yahoo

■ Many others:

https://cwiki.apache.org/confluence/display/SPARK/Powered+By+Spark

It's not that hard

■ Code in Python, Java, or Scala

■ Built around one main concept: the Resilient Distributed Dataset (RDD)

Components of spark:

    Spark Streaming
    Spark SQL
    MLLib
    SPARK CORE
    GraphX

■ Why Python?

- It’s a lot simpler, and this is just an overview.

- Don’t need to compile anything, deal with JAR’s, dependencies, etc

■ But...

– Spark itself is written in Scala

– Scala’s functional programming model is a good fit for distributed processing

– Gives you fast performance (Scala compiles to Java bytecode)

– Less code & boilerplate stuff than Java

– Python is slow in comparison

#### 24. The Resilient Distributed Dataset (RDD)

The SparkContext

■ Created by your driver program

■ Is responsible for making RDD's resilient and distributed!

■ Creates RDD's

■ The Spark shell creates a "sc" object for you

Creating RDD's

■ nums = parallelize([1, 2, 3, 4])

■ sc.textFile("file:///c:/users/frank/gobs-o-text.txt")

– or s3n:// , hdfs://

■ hiveCtx = HiveContext(sc) rows = hiveCtx.sql("SELECT name, age FROM users")

■ Can also create from:

JDBC

Cassandra

HBase

Elastisearch

JSON, CSV, sequence files, object files, various compressed formats

Transforming RDD's

    ■ map
    ■ flatmap
    ■ filter
    ■ distinct
    ■ sample
    ■ union, intersection, subtract, cartesian
    
map example

    ■ rdd = sc.parallelize([1, 2, 3, 4])
    ■ squaredRDD = rdd.map(lambda x: x*x)
    ■ This yields 1, 4, 9, 16

What’s that lambda thing?

    Many RDD methods accept a function as a parameter
    
    rdd.map(lambda x: x*x)
    
    Is the same thing as
    
    def squareIt(x):
        return x*x
        
    rdd.map(squareIt)
    
There, you now understand functional programming.

RDD actions

    ■ collect
    ■ count
    ■ countByValue
    ■ take
    ■ top
    ■ reduce
    ■ ... and more ...

Lazy evaluation

    ■ Nothing actually happens in your driver program until an action is called!

#### 25. Find the movie with the lowest average rating - with RDD's

    LowestRatedMovieSpark.py
    
[maria_dev@sandbox-hdp ~]$ ls

RatingsBreakdown.py  TopMovies.py  u.data  u.data.1

[maria_dev@sandbox-hdp ~]$ mkdir ml-100k

[maria_dev@sandbox-hdp ~]$ cd ml-100k/

[maria_dev@sandbox-hdp ml-100k]$ wget http://media.sundog-soft.com/hadoop/ml-100k/u.item

[maria_dev@sandbox-hdp ~]$ wget http://media.sundog-soft.com/hadoop/Spark.zip

[maria_dev@sandbox-hdp ~]$ unzip Spark.zip 

[maria_dev@sandbox-hdp ~]$ less LowestRatedMovieSpark.py 

[maria_dev@sandbox-hdp ~]$ spark-submit LowestRatedMovieSpark.py 

#### 26.Datasets and Spark 2.0

Working with structured data

■ Extends RDD to a "DataFrame" object

■ DataFrames:

– Contain Row objects

– Can run SQL queries

– Has a schema (leading to more efficient storage)

– Read and write to JSON, Hive, parquet

– Communicates with JDBC/ODBC, Tableau

Using SparkSQL in Python

■ from pyspark.sql import SQLContext, Row

■ hiveContext = HiveContext(sc)

■ inputData = spark.read.json(dataFile)

■ inputData.createOrReplaceTempView("myStructuredStuff")

■ myResultDataFrame = hiveContext.sql("""SELECT foo FROM bar ORDER BY foobar""")

Other stuff you can do with dataframes

■ myResultDataFrame.show()

■ myResultDataFrame.select("someFieldName")

■ myResultDataFrame.filter(myResultDataFrame("someFieldName" > 200)

■ myResultDataFrame.groupBy(myResultDataFrame("someFieldName")).mean()

■ myResultDataFrame.rdd().map(mapperFunction)

Datasets

■ In Spark 2.0, a DataFrame is really a DataSet of Row objects

■ DataSets can wrap known, typed data too. But this is mostly transparent to you in Python, since Python is dynamically typed.

■ So – don’t sweat this too much with Python. But the Spark 2.0 way is to use DataSets instead of DataFrames when you can.

Shell access

■ Spark SQL exposes a JDBC/ODBC server (if you built Spark with Hive support)

■ Start it with sbin/start-thriftserver.sh

■ Listens on port 10000 by default

■ Connect using bin/beeline -u jdbc:hive2://localhost:10000

■ Viola, you have a SQL shell to Spark SQL

■ You can create new tables, or query existing ones that were cached using hiveCtx.cacheTable("tableName")

User-defined functions (UDF's)

    from pyspark.sql.types import IntegerType

    hiveCtx.registerFunction("square", lambda x: x*x, IntegerType())

    df = hiveCtx.sql("SELECT square('someNumericFiled') FROM tableName)

#### 27. Find the movie with the lowest average rating -- with DataFrames

[maria_dev@sandbox-hdp ~]$ less LowestRatedMovieDataFrame.py 

[maria_dev@sandbox-hdp ~]$ export SPARK_MARJOR_VERSION=2

[maria_dev@sandbox-hdp ~]$ spark-submit LowestRatedMovieDataFrame.py 

#### 28.Movie recommendations with MLLib （Machine Learning Algorithm）

    from pyspark.sql import SparkSession
    from pyspark.ml.recommendation import ALS
    from pyspark.sql import Row
    from pyspark.sql.functions import lit

[maria_dev@sandbox-hdp ~]$ spark-submit MovieRecommendationsALS.py 

#### 29. Filter the lowest-rated movies by number of ratings

The problem

■ Our examples of finding the lowest-rated movies were polluted with movies only rated by one or two people.

■ Modify one or both of these scripts to only consider movies with at least ten ratings.

Hints

■ RDD’s have a filter() function you can use

– It takes a function as a parameter, which accepts the entire key/value pair

So if you’re calling filter() on an RDD that contains (movieID, (sumOfRatings, totalRatings)) – a lambda function that takes in “x” would refer to totalRatings as x[1][1]. x[1] gives us the “value” (sumOfRatings, totalRatings) and x[1][1] pulls out totalRatings.

This function should be an expression that returns True if the row should be kept, or False if it should be discarded

■ DataFrames also have a filter() function

– It’s easier – you just pass in a string expression for what you want to filter on.

– For example: df.filter(“count > 10”) would only pass through rows where the “count” column is greater than 10.

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


