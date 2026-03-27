# 🚨 Lumma Stealer Traffic Analysis (Wireshark)

## 📌 Overview

Performed network traffic analysis on a PCAP file to investigate Lumma Stealer activity. The objective was to identify the infected system, associated user, and malicious infrastructure used during the attack.

---

## 🧠 Scenario

* SOC alert triggered: **ET MALWARE Lumma Stealer Victim Fingerprinting**
* Suspicious IP: **153.92.1.49**
* Port: **80 (HTTP)**
* Date: **2026-01-27**

---

## 🌐 Environment

* Network Range: 10.1.21.0/24
* Domain: win11office.com
* AD Domain: WIN11OFFICE
* Domain Controller: 10.1.21.2

---

## 🔍 Investigation Methodology

### 1️⃣ Identify Malicious Traffic

Applied filter:

```
(http.request or tls.handshake.type eq 1) and !(ssdp) and ip.addr eq 153.92.1.49
```

➡️ Isolated HTTP and HTTPS communication with attacker IP.

---

### 2️⃣ Extract Malicious Domain

Analyzed HTTP headers and TLS handshake:

```
Host: whitepepper[.]su
```

---

### 3️⃣ Identify Infected Host

Observed internal communication with attacker:

```
10.1.21.58
```

---

### 4️⃣ Extract MAC Address

Filter:

```
arp
```

➡️ Mapped IP to MAC:

```
00:21:5d:c8:0e:f2
```

---

### 5️⃣ Identify Hostname

Filter:

```
nbns || dhcp
```

➡️ Found:

```
DESKTOP-ES9F3ML
```

---

### 6️⃣ Identify User Account

Filter:

```
kerberos.CNameString
```

➡️ Found:

```
gwyatt
```

---

### 7️⃣ Determine Full Name

Used pattern + search:

```
frame contains "Wyatt"
```

➡️ Found:

```
Gabriel Wyatt
```

---

## 🎯 Final Findings

* **Infected IP:** 10.1.21.58
* **MAC Address:** 00:21:5d:c8:0e:f2
* **Hostname:** DESKTOP-ES9F3ML
* **Username:** gwyatt
* **Full Name:** Gabriel Wyatt
* **Malicious Domain:** whitepepper[.]su

---

## 🛠️ Tools Used

* Wireshark
* Packet Analysis
* Protocol Analysis (HTTP, TLS, ARP, Kerberos)

---

## 🧠 Skills Demonstrated

* Network Traffic Analysis
* Threat Detection
* Incident Response
* Malware Investigation
* Protocol-Level Analysis



---

## 🚀 Conclusion

Successfully identified a Lumma Stealer infection by analyzing network traffic and correlating protocol data to trace the compromised system and associated user.
