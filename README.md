<p align="center">
  <img src="proj-banner.png" alt="Network Device Identification Project" width="100%">
</p>

<h1 align="center">🌐 Network Device Identification & Enumeration</h1>

<p align="center">
  <b>An Educational Project for Local Network Reconnaissance & Analysis</b>
</p>

| Field | Details |
|:------|:--------|
| 👨‍💻 **Author** | Muhammad Ayaz |
| 🎓 **Program/Batch** | cyber security |25 to 29 |
| 🧑‍🏫 **Instructor** | Muhammad Ans Khalid |
| 🛠️ **Tools Used** | Nmap, Zenmap, Python (HostLens, Netwatchdog), Wireshark |
| 🎯 **Objective** | To identify unknown devices on a local network using active and passive reconnaissance techniques. |

---

## 1. Project Introduction
In modern networks, identifying connected devices is crucial for security. However, with the introduction of **MAC Randomization** in iOS and Android devices, identifying unknown devices has become challenging. This project documents the step-by-step process of discovering live hosts, identifying their operating systems, and attempting to unmask devices using random MAC addresses.

## 2. Problem Statement
During a local network scan, several devices appear as "Unknown" because modern smartphones hide their true MAC addresses for privacy. Traditional tools like Nmap can only see the random MAC and closed ports. The challenge is to bypass this limitation and identify the device types using advanced enumeration.

## 3. Objectives & Scope
*   **Objective 1:** Discover all active hosts on the `192.168.18.0/24` subnet.
*   **Objective 2:** Identify the Manufacturer (Vendor) of each device using MAC OUI lookup.
*   **Objective 3:** Perform OS fingerprinting on unknown devices.
*   **Scope:** This project is strictly for educational purposes and is limited to my own local network.

## 4. Requirements Analysis (SRS)

### 4.1 Functional Requirements
*   The system shall extract the local IP and MAC address of the host machine.
*   The system shall perform a Ping Scan to discover all live hosts.
*   The system shall perform deep scanning to identify open ports and OS.
*   The system shall categorize devices based on their MAC Address (Real vs. Private).

### 4.2 Non-Functional Requirements
*   **Accuracy:** The MAC lookup must correctly identify the vendor.
*   **Performance:** Scans should not take more than 5 minutes.
*   **Usability:** The output should be readable in a tabular format (using Python tools).

---

## 5. System Design & Data Flow

### 5.1 Network Topology
*(Insert the Zenmap Topology screenshot here if available)*

### 5.2 Data Flow Diagram (DFD)
The process follows a simple flow: identifying the local IP, scanning the subnet, analyzing the MAC addresses, and classifying the devices.

```mermaid
graph TD
    A[Start: Identify Local IP & Subnet] --> B[Run Nmap Ping Scan]
    B --> C{Are Devices Found?}
    C -->|Yes| D[Extract IP & MAC Addresses]
    C -->|No| A
    D --> E[Perform OUI Lookup on MAC]
    E --> F{Is MAC Private?}
    F -->|Yes| G[Device is Phone/Tablet (Random MAC)]
    F -->|No| H[Identify Vendor: Huawei, Intel, etc.]
    G --> I[Run Deep Scan for OS Fingerprinting]
    H --> I
    I --> J[Generate Final Report]
