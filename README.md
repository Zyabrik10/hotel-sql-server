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

-- запхайте сюда фото-карточку нашоі діаграми

## 1) Samples of queries and stuff
