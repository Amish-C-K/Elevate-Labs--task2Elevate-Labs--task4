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

![setup](https://github.com/Amish-C-K/)

### 🔹 4. Test Rule Using Telnet and Nmap
```bash
telnet localhost 23
nmap -p 23 localhost
```

![setup](https://github.com/Amish-C-K/)

### 🔹 5. Allow SSH (Port 22) and Remove the Block Rule for Port 23
```bash
sudo ufw allow 22
sudo ufw delete deny 23
```

![setup](https://github.com/Amish-C-K/)

## 🧠 Summary
UFW (Uncomplicated Firewall) is a user-friendly frontend for iptables. In this task:

-We enabled the firewall.
-Added a rule to block Telnet traffic (port 23).
-Verified the block using telnet and nmap.
-Allowed SSH traffic (port 22) to ensure secure remote access.
-Finally, cleaned up by removing the test rule.

> This task demonstrated the basic skills required to manage firewall rules and understand how traffic filtering protects the system.

## ✅ Outcome
✔️ Basic UFW management skills
✔️ Understanding of port-based traffic filtering
✔️ Hands-on testing with telnet and nmap
