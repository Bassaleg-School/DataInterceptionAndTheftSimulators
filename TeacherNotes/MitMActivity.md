# **Teacher Guide: Man-in-the-Middle (MitM) Simulation**

## **"The DDR5 RAM Heist"**

**Target Group:** GCSE Computer Science (Year 10/11)

**Curriculum Link:** Cyber Security (Threats to Computer Systems and Networks)

**Duration:** 15-20 Minutes (Standalone Activity) or part of a 1-hour lesson on Network Threats.

### **1\. Educational Context & Pedagogy**

This simulation is designed based on **Active Learning** and **Cognitive Load Theory**.

* **Abstract to Concrete:** MitM attacks are often taught via static diagrams. This tool allows students to *become* the router, making the abstract concept of packet switching and interception concrete.  
* **Chunking:** The conversation is broken down into discrete "packets". Students process one line of data at a time, preventing cognitive overload.  
* **Dual Coding:** Visual cues (Red for attacker, Blue for victim, directional arrows) reinforce the flow of data.

### **2\. Learning Objectives**

By the end of this activity, students will be able to:

1. **Explain** how data is intercepted between a sender and receiver.  
2. **Demonstrate** how **Confidentiality** is breached (Interception/Eavesdropping).  
3. **Demonstrate** how **Integrity** is breached (Data Modification).  
4. **Demonstrate** how **Availability** is breached (Packet Dropping/DoS).

### **3\. Activity Walkthrough**

#### **Phase 1: The Setup (5 Mins)**

* **Scenario:** Tell the class they are stepping into the shoes of a cyber-criminal named "Eve".  
* **The Context:** Alice is selling scarce DDR5 RAM. Bob wants to buy it.  
* **The Goal:** Students must sit in the middle, wait for the shipping address to be sent, and change it to their own address (Unit 1, Bassaleg Road).

#### **Phase 2: The Simulation (10 Mins)**

Instruct students to open the mitm\_attack.html file in their browser.

* **Step 1: Passive Reconnaissance (Eavesdropping)**  
  * Students simply click FORWARD \>\>.  
  * *Teaching Point:* Ask students: "Does Alice or Bob know you are there?" (Answer: No, the chat looks normal to them). This demonstrates a breach of **Confidentiality**.  
* **Step 2: The Attack (Integrity Violation)**  
  * When the packet containing "12 High St, Newport..." appears, the interface warns them.  
  * Students must click MODIFY, delete the text, and type the target address (Unit 1, Bassaleg Road).  
  * *Teaching Point:* This demonstrates a breach of **Integrity**. The message Bob sent is *not* the message Alice received.  
* **Alternative Path: Denial of Service (Availability)**  
  * Encourage some students to use the DROP 🗑️ button on a random packet.  
  * *Teaching Point:* The chat stops. The receiver never gets the message. This demonstrates a breach of **Availability**.

#### **Phase 3: The Review (Plenary)**

Once the "ATTACK SUCCESSFUL" screen appears, ask students to click **"REVIEW EVIDENCE 🔍"**.

**Discussion Questions:**

1. *Look at Alice's screen vs. Bob's screen. Why are they different?*  
   * (Highlights that digital trust is based on the assumption that the channel is secure).  
2. *If this were https (encrypted), what would the 'Packet Sniffer' box look like?*  
   * (It would be jumbled ciphertext. You could still intercept it, but you couldn't read or modify it meaningfully).

### **4\. Technical Concepts Mapped**

| Action in Sim | Cyber Security Concept | CIA Triad Component |
| :---- | :---- | :---- |
| **Reading the packet** in the black box | Packet Sniffing / Interception | **Confidentiality** (Broken) |
| **Modifying text** and forwarding | Data Manipulation / Injection | **Integrity** (Broken) |
| **Dropping** the packet | Packet Loss / Denial of Service | **Availability** (Broken) |
| **Alice sending** the goods to the wrong place | Social Engineering / Trust Exploitation | N/A |

### **5\. Differentiation**

* **Support:** Direct students to watch the "Instruction Bar" at the top closely—it tells them exactly when to act.  
* **Stretch:** Ask students to restart and try to "break" the conversation by modifying an earlier packet (e.g., changing the price from £80 to £800). Ask them to predict how the "code" (the script) handles this logical break.

### **6\. Troubleshooting**

* **"I modified the text but failed\!"**  
  * Check if they typed the specific address required (Unit 1, Bassaleg Road). The simulation checks for this string specifically to confirm the "Heist" was successful.  
* **"The simulation ended abruptly."**  
  * They likely dropped a packet or clicked forward without modifying the critical address packet. Use the RESTART ↻ button.