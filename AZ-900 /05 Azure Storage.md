### Azure Storage Overview

#### 📌 Core Storage Types

| Storage Type   | What It Is | When to Use |
|---------------|------------|-------------|
| **Block Storage** | Raw storage blocks (like disks). Each block storage device is typically attached to one VM at a time. | VM disks, databases, transactional workloads. |
| **File Storage**  | Shared file system accessed over network (SMB). Multiple VMs/computers can mount the same share. | Enterprise file shares, lift-and-shift file servers. |
| **Object Storage** (Blobs) | Stores data as objects (binary/text) with metadata. Accessed via REST APIs; no mounting required. | Upload/download of files, media, backups, archives. |

---

### Azure Storage Services

- **Azure Disks** → Block storage for VMs.
- **Azure Files** → File shares for cloud/on-prem.
- **Azure Blobs** → Object storage for text & binary data.
- **Azure Queues** → Message queuing to decouple producer/consumer apps.
- **Azure Tables** → Basic NoSQL key–value storage (but Cosmos DB recommended for richer features).

> **Prerequisite:** You need to create a **Storage Account** first to use these services.

---

### Durability & Redundancy

Azure Storage always maintains **at least 3 copies** of your data.  
You can choose higher redundancy options based on availability needs:

| Option | Copies & Location | Notes |
|--------|-------------------|-------|
| **LRS** (Locally Redundant) | 3 synchronous copies in **one data center**. | Least expensive, least availability. |
| **ZRS** (Zone Redundant)    | 3 synchronous copies across **3 AZs** in primary region. | Survives AZ failure. |
| **GRS** (Geo Redundant)     | LRS in primary region **+ asynchronous copy** to secondary region (with 3 more copies). | Survives region failure. |
| **GZRS** (Geo Zone Redundant) | ZRS in primary region **+ asynchronous copy** to secondary region (with 3 LRS copies). | Highest availability, most expensive. |

---

#### Azure Storage – Read-Access Redundancy Options

In normal **Geo-Redundant Storage (GRS)** or **Geo-Zone-Redundant Storage (GZRS)**, data is replicated to a secondary region, but **you cannot read or write from the secondary region** until a failover happens.

Sometimes, you may need **read access** to the secondary region **at all times** (e.g., global apps wanting to serve data closer to users).  
That’s where **Read-Access Redundancy Options** come in.

#### Options

| Option | Based On | Read Access to Secondary? | Write Access to Secondary? |
|--------|----------|---------------------------|---------------------------|
| **RA-GRS** (Read-Access Geo-Redundant Storage) | GRS | ✅ Yes | ❌ No |
| **RA-GZRS** (Read-Access Geo-Zone-Redundant Storage) | GZRS | ✅ Yes | ❌ No |


#### URL Pattern to Access Secondary Region

If primary blob endpoint is: **https://myaccount.blob.core.windows.net** then Secondary endpoint will be: **https://myaccount-secondary.blob.core.windows.net**

---

### Azure Region Pairs

- Azure organizes its global datacenters into **regions** (e.g., East US, West Europe). Each region is linked with another nearby region to form a **region pair**
- Pairs are designed to:
  - Provide **disaster recovery** and **geo-redundancy**.
  - Minimize downtime during updates (Azure schedules updates so that only one region of a pair is updated at a time).

--- 

| Disk Type      | Type                  | Use Case                                                                 |
|----------------|---------------------|-------------------------------------------------------------------------|
| Standard HDD   | Hard Disk Drive      | Backup, non-critical, infrequently accessed data                        |
| Standard SSD   | Solid State Drive    | Web servers, lightly used enterprise apps, dev/test environments        |
| Premium SSD    | High-performance SSD | Production or performance-sensitive workloads                           |
| Ultra Disk     | Ultra-high-performance SSD | IO-intensive workloads, heavy databases (SAP HANA, SQL, Oracle), transaction-heavy apps |

---

- Resources : https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction 
