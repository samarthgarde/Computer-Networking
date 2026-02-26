# Computer-Networking 

### ✅ How internet works?
#### What Happens When You Open a Website
1. You Type a Website Name
- ```www.google.com```
But computers do not understand names, they understand IP addresses
2. So the system needs to find the IP first.
3. DNS Translates the name
4. Your Request Travels Through the Internet
5. Data Travels in Small Packets.Internet breaks data into small packets.
6. Server Sends the Website Back
**One Line Flow**
  
```Browser → DNS → ISP → Internet Routers → Server → Response Back → Browser Shows Website```

---

### Physical Cables (Wired Communication
#### Ethernet cable:
This is the most common internet cable in homes and offices.

Used in:

- LAN networks
- Office networking

Speed:

-Up to 1 Gbps (Cat5e)
- 10 Gbps (Cat6/7)
  


### ✅ IP Address

- A unique identifier for each device on a network.
- **IPv4**: e.g., `192.168.1.1`
- **IPv6**: e.g., `2001:0db8:85a3::8a2e:0370:7334`
- Can be **static** (fixed) or **dynamic** (changes via DHCP).

---

### ✅ MAC Address
- A hardware address burned into your network interface.
- Format: `00:1A:2B:3C:4D:5E`
- Used in Layer 2 (Data Link) for LAN communication.

---

### ✅ Port Numbers
- a communication endpoint used by a specific service on a computer.
- Example:
  - `21` → FTP
  - `22` → SSH
  - `80` → HTTP
  - `8080` → Alternate HTTP
  - `53` → DNS
  - `443` → HTTPS
  - `1443`→ Microsoft SQL Serve
  - `3306`→ MySQL/MariaDB
  - `5432` → PostgreSQL
  -  
- Format: `IP:Port` (e.g., `192.168.0.1:22`)

---

### ✅ Protocol
- A set of rules for communication.
- Common protocols:
  - **TCP** – Reliable, connection-oriented.
  - **UDP** – Faster, connectionless.
  - **ICMP** – Used by `ping`.

---

### ✅ Public vs Private IP

| Type        | Range                                | Used For                  |
|-------------|---------------------------------------|---------------------------|
| Private IP  | `10.0.0.0 – 10.255.255.255`<br>`172.16.0.0 – 172.31.255.255`<br>`192.168.0.0 – 192.168.255.255` | Internal LAN/Subnets      |
| Public IP   | All other addresses                   | Internet-accessible hosts |


---

### ✅ Tools to Check Networking in Linux

```bash
ip a             # Show IP addresses
ip r             # Show routing table
ping 8.8.8.8     # Check connectivity
nslookup google.com  # DNS lookup
netstat -tulnp   # Show listening ports and services
```
---

## OSI Model - 7 Layers

| Layer | Layer Name   | Function                                 | Example Protocols                                | Devices Used           | Real-life Example                       |
|-------|--------------|------------------------------------------|-------------------------------------------------|------------------------|------------------------------------------|
| 7     | Application  | Interfaces with user applications        | HTTP, HTTPS, FTP, DNS, SMTP, Telnet, DHCP       | Computer, Browser      | Typing a URL in Chrome                   |
| 6     | Presentation | Data translation, encryption, compression| SSL/TLS, JPEG, MP3, MPEG, ASCII                 | Encryption Software    | Securing data via HTTPS                  |
| 5     | Session      | Establishes, manages, and terminates sessions | NetBIOS, PPTP, RPC, SIP                       | API, OS session manager | Keeping a video call connected           |
| 4     | Transport    | Reliable delivery, error checking, flow control | TCP, UDP, SCTP                                | Firewall, OS kernel    | Streaming a YouTube video                |
| 3     | Network      | Logical addressing and routing           | IP, ICMP, IGMP, IPSec, ARP                     | Router                 | Data travels across internet hops        |
| 2     | Data Link    | MAC addressing, framing, error detection | Ethernet, PPP, ARP, Frame Relay, HDLC          | Switch, NIC            | LAN connection via Ethernet              |
| 1     | Physical     | Transmits raw bits via physical medium (cables, signals, etc.) | Ethernet Cables, Wi-Fi (802.11), Bluetooth | Hub, Cable, Fiber      | Sending bits through copper wire or wireless signal |

