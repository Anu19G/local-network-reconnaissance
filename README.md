#  Local Network Reconnaissance

##  Objective

This project focuses on scanning a local network for open TCP ports using multiple tools to identify potential risks and gain insight into basic network security exposure**.

---

## Tools Used

- **Nmap** – TCP SYN scan for port discovery and host detection  
- **Wireshark** – Packet capture and protocol-level analysis  
- **Netcat** – Manual probing and banner grabbing  
- **Masscan** – High-speed asynchronous port scanner  

---

##  Network Setup

- **Local IP Address:** `192.168.221.128`  
- **Target Subnet:** `192.168.221.0/24`  

---

##  Scan Results Summary

### Nmap Scan

Command:
nmap -sS 192.168.221.0/24


**Findings:**

| IP Address    	| Port 	| Service	| Notes |
|------------------|----------|------------|-------|
| 192.168.221.1 	| 7070/tcp | realserver | May expose internal services if misconfigured |
| 192.168.221.2 	| 53/tcp   | DNS    	| Vulnerable to DNS tunneling or DoS attacks |
| 192.168.221.254   | —    	| —      	| All ports filtered (likely behind a firewall) |
| 192.168.221.128   | —    	| —      	| All ports closed – secure |

---

### Tool-Specific Observations

#### Wireshark
- Captured live packets during Nmap scan
- Applied SYN scan filter:
tcp.flags.syn == 1 and tcp.flags.ack == 0


#### Netcat
- Command used:
nc -v 192.168.221.1 7070

- Result: Port open, no banner received (may require specific input)

#### Masscan
- Command used:
sudo masscan 192.168.221.0/24 -p22,53,80,443,7070 --rate=1000

- Results:
- Port 53 open on `192.168.221.2`
- Port 7070 not detected (likely filtered or rate-limited)

---

## Repository Contents

- `local-network-reconnaissance.docx` – Complete step-by-step task documentation  
- `.pcapng` file – Wireshark capture of scan session (optional, if included)

---

## Concepts Covered

- Port Scanning Techniques  
- TCP SYN Scanning  
- Banner Grabbing  
- Packet Capture & Protocol Filtering  
- Subnet and IP Range Scanning  
- Basic Risk Analysis in Network Security  

---

## Conclusion

This reconnaissance exercise provided practical exposure to multiple scanning tools and techniques used in cybersecurity. It emphasized how different tools can offer unique insights into a network's structure, services, and potential vulnerabilities.


