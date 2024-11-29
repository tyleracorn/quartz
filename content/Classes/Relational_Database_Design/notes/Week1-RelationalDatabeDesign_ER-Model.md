---
title: Week1-RelationalDatabeDesign_ER-Model
type: post
excerpt: excerpt if needed.
date: 2024-04-27
categories:
  - databases
  - entitity relationship model
tags:
  - tags
---
Entity Relationship Model (ER Model) has 3 main parts
- what are the entities the database is going to record
- what are the attributes and identifiers of the entities
- how are the relationships among/between the entities
The Purpose:
Visually represent the different overarching parts of a database such as the entities, attributes, and relationships. This helps define the structure and organize the database and relationships between entities

Concepts
- Entities
	- identifiable abstract of interest. I.e. what we would think of as a Class in programming
	- not about 1 particular record but the group of objects/records
	- This would be the title of a table
- Attributes
	- properties, or characteristics of the entities that we want to record
	- This would be the columns within the specific tables
- Instance
	- A record or member of an entity of interest
	- This would be a row of the table
- Identifier
	- A special attribute used to identify a specific instance of an entity
	- this will be a unique id
	- can be natural (example, SSN or SIN) or artificial (i.e. employee ID)
- Relationships
	- How the members of two or more entities are related
	- Examples
		- Employees and Companies
			- How many companies an employee may work for
			- How many employees a company may have
		- Companies and products
		- Drill companies and drill holes
- Relationship Degree
	- the degree of a relationship is the number of entities that participate in the relationship
	- degree of 1 = unary or recursive
	- degree of 2 = binary relationships - Most relationships in databases are binary
	- degree > 2 - relationship databases can't handle directly. you need to figure out how to define it as 1 or 2
- Relationship Cardinality
	- the number of instances of the entity involved in the relationship
	- 3 types
	- 1:N (One to Many)
		- one instance connects to many instances in another entity
	- N:1 (Many to One)
		- many instances from an entity connect to 1 instance in another entity
	- N:M (Many to Many)
- Relationship Participation
	- Mandatory
	- Optional
- 
