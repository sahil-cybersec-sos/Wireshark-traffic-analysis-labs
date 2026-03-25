# 🚨 NetSupport RAT Traffic Analysis (Wireshark)

## 📌 Overview

Analyzed a PCAP file to identify an infected host communicating with a known malicious IP (45.131.214.85) over TCP port 443. The goal was to perform network-based threat detection and extract host/user details.

---

## 🧠 Scenario

* SOC detected suspicious traffic from internal network
* Alerts indicated possible NetSupport RAT activity
* PCAP analysis required to identify compromised system

---

## 🌐 Environment

* Network Range: 10.2.28.0/24
* Domain: easyas123.tech
* Domain Controller: 10.2.28.2

---

## 🔍 Investigation Steps

### 1. Identify Infected Host

Used Wireshark filter:

```
ip.addr == 45.131.214.85
```

➡️ Found internal IP communicating with attacker

---

### 2. Extract MAC Address

Filter:

```
arp
```

➡️ Mapped IP to MAC address

---

### 3. Identify Hostname

Filter:

```
nbns || dhcp
```

➡️ Extracted system hostname

---

### 4. Identify User Account

Filter:

```
kerberos.CNameString
```

➡️ Extracted logged-in user

---

### 5. Determine Full Name

➡️ Correlated username pattern with naming convention

---

## 🎯 Findings

* **Infected IP:** 10.2.28.88
* **MAC Address:** 00:19:d1:b2:4d:ad
* **Hostname:** DESKTOP-TEYQ2NR<20>
* **Username:** brolf
* **Full Name:** Brian Rolf

---

## 🛠️ Tools Used

* Wireshark
* Network Traffic Analysis
* Protocol Analysis (ARP, DNS, Kerberos)

---

## 🧠 Skills Demonstrated

* Threat Detection
* Packet Analysis
* Incident Investigation
* SOC Workflow

---


## 🚀 Conclusion

Successfully identified the infected host and associated user through structured traffic analysis, demonstrating practical SOC investigation skills.
