# Insert and Query Data

## Overview
This lab continues the work from SQL Lab 1 by inserting sample data into the `Customers` and `Orders` tables and performing basic queries to retrieve and join that data. It simulates common tasks performed by database analysts or entry-level support engineers working with business data.

## Who / What / Where / When / Why

- **Who**: A data analyst at a retail company preparing sales reports.
- **What**: Insert test data into existing tables and run SQL queries to retrieve it.
- **Where**: Within the `ShopEZ` SQL Server database created in Lab 1.
- **When**: After table creation but before data visualization or reporting phases.
- **Why**: To validate that the database structure supports real-world query and reporting needs.

---

## Steps

### Step 1: Switch to the ShopEZ Database

```sql
USE ShopEZ;  -- Sets the current working database context to ShopEZ
```

**Explanation**: Ensures all actions apply to the correct database.

![image](https://github.com/user-attachments/assets/b43fe666-791e-4569-bf1d-8f2c6df93f06)

---

### Step 2: Insert Sample Data into the Customers Table

```sql
INSERT INTO Customers (FirstName, LastName, Email, JoinDate)  -- Specifies the columns to populate
VALUES 
('Alice', 'Johnson', 'alice@example.com', '2023-01-10'),      -- Inserts a new record for Alice Johnson
('Bob', 'Smith', 'bob@example.com', '2023-02-14'),             -- Inserts a new record for Bob Smith
('Charlie', 'Lee', 'charlie@example.com', '2023-03-20');       -- Inserts a new record for Charlie Lee
```

**Explanation**: Adds three sample customers with names, emails, and join dates to simulate real entries.

---

### Step 3: Insert Sample Data into the Orders Table

```sql
INSERT INTO Orders (CustomerID, OrderDate, TotalAmount)  -- Specifies the columns to populate
VALUES 
(1, '2023-02-01', 150.75),  -- Links order to CustomerID 1 (Alice), with a date and total
(2, '2023-03-05', 89.99),   -- Links order to CustomerID 2 (Bob), with a date and total
(1, '2023-03-10', 45.00);   -- Adds another order for Alice (CustomerID 1)
```

**Explanation**: Links orders to existing customers by referencing their `CustomerID` values.

---

### Step 4: View All Customers

```sql
SELECT * FROM Customers;  -- Retrieves all columns and rows from the Customers table
```

**Explanation**: Retrieves all columns and records from the `Customers` table.

---

### Step 5: View All Orders

```sql
SELECT * FROM Orders;  -- Retrieves all columns and rows from the Orders table
```

**Explanation**: Displays all existing order records for inspection.

---

### Step 6: Join Customers and Orders Tables

```sql
SELECT 
    c.FirstName,                 -- Selects the customer's first name
    c.LastName,                  -- Selects the customer's last name
    o.OrderDate,                 -- Selects the order date
    o.TotalAmount                -- Selects the order total amount
FROM 
    Customers c                  -- Alias 'c' represents the Customers table
JOIN 
    Orders o ON c.CustomerID = o.CustomerID;  -- Inner join based on matching CustomerID values
```

**Explanation**: Performs an inner join to combine customer and order data, showing full order context with customer details.

---

## Conclusion
This lab demonstrated how to insert and query data in a SQL Server database. These foundational skills are critical for data entry, reporting, and application backend development. This dataset can now be used for analytics, visualization, or further query practice.
