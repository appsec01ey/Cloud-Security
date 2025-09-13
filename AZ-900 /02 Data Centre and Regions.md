
### Data Centers:
- Org has multiple servers running diff applications ; all these servers needs to be secured and managed
- Thus, we have data centers were all this servers are placed together

### Regions and Zones:

- ### Challenges:
1. **High Latency**:
   - Users from far regions (e.g., Sydney, Mumbai, New York) experience **slow access** to the application.
   - Caused by **longer physical distance** = higher latency.

2. **Low Availability**:
   - If the **only data center** crashes, the application becomes **unavailable**.
  
## Solution 1: Add Another Data Center in the Same Region (London)

### What Gets Solved:
- **Availability improves**: If one data center crashes, the other takes over.

### Still Unsolved:
- **High latency remains** for users in distant locations.
- **Single region dependency**: If the entire London region fails, the app goes down

## Solution 2: Add Another Region (e.g., Mumbai)

- Now there are two regions: **London** and **Mumbai**.
- Each region contains **two data centers**.

### What Gets Solved:
1. **Improved Latency**:
   - Users closer to Mumbai get faster access.
   - You can fully solve this by deploying in **multiple global regions** (e.g., Sydney, New York, Africa).

2. **High Availability**:
   - If an entire region (e.g., London) goes down, the application is still available from another region (e.g., Mumbai).

---
