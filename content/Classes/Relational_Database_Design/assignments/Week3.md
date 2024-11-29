# Lab 1 Functional Dependencies

## Relation 1

ID, Name, Major, Quiz1, Quiz2, Quiz3, Quiz4, Total, Grade
ID => Name, Major,... all
Total -> Grade??
Q1 + Q2 + Q3 + Q4 -> Total

# Relation 2

SKU, Name, VendorID, Price, Date, Quantity, Location, Description

SKU -> Name, VendorID, Location?
SKU + Date -> All?
VendorID?? Unsure but I'm assuming that is the ID of the Vendor and that the Vendor can have multiple items, athough the sample dataset makes it unclear

Answer
SKU -> Name
SKU, VendorID, Date -> Price, Quantity, Location, Description

# Lab 2 Identify Special FD's

## Relation 1

Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

no partial, no transitive
# Relation 2

Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

fd2: D -> L, N, Q

fd3: L -> N

Transitional: 
A, B, C -> D & D -> L, N, Q, 
D -> L & L -> N

# Relation 3

Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q (Partial)

fd2: A -> D, E, F, L, N, Q (Full)

fd3: B, C -> G, H (Full)

fd4: D -> L, N, Q (Full)

fd5: L -> N (Full)

Transitional:
A, B, C, -> D & D -> L, N, Q
D -> L & L -> N
A -> D & D-> L, N, Q
# Relation 4

Is there a partial functional dependency? Is there a transitive functional dependency?

CustomerContact (FirstName_, LastName_, DoB_, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB -> Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo (Partial)

fd2: LastName, DoB → Email (Full)

fd3: DoB → Zodiac (Full)

fd4: Zip → City, State (Full)

fd5: Company → CompanyInfo (Full)

Transitive:
FirstName, LastName, DoB -> Zip & Zip → City, State
FirstName, LastName, DoB -> Company & Company → CompanyInfo

# Lab 3 Normalization Process

# Identify Normalization Form

### Relation 1

Which normal form is the relational model below?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

Answer: Nf3

## Relation 2

Which normal form is the relational model below?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)
fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

fd2: D -> L, N, Q

fd3: L -> N

Answer: Nf2

### Relation 3

Which normal form is the relational model below?

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

fd2: A -> D, E, F, L, N, Q

fd3: B, C -> G, H

fd4: D -> L, N, Q

fd5: L -> N

Answer: Nf1

### Relation 4

Which normal form is the relational model below?

CustomerContact (FirstName_, LastName_, DoB_, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB -> Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo

fd2: LastName, DoB → Email

fd3: DoB → Zodiac

fd4: Zip → City, State

fd5: Company → CompanyInfo

Answer: Nf1

## Normalization Process

### Relational Model 1

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

Customers (CID_, FirstName, LastName, Email, Address, Company, CompanyInfo)

FD1: CID → FirstName, LastName, Email, Address, Company, CompanyInfo (Partial)

FD2: Company → CompanyInfo

T1: CID -> Company & Company -> CompanyInfo

NEW

R1: Customers (CID_, FirstName, LastName, Email, Address, Company(fk))

R1 FD1: CID → FirstName, LastName, Email, Address, Company

R2: Company (Company_, CompanyInfo)

R2 FD1: Company_ -> CompanyInfo

### Relational Model 2

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

CustomerContact (FirstName_, LastName_, DoB_, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

Partial fd1: FirstName, LastName, DoB →  Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo 

Full fd2: LastName, DoB → Email

Full fd3: DoB → Zodiac

fd4: Zip → City, State

fd5: Company → CompanyInfo

Trans1: FirstName, LastName, DoB -> Zip & Zip → City, State

Trans2: FirstName, LastName, DoB -> Company & Company → CompanyInfo

NEW

R1: CustomerContact (FirstName_, LastName_(fk), DoB_(fk), Street, County, Zip(fk),  Company(fk))

R1 Fd1: FirstName, LastName, DoB →  Street, County, Zip, Company

----------------
R2: Zodiac (DoB_, Zodiac)

R2 fd1: DoB → Zodiac

----------------
R3: Email (LastName_, DoB_, Email)

R3 Fd1: LastName_, DoB_, -> Email

----------------
R4: Zip (Zip_, City, State)

R4 Fd1: Zip_ -> City, State

----------------
R5: Company (Company_, CompanyInfo)

R5 Fd1: Company -> CompanyInfo

### Relational Model 3

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

Assignments(A_, B_, C_, D, E, F, G, H, I, J, K, L, N, Q)

Partial fd1: A, B, C →  D, E, F, G, H, I, J, K, L, N, Q

Full fd2: A →  D, E, F, L, N, Q

Full fd3: B, C →  G, H

fd4: D →  L, N, Q

fd5: L → N

fd6: G → H

T1: A, B, C →  D & D →  L, N, Q
T2:  D →  L & L → N
T3:  B, C →  G & G → H

NEW

R1: (A_(fk), B_(fk), C_(fk), I, J, K)
R1 fd1: A, B, C →  G, I, J, K,

-----

R2: (A_, D(fk), E, F,)
R2: fd1: A -> D, E, F

-----
R3: (D_, L(fk), Q)
R3 fd1: D -> L, Q

----
R4: (L_, N)
R4 fd1: L -> N

----
R5: (G_, H)
R5 fd1: G -> H

---
R6: (B_, C_, G(fk))
R6 fd1: B, C -> G