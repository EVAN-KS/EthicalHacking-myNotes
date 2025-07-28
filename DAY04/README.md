# 📘 Ethical Hacking Notes: Key Concepts, Tools, and Networking Basics

## 📡 What is a Network?

A **network** is a collection of interconnected devices (such as computers, servers, routers) that communicate with each other to share data and resources.

- Enables communication via protocols like TCP/IP
- Can be **wired (LAN)** or **wireless (Wi-Fi)**
- Example: Internet is the largest network

---

## 🧠 What is a Summit?

A **Summit** in the cybersecurity world refers to a professional conference or gathering where experts share knowledge, tools, and trends.

### Common Features:
- Expert talks and presentations
- Hands-on workshops
- Live hacking demos
- Capture The Flag (CTF) competitions
- Networking opportunities with ethical hackers and industry leaders

---

## 🔐 What is a MAC ID?

- **MAC (Media Access Control) ID** is a **unique identifier** assigned to a network interface card (NIC).
- Format: `00:1A:2B:3C:4D:5E`
- Used to identify a device within a local network
- It operates at the **Data Link Layer (Layer 2)** of the OSI model

---

## 🌐 What is an IP Address?

An **IP (Internet Protocol) address** is a unique address used to identify a device on a network.

- Two versions:
  - IPv4: `192.168.1.1`
  - IPv6: `2001:0db8:85a3::8a2e:0370:7334`
- Used for communication and routing in a network
- Can be **static** (fixed) or **dynamic** (changes over time)

---

## 📡 TCP vs UDP

| Protocol | Description                              | Type         | Reliability |
|----------|------------------------------------------|--------------|-------------|
| TCP      | Transmission Control Protocol            | Connection-based | Reliable    |
| UDP      | User Datagram Protocol                   | Connectionless   | Unreliable  |

### Key Differences:
- **TCP** ensures data delivery using handshakes and acknowledgments.
- **UDP** is faster but doesn't guarantee delivery.

---

## 📢 What is Broadcast?

- **Broadcasting** is sending a data packet to **all devices** in a network segment.
- Typically used for:
  - ARP requests
  - Network discovery
- Happens at **Layer 2 (Data Link)** and **Layer 3 (Network)**

---

## 🔄 NAT – Network Address Translation

**NAT** translates **private IP addresses** to **public IP addresses** and vice versa.

### Types of NAT:
- Static NAT
- Dynamic NAT
- PAT (Port Address Translation)

**Use Case:** Allows multiple devices on a private network to access the internet using a single public IP.

---

## 🔁 Port Forwarding

**Port forwarding** redirects traffic from one IP/port combo to another.

- Used to access internal network services from outside
- Common in home routers for hosting game servers, web servers, etc.
- Example: Forwarding port 80 to an internal web server


# 🧩 Subnetting (Subnet)

Subnetting is the process of dividing a large IP network into smaller, more manageable subnetworks (subnets). It improves routing efficiency, enhances network security, and helps organize IP address allocation.

---

## 📌 What is a Subnet?

A **subnet** (short for *subnetwork*) is a logical subdivision of an IP network.

### Key Characteristics:
- Organizes IP addresses into manageable blocks  
- Enhances **network performance**, **security**, and **control**  
- Limits broadcast traffic within subnet boundaries  

Each subnet contains:
- **Network Address**
- **Broadcast Address**
- **Range of Usable Host IPs**

---

## 🧮 Example of a Subnet:

- **CIDR Notation:** `192.168.1.0/24`  
- **Subnet Mask:** `255.255.255.0`  
- **Usable IPs:** `192.168.1.1` to `192.168.1.254`  
- **Broadcast Address:** `192.168.1.255`  
- **Total Hosts:** 254 usable IPs  

---

## 🔐 Why Subnet?

- ✅ Reduces overall **network traffic**  
- ✅ Segments departments or functional areas  
- ✅ Improves **routing performance**  
- ✅ Enables implementation of **VLANs** (Virtual LANs)  
- ✅ Adds an extra layer of **security and isolation**

---



## 🧪 Nmap Command (Advanced Port Scanning)

### Command:
```bash
nmap -T4 -A -sV -O -oN output.txt --script default -vv -p 1-1000 -sS -sT target.com
🔹 Flag Breakdown:
Flag	Description
-T4	Timing template for faster execution
-A	Enables OS detection, version detection, script scanning, and traceroute
-sV	Detects service versions
-O	Attempts OS detection
-oN output.txt	Saves the output to a file in normal format
--script default	Runs default NSE (Nmap Scripting Engine) scripts
-vv	Very verbose output
-p 1-1000	Scans ports 1 to 1000
-sS	Stealth SYN scan
-sT	TCP Connect scan (used if SYN not permitted)




