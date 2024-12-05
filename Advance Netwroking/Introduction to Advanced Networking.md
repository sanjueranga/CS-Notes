# Advanced Computer Networks

This note summarises key concepts in mobile and ubiquitous computing, wireless network technologies, and their applications, based on excerpts from a lecture on advanced computer networks.

## Mobile and Ubiquitous Computing

### Mobile Computing
Mobile computing enables individuals to perform computational tasks while on the move, allowing them to access information, communicate, and utilize applications regardless of their location.

### Ubiquitous/Pervasive Computing
Ubiquitous computing involves the integration of computing devices into the environment, often invisibly, with the goal of enhancing daily activities and providing context-aware services.

### Key Characteristics
Both mobile and pervasive computing share characteristics such as:
- **Mobility**
- **Limited Resources**
- **Context-Awareness**
- **Heterogeneity**
- **Security Concerns**

## Constraints in Mobile Computing and Adaptation Strategies

Mobile computers face various constraints, including:
- **Limited resources** in terms of processing power, memory, and battery life.
- **Security and reliability issues.**
- **Variable performance** due to mobility and unstable connectivity.

### Dynamic Adaptation Strategies:
- **Client-Server Model Adaptation:** Functionality is adapted by shifting tasks between client and server depending on connectivity strength.
- **Functionality Adaptation:** For example, the Coda file system uses caching and prefetching to improve performance and security during varied connectivity.
- **Data Adaptation:** Adjusting the quality of data (fidelity) provided to the client application.

## Impacts of Mobility on the Client-Server Model

Mobility necessitates adjustments to the traditional client-server model:
- **Thick Clients:** Clients may need to perform server functions during uncertain connectivity.
- **Dynamic Client-Server Roles:** The boundary between client and server roles can blur to optimise performance and resource usage.

## Fidelity and Agility in Mobile Computing

- **Fidelity:** Refers to the degree to which the data presented on the client matches the server's reference copy.
- **Agility:** Represents the speed and accuracy of an application's adaptation to environmental changes.
- **Trade-offs** exist between information quality, performance, throughput, and fidelity in mobile environments.


## Coda Case: Developing Adaptations in Applications

### Coda
Coda is a file system designed to maximize data availability, even at the expense of accessing potentially stale data. It aims to improve performance and usability in environments with intermittent or unreliable connectivity, such as mobile and ubiquitous computing scenarios.

### Coda Architecture:
Each **Coda client** (called **Venus**) maintains a local cache that stores copies of files it frequently accesses. This enables Venus to function independently when the client is disconnected from the server or when connectivity is weak.

### Venus Adaptation Based on Connectivity:
Venus adapts its functionality depending on the state of the connectivity between the client and the server. These adaptations are crucial for ensuring continuous service, even in challenging conditions like network disruptions or limited bandwidth.

#### Venus States:
1. **Hoarding:**
   - **When**: Strong connectivity with the server.
   - **What**: Venus aggressively prefetches files to store locally in anticipation of future use. This ensures that the client has a local copy of the data, reducing the need for frequent server access.
   
2. **Emulating:**
   - **When**: Disconnected from the server.
   - **What**: In the event of a disconnection, Venus operates autonomously, using the locally cached data. The client can perform read and write operations without any server access, but writes are kept locally until reconnected.

3. **Write-Disconnected:**
   - **When**: Weak connectivity with the server.
   - **What**: The client can still read from the local cache and make changes, but writes are temporarily stored locally until connectivity improves. This ensures that the client can continue operations even with poor network conditions.

4. **Reintegration:**
   - **When**: Connectivity improves.
   - **What**: Once the client regains a stable connection with the server, it synchronizes with the server and reintegrates any changes made during the disconnected state. This includes updating both the local cache and the server data, resolving any potential conflicts.

### Key Benefits of Coda:
- **Availability**: Coda ensures that data remains available even when disconnected from the server.
- **Adaptability**: By dynamically adjusting its functionality based on connectivity, Coda maintains a high level of performance without requiring constant server communication.
- **Conflict Resolution**: Coda handles situations where data has been modified both locally and remotely during disconnection, ensuring data consistency after reintegration.

