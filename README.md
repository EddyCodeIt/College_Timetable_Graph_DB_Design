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
and a Graph Database to optimise composition of timetable on a semester-to-semester bases. 
	
	To keep things simple for the start, I will use timetables for Second and Third years Software Development Courses. 
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
	
		Now I would begin to think about following questions: 
			* What is more important, data points (entitities) or a relationships between them? 
			* What is harder to manage as a time goes by? 
			* How to add data and relationships in a flex-way that initial design plan and DB structure don't change dramatically.
			
		Neo4j have an answer to this: "In order to leverage data relationships, organizations need a database technology 
	that stores relationship information as a first-class entity. That technology is a graph database."
	DBMS's rigid schemas make it difficult to add different connections between data point or adapt to new business requirements.
	
	* Advantages/Disatvantages 

## Starting with Neo4j 
	* Where to donwload and how to install
	* My recommendations...
		1
		2
		3

## How to use Neo4j to store data
	* Nodes
	* Properties
	* Labels
	* Relationships
		- properties
	

## How to query Neo4j database
	* Basic commands



