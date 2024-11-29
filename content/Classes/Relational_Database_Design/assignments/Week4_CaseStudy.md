Your client, PetsCare, is a local clinic that takes care of pets, including pet wellness and vaccination, medical services, surgery including spay and neuter, dental cleaning and treatment, grooming, etc. PetsCare has served the community for more than 20 years, and has been successful in the business.

Recently, the current owner, Claire, who is the daughter of the founder of PetsCare, realized that the old file system solution is very inefficient. She and her team have to spend lots of time taking records, querying for information, and maintaining the data. She decided to turn to you, for a Relational Database Management System.

PetsCare wants to record information about customers, pets, staff, visits. Claire will be available to meet via Zoom tomorrow to discuss details. You should prepare questions for building the DBMS.

## What Questions Do you Ask

Explain to me the general information are keeping track of? Do you only care about patient/pet medical records or do you need to keep track of medical inventory? What's the basic information you want to keep (i.e. patient info) and what are some stretch goals for info that would be nice to have? Such as drug interactions, drug/supply inventory?

Can you take the time to walk through an example patient/pet record and we can talk through the information you currently track and how that information might relate to other information you track?

Coursera "Answer"

You should prepare two categories of questions:

1. The interest of the business, what information should be recorded, what might be the entities for holding the information, what might be used as identities, etc.
    
2. The relationship of the entities, especially the mandatory/optional participation, and the cardinalities. We will need them to clear confusions and to create the Entity Relationship Model.

## Entitity Relationship Model

Lay our your own assumptions and ER Model

Customer
- customerID (pk)
- name
- dob
- contact_info
- insurance_info

Pet
- petID (pk)
- name
- customerID (fk)
- DOB
- pet_type
- breed

Staff
- staffID (pk)
- supervisor (fk)
- contact_info
- qualification_surgery
- qualification_dental
- qualification_***

Visit
- visitID_date_time (pk)
- petID(fk)
- customerID (fk)
- staffID (fk)

Wellness_Rating
- w_record_date (pk)
- petID (fk)
- wellness_rating

Vaccination_Applie
- vac_date (pk)
- vaccinationID (fk)
- petID (fk)

VaccinationType
- vaccinationID (fk)
- vaccination_name
- vaccination_duration
- vaccination_description

Surgery
- surgery_date (pk)
- staffID (fk)
- petID (fk)
- surgery_type (fk)
- surgery_rating

SurgeryType
- surgery_type (pk)
- surgery_description

Dental_Cleaning
- dental_date (pk)
- staffID (fk)
- petID (fk)
- dental_type (fk)
- dental_rating

DentalType
- dental_type (pk)
- dental_description

### Answer

Here is what you summarized about the entities:

- Customers: CustomerID, FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate. CustomerID is the identifier.
    
- Pets: CustomerID, Pet#, NickName, Address, Email, Phone, Category, Species/Breed, Species/Breed Description, Gender, DoB, Notes. CustomerID and Pet# together as the identifier.
    
- Staff: EmployeeID, FirstName, LastName, SSN, Address, Email, Phone, DoB. EmployeeID is the identifier.
    
- Visit: VisitID, Date, Time, Customer, Pet, ServiceID, ServiceName, ServicePrice, ServiceDescription, Staff, Bill, Paid. VisitID is the identifier.
    

Their relationships are:

- A customer may have one or more (zero or more) pets; A pet must belong to one and only one (exactly one) customer.
    
- A staff may treat one or more pets (zero or more); and A pet may be familiar with one or more (zero or more) staff.
    
- A customer may have one or more (zero or more) visits; and each visit must be done by one and only one (exactly one) customer. 
    
- A pet may have one or more (zero or more) visits; and each visit may involve one (zero or one) pet. 
    
- A staff must be in charge of one or more (one or more) visits; and a visit must be charged by one and only one (exactly one) staff.
    
- A customer may be referred by one (zero or one) customer; and a customer may refer one or more (one or more) customers. 
    
- A staff must have one and only one (exactly one) supervisor; A staff may supervise one or more (zero or more) staff.

## Convert to Relational Model

Customer(CustomerID (pk), FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate)

Pets(CustomerID (pk), PetN (pk), Nickname, Address, Email, Phone, Category, Species/Breed, S/B Description, Gender, DoB, Notes)

Visit(VisitID (pk), Date, Time, CustomerID(fk), PetN (fk), ServiceID, ServiceName, ServiceDescription, ServicePrice, Staff, Bill, Paid)

Staff(EmployeeID (pk), FirstName, LastName, SSN, Address, Email, Phone, DoB)

