### Azure Security Services
---

#### 1. Microsoft Defender for Cloud:

- Microsoft Defender for Cloud is Azure’s **unified security solution** that helps you:
  - Continuously assess and improve your **security posture** (CSPM).
  - Protect workloads and applications running in the cloud (CWP).
  - Secure **multi-cloud** and **hybrid** environments.

#### Key Concepts

### 1. CSPM (Cloud Security Posture Management)
- Focuses on the **configuration** of cloud resources.
- Ensures resources follow best practices:
  - Are VMs deployed in private networks?
  - Are VNets properly configured?
- Automatically identifies and fixes configuration risks.

### 2. CWP (Cloud Workload Protection)
- Focuses on the **workloads/applications** deployed to the cloud.
- Continuously monitors running apps to:
  - Detect vulnerabilities.
  - Protect against threats and attacks.
 
- Protects resources across **Azure**, **AWS**, and **Google Cloud** along with **On-prem** resources

---

#### 2. JIT (Just in Time Access) :

- The Problem : - When management ports like **RDP (3389)** or **SSH (22)** are left open, they become potential targets for attacks (brute-force, port scanning).  
- Goal: **Reduce the attack surface** by blocking incoming traffic until access is required.
- **JIT VM Access** is a feature of **Microsoft Defender for Cloud** that reduces the attack surface of virtual machines.  
- Instead of keeping management ports (RDP, SSH) open all the time, JIT allows **temporary, time-bound access** only when needed.

- JIT Access Rules :
  - **Specific Ports:** Only the requested management ports (RDP/SSH) are opened.  
  - **IP Restrictions:** Access limited to your specified IP address or range.  
  - **Time-bound:** Access is granted for a **limited period** (e.g., 1 hour). After that, ports are automatically closed again.  

---

#### 3. CSPM vs SIEM / SOAR:


- CSPM – Cloud Security Posture Management : Microsoft Defender for cloud
  - **Focus:** Detects and fixes **cloud misconfigurations** automatically.  
  - **Goal:** Ensure your cloud setup follows **best practices** and **compliance rules**.  
  - **Azure Service:** **Microsoft Defender for Cloud** provides CSPM capabilities.  

- SIEM – Security Information and Event Management  [Sentinel = SIEM + SOAR]
  - **Focus:** **Collects and analyzes log data** from various sources (cloud, on-prem, hybrid).  
  - **Goal:** Identify potential **security threats** from patterns in log data.
  - **Data Storage Options:** **Azure Monitor Log Analytics Workspace** and  **Azure Storage Account** 
  - **Example Sources:** Azure resources, AWS, GCP, on-prem servers, firewalls.  
  
- SOAR – Security Orchestration, Automation, and Response  
  - **Focus:** **Automates and orchestrates** threat responses across systems.  
  - **Goal:** Reduce response time and manual effort with **playbooks**. [We Write **playbooks** to automate and orchestrate responses to threats.] 
  - **Works With:** SIEM tools like Microsoft Sentinel.
 
---

#### 4. Azure Key Vault:

- A **secure, central place** to store and access **secrets, keys, and certificates** used by cloud apps and services which helps you **protect sensitive information** like API keys, passwords, and cryptographic keys.
- Provides **access control** and **audit logging** for all secrets.
-  What Can You Store : Keys (Generate a keypair ), Secrets, Certificates

---

#### 5. Zero Trust:

- Core Principles of Zero Trust
  
| **Principle**            | **Meaning**                                                                                                   |
|--------------------------|---------------------------------------------------------------------------------------------------------------|
| **Verify Explicitly**     | Use all available signals to validate every access request — identity, device, location, time, application, and data sensitivity. |
| **Use Least Privilege Access** | Grant users and apps only the minimal permissions required, and only for as long as necessary.                          |
| **Assume Breach**         | Design systems as if an attacker is already inside; implement defense-in-depth and segmentation to limit lateral movement. |

- Best Practices :
  - **Apply Zero Trust everywhere**: Users, devices, apps, APIs, microservices, VMs, workloads.  
  - **Encrypt all communications** (even within internal networks).  
  - **Continuously monitor and log** activity to detect anomalies fast.  
  - **Regularly update and patch** devices and applications.  
  - **Automate threat detection and response** using tools like Microsoft Sentinel or Defender for Cloud.

---

