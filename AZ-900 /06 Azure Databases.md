### Azure DB

### Database Challenges and Solutions

#### Scenario
- Database deployed in a data center in London.
- Application connects to this database.

#### Initial Challenges
1. **Database Downtime**  
   - If the data center crashes or server/storage fails, the database is unavailable.
2. **Data Loss**  
   - If the database crashes, data could be permanently lost.
---

#### Step 1: Take Snapshots
- **Action:** Automate database snapshots every hour to another data center.
- **Impact on Challenges:**
  - **Challenge 1:** Not solved – database still down if primary data center fails.
  - **Challenge 2:** Partially solved – you can restore from the latest snapshot, but up to 1 hour of data may be lost.
  - **Challenge 3 (New):** Database performance slows during snapshot creation.
- **Problem:** Data loss window exists (snapshot frequency) and performance impact remains.

---

#### Step 2: Add Transaction Logs
- **Action:** Record transaction logs and copy them to the second data center.
- **Impact on Challenges:**
  - **Challenge 1:** Still not solved – database down if primary data center fails.
  - **Challenge 2:** Solved – restore database from snapshot and apply transaction logs to recover all changes.
  - **Challenge 3:** Database still slows during snapshot creation.
- **Benefit:** Reduces data loss window to near zero, but performance issue persists.

---

#### Step 3: Introduce Standby Database with Replication
- **Action:**  
  - Add a standby database in the second data center.  
  - Enable synchronous replication: every change in master is immediately reflected in standby.  
  - Take snapshots from the standby database, not the master.
- **Impact on Challenges:**
  - **Challenge 1:** Solved – standby database can take over if primary fails.
  - **Challenge 2:** Solved – no data loss due to real-time replication.
  - **Challenge 3:** Solved – snapshots from standby prevent performance impact on master database.

---

#### Database Availability & Durability 

#### Availability
- Use **multiple standby databases** to serve users if primary fails.  
- Distribute across **zones and regions** for higher availability.

#### Durability
- Keep **multiple copies** of data (standbys, snapshots, transaction logs, replicas).  
- Store across **zones and regions**.  
- Challenge: Maintaining **data consistency** across copies.

---

#### RTO and RPO (Database Recovery Metrics)

#### Definitions
- **RPO (Recovery Point Objective):** Maximum acceptable period of data loss.  
- **RTO (Recovery Time Objective):** Maximum acceptable downtime to recover.  
- Trade-off: Lower RTO/RPO → higher cost; design depends on criticality of data.

#### Example
- Your are running an app on VM storing data on a persistent storage and taking snapshots every 48 hours and if VM crahes you can bring it back up from snapshot in 45 mins.  
- WHta is the RTO and RPO when VM crash occurs:  
  - **RTO:** 45 minutes (time to restore from snapshot)  
  - **RPO:** 48 hours (data lost since last snapshot)
 
---

#### Examples of Azure Managed Databases
- **Azure SQL Database** (PaaS SQL Server)
- **Azure Database for MySQL**
- **Azure Database for PostgreSQL**
- **Azure Database for MariaDB**
- **Azure Cosmos DB** (globally distributed NoSQL)
- **Azure Managed Instance for Apache Cassandra**

--- 

## Tasks : We created a Mysql db and a NoSQL (Mongo DB) DB on azure

#### Azure Cache for Redis
- A **fully managed, in-memory data store** based on the open-source Redis engine.
- Provided as a PaaS service by Microsoft Azure.
- Used to **store and retrieve data from memory** for ultra-fast performance.
- Use Case:
   - **Caching** frequently accessed data (DB queries, session state, API results).
   - **Real-time apps** (gaming, chat, leaderboards).
   - **Rate limiting** or token storage for APIs
