#### **What is System Design?**

System design is the process of defining the architecture, components, and data flow of a system to meet specific requirements. It is crucial for designing scalable and efficient applications, particularly in distributed environments.

#### **Key Principles of System Design:**

1. **Scalability** – The ability to handle increasing workloads by adding resources (either hardware or software).
2. **Availability** – The system should remain operational for a high percentage of time.
3. **Fault Tolerance** – The system can continue functioning despite failures of some components.
4. **Maintainability** – The system should be easy to modify, debug, and extend.
5. **Extensibility** – The ability to add new features without affecting existing functionality.

#### **Common System Design Goals**

- **Load Balancing** – Distribute traffic across multiple servers to prevent overload.
- **Fault Tolerance** – Ensure the system continues operating even if some components fail.
- **Distributed Systems** – Use multiple machines to improve performance and availability.
- **High Availability** – Minimize downtime by using replication, failovers, and redundancy.

### **CAP Theorem (Consistency, Availability, Partition Tolerance)**

- **Consistency (C)** – Every read receives the most recent write.
- **Availability (A)** – Every request receives a response (not necessarily the latest data).
- **Partition Tolerance (P)** – The system continues to function despite network failures.
- **CAP Theorem Rule** – In a distributed system, you can only achieve **two** of the three guarantees.
#### **Examples:**

- **CP Systems** (Consistency & Partition Tolerance) – Example: MongoDB in strict mode.
- **AP Systems** (Availability & Partition Tolerance) – Example: DynamoDB.
- **CA Systems** (Consistency & Availability) – Not feasible in a distributed setup.
### **Horizontal vs. Vertical Scaling**

1. **Vertical Scaling (Scale-Up)** – Increasing the power of a single machine (e.g., adding more CPU, RAM).
    - Pros: Simple to implement.
    - Cons: Limited by hardware capacity.
2. **Horizontal Scaling (Scale-Out)** – Adding more machines to distribute load.
    - Pros: Highly scalable and fault-tolerant.
    - Cons: Complex setup (requires load balancers, distributed storage).

### **Key Networking Concepts**

1. **DNS (Domain Name System)** – Translates domain names (e.g., google.com) into IP addresses.
2. **HTTP/HTTPS** – Protocols used for web communication.
3. **Load Balancers** – Distribute network traffic across multiple servers to ensure no single server is overwhelmed.

### **Types of Load Balancers**

- **DNS Load Balancing** – Distributes requests by resolving domain names to multiple IPs.
- **Layer 4 Load Balancing** – Operates at the transport layer (e.g., TCP, UDP).
- **Layer 7 Load Balancing** – Operates at the application layer (e.g., HTTP headers, cookies).

## SQL (Relational Databases) vs. NoSQL (Non-Relational Databases)

| Feature          | SQL (Relational)                             | NoSQL (Non-Relational)                         |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| **Schema**       | Fixed schema (tables, columns)               | Flexible schema (documents, key-value, etc.)   |
| **Data Storage** | Stores structured data in tables             | Stores unstructured/semi-structured data       |
| **Scalability**  | Scales **vertically** (adding more CPU, RAM) | Scales **horizontally** (adding more machines) |
| **Consistency**  | Strong consistency (ACID compliance)         | Eventual consistency (BASE model)              |
| **Examples**     | MySQL, PostgreSQL, Oracle, SQL Server        | MongoDB, Cassandra, Redis, DynamoDB            |
## When to Use SQL vs. NoSQL

✅ **Use SQL When:**

- You need **structured data** (e.g., banking transactions).
- You need **strict consistency** (e.g., financial applications).
- Data relationships matter (e.g., customer orders in an e-commerce site).

✅ **Use NoSQL When:**

- You have **unstructured or semi-structured** data (e.g., JSON documents).
- You need **high scalability** (e.g., social media applications).
- You have **real-time big data** (e.g., recommendation engines, logs).

📌 **Example Decision:**

- A bank would use **SQL (PostgreSQL)** for transactions (strict consistency).
- A social media platform would use **NoSQL (MongoDB, Cassandra)** for posts and comments (scalable, high availability).
## Indexes (Speeding Up Queries)

- **Indexes** improve search speed by reducing the number of rows scanned.
- Think of it like a book index: Instead of flipping through pages, you jump to the right page.
- Example:
    `CREATE INDEX idx_name ON users (name);`

- **Types of Indexes**:
    - **Primary Index** – Automatically created on primary keys.
    - **Secondary Index** – Manually created for frequently queried columns.
    - **Full-Text Index** – Used for searching text data efficiently.
## Sharding (Partitioning Data Across Servers)

- **Sharding** splits large databases into smaller parts (shards) to improve performance.
- Example:
    - A user database with **100M users** can be split based on **user ID ranges** (e.g., 1-10M, 10M-20M).

**Sharding Strategies:**

1. **Range-based** – Divide data based on a range (e.g., users A-M in one shard, N-Z in another).
2. **Hash-based** – Use a hash function to distribute data evenly.
3. **Geo-based** – Store user data based on geographic location.
## Replication (Data Redundancy for High Availability)

- **Replication** makes copies of data across multiple servers to improve reliability and availability.

**Types of Replication:**

1. **Master-Slave Replication** – A master writes data, slaves replicate it (good for read-heavy workloads).
2. **Multi-Master Replication** – Multiple nodes can write and sync with each other.
3. **Read Replicas** – Copies of databases used for handling read queries efficiently.

📌 **Example:**

- Facebook replicates user data across **multiple data centers** worldwide to handle millions of requests.
