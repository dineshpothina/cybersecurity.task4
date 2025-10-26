# cybersecurity.task4

# 🧱 **Windows Firewall Configuration & Port Filtering**

### Overview

This project demonstrates practical firewall management on **Windows 10** using **Windows Defender Firewall with Advanced Security**.
It focuses on how administrators can control network traffic by **creating, testing, and managing rules** that block or allow communication through specific ports.

By implementing and testing a block rule on **port 23 (Telnet)**, this project highlights the critical role of firewall policies in **network defense and secure system configuration**.

---

## 🎯 **Objectives**

* Understand the **function and structure** of Windows Firewall.
* Learn to **create, apply, and test** firewall rules.
* Gain hands-on experience in **blocking and verifying traffic** on selected ports.
* Explore **inbound/outbound rules** and how they affect connectivity.
* Build a foundational skill set for **network traffic filtering** and **endpoint protection**.

---

## ⚙️ **Tools & Environment**

| Component                | Details                                                  |
| ------------------------ | -------------------------------------------------------- |
| **Operating System**     | Windows 10                                               |
| **Firewall Utility**     | Windows Defender Firewall (Advanced Security)            |
| **Protocol**             | TCP                                                      |
| **Port Tested**          | 23 (Telnet – insecure protocol)                          |
| **Verification Command** | `Test-NetConnection -ComputerName localhost -Port 23`    |
| **Result**               | `TcpTestSucceeded : False` → ✅ Port Blocked Successfully |

---

## 🧩 **Step-by-Step Process**

### 🧱 Step 1 — Open Firewall Settings

Opened the **Windows Defender Firewall with Advanced Security** panel using:

```
control firewall.cpl
```

→ Clicked **Advanced Settings** to access inbound and outbound rule management.

📸 *Screenshot:*
![Inbound Rules Overview](Screenshot%20\(3\).png)

---

### 🔍 Step 2 — Review Existing Rules

Examined the existing **Inbound Rules** to understand how applications like Microsoft Teams, Windows services, and other system components communicate over the network.

---

### 🚫 Step 3 — Create a Custom Block Rule

Created a new **Inbound Rule** to **block TCP traffic on port 23**, which is typically used by the unencrypted **Telnet protocol**.

Steps:

1. Click **New Rule → Port → TCP**
2. Specify **Port 23**
3. Select **Block the Connection**
4. Apply to all profiles (Domain, Private, Public)
5. Name it **Block Telnet Port 23**

✅ This rule ensures no incoming Telnet requests are allowed on the host.


---

### 🧪 Step 4 — Verify Firewall Block

Used **PowerShell** to verify that the firewall successfully blocked port 23 connections.

Command:

```powershell
Test-NetConnection -ComputerName localhost -Port 23
```

Output:

```
WARNING: TCP connect to (::1 : 23) failed
TcpTestSucceeded : False
```

This confirms the connection attempt was blocked by the firewall.


---

### 🧹 Step 5 — Cleanup

Removed the test rule to restore normal operation:

* Opened **Inbound Rules**
* Located **Block Telnet Port 23**
* Right-clicked → **Delete**

This ensures system connectivity is back to default while retaining security learning records.

---

## 📊 **Summary of Actions**

| Step | Action                          | Outcome                                       |
| ---- | ------------------------------- | --------------------------------------------- |
| 1    | Accessed Firewall settings      | Successfully launched advanced firewall panel |
| 2    | Reviewed existing inbound rules | Understood allowed and blocked services       |
| 3    | Created Port 23 block rule      | Restricted Telnet connections                 |
| 4    | Verified using PowerShell       | Confirmed the rule worked                     |
| 5    | Deleted test rule               | Restored firewall to default configuration    |

---

## 🔐 **Key Learnings**

* **Inbound vs Outbound Rules:**
  Inbound controls traffic *coming into* your PC; outbound controls *leaving* traffic.
* **Blocking Insecure Protocols:**
  Telnet (port 23) sends data in plain text — blocking it prevents credential theft.
* **Testing Rules:**
  Always verify firewall rules with command-line tools like `Test-NetConnection`.
* **Firewall Importance:**
  Acts as a first line of defense, filtering malicious or unauthorized network packets.

---

## 🧠 **Security Insights**

| Concept                               | Explanation                                                    |
| ------------------------------------- | -------------------------------------------------------------- |
| **Stateful Firewall**                 | Tracks connection states; intelligent filtering decisions.     |
| **Stateless Firewall**                | Filters packets individually, without remembering connections. |
| **NAT (Network Address Translation)** | Hides internal IPs from external access.                       |
| **Common Mistakes**                   | Leaving unnecessary ports open or duplicating rules.           |
| **Best Practice**                     | Regularly audit and document all custom rules.                 |

---

## 🧾 **Repository Contents**

| File                               | Description                                |
| ---------------------------------- | ------------------------------------------ |
| `Screenshot (3).png`               | Firewall Advanced Settings & Inbound Rules |
| `Screenshot (5).png`               | Custom Rule Configuration                  |
| `Screenshot 2025-10-27 015153.png` | PowerShell test result                     |
| `README.md`                        | Full documentation of setup and learning   |

---

## 🚀 **Conclusion**

This hands-on exercise demonstrates how a simple rule can **effectively block insecure services** and strengthen endpoint security.
Understanding and applying firewall configurations is an essential step toward becoming a skilled cybersecurity professional.
