---
title: "Week1_EntityRelationshipModels"
type: post
excerpt: "excerpt if needed."
date: 2024-05-02
categories:
  - categories
tags:
  - tags
---
# Question 1: Create ERD

Read the following statements and draw the Entity Relationship Diagram using Crow’s Foot Notation. 

The ER Model is as below:

A clinic must have one or more doctors; A doctor may belong to one or more clinics.

A patient may visit one or more doctors; A doctor may take one or more patients.

A doctor may have one and only one assistant nurse; An assistant nurse must work for one or more doctors. 

 A patient must have one and only one history record; A record must belong to one and only one patient. 

Now you can draw the ER Diagram based on the ER Model.

Entities: Clinics, Doctors, Patients, Assistant Nurse, History Records, Employee

E&R
- Clinics
	- clinic name*
	- location
- Doctors
	- employee ID*
	- Doctor name
- Assistant Nurse
	- employee ID*
	- employee Name
- History Records
	- record ID*
- Employee
	- Employee ID*
	- position
- Patient
	- patientID*
	- name
	- contact

# Question 2 Interpret the ERD

- What are the Entities?
		- Cars
		- Supervisors
		- Drivers
		- Dependents
		- Division
		- DetailProfile
- Translat to List of Statements
	- Cars may have one or more drivers, drivers may operate one or more cars
	- Drivers must belong to one and only one division, divisions may have one or more drivers
	- Drivers must have one and only one supervisor, supervisors must one or more drivers
	- Drivers may have one ore more dependents, dependents must have one and only one driver
	- Drivers may have one detail profile. the detail profile must have one and only one driver
# Question 3 Create an ERD
Read the following statements about a Database for Art Galleries and collections of drawings. Draw the Entity-Relationship Attribute Diagram with Crow’s Foot Notation. No credit will be granted for other notations. Make sure you have all entities, all attributes (and identifiers), all relationships, and proper multiplicities.

- A gallery must have one and only one location and each location must have one and only one gallery. 
    
    - Galleries have attributes: _GalleryNum(identifier), Name, Phone, Hours, and Intro._ 
        
    - Locations have attributes: _ID(identifier)_, _Country, State, City, Street, and ZipCode._
        
- A gallery may have one or more drawings and each drawing may belong to one and only one gallery. 
    
    - Drawings have attributes: _DrawingNum(identifier), Title, Size, Material, and Date._
        
- A drawing must be created by at least one artist and each artist must create at least one drawing. 
    
    - Artists have attributes: _ArtistNum(identifier), Name, Phone, Birthday, and Email._
        
- An artist may have a bio statement and a bio statement must belong to one artist.
    
    - BioStatements have attributes: _Citizenship, Education, Experience, MasterPiece(s), and BriefIntroduction._