The Coda file system is an example of how adaptation in distributed systems can enhance performance and availability while mitigating the challenges of mobile and ubiquitous computing environments.


## Adaptation Implementation

### 1. Adapting to Hardware/Software Capabilities of the Mobile Device
Adaptation can be implemented in different layers, depending on the capabilities of the mobile device, either at the **proxy** or the **server**:
- **Proxy Adaptation**: Adaptations can be made through proxies that manage the communication between clients and servers. Examples include transcoding proxies, which modify the content to optimize it for the mobile device’s capabilities.

- **Server Adaptation**: The server can adjust the content, format, or delivery strategy based on the client’s capabilities, such as adjusting image resolution or data size for mobile devices.

### 2. Adapting to Connectivity of the Mobile Device
Adaptation based on the **connectivity** of the mobile device can occur at both the **server** and **client** ends:
- **Server-Side Adaptation**: Servers can change the way data is delivered based on network quality (e.g., switching from high-quality video to lower resolution in case of weak connectivity).
- **Client-Side Adaptation**: The mobile client may adjust its behavior to cope with fluctuating connectivity, such as switching to offline modes or reducing data consumption when connectivity is poor.

### 3. Adapting to Resource Availability at the Mobile Device
Adaptation based on the **resource availability** of the mobile device occurs primarily at the **client** side:
- **Resource-Constrained Clients**: Mobile devices with limited CPU power, memory, or battery life must adapt by offloading tasks to the server or reducing the frequency of resource-intensive operations.

---

## Proxy-Based Adaptation

### Proxies in Mobile Computing:
- **Proxies** can be used in environments with constraints like **firewalls**, **NATs (Network Address Translators)**, or any intermediary that can optimize network traffic.
- **Data Adapter**: A transcoding proxy works as a data adapter that converts data objects from one representation to another to match the mobile device’s capabilities. This includes resizing images, compressing files, or simplifying web pages.

### Dynamic Adaptation:
- **Bandwidth Availability**: The amount of available bandwidth on the mobile network determines whether data can be transmitted without modification or needs to be adapted (e.g., by compressing it).
- **Device Capability**: The hardware/software limitations of the mobile device may require adaptation at the proxy or server level, such as reducing video quality or simplifying graphics.

---

## Transcoding Module Composition

The transcoding module is responsible for adapting data between the server and the client through the proxy. Key components include:

- **Policy Module**: Defines the strategy for minimizing latency and optimizing document retrieval based on available resources.
  - **Objective**: Minimize latency in document retrieval.
  - **Key Metrics**:
    - **Dsc**: Document retrieval time without the proxy.
    - **Dspc**: Document retrieval time with the proxy.
    - **Bsp**: Server-to-proxy bandwidth.
    - **Bpc**: Proxy-to-client bandwidth.
    - **RTTpc**: Round-trip time (RTT) between the proxy and the client.
    - **RTTsp**: RTT between the server and the proxy.
    - **S**: Document size.
    - **Dp(S)**: Proxy delay function, which calculates the processing delay of the proxy based on document size.
    - **Sp(S)**: Output size function, which relates the transcoded document size to the input document size.

### Example: Round-Trip Time (RTT) Calculation

The round-trip time (RTT) is a critical factor in determining the latency of data retrieval over a network. RTT consists of the time it takes for a signal to travel from the sender to the receiver and back.

For a simple calculation of RTT:

RTT=RTTpc​+RTTsp​

Where:
- **RTTpc** is the time taken for the signal to travel from the proxy to the client.
- **RTTsp** is the time taken for the signal to travel from the server to the proxy.

### Transcoding Threshold:
Transcoding is beneficial when **Dspc < Dsc**, which means the time to retrieve the document through the proxy is less than the time to retrieve it directly from the server. This is known as the **transcoding threshold**. The input document size at which transcoding becomes effective can be calculated to optimize network performance and resource utilization.

---

## WebExpress: Optimizations for Wireless Browsing