---

### 🔹TCP/IP Model – 4 Layers

| Layer | Name              | Corresponds to OSI Layers          | Protocols                     |
|-------|-------------------|------------------------------------|-------------------------------|
| 4     | Application       | OSI Layers 5–7                     | HTTP, DNS, SMTP, SSH          |
| 3     | Transport         | OSI Layer 4                        | TCP, UDP                      |
| 2     | Internet          | OSI Layer 3                        | IP, ICMP, ARP                 |
| 1     | Network Access    | OSI Layers 1–2                     | Ethernet, Wi-Fi               |
---

### 🔹OSI vs TCP/IP Comparison

| OSI Model (7 Layers) | TCP/IP Model (4 Layers) |
|----------------------|-------------------------|
| Application          | Application             |
| Presentation         | Application             |
| Session              | Application             |
| Transport            | Transport               |
| Network              | Internet                |
| Data Link            | Network Access          |
| Physical             | Network Access          |

---

### 🔹DevOps Use Cases

| Tool       | OSI Layer | Purpose                              |
|------------|-----------|--------------------------------------|
| `ping`     | Layer 3   | Check host reachability              |
| `traceroute` | Layer 3 | Show packet route across networks    |
| `curl`     | Layer 7   | Fetch data from HTTP APIs            |
| `telnet`   | Layer 4   | Test TCP ports                       |
| `wireshark`| All       | Packet-level analysis                |
| `netstat`  | Layer 4   | Show open ports and connections      |

---

## Subnetting & CIDR

Subnetting and CIDR are essential for organizing and managing IP addresses within networks — especially in cloud infrastructure and container orchestration.

---
### 🔹 What is Subnetting?

**Subnetting** is the process of dividing a large IP network into smaller, more manageable subnetworks (subnets). It helps:
- Improve network performance
- Enhance security and isolation
- Optimize IP address usage

---

### � IP Address Structure

### IPv4 Format:
- 32-bit address written as 4 octets (e.g., `192.168.10.15`)
- Divided into **Network** and **Host** portions

---

### 🔹What is CIDR?

**CIDR** = Classless Inter-Domain Routing
- Notation: `IP_address/prefix_length`
- Example: `192.168.1.0/24`

### Prefix Length:
- `/24` → First 24 bits are the network part
- Remaining 8 bits are for hosts

---

### 🔹Subnet Mask Table (Common Prefixes)

| CIDR     | Subnet Mask        | Hosts per Subnet |
|----------|--------------------|------------------|
| /30      | 255.255.255.252    | 2 usable         |
| /29      | 255.255.255.248    | 6 usable         |
| /28      | 255.255.255.240    | 14 usable        |
| /27      | 255.255.255.224    | 30 usable        |
| /26      | 255.255.255.192    | 62 usable        |
| /24      | 255.255.255.0      | 254 usable       |
| /16      | 255.255.0.0        | 65,534 usable    |

---

### 🔹Example: Subnetting a `/24` Network

- Given: `192.168.1.0/24`
- Want: 4 subnets
- Solution: Use `/26` (2 extra bits)

### Resulting Subnets:
- `192.168.1.0/26` → Hosts: `.1` to `.62`
- `192.168.1.64/26` → Hosts: `.65` to `.126`
- `192.168.1.128/26` → Hosts: `.129` to `.190`
- `192.168.1.192/26` → Hosts: `.193` to `.254`

---

### 🔹How to Calculate Subnets (Manual Steps)
1. Convert subnet mask to binary
2. Count number of host bits
3. 2ⁿ - 2 = usable hosts
4. Increment subnet base by block size
   - Block size = `256 - subnet mask last octet`

---

### 🔹Use Cases in DevOps

