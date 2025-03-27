
# Q1 Identified Errors in data
1) **Tell us about a time when you identified an error through QA/QC of geological data.**

- Situation:
	- Project ECD
	- Reviewing drill hole assay data that our client recieved from the lab. They performed a typical drilling QAQC program with standards and blanks submitted alongside their assay samples. 
- Task
	- I was responsiblle for reviewing the QAQC and providing feedback on the results
- Action
	- I noticed a number of the results from the standards were outside of the certified ranges for those standards, so I reviewed did a number of checks to determine what might be wrong. 
		- I looked at the lab results over time and noticed the cyclycle standard results which is a good indication that the labs is doing their internal QAQC
		- I plotted the standards along with the other standards and noticed some of the results where plotting in and amongst other standards expected values. 
			- For these results I reached out to the geologist and had them go back and check the logs, and we determined these were mis-labled. We corrected the label and these results they passed
		- Some of the results still failed
			- I gave 2 sets of recommendations
				- samples in "unmineralized zones" acknowledge and document the failed QAQC but continue as is (this is in an area we are not as concerned with)
					- Little to no ramifications for this project
				- samples near mineralized zones, take all samples in the same batch as the standard that failed and have the lab re-assay with left over material
					- potential rammification of wrong assay values which can lead to biased mineral resource estimatation results
# Q2  Manage multiple groups needs
**Tell us about a time when you worked with multiple interest groups to deliver a single digital geoscience product that best suited each group’s needs.**

Project Storm
	- Situation
		- client 1 wants exploration targetting expansive model
		- client 2 wants reportable and defendable model for economics
	- Task
		- get final product(s) within deadline and in budget
	- Action
		- talked with both clients about needs, deadlines and budgets
		- both clients were talking to each other outside of our meetings so everyone understood the needs of the other
		- I helped put together a two stage budget
			- stage 1
				- model with some "pie in the sky" options to meet the earlier deadline of client 1
				- Classify the model accurately so we could drop out "exploration" targets for client 2
			- stage 2
				- rechecked model with tighter constraints
				- perform economics on model with exploration dropped
	- Resutls
		- we had weekly check in meetings to keep client 1 abreast of where we were
			- finished on time and in budget
		- reviewed model for stage 2 with exploration dropped
			- in the end our classification wasn't enough so we needed to modify the model slightly
		- we met client 2 deadline. budget was over but within the +/- 10% we gave as our budget accuracy
		- both clients were happy with the results

# Q3 Analyze and Deliver Complicated data in deadline
Tell us about a time when you had to analyze and deliver complicated geological data on a strict deadline. What was the situation?

## Completing Multiple MREs Simultaneously
- Situation
	- My current Job :)
	-  Completing Multiple MREs Simultaneously
- **Situation:**
    - Two Mineral Resource Estimates (MREs) needed completion simultaneously.
    - One had a hard deadline (external funding), while the other had a soft, internal deadline.
- **Task:**
    - Manage both projects efficiently, ensuring the first met its strict deadline without compromising overall quality.
    
- **Actions:**
    1. Created project timelines by collaborating with clients to confirm deadlines (hard vs. soft).
    2. Identified critical milestones where delays could jeopardize deadlines.
    3. - talk to SME's - make sure we represent the data accurately
	    - focus on scope. Do what we can in the time we have. Doesn't have to be the BEST just good enough for the scope
    4. Regularly communicated progress updates to clients.
    5. Addressed unforeseen delays in modeling work by:
        - Prioritizing the hard-deadline project.
        - Reassigning resources to accelerate completion.
        - Notifying the soft-deadline client of potential delays.
- **Result:**
    - Delivered the first project on time, meeting the client’s critical funding deadline.
    - Completed the second project slightly late, but the client accepted the revised timeline.

# Q4 Transform Data

Tell us about a time when you had to transform a dataset from one schema to another, but you were not familiar with the schemas.

I haven't done work where I have transformed formal database schemas from one to another.

however I do often clean up drill hole databases for a mineral resource estimate which involves very similar processes. I need to pull data out of either a database or excel file.
project Lemhi (L)
- had to clean up different generations of data from different sources (excel files, databases, text files)
	- some data needed to get help finding the correct metadata
		- was the assay in oz/t or g/t?
	- some used common sense.
		- -90 drill angle versus 90. 
			- had to flip some drill angle recordings
	- managed a group of people who did some manual checks
		- evaluated the option of using machine learning to parse pdf's but determined we didn't have the time to implement
- Task was analyzing the data and talking to people who knew more about the data to figure out all of the metadata needed to actually use the data properly
result 
	a clean database that we have used going forward with all releavant and available metadata inserted.


# Q5 Evaluate and Improve stuff
Describe two examples of how you evaluated and improved a data product or a software application.
1) DHDB Repo
- Situation
	-  Exploration companies often store their drill hole databases, that eventuially get used for mineral resource estimates, in unique and varried ways. Cleaning this up, standardizing the metadata etc, and checking for common input errors is often time consuming and a pretty manual task
- Task
	- I have been working for a while on taking tools available in python to create a semi-automated dhdb cleanup and checking tool
- Actions
	- This is a complicated process, so I have been working on this off and on for a while. I started very simply with just some easy checks and standardizations.
		- renaming column names to standardized names
		- standardize information in each table
		- check for missing data
			- insert missing data if available from other tables 
		- check for duplicate data 
		- export any errors to an excel file that we can use to go back and the check logs with
	- Over time, every other project I'll evaluate the tool and add a little bit here and there
		- check for overlapping intervals
		- create a "best assay" column when multiple assay methods are used
		- fill in missing intervals with a no-data value (this can be just as important as a present value)
- Results
	- The cleanup and standardizing of dhdb data for a Mineral resource estimate has spead up a lot for us. I don't have hard numbers, but it is easily 3-4 times faster for me to clean up data now (depending on the number of errors I come across)

1) 

# Q6 FAIR and Showings Database

F
appears to have rich meta data
metadata includes explicity identifier
data is registerd and indexed in a somewhat serchable way. Felt clunky and not the most intuative. also there are two mineral showings databases online that don't match each other. one is table only search and one is map only search

A
open, and free
metadata is accessible, not sure about when data is no longer available


I
the downloaded data uses columns with description or metadata about the column itsef. It's not universal. having 

R
didn't see a clear data usage license
meta data is rich with relevant attributes

Project 1
1) Budget - very rough ball park, as in are we looking at something very very small or something larger
2) Research
	1) check in with user groups and get feedback on who uses it and how. Do they find it useful or is it hard for them to use?
		1) check in with the NTGS employees that know about the data and shareholders
	2) Check in with SME's in NTGS. are we missing meta data. is the metadata useful?
		1) are their shareholders that should be using the data but aren't? why?
	3) Look at other similar groups (Yukon, Alberta, BC, Federal) 
		1) the more unified the better
3) IF there is anything missing now would be the time to add it in
4) More detailed budget scoping
	1) stage 1 merge the two showings databases
		1) the map view seems very useful but it looks out of date
	2) Stage 2
		1) Research v2 to see if there would be anything usefull to add?
		2) color showings on map by commodity
		3) color by commodity grade
		4) Add geologic maps as layers to showings map
	3) stage 3
		1) Reserach v3 Ways for the NTGS to use the showings database in internal research projects
		2) prospectivity maps?

Q7

what is a relational database
1) programing
2) database development
3) using spatial information system
Q8


what are the major developments in geospatial tech and web services. 
name a few commercial and open source platforms
what is your level of experience with these platforms
