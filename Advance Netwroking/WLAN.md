# Wireless Communication

Wireless communication refers to the transmission of data over a distance without requiring a physical connection between devices. It employs electromagnetic waves, such as radio, microwave, and infrared, for data transmission.

---

## Example Technologies:

1. **Wireless Personal Area Networks (WPANs):**
    
    - Example: Bluetooth.
2. **Wireless Local Area Networks (WLANs):**
    
    - Example: Wi-Fi.
3. **Wireless Wide Area Networks (WWANs):**
    
    - Examples: GSM, GPRS (2G/2.5G).
4. **Advanced Wireless Technologies:**
    
    - **3G:** UMTS, IMT-2000, W-CDMA.
    - **4G:** LTE Advanced.
    - **5G:** Latest generation with ultra-low latency and high speeds.

---

## Wireless Local Area Networks (WLAN)

### Overview:

- Connects two or more devices using wireless methods.
- Typically provides access to the internet through an **Access Point (AP)** or **Wireless Access Point (WAP)**.
- Common in homes and commercial environments due to ease of installation.
- The most common WLAN technology is **IEEE 802.11 (Wi-Fi)**.

---

### History of WLAN:

- **1997:** Standardization of 802.11 with speeds of 1 Mbps and 2 Mbps.
- Operates in unlicensed **2.4 GHz and 5 GHz ISM bands**.
- **Current Standards:**
    - 802.11ax (Wi-Fi 6 and 6E).
    - **Upcoming:** 802.11be and 802.11bx (2024).

---

### IEEE 802.11n (Wi-Fi 4):

- Introduced enhancements like **MIMO (Multiple Input, Multiple Output)** and **Spatial Division Multiplexing (SDM)** to increase throughput.
- **Basic Service Set (BSS):** The fundamental building block of 802.11 LANs.

#### Features:

1. Low-density parity-check code.
2. Use of advanced channel models.
3. Supports infrastructure-based **Basic Service Set (BSS)** interconnected through a **Distribution System (DS)** to form an **Extended Service Set (ESS)**.

---

## WLAN Data Transmission Techniques

### **Orthogonal Frequency Division Multiplexing (OFDM):**

- **Principle:** Instead of transmitting a single high-speed signal, divides the data across multiple lower-speed subcarriers.
- **Benefits:**
    1. Efficient spectral use.
    2. Robust against interference and multipath propagation.

#### Key Features of OFDM:

1. Enabled by hardware-based **Digital Signal Processing** (e.g., IFFT/FFT).
2. Narrower subcarriers spaced closely together.
3. Subcarriers are orthogonal to each other to minimize interference.

#### OFDM in IEEE 802.11a:

- Fundamental sampling rate: **20 MHz**.
- **FFT/IFFT Size:** 64-point.
- Symbol duration: **3.2 μs** with frequency spacing of **312.5 kHz**.
- Of the **64 subcarriers**, **52 are used**, while **12 are reserved**.

---

### **Multiple Input, Multiple Output (MIMO):**

- A key feature in 802.11n.
- **MIMO/SDM (Spatial Division Multiplexing):**
    - Utilizes multiple antennas for simultaneous data streams.
    - Significantly improves throughput as spatial paths are resolved separately.

---

## Summary of WLAN Protocol Stack

### Physical Layer:

- Responsible for modulation/demodulation and handling RF signals.
- Example technologies: DSSS, OFDM.

---

## Evolution of Wireless Technologies

### 1. **2G/2.5G (GSM and GPRS):**

- **GSM:** First-generation digital cellular networks.
- **GPRS:** Added packet data services to GSM (2.5G).

### 2. **3G:**

- Technologies: UMTS, IMT-2000, and W-CDMA.
- Features higher data rates for internet and video streaming.

### 3. **4G (LTE Advanced):**

- Supports IP-based voice, data, and multimedia streaming.
- Enhanced speeds and reduced latency.

### 4. **5G:**

- Current standard in wireless communication.
- Offers ultra-low latency, massive device connectivity, and gigabit-level data speeds.