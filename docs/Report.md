
### **1. Flags Section**
**Screenshots to Capture:**
- A **Wireshark screenshot** of each packet with a highlighted TCP flag (e.g., SYN, ACK, FIN, RST).
  - Highlight the **TCP Header Flags** field in the packet details.
- Include screenshots for all flags you set using `hping3`.

**Commands to Show:**
- The `hping3` command used to set each flag.
  - Example for SYN flag:
    ```bash
    hping3 -S -p [target_port] [target_ip]
    ```

---

### **2. Start and End of a TCP Session**
**Screenshots to Capture:**
- A **Wireshark screenshot** showing:
  - **SYN Packet:** The first packet that initiates the session.
  - **FIN Packet:** The packet that terminates the session.
- Highlight sequence numbers, acknowledgment numbers, and flags (SYN/FIN).

**Commands to Show:**
- The `ncat` command used to create the session.
  - Example:
    ```bash
    ncat -l -p 12345
    ncat 127.0.0.1 12345
    ```

---

### **3. Same Data, Different Packets Within a Session**
**Screenshots to Capture:**
- Two **Wireshark screenshots** showing:
  - The first packet ("hello") and its sequence/acknowledgment numbers.
  - The second packet ("hello") and how these numbers changed.
- Highlight relevant fields in the **TCP Header** (sequence/acknowledgment numbers).

**Commands to Show:**
- The `ncat` command used to send data within the session:
  ```bash
  ncat -l -p 12345
  ncat 127.0.0.1 12345
  ```

---

### **4. Same Data, Different Packets Across Sessions**
**Screenshots to Capture:**
- Two **Wireshark screenshots**, one from each session:
  - Highlight differences in source/destination ports, sequence numbers, and flags.
- Use filters like `tcp.port == [your_port]` to isolate packets from each session.

**Commands to Show:**
- The `ncat` commands used for each session:
  ```bash
  ncat -l -p 12345
  ncat 127.0.0.1 12345
  ```
  (Repeat with the session restarted.)

---

### **5. Website Download and TCP Analysis**
**Screenshots to Capture:**
- A **Wireshark screenshot** showing the start of the download (SYN packets).
- A screenshot of retransmissions or duplicate ACKs (if applicable).
- Screenshots of your **graphs**:
  - Throughput over time.
  - Window size over time.
  - Congestion window over time.
  - Retransmissions over time.

**Commands to Show:**
- The `curl` command used to download the file:
  ```bash
  curl -O [file_url]
  ```

---

### **General Notes for Screenshots:**
- Annotate your screenshots (e.g., highlight key fields like flags, sequence numbers, or ports).
- Crop the images to show only the relevant packet details for clarity.

---