# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
![fitness](https://github.com/user-attachments/assets/9f303f08-ecdb-49e1-b650-1beb965a4809)



### Entities and Attributes

| Entity | Attributes (PK, FK)                | Notes   |
|--------|--------------------                |----------|
| User   |user_id (PK), name,mobile_no, address |Identifies the user.|  
| Permission| per_id (PK), per_module, per_name|Defines permissions granted to the user.|       
|Trainer| trainer_id (PK), name, mobile, email|Represents trainers managing the members.|      
| Member|mem_id (PK), mem_type, mem_name, mem_mobile, mem_email| Represents gym members.|       
| Fitness|fit_id (PK), fit_type, fit_desc|Defines the fitness programs.|          


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|User - Permission|1:N|Mandatory (A user must have at least one permission) | A user can have multiple permissions.|     
| User - Trainer| N:M|Optional (User may or may not be a trainer)| A user can manage many trainers and vice versa.|
| Trainer - Fitness|1:N|Mandatory (A trainer must be associated with at least one fitness type)|Trainers manage fitness types.|
|Member - Fitness|N:M|Optional (Members may or may not be associated with a fitness type)|A member can be associated with multiple fitness types.|

### Assumptions
- Role-Based Access: Users have different roles (e.g., admin, trainer, member), with permissions assigned based on their role.
- Trainer-Managed Programs: Trainers manage fitness programs, and members can join multiple fitness types, each guided by a trainer.
- Flexible Member Participation: Members can participate in multiple fitness programs, with flexibility in the types and number of programs they join.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
![city](https://github.com/user-attachments/assets/16eaefc1-0896-4891-bfcc-2d204420807e)



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Member|member_id (PK), name|Represents library members.|
|Book|book_id (PK), title|Represents books available for loan.|
|Loan|loan_id (PK), date, return_date, member_id (FK), book_id (FK)|Represents the loan transactions between members and books.|
|Event|event_id (PK), name, date|Represents events that members can register for.|
|Speaker|speaker_id (PK), name|Represents speakers for events.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member - Loan|1:N|Mandatory (A member must have at least one loan)|A member can loan multiple books, but a loan belongs to one member.|
|Book - Loan|1:N|Mandatory (A book must be loaned to at least one member)|A book can be loaned to multiple members over time, but a loan record is for one book.|
|Member - Event|M:N|Optional (A member may or may not register for an event)|Members can register for many events, and each event can have many members.|
|Speaker - Event|M:N|Optional (An event may or may not have a speaker)|An event can have multiple speakers, and a speaker can be assigned to multiple events.|
### Assumptions
- Member-Book Loan System: A Member can borrow multiple Books with a Loan representing each borrowing transaction, which includes the loan and return dates.
- Event Participation: Members can register for multiple Events, and each Event can have multiple Members attending, with optional speakers.
- Speaker-Event Association: Events may feature one or more Speakers, and a Speaker can be involved in multiple Events.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
![Table](https://github.com/user-attachments/assets/67414d6f-d30b-4094-8793-244edc6e1a7a)




### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Customer      |CustomerID (PK), Name, Phone_No |  Customers reserving tables or ordering food     |
|  Waiter      |   WaiterID (PK), Name|  Waiters serve reservations/orders            |
| Reservation/Order       |  OrderID (PK), Date, Time, Guests | Customer reservations and placed orders                  |
| Dish       |   DishID (PK), Name, CategoryNo (FK)|Dishes available to order                     |
| Category       |  CategoryNo (PK), CategoryName| Dish classification (Starter, Main, Dessert)             |
|Bill | BillID (PK), Amount, Total|Bill generated for each order                     |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Customer – Waiter             |  1:1          |Mandatory               | Each reservation handled by one waiter      |
|  Order – Dishes            |   M:N         |   Mandatory for order            |     An order contains many dishes  |
|  Order – Bill            |    1:M        |   Mandatory for Bill            |  Each order generates one bill     |

### Assumptions
- Each reservation/order is served by one waiter.

- A dish belongs to exactly one category.

- Bills are generated only after placing an order.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**

