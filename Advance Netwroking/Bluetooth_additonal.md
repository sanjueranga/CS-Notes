### Comprehensive Notes on Other Technologies in Sensor Networks

#### ZigBee

ZigBee is a wireless communication protocol used mainly in low-power, low-data-rate applications, often seen in sensor networks. It operates on the IEEE 802.15.4 standard and provides low-cost, low-power wireless communication. ZigBee is particularly suitable for IoT (Internet of Things) applications.

#### Low Rate WPAN (LR-WPAN) Device Types

In an LR-WPAN network, there are two types of devices:

1. **Full-Function Devices (FFD)**:
    
    - Can operate in 3 modes: as a PAN coordinator, a coordinator, or a device.
    - Capable of talking to both Reduced-Function Devices (RFDs) and other FFDs.
2. **Reduced-Function Devices (RFD)**:
    
    - Intended for simple applications.
    - Can only communicate with FFDs, not other RFDs.

#### Physical Layer Management Entity (PLME) and Physical Data (PD) Service Access Point (SAP)

- **PLME**: Manages physical layer operations in LR-WPAN devices.
- **PD SAP**: Interface between the data link layer and the physical layer, allowing the exchange of data.

---

### WPAN Network Architectures

IEEE 802.15.4 supports multiple network topologies, which include star, peer-to-peer, and mesh.

#### WPAN Network Architecture (Star Topology)

- **PAN Coordinator**: Must include at least one FFD acting as the PAN coordinator.
    - The PAN coordinator is responsible for initiating, terminating, or routing communication within the network.
    - In a star network, after the first FFD is activated, it can establish its network and become the PAN coordinator.
    - PAN coordinator can allow other devices to join the network.

#### WPAN Network Architecture (Other Topologies)

- **Peer-to-Peer**:
    - In a peer-to-peer network, each FFD can communicate with any other FFD within radio range.
    - One of the FFDs is chosen as the PAN coordinator.
    - Peer-to-peer networks are ad hoc, self-organizing, self-healing, and can incorporate mesh networking.

---

### Resource and Neighbor Discovery

- **Nomadic and Ad-Hoc Network Discovery**:
    
    - The discovery process identifies dynamic connectivity, location, and context of resources and hosts.
    - Neighbor discovery is vital in many routing protocols for wireless sensor networks.
- **Complications in Ad-Hoc Neighbor Discovery**:
    
    - In mobile ad-hoc networks (MANETs), network topology is dynamic and unknown.
    - The neighborhood is constantly changing, and ad-hoc modes do not allow transit (non-multi-hop).

---

### Mobile Ad-Hoc Network (MANET) Neighbor Discovery

#### MANET Neighbor Discovery Protocol (NHDP)

- **Proactive and Reactive Discovery**:
    - Uses **HELLO messages** to discover neighbors.
    - **Proactive**: Sent periodically to maintain neighborhood knowledge.
    - **Responsive**: Sent when there is a change in the network topology (e.g., new, lost, or changed links).

#### Basic Terminology in MANET NHDP

- **Heard**: An interface is heard if it can receive control signals.
- **Link**: A communication link that is heard by both devices.
- **Symmetric Link**: Both devices can hear each other.
- **1-Hop Neighbor**: Direct neighbors in communication range.
- **2-Hop Neighbor**: Neighbors of 1-hop neighbors.

---

### HELLO Messages in MANET NHDP

- **HELLO Message**: Used to identify and propagate neighbor information.
    
    - **Basic Functionality**:
        - Identifies the interface sending the message and its network address.
        - Allows other devices to associate network addresses with 1-hop neighbors.
        - Propagates 1-hop neighbor information.
- **Generation of HELLO Messages**:
    
    - **Proactive**: Sent periodically at a fixed or dynamic interval (HELLO_INTERVAL).
    - **Responsive**: Sent in response to changes in neighborhood or router status.

---

### Information Bases in MANET NHDP

- **Interface Information Base (IIB)**: Contains information about 1-hop and symmetric 2-hop neighbors.
- **Link Set**: Holds link status information.
- **2-Hop Set**: Contains 2-hop neighbor information.
- **Neighbor Information Base (NIB)**: Holds network addresses of 1-hop symmetric neighbors.
- **Lost Neighbor Set**: Tracks recently lost neighbors.

---

### Routing in MANET

- **OLSR (Optimized Link State Routing) Protocol**: A proactive link-state routing protocol optimized for mobile ad-hoc networks.
    - **HELLO and Topology Control (TC) Messages**: Used for neighbor discovery and topology updates.

#### OLSR Characteristics

- **Table-driven**: Maintains routing tables at all times, ensuring fast route availability.
- **Link-state Algorithm**: Only advertises links from nodes in its **Multipoint Relay (MPR) Selector** set.
- **Reliability**: Non-reliable and connection-less. Uses frequent updates and sequence numbers to prevent stale information.
- **Routing**: Uses hop-by-hop routing with dynamic table entries.

---

### MultiPoint Relay (MPR) Selection in OLSR

- **MPR Selection**: Each node selects a set of 1-hop neighbors as MPRs.
    - **Control Packets**: Only retransmitted by nodes in the MPR set.
    - **Optimal Selection**: MPRs are selected to cover all 2-hop neighbors, optimizing flooding.
- **MPR Selector Set (MS)**: The set of nodes that select a particular node as part of their MPR.

---

### HELLO Messages in OLSR

- **HELLO Messages**: Used to determine the MPR set and establish symmetric neighbors.
    - **Sequence Numbers**: Used to track the status of MPR sets.
    - **Neighborhood Information**: Includes details on extended 1-hop and 2-hop neighbors.

---

### OLSR Extension: Topology Control Message (TC)

- **TC Messages**: Nodes exchange topology information, including the list of advertised neighbors and sequence numbers.
    - Only MPR nodes generate and forward TC messages.
    - TC messages reduce the need to advertise all links in the network.