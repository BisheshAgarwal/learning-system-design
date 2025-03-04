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

## **Consistency Models (How Data is Synchronized Across Nodes)**

Consistency determines **how quickly** data updates are visible to all nodes.

- **Strong Consistency** – A read always returns the latest write. (e.g., SQL databases)
- **Eventual Consistency** – Data updates may take time to propagate but eventually sync (e.g., NoSQL databases like DynamoDB).

**Example:**

- **Bank Transactions (SQL, Strong Consistency)** – A transfer must update both sender and receiver accounts instantly.
- **Social Media Feeds (NoSQL, Eventual Consistency)** – A post might take a second to appear on all user feeds.

# **CAP Theorem & ACID vs. BASE**

## **1. CAP Theorem (Trade-offs in Distributed Databases)**

In a **distributed database**, you can only have **two** of these three:

1. **Consistency (C)** – Every read gets the latest write.
2. **Availability (A)** – Every request gets a response (even if some nodes are down).
3. **Partition Tolerance (P)** – The system functions even if network communication fails.

|Database|Type|CAP Properties|
|---|---|---|
|MySQL|SQL|CA (No partition tolerance)|
|MongoDB|NoSQL|CP (Strong consistency, partition tolerance)|
|DynamoDB|NoSQL|AP (Availability, partition tolerance)|

📌 **Example Trade-offs:**

- **Google Spanner (CP)** – Prioritizes consistency in financial transactions.
- **Amazon DynamoDB (AP)** – Prioritizes availability for fast e-commerce transactions.

## **2. ACID vs. BASE (Data Consistency Models)**

### **ACID (SQL Databases - Strong Consistency)**

Ensures **data reliability** in transactions.

1. **Atomicity** – A transaction is **all or nothing**.
2. **Consistency** – Data remains in a valid state.
3. **Isolation** – Transactions do not interfere with each other.
4. **Durability** – Data is permanently stored.

📌 **Example:**

- If a bank transaction is interrupted mid-transfer, ACID ensures **either full transfer or nothing happens** (no money loss).

### **BASE (NoSQL Databases - Eventual Consistency)**

Focuses on **availability & performance** over strict consistency.

1. **Basically Available** – System is almost always operational.
2. **Soft State** – Data may change over time (not strongly consistent).
3. **Eventual Consistency** – Data will sync but not instantly.

📌 **Example:**

- When you post on Twitter, your tweet may **not appear instantly** for all followers but syncs in a few seconds.

# **Understanding Caching & Eviction Strategies**

## **1. What is Caching?**

Caching is the process of **storing frequently accessed data in a fast storage layer (like RAM)** to reduce latency and improve performance.
### **How Caching Works**

1. A user requests data from the server.
2. The system first **checks the cache**.
3. If data is found (**cache hit**), it's **returned instantly**.
4. If data isn’t found (**cache miss**), it's **fetched from the database** and stored in the cache for future use.

✅ **Example:**

- When you **visit a website**, images, CSS, and JS files are cached in your browser to load faster next time.

✅ **Benefits of Caching:**

- **Faster response times**
- **Reduces database load**
- **Handles more traffic with fewer resources**
## **2. Types of Caching**

### **1. Application Caching (In-Memory Caching)**

- Stores frequently accessed **database queries, API responses, or computations** in memory.
- **Example:** A website caching user session data using **Redis**.

### **2. Database Caching**

- Stores database query results in a cache layer.
- **Example:** MySQL’s built-in query cache, or caching in **Memcached**.

### **3. Content Caching (CDNs - Content Delivery Networks)**

- Stores static content like images, videos, and scripts **closer to users**.
- **Example:** Cloudflare or AWS CloudFront caches images for faster loading.

## **3. Cache Eviction Strategies (Managing Cache Memory)**

Caches have **limited storage**, so old data must be removed when new data is added. This is where **cache eviction policies** come in.
### **1. Least Recently Used (LRU)**

- Removes the **oldest unused** data first.
- **Best for:** General caching where old data becomes irrelevant over time.
- **Example:** Web browsers remove least-used tabs from memory.

### **2. Least Frequently Used (LFU)**

- Removes the **least accessed** items first.
- **Best for:** Systems with repetitive access patterns.
- **Example:** A music streaming app caches frequently played songs.

### **3. First In, First Out (FIFO)**

- Removes the **oldest added** data first.
- **Best for:** Simple caching systems.
- **Example:** A queue-based system storing temporary API results.

**Comparison Table:**

|Strategy|Removes|Best Use Case|
|---|---|---|
|**LRU**|Least recently used data|Web browsers, session caching|
|**LFU**|Least frequently accessed data|Recommendation systems|
|**FIFO**|Oldest stored data|Message queues, limited cache space|
# **Caching Solutions & CDNs**

## **1. Caching Solutions: Redis & Memcached**

|Feature|**Redis**|**Memcached**|
|---|---|---|
|**Data Storage**|Key-value store|Key-value store|
|**Persistence**|Supports data persistence|No persistence|
|**Data Types**|Strings, Lists, Sets, Hashes|Only Strings|
|**Performance**|Faster for complex data structures|Faster for simple key-value pairs|
|**Use Cases**|User sessions, leaderboards, real-time analytics|Simple caching (e.g., API responses)|

✅ **When to Use Redis?**

- If **you need data persistence** (storing cached data after a reboot).
- If you need **advanced data structures** (e.g., queues, counters).

✅ **When to Use Memcached?**

- If **you just need simple key-value storage**.
- If **high-speed caching** is required without persistence.
## **2. How CDNs Improve Performance**

CDNs (Content Delivery Networks) **store and distribute content from edge servers worldwide** to reduce latency.

### **How CDNs Work:**

1. A user requests a website (e.g., an image or video).
2. Instead of fetching it from the **main server**, the CDN serves it from the **nearest edge server**.
3. This reduces **load time** and **server traffic**.

✅ **Example:**

- **Netflix** uses CDNs to stream videos faster by caching them on global edge servers.
- **Cloudflare, Akamai, AWS CloudFront** are popular CDN providers.
