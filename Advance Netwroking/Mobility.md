### **1. Wireless Mobility Management – L2 (Data Link Layer)**

- **Roaming**: Moving from one access point (AP) to another for maintaining connectivity.
    - **Steps**:
        1. **Scanning**: The device listens for beacon signals or sends probes to discover APs.
        2. **Reassociation Request**: Sent to one or multiple APs.
        3. **Reassociation Response**:
            - **Success**: The AP accepts the device, and connectivity is maintained.
            - **Failure**: Scanning continues.
        4. **AP Integration**: AP signals the distribution system (DS) to update the database about the device's new location.

---

### **2. Wireless Mobility Management – L3 (Network Layer)**

- **Mobility Management (MM) with IP**: IP assumes static hosts; MM ensures:
    - **Session Continuity**: Uninterrupted data delivery during movement.
    - **Reachability**: Retaining the same IP address despite switching access points.

---

### **3. Key Concepts of Mobility with IP**

1. **Host Address Update**:
    
    - Changing IP addresses may cause service interruptions or lost connections.
    - Flat IP (single layer routing) is impractical for large networks.
2. **Handoff (Handover)**:
    
    - Maintaining connectivity when switching between networks or access points.
    - Types:
        - **Horizontal Handoff**: Between similar networks (e.g., Wi-Fi to Wi-Fi).
        - **Vertical Handoff**: Between different networks (e.g., Wi-Fi to cellular).

---

### **4. Host-Based Mobility Management**

- **Mobile IPv4 (MIPv4)**:
    - **Mobile Node (MN)**: Device that moves between networks.
    - **Correspondent Node (CN)**: Device communicating with the MN.
    - **Home Agent (HA)**: Tracks the MN in the home network.
    - **Foreign Agent (FA)**: Supports MN in visited networks.

#### **Key Addresses in MIPv4**:

1. **Home Address (HoA)**: Permanent IP assigned by the home network.
2. **Care-of Address (CoA)**: Temporary IP in the visited network.

#### **Mechanisms**:

- **Agent Discovery**:
    - HA and FA advertise their presence.
    - MN listens or requests agents using ICMP Router Advertisement.
- **Registration**: MN registers its CoA with the HA.

#### **Data Delivery**:

- **Non-Optimal Routing**:
    - Packets are routed through the HA, creating triangular routing.
    - HA and FA use tunneling to forward data.

---

### **5. Network-Based Mobility Management**

- **Proxy Mobile IP (PMIP)**:
    - Mobility managed by the network, transparent to the MN.
    - **Local Mobility Anchor (LMA)**: Tracks MN in its domain.
    - **Mobile Access Gateway (MAG)**: Manages MN's movements locally.

---

### **6. Advanced Handoff Scenarios**

- **Soft Handoff**: Maintains connection with both old and new APs during the transition.
- **Hard Handoff**: Drops the old connection before establishing a new one.

#### **Horizontal vs. Vertical Handoff**:

- **Horizontal**: Switching within the same type of network.
- **Vertical**: Switching between different technologies (e.g., Wi-Fi to 4G).

---

### **7. Media Independent Handover (MIH)**

- **IEEE 802.21 Standard**: Ensures seamless IP session handover across L2 technologies.
- **Components**:
    - **Media Independent Handover Function (MIHF)**: Sits between L2 and L3 to coordinate handovers.

#### **MIH Services**:

1. **Event Notifications**: Alerts for signal degradation.
2. **Commands**: Initiate handovers or request alternate APs.
3. **Information Service**: Shares performance metrics and service details.

---

### **8. Mobile IPv6 (MIPv6)**

- Eliminates the need for Foreign Agents (FA).
- Allows MN to roam freely between networks without mobility-specific infrastructure.
- Uses Binding Updates (BU) and Binding Acknowledgements (BA) for MN-HA communication.

---

### **9. Software-Defined Network (SDN) Mobility Management**

- Emerging solution using SDN for centralized and efficient mobility management.
- **Challenges**: Scalability, architecture complexity.

---

### **Comparison of Key Mechanisms**

|**Feature**|**MIPv4**|**MIPv6**|**PMIP**|
|---|---|---|---|
|**Agents**|HA, FA|HA (no FA)|LMA, MAG|
|**Addressing**|HoA, CoA|HoA, CoA|HoA only|
|**Handoff**|Host-based|Host-based|Network-based|
|**Optimization**|Non-optimal routing|Improved with routing optimization|Transparent to MN|

---

