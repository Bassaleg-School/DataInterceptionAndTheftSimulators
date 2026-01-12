# **Teacher Notes: Session Hijacking Simulation**

**Resource:** "Dai's Ducklings" E-Commerce Simulation

**Context:** GCSE Computer Science (Made for Wales) \- Cyber Security & Network Security

**Pedagogical Approach:** Dual Coding, Chunking, Inquiry-Based Learning

## **1\. Concept Overview**

This single-file simulation is designed to demystify **Session Hijacking** by visualizing the usually invisible "handshake" between a client and a server.

It removes the complexity of setting up real Virtual Machines or using packet sniffers (like Wireshark), allowing students to focus purely on the **logic** of the vulnerability: *if you possess the session token, the server believes you are the user.*

### **Learning Objectives**

1. Understand that servers use **Session IDs** (cookies) to recognise logged-in users because HTTP is stateless.  
2. Demonstrate how an attacker can steal a session ID to impersonate a victim.  
3. Observe that "hacking" a session allows access without knowing the user's password.

## **2\. Activity Walkthrough**

### **Phase 1: The Victim (Alice)**

* **Action:** Ask students to interact with the **Left Panel**.  
* **Task:** Log in as "Alice".  
* **Observation:** Watch the **Middle Panel (Network)**. A packet appears: Set-Cookie: ID=DAI-xxxx-QUACK.  
* **Teaching Point:** Explain that this "ID card" is what the server uses to remember Alice. It is not her password; it is her temporary pass.

### **Phase 2: The Attack**

* **Action:** Direct attention to the **Middle Panel**.  
* **Task:** Identify the Session ID.  
* **Action:** Move to the **Right Panel (Attacker)**.  
* **Task:** Enter the stolen ID into the "Hacker Developer Tools" and click **Inject Cookie**.  
* **Result:** The attacker's screen refreshes and shows "Welcome Alice".

### **Phase 3: The Impact (Synchronised State)**

* **Action:** Ask the student (as the Attacker) to buy the "Golden Cascade" duck (£500).  
* **Observation:** Look immediately at the **Left Panel (Alice)**.  
* **Result:** Alice's balance drops instantly on her screen too.  
* **Teaching Point:** This proves the attacker isn't just looking at a screenshot; they have live access to the account on the server.

## **3\. Design Rationale & Trade-offs (Teacher Intel)**

We made specific design choices to reduce *extraneous cognitive load* and focus on the core concept. Here is what you need to know about those trade-offs:

### **A. The "Logout" Button Omission**

* **What we did:** We deliberately removed the "Logout" button for Alice, leaving only "Close Browser".  
* **Why:** In a real-world scenario, clicking "Logout" usually destroys the session token on the server immediately, preventing the hack.  
* **Pedagogy:** Including "Logout" often confuses students who click it *before* attempting the hack, causing the simulation to fail. By removing it, we ensure the hack works every time for the demonstration.  
* **Classroom Discussion:** Ask students: *"How could Alice have prevented this?"* (Answer: By explicitly logging out, which invalidates the token, rather than just closing the window).

### **B. HTTP vs. HTTPS (The "Visible" Network)**

* **What we did:** The network panel shows the Session ID in plain text.  
* **Why:** To visualise the data flow.  
* **The Reality:** Modern websites use HTTPS (TLS/SSL), which encrypts this traffic. A hacker on the WiFi would see scrambled data.  
* **Classroom Discussion:** Explain that this simulation assumes the website is using an older, insecure **HTTP** connection, or that the attacker has performed a sophisticated "SSL Stripping" attack. This highlights the importance of the padlock icon (HTTPS).

### **C. The "Simple" Session ID**

* **What we did:** IDs generate as DAI-1234-QUACK.  
* **The Reality:** Real session IDs are long, complex hashes (e.g., b49a59f93...).  
* **Pedagogy:** We used a recognizable format to make it easier for students to spot the pattern and type it out (Chunking), avoiding frustration with copying complex strings.

## **4\. Discussion Questions**

1. **Why didn't the attacker need Alice's password?** (Because the server trusts the Session ID).  
2. **If Alice changes her password while the attacker is logged in, will the attacker be kicked out?** (Usually, yes—changing a password normally resets all active sessions. This is a good extension question).  
3. **Why is using public WiFi for banking risky without a VPN?** (If the connection isn't perfectly secure, this "sniffing" can happen).