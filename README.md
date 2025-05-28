**Topic:** Hotel

**Short description:** Capsule hotel, it's a unique type of accommodation featuring mane small, bed-sized rooms so called capsules.

**Memebers:** Oleksandr Mazurok, Oleksandr Katsal, Helena Parinova, Karyna Nemliienko, Anton Krykhta, Dinmukhammed Abdullayev 

---

# 1. Scope and Brief Description of the System

The Cupsule Hotel Management System, is a database application designed to help administration to manage hotel(room reservations, room cleaning, security) 

- Client registration;
- Possibility for a client to book a room;
- Storage of client data (passport, PESEL(optional), phone, email);
- A system to change the room number if a client wants to switch rooms;
- A system that has client priority understanding (system has a list of clients where they sorted based on the time client had made a reservation, and if they don't confirm/pay for the reservation they are removed from this list and we move to the next client on th list and repeat);

# 2. System Requirements and Technical stack
-Database Management System:
Microsoft SQL Server

-Database Design Tool:
SQL Server Management Studio 

-Query Language:
Transact-SQL

-Data Storage Type:
Relational database

-Core Components Used:
Tables
Primary & Foreign Keys
Views 
Stored Procedures 
Indexes 
Constraints 


## 1) Functional Requirements List:

- Adding new records to the database: 
The system must allow users to add new data to the tables (e.g., new clients, products).

- Chec room anailability:
The sistem automatically checks for available rooms on selected dates.

- Editing data: 
The system should allow editing of existing data, such as changing a client's address and so on

- Searching for data: 
Users should be able to search for data based on various criteria (e.g., name, phone number, registration date).

- Reporting: 
The system must be able to generate reports based on collected data (e.g., a list of all orders in a given period).

- User permission management: 
The system should allow different users to perform different actions based on assigned roles (e.g., administrator, employee).

- Notifications and warnings:
Displey warnings if, for example, the client already has a booking or dates overlap.

## 2) Technical Stack:

- Database: MySQL
- Query Language: SQL
- Database Design tools: MySQL Workbench, dbdiagram.io
- System of version control: Git, GitHub 

# 3. Database Design + description (опис бази, візьміть за приклад базу northwind, вона найбільше схожа на нашу ситуацію)

## Design

![db-totel-diagram](https://github.com/user-attachments/assets/1f580f38-2542-4136-87ae-1b7590bf3f02)

## System Requirements and Technical Stack

1) Functional Requirements

The Capsule Hotel Management System is expected to support the following core functionalities:
 • Adding new records to the database:
The system must allow users to insert new data into relevant tables, such as adding new clients, capsules, and bookings.
 • Checking room availability:
The system must automatically check for available capsules for a selected date range before confirming a reservation.
 • Editing data:
Users should be able to update existing information, such as modifying client contact details or adjusting booking dates.
 • Searching for data:
The system should support searching by various criteria (e.g., client name, passport number, phone number, booking date).
 • Generating reports:
The system must generate reports based on stored data, such as a list of all bookings in a specific time period or capsule occupancy statistics.
 • User role and permission management:
Different user roles (e.g., administrator, employee) should have different levels of access and control within the system.
 • Notifications and warnings:
The system should display alerts if a client tries to book an already reserved capsule, or if booking dates overlap.

⸻

2) Technical Stack

The system will use the following tools and technologies:
 • Database Management System:
Microsoft SQL Server — used for storing and managing all hotel data in a secure and structured way.
 • Query Language:
Transact-SQL (T-SQL) — used for writing all data manipulation and retrieval queries within Microsoft SQL Server.
 • Database Design Tool:
SQL Server Management Studio (SSMS) — the main tool used to create the schema, manage tables, and run SQL queries.
 • Data Storage Type:
Relational Database — the data is stored in structured tables that are connected by relationships.
 • Core Components Used:
 • Tables — store data about clients, bookings, capsules, staff, etc.
 • Primary & Foreign Keys — maintain data integrity and relationships between tables.
 • Views — used to simplify complex queries or generate summary reports.
 • Stored Procedures — encapsulate business logic like booking confirmation or cancellation.
 • Indexes — improve query performance, especially on large datasets.
 • Constraints — enforce business rules, like preventing double bookings or invalid data entry.
 • Version Control System:
Git, GitHub — used for tracking changes in database design scripts and application code, enabling team collaboration.
