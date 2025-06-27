# 🔐 Task 4: Setup and Use a Firewall on Linux (Kali) and Windows using UFW and Windows Firewall

# Setup and Use a Firewall on Linux (Kali)

## 🎯 Objective
Configure and test basic firewall rules to allow or block traffic using **UFW (Uncomplicated Firewall)**.

---

## 🧰 Tools Used
- Kali Linux (root user)
- UFW (default firewall)
- Telnet & Nmap for testing

---

## 🛠️ Steps and Commands Used

### 🔹 1. Enable UFW
```bash
ufw status verbose
sudo ufw enable
```

### 🔹 2. Check Status and List Rules
```bash
sudo ufw status numbered
```

### 🔹 3. Block Inbound Traffic on Port 23
```bash
sudo ufw deny 23

sudo ufw status numbered
```

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-1.png)

### 🔹 4. Test Rule Using Telnet and Nmap
```bash
telnet localhost 23
nmap -p 23 localhost
```

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-2.png)

### 🔹 5. Allow SSH (Port 22) and Remove the Block Rule for Port 23
```bash
sudo ufw allow 22
sudo ufw delete deny 23
```

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-3.png)

---
# Setup and Use a Firewall on Windows

## 🎯 Objective
Configure and test basic firewall rules to allow or block traffic using **Windows Defender Firewall**.

---

## 🧰 Tools Used
- Windows 10/11
- Windows Defender Firewall with Advanced Security
- Telnet Client (optional)
- Command Prompt (Admin)

---

## 🛠️ Step-by-Step Process

### ✅ 1. Open Firewall Management Console
- Press `Win + R`, type `wf.msc`, press **Enter**

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-4.png)

### ✅ 2. Block Port 23 (Telnet)
1. In the right-hand pane, click **New Rule**
2. Select **Port** → Click **Next**
3. Choose **TCP** and enter port `23` → **Next**
4. Select **Block the connection** → **Next**
5. Apply to all profiles (Domain, Private, Public) → **Next**
6. Name the rule: `Block Telnet Port 23` → Click **Finish**

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-6.png)

### ✅ 3. Install and Use Telnet to Test Block

#### 🔹 Install Telnet via DISM:
Open Command Prompt as Administrator:
```cmd
dism /online /Enable-Feature /FeatureName:TelnetClient
```

### 🔹 Test Port 23:
```bash
telnet localhost 23
```

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-7.png)

### ✅ 4. Allow SSH Port (22)
1. Open New Rule again
2. Select Port → Next
3. Choose TCP, enter port 22 → Next
4. Select Allow the connection → Next
5. Apply to all profiles → Next
6. Name it: Allow SSH Port 22 → Finish

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-8.png)


### ✅ 5. Remove the Telnet Block Rule
- Go to Inbound Rules
- Right-click on Block Telnet Port 23 → Delete

![setup](https://github.com/Amish-C-K/Elevate-Labs--task4/blob/main/images/t4-10.png)

## 🧠 Summary
UFW (Uncomplicated Firewall) is a user-friendly frontend for iptables. In this task:

- We enabled the firewall.
- Added a rule to block Telnet traffic (port 23).
- Verified the block using telnet and nmap.
- Allowed SSH traffic (port 22) to ensure secure remote access.
- Finally, cleaned up by removing the test rule.

> This task demonstrated the basic skills required to manage firewall rules and understand how traffic filtering protects the system.

Windows Defender Firewall allows administrators to define traffic rules for enhanced security. In this task:

- We blocked port 23 to prevent Telnet access (a known insecure protocol).
- We allowed port 22 for secure SSH communication.
- We validated blocking via Telnet.
- Finally, we removed the test rule to return to the original state.

> This task demonstrates how basic firewall rules can protect a system by filtering unwanted or risky traffic.

## ✅ Outcome
✔️ Basic UFW management skills
✔️ Understanding of port-based traffic filtering
✔️ Hands-on testing with telnet and nmap
✔️ Configured inbound rules
✔️ Cleaned up rules properly
