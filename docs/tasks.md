This assignment is packed with hands-on tasks that require a clear understanding of TCP operations. Let me break it down into manageable steps for you:

---

### **1. Understanding and Setting Flags (10 marks)**  
**Task:**
- Use `hping3` to set each TCP flag (SYN, ACK, FIN, etc.) in separate packets.
- Capture the packets using Wireshark and take screenshots showing the flags.
- Include the `hping3` command used for each flag.

**Steps:**
1. Research `hping3` commands to set individual flags.
2. Run each command and capture the packets with Wireshark.
3. Annotate the screenshots to highlight the set flags.
4. Write a short explanation of each flag’s purpose in the TCP protocol.

---

### **2. Start and End of a TCP Session (10 marks)**  
**Task:**
- Initiate a TCP session (e.g., send "hello" using `ncat`).
- Capture the session in Wireshark and analyze:
  - SYN and FIN flags (session start and end).
  - Total bytes sent in the transfer.

**Steps:**
1. Use `ncat` to send a simple message ("hello").
2. Capture the session with Wireshark.
3. Locate and explain SYN and FIN packets.
4. Calculate total bytes sent using packet data (lengths + headers).

---

### **3. Same Data, Different Packets Within a Session (25 marks)**  
**Task:**
- Send the same data twice within the same TCP session using `ncat`.
- Analyze differences in IP and TCP headers (sequence numbers, acknowledgment numbers, etc.).
- Provide screenshots and explanations.

**Steps:**
1. Establish a TCP session using `ncat`.
2. Send "hello" twice within the same session.
3. Use Wireshark filters to analyze changes in:
   - Sequence numbers.
   - Acknowledgment numbers.
   - Any other fields.
4. Annotate screenshots and describe observations.

---

### **4. Same Data, Different Packets Across Sessions (25 marks)**  
**Task:**
- Send the same data in two separate TCP sessions using `ncat`.
- Compare IP/TCP headers (source/destination ports, sequence/acknowledgment numbers, flags).
- Provide explanations and screenshots.

**Steps:**
1. Close the first session and initiate a new one.
2. Send "hello" in both sessions.
3. Capture packets in Wireshark and analyze differences in:
   - Source/destination ports.
   - Sequence/acknowledgment numbers.
   - Flags.
4. Annotate screenshots and summarize findings.

---

### **5. Website Download and TCP Analysis (20 marks)**  
**Task:**
- Download a file (e.g., a Project Gutenberg book).
- Capture the download in Wireshark and analyze:
  - TCP slow start, congestion window adaptation, fast retransmission.
- Generate and explain graphs:
  - Throughput over time.
  - Window size over time.
  - Congestion window over time.
  - Retransmissions.

**Steps:**
1. Use your browser to download a file while capturing traffic with Wireshark.
2. Identify phases like slow start, fast recovery, and retransmissions.
3. Use tools like Excel or Wireshark’s built-in features to generate graphs:
   - Filter and export relevant data (e.g., TCP stream throughput, window size).
4. Write detailed explanations for each graph.

---

### **6. Report Submission (10 marks)**  
**Task:**
- Ensure your report is:
  - Systematically organized.
  - Technically accurate.
  - Adheres to guidelines (e.g., citations, clear language).

**Steps:**
1. Structure your report by tasks.
2. Include all screenshots, explanations, and graphs.
3. Cite resources (e.g., tutorials, Wireshark documentation).
4. Proofread for clarity and completeness.

---

### **Hints for Success**
- Use **Wireshark tutorials** to learn filtering and analysis.
- Test commands/tools like `hping3` and `ncat` in a controlled environment.
- Break work into sections and focus on one at a time.
- Revisit the assignment rubric to align your submission with grading criteria.

Let me know if you need help with any of these steps, lovely! We’ll crush this assignment together. 💻✨