Browsing over wireless networks can be costly and slow due to high latency and low bandwidth, especially in cellular networks where there might be **pay-per-minute** charging. To address these inefficiencies, **WebExpress** was developed at IBM to optimize web browsing on wireless networks.

### Techniques Used in WebExpress:
1. **Caching**: Reduces latency by storing frequently accessed content closer to the client.
2. **Differencing**: Only the changes between previously retrieved documents and the new ones are transmitted, reducing data transfer.
3. **Protocol Reduction**: Involves optimizing protocols like **TCP/IP** by using **Virtual Sockets** to reduce connection overhead. This minimizes the need for repeated connection setups, improving performance.
4. **HTTP Header Reduction**: WebExpress reduces the verbosity of HTTP headers, which can be quite large and inefficient for mobile devices with limited bandwidth.

---

By employing these adaptation strategies, mobile computing systems can improve the user experience by reducing latency, optimizing bandwidth usage, and adapting to varying network conditions and device capabilities.

## Wireless Network Technologies

### Wireless Networks
Wireless networks are defined as interconnected nodes exchanging information through a wireless medium.

### Wireless Links
Various technologies are employed for wireless links, including:
- **Terrestrial Microwave**
- **Communication Satellites**
- **Cellular and PCS Systems**
- **Radio and Spread Spectrum**
- **Free-Space Optical Communication**

Each has unique characteristics and applications, depending on the distance, environment, and data transfer needs.

### Wireless Frequency Spectrum
Spectrum allocation and the use of **ISM (Industrial, Scientific, and Medical)** frequency bands are key aspects of wireless networking.

## Types of Wireless Networks

1. **Wireless PAN (Personal Area Network):**
   - Interconnects devices within a person's reach, using technologies like **Bluetooth**, **infrared (IrDA)**, and **ZigBee**.
  
2. **Wireless LAN (Local Area Network):**
   - Connects devices over a short distance, commonly using **Wi-Fi** based on the IEEE 802.11 standard.
  
3. **Wireless Broadband:**
   - Utilizes **cellular networks** and other technologies to provide wide-area network coverage.
  
4. **Wireless WAN (Wide Area Network):**
   - Covers large geographical areas, employing technologies like **satellite** and **microwave links**.

## Specific Wireless Technologies

- **IrDA (Infrared Data Association):**
  - Enables short-range, line-of-sight communication using infrared light. Limited by range, data rates, and potential interference from objects.
  
- **Bluetooth:**
  - A widely used wireless protocol for short-range data exchange. Employs frequency hopping spread spectrum and allows for the creation of **piconets** and **scatternets**.

- **ZigBee:**
  - A low-power, low-data-rate mesh network technology primarily used in embedded applications such as home automation and sensors.

- **Wireless Body Area Networks (WBAN):**
  - Utilizes IEEE 802.15.6 standards to provide real-time health monitoring services.

- **Visible Light Communication (VLC):**
  - Defined by IEEE 802.15.7, it uses visible light for communication, offering different data rates based on the PHY layer used.

## WLANs (Wireless Local Area Networks)

### Advantages:
- **Flexibility**
- **Ad-hoc network capabilities**
- **Robustness**
- **Cost-effectiveness**

### Drawbacks:
- **Lower bandwidth** compared to wired networks.
- **Potential compatibility issues** with proprietary solutions.

### Design Goals:
- **Seamless operation**
- **Low power consumption**
- **Ease of use**
- **Security, privacy, and safety**

## Cellular Networks

### Architecture:
Composed of base stations, access points, and relays to provide wide-area coverage.

### Evolution:
Cellular networks are continuously evolving with each generation (e.g., **4G**, **5G**) to provide improved capabilities.



## Limitations of Wireless Technologies

While offering convenience and cost advantages, wireless technologies have limitations:
- **Bandwidth limitations** compared to wired connections.
- **Lack of universal standards.**
- **Device constraints**, such as small screen sizes and limited input methods.
- **Susceptibility to electromagnetic interference.**
- **Security vulnerabilities** due to the open nature of wireless transmission.

This note covers the fundamental concepts and technologies related to mobile and ubiquitous computing, along with the evolution and challenges of wireless networks.
