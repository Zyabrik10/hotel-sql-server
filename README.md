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
- **Database Management System**: Microsoft SQL Server
- **Database Design Tool**: SQL Server Management Studio 
- **Query Language**: Transact-SQL
- **Data Storage Type**: Relational database
- **Core Components Used**: 
  - Tables Primary & Foreign Keys
  - Views 
  - Stored Procedures 
  - Indexes 
  - Constraints 


## 1) Functional Requirements List:

- **Adding new records to the database**: The system must allow users to add new data to the tables (e.g., new clients, products).
- **Chec room anailability**: The sistem automatically checks for available rooms on selected dates.
- **Editing data**: The system should allow editing of existing data, such as changing a client's address and so on
- **Searching for dat**a: Users should be able to search for data based on various criteria (e.g., name, phone number, registration date).
- **Reporting**: The system must be able to generate reports based on collected data (e.g., a list of all orders in a given period).
- **User permission management**: The system should allow different users to perform different actions based on assigned roles (e.g., administrator, employee).
- **Notifications and warnings**: Displey warnings if, for example, the client already has a booking or dates overlap.

## 2) Technical Stack:

- **Database**: MySQL
- **Query Language**: SQL
- **Database Design tools**: MySQL Workbench, dbdiagram.io
- **System of version control**: Git, GitHub 

# 3. Database Design

## Diagram

![db-totel-diagram](https://github.com/user-attachments/assets/1f580f38-2542-4136-87ae-1b7590bf3f02)

# Database Schema Documentation

## Clients
Contains information about clients:
- `client_id` – unique client identifier.
- `client_name`, `surname` – first and last name.
- `passport_id`, `pesel` – identification documents.
- `phone`, `email` – contact information.

## Reservations
Contains data about room bookings:
- `reservation_id` – unique reservation identifier.
- `client_id` – relation to Clients table.
- `room_id` – relation to Rooms table.
- `start_date`, `end_date` – stay dates.

## ReservedRoom
Stores information about reserved rooms (multiple rooms per reservation possible):
- `reservation_id` – relation to Reservations.
- `room_id` – relation to Rooms.
- `reserved_cost` – specific room cost.

## Payments
Payment information for reservations:
- `payment_id` – unique payment identifier.
- `reservation_id` – relation to Reservations.
- `amount`, `payment_date`, `payment_method` – sum, date and payment method.

## Rooms
Description of hotel rooms:
- `room_id` – room identifier.
- `room_num` – room number (displayed to users).
- `type_id` – relation to Types (room type).

## Types
Room types (economy, standard, luxury):
- `type_id` – unique type identifier.
- `title` – type name (e.g., "Deluxe").
- `cost` – price per night.
- `description` – additional description.

## Employees
Hotel staff:
- `employee_id` – employee identifier.
- `name`, `surname`, `email`, `phone` – personal data.
- `position` – job position.
- `department_id` – relation to Departments.

## Departments
Hotel departments:
- `department_id` – department identifier.
- `title` – name (e.g., "Housekeeping", "Administration").
- `description` – description.

## Cleaning_Schedule
Room cleaning schedule:
- `cleaning_id` – unique cleaning identifier.
- `employee_id` – cleaning employee (relation to Employees).
- `room_id` – room being cleaned.
- `date` – cleaning date.
- `cleaning_status` – status ("Pending", "Completed", "Missed", etc.).

## Main Relationships:
- `Reservations` linked with `Clients` and `Rooms`
- `ReservedRoom` and `Payments` linked with `Reservations`
- `Rooms` has type via `Types`
- `Cleaning_Schedule` connects `Employees` and `Rooms`
- `Employees` belong to `Departments`
