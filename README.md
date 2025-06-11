# Hotel

Topic: Hotel

Short description: Capsule hotel, it's a unique type of accommodation featuring mane small, bed-sized rooms so called capsules.

Memebers: Oleksandr Mazurok, Oleksandr Katsal, Helena Parinova, Karyna Nemliienko, Anton Krykhta, Dinmukhammed Abdullayev 

---

## Scope and Brief Description of the System

The Cupsule Hotel Management System, is a database application designed to help administration to manage hotel(room reservations, room cleaning, security) 

- Client registration
- Possibility for a client to book a room
- Storage of client data (passport, PESEL(optional), phone, email)
- A system to change the room number if a client wants to switch rooms
- A system that has client priority understanding (system has a list of clients where they sorted based on the time client had made a reservation, and if they don't confirm/pay for the reservation they are removed from this list and we move to the next client on th list and repeat)

## System Requirements and Technical stack
- Database Management System: Microsoft SQL Server
- Database Design Tool: SQL Server Management Studio 
- Query Language: Transact-SQL
- Data Storage Type: Relational database
- Core Components Used: 
  - Tables Primary & Foreign Keys
  - Views 
  - Stored Procedures 
  - Indexes 
  - Constraints 

### Functional Requirements List:

- Adding new records to the database: The system must allow users to add new data to the tables (e.g., new clients, products).
- Chec room anailability: The sistem automatically checks for available rooms on selected dates.
- Editing data: The system should allow editing of existing data, such as changing a client's address and so on
- Searching for dat**a: Users should be able to search for data based on various criteria (e.g., name, phone number, registration date).
- **Reporting: The system must be able to generate reports based on collected data (e.g., a list of all orders in a given period).
- User permission management: The system should allow different users to perform different actions based on assigned roles (e.g., administrator, employee).
- Notifications and warnings: Displey warnings if, for example, the client already has a booking or dates overlap.

### Technical Stack:

- Database: MySQL
- Query Language: SQL
- Database Design tools: MySQL Workbench, dbdiagram.io
- System of version control: Git, GitHub 

## Database Design

### Diagram

![digram](https://github.com/user-attachments/assets/9923ac84-1218-41c8-9348-a1f4762c3a59)

### Database Schema Documentation

#### Clients

| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| clients_id  | int | primary key | Unique identification of client |
| client_name | varchar(50) | NOT NULL | Name of client | 
| surname | varchar(50) | NOT NULL | Surname of client |
| passport_id | varchar(8) | NOT NULL | Passport number |
| pesel | varchar(11) | ALLOW NULL | Optional identification number |
| phone | varchar(20) | NOT NULL | Phone number of client |
| email | varchar(50) | NOT NULL | e-mail address of client |

#### Reservations

| Name          | Data type| Limits                | Description                        |
| --------      | -------  | --------              | -------                            |
| reservation_id| int      | Primary key, NOT NULL |Unique identifier of the reservation|
| client_id     | int      | NOT NULL              |Unique identifier of the client     | 
| start_date    | date     | NOT NULL              |Start date of the reservation       | 
| end_date      | date     | NOT NULL              |Reservation end date                |

#### ReservedRoom

| Name          | Data type| Limits                | Description                        |
| --------      | -------  | --------              | -------                            |
| reservation_id| int      | Primary key, NOT NULL |Unique identifier of the reservation|
| reserved_cost | money    | NOT NULL              |Full room reservation cost          | 
| room_id       | date     | NOT NULL              |Unique identifier of the room       |

#### Payments

| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| payment_id  | int | ALLOW NULL | Unique identifier for each payment |
| reservation_id | int | ALLOW NULL | Foreign key linking to the reservation | 
| amount | money | ALLOW NULL | Total amount paid | 
| payment_date | date | NOT ALLOW | Date when the payment was made |  
| payment_method | varchar(50) | NOT ALLOW | Method of payment (e.g., Cash, Card, Online) |

#### Rooms

| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| room_id  | int | primary key, NOT NULL | unique identifier of the room |
| room_num | int | NOT NULL | Name of client | Room number visible to guests |
| type_id | int | NOT NULL | Surname of client | Foreign key referencing the room type |

#### Types

| Name        | Data type   | Limits                | Description                      |
| --------    | -------     | --------              | -------                          |
| type_id     | int         | Primary key, NOT NULL |Unique identifier of the room type|
| title       | varchar(50) | NOT NULL              |Room title visible to guests      | 
| cost        | money       | NOT NULL              |Room cost visible to guests       | 
| description | text        | ALLOW NULL            |Description of the room           |

#### Employees

| Name | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| employee_id | int | PRIMARY KEY | Unique identifier of employee |
| name | varchar(50) | NOT NULL | Name of employee |
| surname | varchar(50) | NOT NULL | Surname of employee |
| position | varchar(50) | NOT NULL | Position of employee |
| department_id | int | ALLOW NULL | Unique identifier of department |
| email | varchar(50) | ALLOW NULL | Email address of employee |
| phone | varchar(50) | ALLOW NULL | Phone number of employee |

#### Departments

| Name | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| department_id | int | PRIMARY KEY | Unique identifier of the department |
| title | varchar(50) | NOT NULL | Name of the department |
| description | text | ALLOW NULL | Optional description of the department |

#### Cleaning_Schedule

| Name    | Data type | Limits | Description |
| -------- | ------- | -------- | ------- |
| cleaning_id  | int | primary key |  | unique ID of the cleaning task|
| employee_id | int | ALLOW NULL | ID of the assigned cleaning employee |
| room_id | int | ALLOW NULL | ID of the room to be cleaned |
| date | date | ALLOW NULL | Date of scheduled or completed cleaning |
| cleaning_status | varchar(50) | ALLOW NULL | Status of cleaning (e.g., Scheduled, Done) |

## Views

1. **vw_client_reservation_summary**

    Provides a complete summary of each client's reservations, including personal details, reservation dates, assigned room number and type, reserved cost, and associated payment information. Useful for generating client activity reports, billing audits, or customer service inquiries.

    ```sql
    CREATE VIEW vw_client_reservation_summary AS
    SELECT 
      c.client_id,
      c.client_name,
      c.surname,
      c.email,
      r.reservation_id,
      r.start_date,
      r.end_date,
      rm.room_num,
      t.title AS room_type,
      rr.reserved_cost,
      p.amount AS payment_amount,
      p.payment_date,
      p.payment_method
    FROM clients AS c
    JOIN reservations AS r ON c.client_id = r.client_id
    LEFT JOIN reservedroom AS rr ON r.reservation_id = rr.reservation_id
    LEFT JOIN rooms AS rm ON rr.room_id = rm.room_id
    LEFT JOIN types AS t ON rm.type_id = t.type_id
    LEFT JOIN payments AS p ON r.reservation_id = p.reservation_id;
    ```

2. **vw_current_guests**

    Lists guests who are currently staying at the hotel (based on today’s date). Helpful for reception and room service coordination.

    ```sql
    CREATE VIEW vw_current_guests AS
    SELECT 
      c.client_id,
      c.client_name,
      c.surname,
      r.start_date,
      r.end_date
    FROM clients AS c
    JOIN reservations AS r ON c.client_id = r.client_id
    WHERE CAST(GETDATE() AS DATE) BETWEEN r.start_date AND r.end_date;

    ```

3. **vw_employee_task_summary**
    
    Displays the count of cleaning tasks assigned to each employee, grouped by cleaning status. Helps monitor staff workload and task distribution.

    ```sql
    CREATE VIEW vw_employee_task_summary AS
    SELECT 
      e.employee_id,
      e.name,
      e.surname,
      cs.cleaning_status,
      COUNT(*) AS task_count
    FROM employees AS e
    JOIN cleaning_schedule AS cs ON e.employee_id = cs.employee_id
    GROUP BY e.employee_id, e.name, e.surname, cs.cleaning_status;
    ```

4. **vw_empty_rooms_by_type**

    Shows how many rooms of each type are currently available (i.e., not reserved today). Supports real-time room availability tracking.

    ```sql
    CREATE VIEW vw_empty_rooms_by_type AS
    SELECT 
      t.title AS room_type,
      COUNT(*) AS available_rooms
    FROM rooms AS r
    JOIN types AS t ON r.type_id = t.type_id
    WHERE r.room_id NOT IN (
      SELECT rr.room_id
      FROM reservedroom AS rr
      JOIN reservations AS res ON rr.reservation_id = res.reservation_id
      WHERE CAST(GETDATE() AS DATE) BETWEEN res.start_date AND res.end_date
    )
    GROUP BY t.title;
    ```

5. **vw_frequent_clients**

    Lists clients with the highest number of reservations. Useful for loyalty programs, marketing, or identifying VIP clients.

    ```sql
    CREATE VIEW vw_frequent_clients AS
    SELECT 
      c.client_id,
      c.client_name,
      c.surname,
      COUNT(r.reservation_id) AS total_reservations
    FROM clients AS c
    JOIN reservations AS r ON c.client_id = r.client_id
    GROUP BY c.client_id, c.client_name, c.surname;
    ```

6. **vw_monthly_revenue**

    Summarizes total payments received per month. Helps track monthly revenue and financial performance.

    ```sql
    CREATE VIEW vw_monthly_revenue AS
    SELECT 
      FORMAT(p.payment_date, 'yyyy-MM') AS month,
      SUM(p.amount) AS total_revenue
    FROM payments AS p
    GROUP BY FORMAT(p.payment_date, 'yyyy-MM');
    ```

7. **vw_room_availability**

    Displays the current availability status ("occupied" or "available") of each room based on today’s date. It includes the room ID, room number, and room type. Useful for front desk operations, real-time room tracking, and allocation decisions.

    ```sql
    CREATE VIEW vw_room_availability AS
    SELECT 
        R.room_id,
        R.room_num,
        T.title AS room_type,
        CASE 
            WHEN EXISTS (
                SELECT 1 
                FROM ReservedRoom RR
                JOIN Reservations RS ON RR.reservation_id = RS.reservation_id
                WHERE RR.room_id = R.room_id
                  AND CAST(GETDATE() AS DATE) BETWEEN RS.start_date AND RS.end_date
            ) 
            THEN 'occupied'
            ELSE 'available'
        END AS availability
    FROM Rooms R
    JOIN Types T ON R.type_id = T.type_id;
    ```

8. **vw_upcoming_reservations**

    Displays the current availability status ("occupied" or "available") of each room based on today’s date. It includes the room ID, room number, and room type. Useful for front desk operations, real-time room tracking, and allocation decisions.

    ```sql
    CREATE VIEW vw_upcoming_reservations AS
    SELECT 
      r.reservation_id,
      c.client_name, 
      c.surname, 
      r.start_date, 
      r.end_date
    FROM reservations AS r
    JOIN clients AS c ON r.client_id = c.client_id;
    ```

    
# Procedures

1. **p_update_cleaning_status**

    Updates the cleaning status of a specific room for a given cleaning date. This procedure is typically used to mark a cleaning task as completed or update its progress.

    ```sql
    CREATE OR ALTER PROCEDURE p_update_cleaning_status
        @room_id INT,
        @cleaning_date DATE,
        @new_status VARCHAR(50)
    AS
    BEGIN
        DECLARE @error_msg NVARCHAR(200)
    
    -- Check if room exists
    IF NOT EXISTS (SELECT 1 FROM Rooms WHERE room_id = @room_id)
    BEGIN
        SET @error_msg = 'Room with ID ' + CAST(@room_id AS NVARCHAR(10)) + ' does not exist.'
        RAISERROR(@error_msg, 16, 1)
        RETURN
    END
    
    -- Check if cleaning record exists for this room and date
    IF NOT EXISTS (SELECT 1 FROM Cleaning_Schedule WHERE room_id = @room_id AND due_date = @cleaning_date)
    BEGIN
        SET @error_msg = 'No cleaning scheduled for room ' + CAST(@room_id AS NVARCHAR(10)) + 
                         ' on date ' + CONVERT(NVARCHAR(10), @cleaning_date, 120) + '.'
        RAISERROR(@error_msg, 16, 1)
        RETURN
    END
    
    -- Check if new_status is valid
    IF @new_status NOT IN ('done', 'undone', 'pending')
    BEGIN
        RAISERROR('Invalid status. Allowed values are: ''done'', ''undone'', ''pending''.', 16, 1)
        RETURN
    END
    
    -- If all checks passed, perform the update
    UPDATE Cleaning_Schedule
    SET cleaning_status = @new_status
    WHERE room_id = @room_id AND due_date = @cleaning_date
    
    -- If status is being set to 'done', update the finish_date to current date
    IF @new_status = 'done'
    BEGIN
        UPDATE Cleaning_Schedule
        SET finish_date = GETDATE()
        WHERE room_id = @room_id AND due_date = @cleaning_date
    END
    END
    ```

2. **p_cancel_reservation**

    Cancels a reservation by removing all associated entries from the Payments, ReservedRoom, and Reservations tables. Ensures that no orphan data remains.

    ```sql
    CREATE OR ALTER PROCEDURE p_cancel_reservation
    @reservation_id INT
    AS
    BEGIN
        SET NOCOUNT ON;
    
    BEGIN TRY
        BEGIN TRANSACTION;
        
        -- Check if reservation exists
        IF NOT EXISTS (SELECT 1 FROM Reservations WHERE reservation_id = @reservation_id)
        BEGIN
            RAISERROR('Reservation with ID %d does not exist.', 16, 1, @reservation_id);
            ROLLBACK TRANSACTION;
            RETURN;
        END
        
        -- First get the client_id from the reservation
        DECLARE @client_id INT;
        SELECT @client_id = client_id FROM Reservations WHERE reservation_id = @reservation_id;
        
        -- Delete payment records for this client (if they exist)
        -- Note: This assumes payments are linked by client_id, not reservation_id
        DELETE FROM Payments
        WHERE client_id = @client_id;
        
        -- Delete reserved rooms
        DELETE FROM ReservedRoom
        WHERE reservation_id = @reservation_id;
        
        -- Finally delete the reservation
        DELETE FROM Reservations
        WHERE reservation_id = @reservation_id;
        
        COMMIT TRANSACTION;
        
        PRINT 'Reservation ' + CAST(@reservation_id AS VARCHAR(10)) + ' successfully canceled.';
    END TRY
    BEGIN CATCH
        IF @@TRANCOUNT > 0
            ROLLBACK TRANSACTION;
            
        DECLARE @ErrorMessage NVARCHAR(4000) = ERROR_MESSAGE();
        DECLARE @ErrorSeverity INT = ERROR_SEVERITY();
        DECLARE @ErrorState INT = ERROR_STATE();
        
        RAISERROR(@ErrorMessage, @ErrorSeverity, @ErrorState);
    END CATCH
    END;
    ```

3. **p_register_payment**

    Registers a new payment made by a client. This procedure inserts a new record into the Payments table.

    ```sql
    CREATE OR ALTER PROCEDURE p_register_payment
    @client_id INT,
    @amount MONEY,
    @payment_date DATE,
    @payment_description NVARCHAR(100) = NULL
    AS
    BEGIN
        SET NOCOUNT ON;
    
    BEGIN TRY
    	-- Validate client exists
        IF NOT EXISTS (SELECT 1 FROM Clients WHERE client_id = @client_id)
        BEGIN
            RAISERROR('Client with ID %d does not exist.', 16, 1, @client_id);
            RETURN;
        END
        
        -- Validate input parameters
        IF @client_id IS NULL OR @amount IS NULL OR @payment_date IS NULL OR @payment_description IS NULL
        BEGIN
            RAISERROR('Client ID, amount, payment date and payment description cannot be NULL', 16, 1);
            RETURN;
        END
        
        IF @amount <= 0
        BEGIN
            RAISERROR('Payment amount must be positive', 16, 1);
            RETURN;
        END
        
        IF @payment_date < GETDATE()
        BEGIN
            RAISERROR('Payment date cannot be in the past', 16, 1);
            RETURN;
        END
        
        -- Get next available payment_id (max + 1)
        DECLARE @next_payment_id INT;
        SELECT @next_payment_id = ISNULL(MAX(payment_id), 0) + 1 FROM Payments;
        
        -- Insert payment record
        INSERT INTO Payments (
            payment_id, 
            client_id, 
            amount, 
            payment_date,
            payment_description
        )
        VALUES (
            @next_payment_id,
            @client_id,
            @amount,
            @payment_date,
            @payment_description
        );
        
    END TRY
    BEGIN CATCH
        DECLARE @ErrorMessage NVARCHAR(4000) = ERROR_MESSAGE();
        DECLARE @ErrorSeverity INT = ERROR_SEVERITY();
        DECLARE @ErrorState INT = ERROR_STATE();
        
        RAISERROR(@ErrorMessage, @ErrorSeverity, @ErrorState);
    END CATCH
    END;
    ```

4. **p_reassign_cleaner**

    Reassigns a cleaning task to a different employee. Updates the `employee_id` for a specific cleaning task in the Cleaning_Schedule.

    ```sql
    CREATE OR ALTER PROCEDURE p_reassign_cleaner
        @cleaning_id INT,
        @new_employee_id INT
    AS
    BEGIN
        BEGIN TRY
            -- Validate cleaning task exists
            IF NOT EXISTS (SELECT 1 FROM Cleaning_Schedule WHERE cleaning_id = @cleaning_id)
            BEGIN
                RAISERROR('Cleaning task with ID %d does not exist.', 16, 1, @cleaning_id);
                RETURN;
            END
        
        -- Validate new employee exists
        IF NOT EXISTS (SELECT 1 FROM Employees WHERE employee_id = @new_employee_id)
        BEGIN
            RAISERROR('Employee with ID %d does not exist.', 16, 1, @new_employee_id);
            RETURN;
        END
        
        -- Check if employee is being reassigned to the same person
        DECLARE @current_employee_id INT;
        SELECT @current_employee_id = employee_id 
        FROM Cleaning_Schedule 
        WHERE cleaning_id = @cleaning_id;
        
        IF @current_employee_id = @new_employee_id
        BEGIN
            RAISERROR('Employee is already assigned to this cleaning task.', 16, 1);
            RETURN;
        END
        
        -- Perform the reassignment
        UPDATE Cleaning_Schedule
        SET employee_id = @new_employee_id
        WHERE cleaning_id = @cleaning_id;
    END TRY
    BEGIN CATCH
        DECLARE @ErrorMessage NVARCHAR(4000) = ERROR_MESSAGE();
        DECLARE @ErrorSeverity INT = ERROR_SEVERITY();
        DECLARE @ErrorState INT = ERROR_STATE();
        
        RAISERROR(@ErrorMessage, @ErrorSeverity, @ErrorState);
    END CATCH
    END;
    ```

5. **p_generate_client_report**

    Generates a full report of a client’s activity, including reservations, room types, room numbers, and reservation payment.

    ```sql
    CREATE OR ALTER PROCEDURE p_generate_client_report
	@client_id INT
     AS
     BEGIN
	
	IF NOT EXISTS (SELECT 1 FROM Clients WHERE client_id = @client_id)
    	BEGIN
        	RAISERROR('Client with ID %d does not exist.', 16, 1, @client_id);
        	RETURN;
    	END
	
	SELECT 
	        c.client_name, 
	        c.surname, 
	        r.reservation_id, 
	        r.start_date, 
	        r.end_date,
	        ro.room_num, 
	        t.title AS room_type, 
	        p.amount, 
	        p.payment_date AS 'reservation_payment_date'
	FROM Clients c
	JOIN Reservations r ON c.client_id = r.client_id 
	LEFT JOIN ReservedRoom rr ON r.reservation_id = rr.reservation_id
	LEFT JOIN Rooms ro ON rr.room_id = ro.room_id
	LEFT JOIN Types t ON ro.type_id = t.type_id
	LEFT JOIN Payments p ON r.client_id = p.client_id
	WHERE c.client_id = @client_id;
    END;
    ```
