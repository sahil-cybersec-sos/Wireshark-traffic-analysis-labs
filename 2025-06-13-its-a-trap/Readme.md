# 🚨 Traffic Analysis Exercise – "It's a Trap!"

## 📌 Overview

Performed network traffic analysis on a PCAP file to identify a compromised Windows system within an enterprise network. The objective was to detect suspicious activity and extract host and user details.

---

## 🧠 Scenario

* Network Range: 10.6.13.0/24
* Domain: massfriction.com
* Domain Controller: 10.6.13.3

---

## 🔍 Investigation Steps

### 1️⃣ Identify Suspicious Host

Used:
Statistics → Conversations → IPv4

➡️ Found abnormal traffic from:
10.6.13.133

---

### 2️⃣ Extract MAC Address

Filter:
arp

➡️ Identified MAC:
00:26:b9:71:ad:36

---

### 3️⃣ Identify Hostname

Filter:
nbns || dhcp

➡️ Found:
DESKTOP-5AVE44C

---

### 4️⃣ Identify User Account

Filter:
kerberos.CNameString

➡️ Extracted:
gaines

---

## 🎯 Final Findings

* **Infected IP:** 10.6.13.133
* **MAC Address:** 00:26:b9:71:ad:36
* **Hostname:** DESKTOP-5AVE44C
* **Username:** rgaines

---

## 🛠️ Tools Used

* Wireshark
* Network Protocol Analysis
* Packet Inspection

---

## 🧠 Skills Demonstrated

* Network Traffic Analysis
* Threat Detection
* Incident Investigation
* Protocol Analysis (ARP, DHCP, NBNS, Kerberos)

---


## 🚀 Conclusion

Successfully identified a compromised system by analyzing network traffic patterns and extracting host and user information using multiple protocols.
