### Azure Storage Overview

#### 📌 Core Storage Types

| Storage Type   | What It Is | When to Use |
|---------------|------------|-------------|
| **Block Storage** | Raw storage blocks (like disks). Each block storage device is typically attached to one VM at a time. | VM disks, databases, transactional workloads. |
| **File Storage**  | Shared file system accessed over network (SMB). Multiple VMs/computers can mount the same share. | Enterprise file shares, lift-and-shift file servers. |
| **Object Storage** (Blobs) | Stores data as objects (binary/text) with metadata. Accessed via REST APIs; no mounting required. | Upload/download of files, media, backups, archives. |

---

## ☁️ Azure Storage Services

- **Azure Disks** → Block storage for VMs.
- **Azure Files** → File shares for cloud/on-prem.
- **Azure Blobs** → Object storage for text & binary data.
- **Azure Queues** → Message queuing to decouple producer/consumer apps.
- **Azure Tables** → Basic NoSQL key–value storage (but Cosmos DB recommended for richer features).

> **Prerequisite:** You need to create a **Storage Account** first to use these services.

---

## 🛡️ Durability & Redundancy

Azure Storage always maintains **at least 3 copies** of your data.  
You can choose higher redundancy options based on availability needs:

| Option | Copies & Location | Notes |
|--------|-------------------|-------|
| **LRS** (Locally Redundant) | 3 synchronous copies in **one data center**. | Least expensive, least availability. |
| **ZRS** (Zone Redundant)    | 3 synchronous copies across **3 AZs** in primary region. | Survives AZ failure. |
| **GRS** (Geo Redundant)     | LRS in primary region **+ asynchronous copy** to secondary region (with 3 more copies). | Survives region failure. |
| **GZRS** (Geo Zone Redundant) | ZRS in primary region **+ asynchronous copy** to secondary region (with 3 LRS copies). | Highest availability, most expensive. |

---