| Platform | Use Case                               |
|----------|----------------------------------------|
| AWS      | Dividing VPC into public/private subnets |
| Kubernetes | Allocating Pod and Service CIDRs       |
| Docker   | Custom bridge networks for containers  |

---

### 🔹Helpful Tools

- [Subnet Calculator – ipcalc](https://jodies.de/ipcalc)
- `ipcalc` (CLI):
```bash
sudo apt install ipcalc
ipcalc 192.168.1.0/25
```
---

## DNS (Domain Name System)

DNS (Domain Name System) is a critical component of networking.

### 🔹What is DNS?

DNS works like the **"phonebook of the internet"**.
Instead of remembering IP addresses, users type domain names.

---

### 🔹How DNS Works

When you type a website like `example.com`, the process looks like this:

1. **Browser Cache**: Checks local DNS cache
2. **OS Resolver**: OS checks `/etc/hosts` (Linux/Mac) or local DNS cache
3. **DNS Server**: Queries recursive DNS resolver (usually provided by ISP or Google)
4. **Root Server**: Points to TLD servers (.com, .org, etc.)
5. **TLD Server**: Points to authoritative DNS server for domain
6. **Authoritative Server**: Returns final IP for domain

---
### 🔹DNS Record Types

| Record Type | Purpose                                | Example                        |
|-------------|-----------------------------------------|--------------------------------|
| A           | Maps domain to IPv4 address             | `example.com → 93.184.216.34`  |
| AAAA        | Maps domain to IPv6 address             | `example.com → ::1`            |
| CNAME       | Alias one domain to another             | `www.example.com → example.com`|
| MX          | Mail server for domain                  | Mail goes to `mail.example.com`|
| TXT         | Text data, often for verification (SPF, DKIM) | Google site verification |
| NS          | Name servers for the domain             | `ns1.example.com`              |

---

### 🔹DevOps Use Cases for DNS

| Use Case                        | Description                                     |
|----------------------------------|-------------------------------------------------|
| Load Balancing (Round-robin DNS)| Distribute traffic across multiple IPs          |
| Custom Domains for Apps         | Assign `myapp.company.com` to app service       |
| Service Discovery               | Internal DNS resolves service names             |
| SSL Certificates                | TXT records used for domain verification        |

---
### 🔹DNS Tools (Linux CLI)

### 🧪 `dig` – DNS Query Tool
```bash
dig example.com
dig +short google.com
```
---

## Routing & switching

Routing and Switching are core components of network communication.

### 🔹What is Switching?

**Switching** occurs at **Layer 2 (Data Link Layer)** of the OSI model.
It connects devices **within the same network (LAN)**.

### ✅ Features:
- Uses **MAC addresses** to forward frames.
- Switches learn the MAC addresses of connected devices.
- Reduces unnecessary data flooding (unlike hubs).

### 🛠️Real Example:
- In a local network, a switch connects computers, printers, and routers.
- Each device gets a dedicated path to communicate.

---

### 🔹What is Routing?

**Routing** occurs at **Layer 3 (Network Layer)** of the OSI model.
It connects **multiple networks together** and routes data between them.

### ✅ Features:
- Uses **IP addresses** to route packets.
- Routers maintain **routing tables**.
- Can be **static** or **dynamic** (using routing protocols like OSPF, BGP).

###  Real Example:
- A router connects your home network to the internet.
- In cloud (AWS/GCP), **route tables** define how traffic flows inside VPCs.

### 🔹Key Differences

| Feature       | Switching                          | Routing                               |
|---------------|------------------------------------|----------------------------------------|
| OSI Layer     | Layer 2 (Data Link)                | Layer 3 (Network)                      |
| Address Used  | MAC Address                        | IP Address                             |
| Purpose       | Connect devices in same network    | Connect different networks             |
| Device Used   | Switch                             | Router                                 |
| Protocol      | Ethernet                           | IP (Routing Protocols: BGP, OSPF)      |

---

### 🔹Linux Routing Basics

### 🧪 View Routing Table
```bash
ip route show
```












