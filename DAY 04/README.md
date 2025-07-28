# 🛡️ Ethical Hacking Notes – Networking Basics & Nmap

---

## 🔸 1. What is a Network?

A **network** is a system where multiple computers or devices are connected to communicate, share resources, and transfer data.

- Devices are connected via cables, wireless signals, or both.
- Common types of networks:
  - **LAN (Local Area Network):** Covers a small area (home, school, office).
  - **WAN (Wide Area Network):** Covers a large area (cities, countries, internet).

---

## 🔸 2. What is a Subnet?

A **subnet** (short for subnetwork) is a smaller section of a larger network.

- Used to **organize**, **secure**, and **manage** networks efficiently.
- Devices in the same subnet can communicate directly.
- Example: `192.168.1.0/24` includes IPs from `192.168.1.1` to `192.168.1.254`.

---

## 🔸 3. MAC Address (Media Access Control Address)

A **MAC address** is a unique identifier assigned to a device’s network interface.

- Used for communication at the **Data Link Layer (Layer 2)**.
- Format: `00:1A:2B:3C:4D:5E`
- Assigned by the manufacturer and usually fixed.

---

## 🔸 4. IP Address (Internet Protocol Address)

An **IP address** identifies a device on a network.

- Used for routing data across networks (Layer 3 – Network Layer).
- Two main types:
  - **IPv4:** Example – `192.168.0.1`
  - **IPv6:** Example – `2001:0db8:85a3::8a2e:0370:7334`

---

## 🔸 5. TCP vs UDP

| Feature     | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
|------------|--------------------------------------|------------------------------|
| Type       | Connection-oriented                  | Connectionless               |
| Reliability| Reliable (data retransmission)       | Unreliable (no retransmit)   |
| Speed      | Slower (due to error checking)       | Faster                       |
| Use Cases  | Web browsing, file transfers         | Video streaming, VoIP, DNS   |

---

## 🔸 6. What is Broadcast?

**Broadcasting** means sending data from one device to **all** devices in a network segment.

- Used when the destination is unknown (e.g., ARP requests).
- Example: When a device joins a network, it broadcasts to find the gateway.

---

## 🔸 7. NAT – Network Address Translation

**NAT** allows multiple devices on a private network to share one public IP address.

- Converts private IPs (like `192.168.0.x`) to a public IP for internet access.
- Improves **security** and **IP address efficiency**.
- Common in routers and firewalls.

---

## 🔸 8. Port Forwarding

**Port forwarding** allows external devices to access services inside a private network.

- Redirects traffic from a specific port on a public IP to an internal device.
- Example: Forwarding port `8080` on your router to `192.168.1.10:80` (web server).
- Used in gaming, hosting, remote desktop access, and more.

---

## 🔸 9. Nmap Command Breakdown

Nmap is a powerful network scanning tool used in ethical hacking for reconnaissance.

### ✅ Example Command:

```bash nmap -T4 -A -sV -O -oN output.txt --script default -vv -p 1-1000 -sS -sT target.com

🔹 Flag Breakdown:
Flag	Description
-T4	Timing template for faster execution
-A	Enables OS detection, version detection, script scanning, and traceroute
-sV	Detects service versions
-O	Attempts OS detection
-oN output.txt	Saves the output in a normal format to a file named output.txt
--script default	Runs default NSE (Nmap Scripting Engine) scripts
-vv	Very verbose; provides additional output detail
-p 1-1000	Scans ports from 1 to 1000
-sS	Stealth SYN scan
-sT	TCP Connect scan (fallback when SYN is not possible)

🔸 What is a Summit?
In cybersecurity and ethical hacking, a Summit refers to a high-level conference or event where professionals, researchers, and hackers convene to:

Discuss cyber threats

Share tools and tactics

Explore emerging trends in digital security

🔹 Key Features of a Cybersecurity Summit:
Expert Talks – Industry experts and researchers present talks on real-world incidents and findings.

Workshops – Hands-on sessions teaching practical ethical hacking tools and techniques.

Live Demos – Demonstrations of vulnerabilities, exploits, and defensive tools.

Networking – Connect with ethical hackers, developers, and cybersecurity leaders.

CTFs (Capture the Flag) – Competitive challenges to test and improve hacking skills.

🔹 Popular Cybersecurity Summits:
Event Name	Description
DEF CON	One of the world's largest and most notable hacker conventions.
Black Hat	A global series of cybersecurity summits with deep technical talks.
OWASP Summit	Focused on web application security and open-source collaboration.
Nullcon	Indian-based conference centered on ethical hacking and research.
