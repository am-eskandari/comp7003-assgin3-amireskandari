# comp7003-assign3-amireskandari



tcp.port == 12345 && (ip.addr == 192.168.0.10 || ip.addr == 102.168.0.88)

curl -O https://www.gutenberg.org/cache/epub/74846/pg74846.txt

ip.addr == 152.19.134.47

tcp.port == 40758 && ip.addr == 152.19.134.47

stream index = 0



1. throughpu mbs(sumyfielfd)/time 10ms
2.
3. 
4.
5.


  tcp.analysis.fast_retransmission

tcp.stream eq 0

tcp.window_size




5. tcp.analysis.retransmission packet/10ms


---

To adjust your IO graphs in Wireshark to an interval of **10 milliseconds**, follow these specific steps for each graph:

---

### **1. Throughput (Mbps) Over Time**
- **Filter:** `tcp.stream eq 0`
- **Y-Axis:** Bits per second (bps) converted to Mbps.
- **Interval:** 0.01 seconds (10 ms).
- **Steps:**
  1. Go to `Statistics > IO Graphs`.
  2. Add a new graph by clicking `+`.
  3. Set the filter to `tcp.stream eq 0`.
  4. Set the Y-axis unit to "Bits" and interval to `0.01 seconds`.
  5. To display Mbps, divide by \(10^6\) in the "Advanced" settings.
  6. Rename the graph as "Throughput (Mbps)."

---

### **2. Window Size (Bytes) Over Time**
- **Filter:** `tcp.stream eq 0`
- **Y-Axis:** TCP Window Size (bytes).
- **Interval:** 0.01 seconds (10 ms).
- **Steps:**
  1. Go to `Statistics > IO Graphs`.
  2. Add another graph.
  3. Set the filter to `tcp.window_size`.
  4. Change the Y-axis unit to "Advanced... > Field Value."
  5. Select `tcp.window_size` as the field.
  6. Set the interval to `0.01 seconds`.

---

### **3. Congestion Window (Bytes) Over Time** (Approximation)
- **Filter:** `tcp.stream eq 0`
- **Y-Axis:** Sequence numbers as a proxy for congestion window size.
- **Interval:** 0.01 seconds (10 ms).
- **Steps:**
  1. Go to `Statistics > IO Graphs`.
  2. Add another graph.
  3. Set the filter to `tcp.seq` or leave it as `tcp.stream eq 0`.
  4. Change the Y-axis unit to "Advanced... > Field Value."
  5. Set the interval to `0.01 seconds`.

---

### **4. Cumulative Number of Retransmissions Over Time**
- **Filter:** `tcp.analysis.retransmission`
- **Y-Axis:** Cumulative retransmissions (packet count).
- **Interval:** 0.01 seconds (10 ms).
- **Steps:**
  1. Go to `Statistics > IO Graphs`.
  2. Add another graph.
  3. Set the filter to `tcp.analysis.retransmission`.
  4. Change the Y-axis to "Packet Count."
  5. Set the interval to `0.01 seconds`.

---

### **5. Retransmission Graph**
- **Filter:** `tcp.analysis.retransmission || tcp.analysis.duplicate_ack`
- **Y-Axis:** Packet count.
- **Interval:** 0.01 seconds (10 ms).
- **Steps:**
  1. Go to `Statistics > IO Graphs`.
  2. Add another graph.
  3. Set the filter to `tcp.analysis.retransmission || tcp.analysis.duplicate_ack`.
  4. Set the Y-axis to "Packet Count."
  5. Set the interval to `0.01 seconds`.

---

### **Adjusting Interval to 10 ms**
1. In the **IO Graphs** window, locate the **"Interval"** field at the top right.
2. Change the value from the default `1 second` to `0.01 seconds` for all graphs.
3. Ensure all graphs update dynamically to reflect finer time resolution.

---

### **Export and Documentation**
- **Export the Graphs**:
  - Click "Export" to save each graph as a PNG file for inclusion in your report.
- **Document Observations**:
  - Annotate key features like slow start, congestion avoidance, retransmissions, and window size changes.

If you run into any issues, let me know, and I’ll guide you through it! 😊