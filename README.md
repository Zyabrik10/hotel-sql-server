**Topic:** Hotel

**Short description:** Capsule hotel, it's a unique type of accommodation featuring mane small, bed-sized rooms so called capsules.

**Memebers:** Oleksandr Mazurok, Oleksandr Katsal, Helena Parinova, Karyna Nemliienko, Anton Krykhta, Dinmukhammed Abdullayev 

---

# 1. Scope and Brief Description of the System

The Cupsule Hotel Management System, is a database application designed to help administration to manage hotel(room reservations, room cleaning, security) 

- Client registration
- Possibility for a client to book a room
- Storage of client data (passport, PESEL(optional), phone, email)
- A system to change the room number if a client wants to switch rooms
- A system that has client priority understanding (system has a list of clients where they sorted based on the time client had made a reservation, and if they don't confirm/pay for the reservation they are removed from this list and we move to the next client on th list and repeat)

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
| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| clients_id  | int | primary key | Unique identification of client |
| client_name | varchar(50) | NOT NULL | Name of client | 
| surname | varchar(50) | NOT NULL | Surname of client |
| passport_id | varchar(8) | NOT NULL | Passport number |
| pesel | varchar(11) | ALLOW NULL | Optional identification number |
| phone | varchar(20) | NOT NULL | Phone number of client |
| email | varchar(50) | NOT NULL | e-mail address of client |

## Reservations
| Name          | Data type| Limits                | Description                        |
| --------      | -------  | --------              | -------                            |
| reservation_id| int      | Primary key, NOT NULL |Unique identifier of the reservation|
| client_id     | int      | NOT NULL              |Unique identifier of the client     | 
| start_date    | date     | NOT NULL              |Start date of the reservation       | 
| end_date      | date     | NOT NULL              |Reservation end date                |

## ReservedRoom
| Name          | Data type| Limits                | Description                        |
| --------      | -------  | --------              | -------                            |
| reservation_id| int      | Primary key, NOT NULL |Unique identifier of the reservation|
| reserved_cost | money    | NOT NULL              |Full room reservation cost          | 
| room_id       | date     | NOT NULL              |Unique identifier of the room       |

## Payments
| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| payment_id  | int | ALLOW NULL | Unique identifier for each payment |
| reservation_id | int | ALLOW NULL | Foreign key linking to the reservation | 
| amount | money | ALLOW NULL | Total amount paid | 
| payment_date | date | NOT ALLOW | Date when the payment was made |  
| payment_method | varchar(50) | NOT ALLOW | Method of payment (e.g., Cash, Card, Online) |

## Rooms
| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| room_id  | int | primary key, NOT NULL | unique identifier of the room |
| room_num | int | NOT NULL | Name of client | Room number visible to guests |
| type_id | int | NOT NULL | Surname of client | Foreign key referencing the room type |

## Types
| Name        | Data type   | Limits                | Description                      |
| --------    | -------     | --------              | -------                          |
| type_id     | int         | Primary key, NOT NULL |Unique identifier of the room type|
| title       | varchar(50) | NOT NULL              |Room title visible to guests      | 
| cost        | money       | NOT NULL              |Room cost visible to guests       | 
| description | text        | ALLOW NULL            |Description of the room           |

## Employees
| Name | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| employee_id | int | PRIMARY KEY | Unique identifier of employee |
| name | varchar(50) | NOT NULL | Name of employee |
| surname | varchar(50) | NOT NULL | Surname of employee |
| position | varchar(50) | NOT NULL | Position of employee |
| department_id | int | ALLOW NULL | Unique identifier of department |
| email | varchar(50) | ALLOW NULL | Email address of employee |
| phone | varchar(50) | ALLOW NULL | Phone number of employee |

## Departments
| Name | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| department_id | int | PRIMARY KEY | Unique identifier of the department |
| title | varchar(50) | NOT NULL | Name of the department |
| description | text | ALLOW NULL | Optional description of the department |

## Cleaning_Schedule
| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| cleaning_id  | int | primary key |  | unique ID of the cleaning task|
| employee_id | int | ALLOW NULL | ID of the assigned cleaning employee |
| room_id | int | ALLOW NULL | ID of the room to be cleaned |
| date | date | ALLOW NULL | Date of scheduled or completed cleaning |
| cleaning_status | varchar(50) | ALLOW NULL | Status of cleaning (e.g., Scheduled, Done) |
