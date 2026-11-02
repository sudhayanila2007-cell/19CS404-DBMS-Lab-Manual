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
<img width="1481" height="727" alt="WhatsApp Image 2026-11-02 at 8 32 22 AM" src="https://github.com/user-attachments/assets/81e76de0-3d0c-48fa-b30f-cbd815af98fd" />

### Entities and Attributes

| **Entity**       | **Attributes (PK, FK)**                                  | **Notes**                                          |
| ---------------- | -------------------------------------------------------- | -------------------------------------------------- |
| Member           | Member_ID (PK), Name, Phone, Membership_Type, Start_Date | Stores member registration and membership details. |
| Program          | Program_ID (PK), Program_Name, Duration                  | Stores fitness program details.                    |
| Trainer          | Trainer_ID (PK), Name, Specialization                    | Stores trainer information and specialization.     |
| Personal_Session | Session_ID (PK), Date                                    | Stores personal training session details.          |
| Attendance       | Attendance_ID (PK), Status, Date                         | Records member attendance details.                 |
| Payment          | Payment_ID (PK), Amount, Payment_Type, Payment_Date      | Stores payment transaction details.                |


### Relationships and Constraints

| **Relationship**                          | **Cardinality** | **Participation** | **Notes**                                                                                   |
| ----------------------------------------- | --------------- | ----------------- | ------------------------------------------------------------------------------------------- |
| Member — Joins — Program                  | 1:N (As drawn)  | Partial           | One member can join multiple programs.                                                      |
| Program — Has — Trainer                   | M:N             | Partial           | A program can have multiple trainers, and a trainer can handle multiple programs.           |
| Member — Books — Personal_Session         | 1:N             | Partial           | A member can book multiple personal sessions, while each session is booked by one member.   |
| Trainer — Conducted_by — Personal_Session | 1:N             | Partial           | One trainer can conduct multiple personal sessions.                                         |
| Personal_Session — Has — Attendance       | M:1 (As drawn)  | Partial           | Multiple personal sessions are connected to one attendance record according to the diagram. |
| Member — Makes — Payment                  | 1:N (Assumed)   | Partial           | A member can make multiple payments, and each payment belongs to one member.                |


### Assumptions
1.Each member, program, trainer, session, attendance record, and payment has a unique ID.

2.A member can join multiple fitness programs.

3.A program can have multiple trainers, and a trainer can handle multiple programs.

4.Each personal training session is associated with one member and one trainer.

5.Attendance is maintained to track member participation.

6.Payments are made only by registered members.

7.Each payment is associated with a unique Payment_ID.

8.A member can make multiple payments for gym services.

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
<img width="1122" height="612" alt="WhatsApp Image 2026-11-02 at 8 43 10 AM" src="https://github.com/user-attachments/assets/da7d8c52-ca7c-43d2-a4e5-69c8ab4e4d3f" />

### Entities and Attributes

| **Entity**            | **Attributes (PK, FK)**                                           | **Notes**                                               |
| --------------------- | ----------------------------------------------------------------- | ------------------------------------------------------- |
| Entity                | User_ID (PK), Reg_No, Book_No, Issue_Return                       | Stores user registration and book issue/return details. |
| Staff                 | Staff_ID (PK), Name                                               | Stores library staff information.                       |
| Authentication_System | Login_ID (PK), Password                                           | Maintains login credentials for staff.                  |
| Readers               | User_ID (PK), FirstName, LastName, Name, Email, Phone_No, Address | Stores reader registration and contact details.         |
| Books                 | ISBN (PK), Book_No, Title, Author_No, Category, Edition           | Stores book information and classification details.     |
| Publisher             | Publisher_ID (PK), Name, Year_Of_Publisher                        | Stores publisher information.                           |


### Relationships and Constraints

