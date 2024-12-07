# **Guide for Lab Walkthrough**

<br>

## **Steps to Begin with Flags**

### 1. Install Tools (if not already installed):
- Ensure `hping3` and Wireshark are set up on your system.
- Test `hping3` by running a basic ping command to confirm it’s working.

### 2. Research `hping3` Commands for Flags:
- Look into commands to set TCP flags individually (e.g., SYN, ACK, FIN).
- Example for setting the SYN flag:
  ```bash
  hping3 -S -p [target_port] [target_ip]
  ```

### 3. Set Up Wireshark:
- Start Wireshark and choose the appropriate network interface.
- Begin capturing packets.

### 4. Run Commands and Capture Flags:
- Use `hping3` to send packets with each of the following flags:
  - **SYN**
  - **ACK**
  - **FIN**
  - **RST**, etc.
- After sending each packet:
  - Stop Wireshark.
  - Save the capture file.
  - Annotate the packets (e.g., highlight the flag field in the TCP header).

### 5. Document Commands and Screenshots:
- Take a screenshot for each flag captured in Wireshark.
- Write a brief explanation of each flag’s role in TCP.

---

<br>


## **Next: Start and End of a TCP Session**

### **Steps to Tackle This Section:**

### 1. Set Up Tools:
- Confirm that `ncat` is installed. If not, install it.
- Keep Wireshark ready to capture packets.

### 2. Initiate a TCP Session:
- Use `ncat` to send a simple message like "hello" to a target.
- Example commands for a local session:
  - On one terminal (listener):
    ```bash
    ncat -l -p 12345
    ```
  - On another terminal (sender):
    ```bash
    ncat 127.0.0.1 12345
    ```
  - Type "hello" in the sender terminal and press Enter.

### 3. Capture the Session in Wireshark:
- Start Wireshark and capture packets during the `ncat` session.
- Look for the **SYN**, **ACK**, and **FIN** flags in the packet capture.

### 4. Analyze and Document:
- **SYN:** Identify the packet that starts the session.
- **FIN:** Identify the packet that ends the session.
- Calculate the **total number of bytes sent**:
  - Sum the sizes of headers and payloads in Wireshark.

### 5. Take Screenshots:
- Highlight the **SYN** and **FIN** packets in Wireshark.
- Include the data showing the **total bytes transferred**.

### 6. Write Explanations:
- Describe the following:
  - The role of **SYN** and **FIN** in TCP session management.
  - How you calculated the **total bytes sent**.

---


<br>


# **Next: Same Data, Different Packets Within a Session**

 **Objective:**  
Send the same data (e.g., "hello") twice within the same TCP session and analyze how the IP and TCP header fields differ.

---

# **Steps to Tackle This Task**

1. **Set Up the Environment:**
   - Make sure `ncat` is running on a local port.
   - Example commands:
     - **Listener:**
       ```bash
       ncat -l -p 12345
       ```
     - **Sender:**
       ```bash
       ncat 127.0.0.1 12345
       ```

2. **Send the Data:**
   - Send "hello" in the terminal and press Enter.
   - Send "hello" again without closing the session.
   - This ensures two packets with the same payload are sent within the same session.

3. **Capture Packets with Wireshark:**
   - Start Wireshark before sending data.
   - Filter TCP traffic for the session using:
     ```text
     tcp.port == 12345
     ```
   - Stop capturing after both messages are sent.

4. **Analyze Packet Differences:**
   - Compare fields in the TCP and IP headers:
     - **Sequence Numbers:** Note how they increment for each packet.
     - **Acknowledgment Numbers:** Identify changes after each packet is acknowledged.
     - **Flags:** Observe any differences in ACK or PSH flags.
   - Use Wireshark’s packet details view for a deep dive.

5. **Document Findings:**
   - **Screenshots:** Take one for each packet sent (first "hello" and second "hello").
   - **Analysis:** Write about:
     - Sequence and acknowledgment numbers.
     - Flag behavior.
     - Any other notable differences.

---

# **Tips:**
- Use Wireshark’s **Follow TCP Stream** feature to see all packets in the session.
- Highlight changes between the first and second transmissions for clarity.

---

