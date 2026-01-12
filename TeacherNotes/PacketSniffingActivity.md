# **Teacher Notes: Packet Sniffing Simulator**

**For: GCSE Computer Science & Digital Technology** **Curriculum Alignment:** WJEC/Eduqas GCSE Computer Science (Networks & Cyber Security), Digital Technology (Data Security).

## **Overview**

This standalone HTML simulator allows students to experience the concept of packet sniffing without the legal or technical complexities of using real tools like Wireshark on a live network. It leverages **dual coding** by presenting a visual network topology alongside a raw data stream, helping students connect the abstract concept of "data transmission" with the concrete risk of "interception."

## **Learning Objectives**

By the end of this activity, students should be able to:

1. **Define Packet Sniffing:** Understand that data travels in packets that can be intercepted.  
2. **Identify Risks:** Recognise that unencrypted (HTTP) or weakly encrypted (WEP) data allows attackers to read sensitive information like passwords.  
3. **Analyse Metadata:** Observe that even when encryption (WPA3/HTTPS) is used, "metadata" such as source and destination IP addresses remains visible.  
4. **Distinguish Techniques:** Differentiate between **Passive** sniffing (listening) and **Active** sniffing (ARP Poisoning/Man-in-the-Middle).

## **Lesson Activity Guide**

### **1\. The "Open" Network (Baseline Assessment)**

* **Settings:** Encryption: None (Open), Mode: Passive.  
* **Task:** Ask students to watch the traffic from "Laptop A".  
* **Observation:** They will see HTTP packets.  
* **Key Question:** "If I am sitting in the corner of this coffee shop with a laptop, what can I see?"  
* **Discovery:** Click on a packet. The payload is fully visible. If they catch a POST packet, they can read the username and password.

### **2\. The Failed Shield (WEP)**

* **Settings:** Encryption: WEP, Mode: Passive.  
* **Context:** Explain that WEP was the old standard for WiFi security.  
* **Task:** Observe the traffic.  
* **Observation:** The protocol column might still show HTTP, but the info column says "(WEP Decrypted)".  
* **Teaching Point:** WEP has mathematical flaws (IV weakness) that allow sniffers to "crack" the key in minutes. For the purpose of this simulation, we treat it as if the hacker already has the key.  
* **Visual Cue:** Note how the packet details show "\[WEP KEY FOUND\]".

### **3\. The Secure Standard (WPA3 & HTTPS)**

* **Settings:** Encryption: WPA3, Mode: Passive or Active.  
* **Task:** Look at traffic from "Laptop B" (Admin) or switch the network to WPA3.  
* **Observation:** The payload is now scrambled hex code (...7f 8a 2b...).  
* **Crucial Learning Point:** Ask students to look at the **Source** and **Destination** columns.  
  * *Can we read the message?* No.  
  * *Do we know who they are talking to?* **Yes.**  
  * *Why does this matter?* Even encrypted traffic reveals patterns (e.g., we know the user is talking to the bank's IP address, even if we can't see the transaction).

### **4\. Active vs. Passive Sniffing**

* **Concept:**  
  * **Passive:** The hacker just listens. Hard to detect.  
  * **Active:** The hacker manipulates the network (e.g., ARP Poisoning) to force traffic to flow through them.  
* **Demo:** Toggle the "Sniffing Mode" to Active.  
* **Visual:** A red line connects the sniffer to the main network path, pulsating to represent the injection of malicious ARP packets.  
* **Discussion:** Why is Active sniffing riskier for the hacker? (It generates noise and can be detected by intrusion detection systems).

## **Technical Explanations for Curious Students**

"Why can I still see packets in WPA3?"  
In a real scenario, if you are in "Monitor Mode" (Passive), you can see the raw 802.11 frames flying through the air, but the content is encrypted garbage. This simulator shows "Encrypted Data" to represent those raw frames.  
"What is ARP Poisoning?"  
(Simulated by 'Active' mode)  
Computers use ARP to map IP addresses to MAC addresses. ARP Poisoning involves the hacker sending fake "I am the Router" messages to the victim, and "I am the Victim" messages to the Router. The simulator simplifies this by showing the red attack line diverting the traffic flow.

## **Differentiation Strategies**

* **Support:** Focus solely on the difference between the red text (stolen credentials) and the grey text (encrypted data). Use the "Display Filter" to isolate "Laptop A" and ignore the noise.  
* **Stretch:** Ask students to explain why "Laptop B" (Admin) was safe even when the network encryption was set to "None". (Answer: They were using TLS/HTTPS, which encrypts at the Application layer, providing a second tunnel of security regardless of the WiFi).

## **Assessment Questions**

1. Which protocol allowed us to see the user's password clearly? (HTTP)  
2. If I am using WPA3 WiFi, can a hacker see which websites I am visiting? (Yes, via IP address/DNS, though the specific page content is hidden).  
3. Describe the difference between Passive and Active sniffing.

| Question / Task |
| ----- |
| **1\. Define the purpose of a packet analyser (sniffer).** |
| *Answer: Software or hardware used to intercept and analyse data traffic on a network.* |
| **2\. Set the simulator to 'Encryption: None'. Select a packet from Laptop A. What sensitive data can you read?** |
| *Answer: You can read the HTTP headers and the payload, specifically the username and password.* |
| **3\. Switch to 'Encryption: WPA3'. Look at the 'Info' column. How has the data changed?** |
| *Answer: The data is now 'Encrypted Data' and looks like scrambled letters/numbers (Hex).* |
| **4\. In WPA3 mode, look at the 'Destination' column. What information is NOT hidden by encryption?** |
| *Answer: The IP address of the destination server (metadata) is still visible.* |
| **5\. Switch to 'Encryption: WEP'. Why can you read the message even though it says it is encrypted?** |
| *Answer: WEP is a weak encryption standard that is easily cracked. The simulator shows it as 'Decrypted' to simulate a hacker breaking the key.* |
| **6\. Switch Sniffing Mode to 'Active'. What is happening in the network diagram?** |
| *Answer: A red line appears, showing the sniffer interfering with the connection (ARP Poisoning) to redirect traffic.* |
| **7\. Explain the key difference between Active and Passive sniffing.** |
| *Answer: Passive sniffing involves only listening (stealthy), while Active sniffing involves manipulating network traffic to intercept data (riskier).* |
