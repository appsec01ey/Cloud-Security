### Azure Security Services

#### Microsoft Defender for Cloud:

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

#### JIT (Just in Time Access) :

- The Problem : - When management ports like **RDP (3389)** or **SSH (22)** are left open, they become potential targets for attacks (brute-force, port scanning).  
- Goal: **Reduce the attack surface** by blocking incoming traffic until access is required.
- **JIT VM Access** is a feature of **Microsoft Defender for Cloud** that reduces the attack surface of virtual machines.  
- Instead of keeping management ports (RDP, SSH) open all the time, JIT allows **temporary, time-bound access** only when needed.

- JIT Access Rules :
  - **Specific Ports:** Only the requested management ports (RDP/SSH) are opened.  
  - **IP Restrictions:** Access limited to your specified IP address or range.  
  - **Time-bound:** Access is granted for a **limited period** (e.g., 1 hour). After that, ports are automatically closed again.  

---