| **Relationship**                      | **Cardinality** | **Participation** | **Notes**                                                             |
| ------------------------------------- | --------------- | ----------------- | --------------------------------------------------------------------- |
| Entity — Manages — Staff              | N:1             | Partial           | Multiple entity records can be managed by one staff member.           |
| Staff — Login — Authentication_System | N:1             | Partial           | Multiple staff members are associated with the authentication system. |
| Staff — Keeps_Track_Of — Readers      | M:N             | Partial           | Multiple staff members can keep track of multiple readers.            |
| Staff — Maintain — Books              | 1:N             | Partial           | One staff member can maintain multiple books.                         |
| Readers — Reserve_Return_Date — Books | 1:N (As drawn)  | Partial           | One reader can reserve or borrow multiple books.                      |
| Books — Relationship — Publisher      | N:1             | Partial           | Multiple books can be associated with one publisher.                  |


### Assumptions
1.Each reader, staff member, book, and publisher has a unique ID.

2.Each reader is identified by a unique User_ID.

3.Each book is identified by its ISBN.

4.Staff members are responsible for managing library operations.

5.Readers can borrow or reserve multiple books.

6.ReserveDate, Due_Date, and Return_Date are maintained to track borrowing and returning activities.

7.One publisher can publish multiple books.

8.Each book is associated with one publisher.

T9.he authentication system maintains login credentials for staff members.

10.Staff members maintain book records and reader information.

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
<img width="1075" height="747" alt="image" src="https://github.com/user-attachments/assets/e48070ef-8780-4a41-9751-0ba8f1613986" />


### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**                        | **Notes**                                                                          |
| ----------- | ---------------------------------------------- | ---------------------------------------------------------------------------------- |
| Customer    | C_ID (PK), Name, Email, Phone_No, Address      | Stores customer registration and contact information.                              |
| Reservation | R_ID (PK), Date, C_ID (FK), ID (FK)            | Stores customer reservation details and restaurant reference.                      |
| Restaurant  | ID (PK), Name, Location                        | Stores restaurant details and location information.                                |
| Order       | O_ID (PK), ID (FK), C_ID (FK), Amount, Date    | Stores customer order details and associated restaurant.                           |
| Delivery    | D_ID (PK), Date, Status, O_ID (FK)             | Stores delivery information and order status.                                      |
| Receive     | No attributes specified                        | Represents the receiving relationship between Order and Restaurant in the diagram. |
| Menu_Item   | M_ID (PK), Name, Price, Description, R_ID (FK) | Stores menu item details and restaurant reference.                                 |


### Relationships and Constraints

| **Relationship**                        | **Cardinality**       | **Participation** | **Notes**                                                    |
| --------------------------------------- | --------------------- | ----------------- | ------------------------------------------------------------ |
| Customer — Have — Reservation           | 1:N                   | Partial           | One customer can make multiple reservations.                 |
| Reservation — Relationship — Restaurant | N:1                   | Partial           | Multiple reservations can be associated with one restaurant. |
| Customer — Place — Order                | 1:N                   | Partial           | One customer can place multiple orders.                      |
| Order — Receive — Restaurant            | M:1 (Through Receive) | Partial           | Multiple orders can be received by one restaurant.           |
| Restaurant — Offers — Menu_Item         | 1:N                   | Partial           | One restaurant can offer multiple menu items.                |
| Order — Associated_With — Delivery      | 1:1                   | Partial           | Each order is associated with one delivery record.           |


### Assumptions
-Each customer, reservation, restaurant, order, delivery, and menu item has a unique ID.

-A customer can make multiple reservations.

-Each reservation belongs to one restaurant.

-Customers can place multiple orders.

-Each order is associated with a particular restaurant.

-A restaurant can offer multiple menu items.

-Each menu item belongs to one restaurant.

-Each order is associated with one delivery record.

-Delivery status is maintained to track order delivery.

-Order amount and date are maintained for billing and tracking purposes.

-The Receive entity represents the process of receiving orders by the restaurant.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
