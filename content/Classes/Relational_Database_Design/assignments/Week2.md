
# Lab2_Relational_Schema
**GradeBook**: (<u>ID</u> , Name, Major(fk), Quiz1, Quiz2, Quiz3, Quiz4)

# Video Practice

ERAD to Relational Model Practice:

Instructors(Name, ^EmpID, SSN, DoB, Email, Salary, SupervisorID(fk))
Courses(Title, ^Course#, Time, Location, Description, Title(fk))
Instructor_to_Course(EmpID(fk), Course#(fk))

Programs(^Title, Chair, Office#, Contact, Description)

Students(Name, ^StuID, DoB, Email, Title(fk), EmpID(fk))
Students_to_Courses(StuID(fk), Course#(fk))
Students_to_Studetns(StuID(fk), FriendID(fk))

# Lab3 Convert ERDs to Relational Models

## ERD1

Locations(^ID, State, City, Street, ZipCode, Country)

Galleries(^GalleryNum, Name, Phone, Hours, Introduction, LocationID(fk))

Drawings(^DrawingNum, Title, Size, Material, Date, GalleryNum(fk))

Artists(^ArtistNum, Name, Phone, Birthday, Email)
Artists_to_Drawing(ArtistNum(fk), DrawingNum(fk))
Artist_to_Artist(ArtistNum(fk), FriendNum(fk))

## ERD 2

Locations(^ID, State, City, Street, ZipCode, Country, GalleryNum(fk))

Galleries(^GalleryNum, Name, Phone, Hours, Introduction)

Drawings(^DrawingNum, Title, Size, Material, Date, GalleryNum(fk), ArtistNum(fk))

Artists(^ArtistNum, Name, Phone, Birthday, Email, ReferredNum(fk))

# Assignment 1

## Question 1 - Understand a Relation

Name of relation: MotorVehicleCollisions
Degree of relation: 11
Cardinality: 9
Primary Key: CollisionID
Domain of ZIPCODE: Numbers max 5 long
Domain of Crash Date: Date mm/dd/yyyy

## Question 2 - Interpret an ERD

Cars(^CarID, Manufactor, Model, Year)

Drivers(Name, ^EmployeeID, SSN, DoB, Phone, DivisionName(fk), MentorID(fk))
Driver_to_Driver(EmployeeID(fk), FriendID(fk))

Driver_to_Car(CarID(fk), EmployeeID(fk))

Dependents(^ID, Name, Gender, DoB, EmployeeID(fk))

Division(^DivisionName, Location, Phone, Email)