--- 
Customer_Referral(CustomerID_beingRefferred (fk), CustermID_referredBy (fk) ) 

Customer_Own_Pet(CustomerID (fk), PetN (fk))

Customer_Visit(CustomerID (fk), VisitID (fk))

Pet_staff_familiar(CustomerID (fk), PetN(fk), EmployeeID (fk))

Staff_Visit_InCharge(VisitID (fk), EmployeeID(fk))

Staff_Supervisor(EmployeeID_Supervisor(fk), EmployeeID_supervisee(fk))

## Normalize RM

Before normalization, you should ask Claire about the Functional Dependencies of the relations. Here is what you got from her:

- Customers (CustomerID, FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate, ReferredByCustomerID(fk)).
    
    - FD1: CustomerID → FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate, ReferredByCustomerID
        
- Pets (CustomerID(fk), Pet#, NickName, Address, Email, Phone, Category, Species/Breed, Species/Breed Description, Gender, DoB, Notes). 
    
    - FD1: CustomerID, Pet# → NickName, Address, Email, Phone, Category, Species/Breed, Species/Breed Description, Gender, DoB, Notes.
        
    - FD2: CustomerID → Address, Email, Phone
        
    - FD3: Species/Breed → Species/Breed Description
        
- Staff (EmployeeID, FirstName, LastName, SSN, Address, Email, Phone, DoB, SupervisorID(fk)). 
    
    - FD1: EmployeeID  → FirstName, LastName, SSN, Address, Email, Phone, DoB, SupervisorID
        
- Visit (VisitID, Date, Time, CustomerID(fk), Pet(fk), ServiceID, ServiceName, ServicePrice, ServiceDescription, EmployeeID(fk), Bill, Paid).
    
    - FD1: VisitID → Date, Time, CustomerID, Pet, ServiceID, ServiceName, ServicePrice, ServiceDescription, EmployeeID, Bill, Paid
        
    - FD2: ServiceID  → ServiceName, ServicePrice, ServiceDescription.
        
- Pets_Staff(CustomerID(fk), Pet#(fk),EmployeeID(fk))
    
    - There is no non-primary-key attribute.
        

Now you can normalize this Relational Model to 3NF.

--- 
Customers (CustomerID (pk), FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate, CustermID_referredBy (fk) )

Pets (CustomerID (pk/fk), PetN (pk), Nickname, Category, Species/Breed (fk), Gender, DOB, Notes)

Species_Breed(Species/Breed (pk), S/B_Description)

Staff(EmployeeID (pk), FirstName, LastName, SSN, Address, Email, Phone, DoB, SupervisorID(fk))

Visit(VisitID (pk), Date, Time, CustomerID(fk), PetN (fk), ServiceID(fk), Staff(fk), Bill, Paid)

Service(ServiceID(pk), ServiceName, ServicePrice, ServiceDescription)

Pet_staff_familiar(CustomerID (fk), PetN(fk), EmployeeID (fk))


## Final Output

Now the final Relational Model in 3NF is as below:

- Customers (CustomerID(pk), FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate, ReferredByCustomerID(fk)).
    
    - FD1: CustomerID → FirstName, LastName, Address, Email, Phone, DoB, PaymentInfo, JoinDate, ReferredByCustomerID
        
- Pets (CustomerID(pk/fk), Pet#(pk), NickName, Category, Species/Breed(fk), Gender, DoB, Notes). 
    
    - FD1: CustomerID, Pet# → NickName, Category, Species/Breed, Gender, DoB, Notes.
        
- Species (Species/Breed(pk), Species/Breed Description)
    
    - FD1: Species/Breed → Species/Breed Description
        
- Staff (EmployeeID(pk), FirstName, LastName, SSN, Address, Email, Phone, DoB, SupervisorID(fk)). 
    
    - FD1: EmployeeID  → FirstName, LastName, SSN, Address, Email, Phone, DoB, SupervisorID
        
- Visit (VisitID(pk), Date, Time, CustomerID(fk), Pet(fk), ServiceID(fk), EmployeeID(fk), Bill, Paid).
    
    - FD1: VisitID → Date, Time, CustomerID, Pet, ServiceID, EmployeeID, Bill, Paid
        
- Service (ServiceID(pk), ServiceName, ServicePrice, ServiceDescription)
    
    - FD1: ServiceID  → ServiceName, ServicePrice, ServiceDescription
        
- Pets_Staff(CustomerID(fk), Pet#(fk),EmployeeID(fk))
    
    - There is no non-primary-key attribute.