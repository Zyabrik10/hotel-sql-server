**Topic:** Hotel
**Short description:** Capsale hotel, it's a unique type of accommodation featuring mane small, bed-sized rooms so called capsules.

**Memebers:** Oleksandr Mazurok, Oleksandr Katsal, Helena Parinova, Karyna Nemliienko, Anton Krykhta, Dinmukhammed Abdullayev 

--- 
# 1. Scope and Brief Description of the System
The Cupsule Hotel Management System, is a database application designed to help administration to manage hotel(room reservations, room cleaning, security) 

- Client registration;
- Possibility for a client to book a room;
- Storage of client data (passport, PESEL(optional), phone, email);
- A system to change the room number if a client wants to switch rooms;
- A system that has client priority understanding (system has a list of clients where they sorted based on the time client had made a reservation, and if they don't confirm/pay for the reservation they are removed from this list and we move to the next client on th list and repeat);

# 2. System Requirements and Functions
## 1) Functional Requirements List

- Adding new records to the database: 
The system must allow users to add new data to the tables (e.g., new clients, products).

- Editing data: 
The system should allow editing of existing data, such as changing a client's address and so on

- Searching for data: 
Users should be able to search for data based on various criteria (e.g., name, phone number, registration date).

- Reporting: 
The system must be able to generate reports based on collected data (e.g., a list of all orders in a given period).

- User permission management: 
The system should allow different users to perform different actions based on assigned roles (e.g., administrator, employee).

2) User Stories

As a system administrator, I want to be able to add new users to control system access.

As an employee, I want to search for clients by phone number to quickly find their contact information.

As a business analyst , I want to generate sales reports to analyze business performance.

As a client, I want to edit my profile to change my contact details.

3. Database Design
Database Schema
(Diagram representing the database schema)

Description of Individual Tables
(For each table, a description in tabular format)

Table Name: (table name)

Description: (description of the table, comments)


Attribute NameTypeDescription/Remarks
Attribute 1 …
Attribute 2 …

4. Implementation
DDL Statements
(For each table, paste the DDL statement creating the table)
'''
create table tab1 (
   a int,
   b varchar(10)
)
'''
Views
(For each view, paste the SQL code defining the view along with a comment)

Procedures/Functions
(For each procedure/function, paste the SQL code defining it along with a comment)

Triggers
(For each trigger, paste the SQL code defining the trigger along with a comment)
