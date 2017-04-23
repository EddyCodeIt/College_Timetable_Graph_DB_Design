# Graph Database for College Timetable
_**Project for Graph Theory Module in Software Development Year 3**_

## Introduction
Every year college faces a problems with organising and optimising a timetabling system for the following year.
Usually it takes up to a month, after studies have commenced, to rearrange timeslots 
and match them with appropriate rooms within a building. It involves quite a time, people and resources to facilitate every need.
Most managers and developers would agree that timetabling system within a big organisation is one of those common problems
that requires thorough analysation and planning at the beggining of system development. Mistakes in initial design can lead to 
a big problems later or even complete system failure. 

For this project I will attempt to deliver design of a timetable system using Graph Theory fundamentals 
and a Graph Database to optimise composition of database for a timetable.
	
To keep things simple for the start, I will use my current timetable for Semester 6. 
This should help me to identify potential data types used to compose timetables, as well as give me some initial values to kick off with.
To store data, I will use Neo4j database, a Graph Database that is providing online database management system 
that allows to manipulate Graph Data Models. Typical Graph Model would be composed of two elements: a node and a relationship.
	
## Neo4j Database 
### What is graph database

A Graph, in a Graph Database, is a composition of nodes (representing entitities like Person, Car, Company, Book, etc...)
and a relationships between those nodes that represent how those nodes are associated (Person has a Car, Company publish a Book, etc...).
Neo4j Database is management system that allows to manipulate nodes and relationships with this Graph. 
Operations on Database Model is very well know CRUD operations (Create, Read, Update, Delete). Neo4j providing us with 
Web-interface and Cypher Query Language to conduct CRUD operations against our Data Model, in this particular project it is 
college timetable system.

### Why should we use graph databases

Most popular way in storing data this days still remain to be in a relational databases. A data is stored in
tabular structure. "Ironically, however, relational databases aren't effective at handling data relationships, 
especially when those relationships are added or adjusted on an ad hoc basis.
The greatest weakness of relational databases is that their schema is too inflexible. " - from Neo4j [article] (https://neo4j.com/blog/why-graph-data-relationships-matter/)

**Now I would begin to think about following questions: **
* What is more important, data points (entitities) or a relationships between them? 
* What is harder to manage as a time goes by? 
* How to add data and relationships in a flex-way that initial design plan and DB structure don't change dramatically.
	
Neo4j have an answer to this: "In order to leverage data relationships, organizations need a database technology 
that stores relationship information as a first-class entity. That technology is a graph database."
DBMS's rigid schemas make it difficult to add different connections between data point or adapt to new business requirements.

* Advantages/Disatvantages 

	
## Timetable System Data
* What kind of data database would need to store?
1) Teachers
2) Lecture rooms
3) Laboratory rooms
4) Any other special kinds of rooms
5) Courses
6) Modules of this courses
7) Student
8) Any other object that can represent an entity 


* How can I break data into groups and use Neo4j to help me organising my data?

Neo4j syntaxis allows to place a Lable on an entity. Labels in neo4j representing a groups that entity can become part of. One entity can have many labels. It allows to have a shortcuts in data search patterns for faster data quering. 

* How would my data relate to one another? Design plan:

![](https://github.com/EddyCodeIt/College_Timetable_Graph_DB_Design/blob/master/Doc%20Snippets/design.jpg)

On a diagram I have 5 groups a node, in Neo4j, can possible belong to and properties this nodes can have. 
Than I thought of a Module not only as a subject to be taught as a part of Course, but also as an event that can occur in
a particular room. The Module, an event, can be related to a room with some properties like time it start, ends, a day of the week
and also a type of an event it is. 
Each Module can also be related to some Teacher it thaught by.  
It is possible to expand this graph limitlessly with new groups like Course and add relationships to Modules, than create
a Student and related it to a course. Neo4j allows to handle data this way. 

## Starting with Neo4j 
* Where to donwload and how to install
1) Download [link] (https://neo4j.com/download/)
2) Installation [guide] (https://neo4j.com/docs/operations-manual/current/installation/)

It is recommended to create separated directories for each database you creating. 

## How to use Neo4j to store data
* Nodes
In Neo4j, each node represent a peace of data or an entity. 
For example, in timetable scenario, a particular module would be represented as a node in Neo4j

* Properties
In Neo4j, there are 2 types of properties, a node properties and relationship properties.
Property is a data about a node or a relationship. 
For example a node that represent a module would have property name that will store a name of this module.
Relationship property would be similar to a node property, but store a data relevant to a particular relationship.

* Labels
As mentioned above in one of the topics, Labels help organise nodes into groups of same data type.

* Relationships
In Neo4j, relationships represent a link between 2 nodes. This link can be descriptive via properties, but not necessarly.
One node can have many different relationships with other nodes. Pair of nodes also can have many different relationships
between each other.

## Working with Neo4j

To work with Neo4j, I used following [Cheat Sheet](https://neo4j.com/docs/cypher-refcard/current/) with Cypher queries syntaxis.

Lets examin few queries I used to create database. 

**Creating Module** 

`Create(gt:Module{name: "GRAPH THEORY" , credits: 5, lectures_hpw: 2, labs_hpw: 1})`

Create() creates new nodes and relationships.
Function parameter `gt` is a naming convension for this specific node, you can name it any way you like. It is kept in memory until Play (Execution mechanism in Neo4j) has fully executed all given statements.
You can execute multiple queries at once, for example creating a new node and use its naming convension
to link a relationship to it. 
`:Module` is a Label this object is assigned to. 
Inside braces `{name: "GRAPH THEORY"}` we specify what properties we want a node to have.

**Creating a Relationship** 

We can use Graph Theory Module `gt` we've created before.
Let's just create another node for room and make a relationship between those two nodes we have.

`Create(r145:LectureRoom{number: 145, capacity: 20})`

`Create(gt)-[:HAPPEN_IN {start: 9, end: 10, day: "Monday", type: "lab", group: "A"}]->(r145)`

Creating a relationship follows this syntaxis: ()-[]->()
where first node() has a relationship [] with second node ()

**Quering Database** 

Now lets try to find created nodes and relationship between them.

To simply find Module and return a node: 
`match(gt:Module{name: "GRAPH THEORY"}) return gt`

To find multiple nodes at once: 
`match(gt:Module{name: "GRAPH THEORY"}),(r145:LectureRoom{number: 145})
return gt, r145`
This will also return relationship between nodes.

It is possible to search for relationship and it's nodes like this too: 
`match(gt:Module{name: "GRAPH THEORY"})-[r]->(r145:LectureRoom{number: 145})
return r, gt, r145`

To find all relationships with the lecture rooms:
`match(gt:Module{name: "GRAPH THEORY"})-[r]->(lr:LectureRoom)
return r, gt, lr`


**Quering Rooms**

Now lets try to query all Lab Rooms that have classes starting at 16:00 on Monday.

`match(fr:LabRoom)<-[r{day: "Monday", start: 16}]-(n) return fr, r, n`


**Demo Database for GMIT**


