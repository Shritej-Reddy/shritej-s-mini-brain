PostgreSQL (Postgres) is a **powerful, open-source relational database** known for its **scalability, extensibility, and compliance with SQL standards**. It supports **advanced features** like JSONB, indexing, full-text search, and strong ACID compliance.

## **1️⃣ PostgreSQL Architecture Overview**

### **🔹 Key Components**

- **Postmaster Process** → Manages database connections.
    
- **Backend Processes** → Handle client requests and queries.
    
- **WAL (Write-Ahead Logging)** → Ensures durability and recovery.
    
- **Shared Buffers** → Cache for query performance.
    

✅ **Basic PostgreSQL Architecture:**
```
Client  --->  Postmaster  --->  Backend Process  --->  Data Storage
```

## **2️⃣ Basic PostgreSQL Commands**

### **🔹 Database Operations**

```
-- Create a database
CREATE DATABASE mydb;

-- Connect to a database
\c mydb;

-- List all databases
\l

-- Drop a database
DROP DATABASE mydb;

```

