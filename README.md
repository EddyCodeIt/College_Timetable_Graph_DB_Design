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
- Add plan image here...


	
	
## Starting with Neo4j 
* Where to donwload and how to install
1) Download [link] (https://neo4j.com/download/)
2) Installation [guide] (https://neo4j.com/docs/operations-manual/current/installation/)

* My recommendations...
1. I would recommend to create separate directories for each database you creating. 
2
3

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
* Node CRUDs
* Relationship CRUDs
* Simple Quering commands


	