# **Next: Same Data, Different Packets Across Sessions**

 **Objective:**  
Send the same data (e.g., "hello") in two separate TCP sessions and analyze how the headers (IP and TCP) differ.

---

# **Steps to Tackle This Task**

1. **Set Up the First Session:**
   - Open two terminals:
     - **Listener:**
       ```bash
       ncat -l -p 12345
       ```
     - **Sender:**
       ```bash
       ncat 127.0.0.1 12345
       ```
   - Type "hello" and press Enter to send it.
   - Close the session (Ctrl+C or send a FIN/quit command).

2. **Set Up the Second Session:**
   - Repeat the same steps as above but restart `ncat` for both the listener and sender.
   - Send "hello" again and close the second session.

3. **Capture Packets in Wireshark:**
   - Start capturing before initiating the first session and stop after the second session ends.
   - Use a filter to isolate traffic for analysis:
     ```text
     tcp.port == 12345
     ```
   - Save the capture file for reference.

4. **Analyze Packet Differences:**
   - Use Wireshark to compare headers between the two sessions:
     - **Source/Destination Ports:** Note differences in ephemeral ports assigned to each session.
     - **Sequence Numbers:** Examine how the sequence numbers start fresh for each session.
     - **Acknowledgment Numbers:** Check how acknowledgment numbers differ across sessions.
     - **Flags:** Identify the SYN and FIN flags marking session start and end.

5. **Document Findings:**
   - **Screenshots:** Take one for a packet from each session.
   - **Analysis:** Write about:
     - How the sequence and acknowledgment numbers differ across sessions.
     - Differences in source/destination ports.
     - Any notable changes in the flags or headers.

---

# **Tips:**
- Use Wireshark’s **Comparative Packet Analysis** to line up fields side-by-side.
- Save your capture for submission to ensure you have visual proof for your analysis.

---

# **Next: Website Download and TCP Analysis**

 **Objective:**  
Download a file (e.g., a Project Gutenberg book) and analyze the TCP behavior during the download, focusing on slow start, congestion control, and retransmissions. Generate graphs to visualize key metrics.

---

# **Steps to Tackle This Task**

 **1. Prepare for the Download:**
   - **Choose a File:** Use a book from Project Gutenberg (e.g., *https://www.gutenberg.org/*).
   - **Wireshark Setup:**
     - Start capturing on the network interface you’ll use for the download.
     - Filter for TCP traffic to avoid unrelated packets:
       ```text
       tcp.port == 80 || tcp.port == 443
       ```

 **2. Perform the Download:**
   - Open a browser or use `curl` to download the file:
     ```bash
     curl -O [file_url]
     ```
   - Stop the Wireshark capture after the download completes.

 **3. Analyze TCP Behavior:**
   - Open the Wireshark capture and focus on the download session.
   - Identify key phases:
     - **Slow Start:** Look for the initial increase in window size.
     - **Congestion Control:** Examine how the congestion window adapts.
     - **Retransmissions:** Filter packets for retransmissions or duplicate ACKs:
       ```text
       tcp.analysis.retransmission
       ```
   - Note packet sequences, RTT, and throughput changes.

 **4. Generate Graphs:**
   - Use Wireshark’s built-in tools or export data for graphing in Excel:
     - **Throughput (Mbps) over time:** Measure data transferred per time unit.
     - **Window Size (bytes) over time:** Plot the TCP window size from the headers.
     - **Congestion Window (bytes) over time:** Show how the congestion window adapts.
     - **Cumulative Retransmissions:** Plot retransmissions over time.
     - **Retransmission Graph:** Highlight retransmission events.

 **5. Document Findings:**
   - Include the following:
     - **Screenshots**: Show key packets and metrics from Wireshark.
     - **Graphs**: Label axes and provide clear explanations.
     - **Explanations**: Describe:
       - How slow start operates in your capture.
       - How the congestion window adapts to changes.
       - Causes and impact of retransmissions.

---

# **Tips for Success:**
- Use **TCP Stream Graphs** in Wireshark for quick insights:
  - **Statistics → TCP Stream Graph → Throughput.**
- Double-check all screenshots and graphs for clarity—this section is worth 20% of your grade!

---