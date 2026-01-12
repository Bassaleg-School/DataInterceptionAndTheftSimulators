# **Teacher Notes: Evil Twin & IP Spoofing Simulator**

**Subject:** Computer Science / Digital Technology

**Key Stage:** KS4 (GCSE) & KS5 (A-Level)

**Topic:** Network Threats, Network Security, Ethical Hacking

## **1\. Overview**

This interactive HTML5 simulation demonstrates a **Man-in-the-Middle (MitM)** attack using an **"Evil Twin"** access point, followed by an **IP Spoofing** attack to bypass a router's firewall.

It is designed to visually separate the physical layer attack (Signal Strength/Connection) from the network layer attack (IP Header manipulation), utilizing the pedagogical principle of **chunking** to reduce cognitive load.

## **2\. Curriculum Links (Wales)**

### **WJEC GCSE Computer Science (New Spec)**

* **Unit 1 (Networks):** Understanding distinct types of network threats (eavesdropping, IP spoofing).  
* **Unit 1 (Network Security):** How firewalls use IP addresses to filter traffic.

### **WJEC A-Level Computer Science**

* **Unit 3 (Implications of Computer Use):** Privacy and the technical mechanics of interception.  
* **Unit 3 (Data Structures):** Understanding packet headers (Source/Destination IP).

## **3\. Lesson Walkthrough & Instructions**

### **Starter (5 Minutes)**

* **Discussion:** Ask students, "When you connect to 'Free WiFi' at a coffee shop, how do you know it is legitimate?"  
* **Concept:** Introduce the concept of an **Evil Twin**—a rogue access point that mimics a legitimate one.

### **Activity Phase 1: The Evil Twin (5-10 Minutes)**

* **Task:** Instruct students to open the ip\_spoofing\_sim.html file.  
* **Action:** Have them drag the **"Signal Booster"** slider.  
* **Observation:** Ask them to watch the Victim's connection line.  
  * *Question:* "At what percentage does the Victim switch connection?" (Answer: \>50%)  
  * *Concept:* Devices typically auto-connect to the strongest signal for a known SSID.  
* **Result:** The status changes to **"COMPROMISED"** and the "Locked" button becomes active.

### **Activity Phase 2: The Intercept (5 Minutes)**

* **Action:** Click **"Wait for Victim Login"**.  
* **Visual:** A blue packet travels from the Victim to the Attacker (Evil Twin).  
* **Key Moment:** The packet *stops* at the attacker.  
  * *Teacher Note:* Explain that this is the "Eavesdropping" phase. The attacker now has the password (visible in the log), but the attack isn't finished. If they don't forward the packet, the victim will know the internet is down.

### **Activity Phase 3: The Spoof (10-15 Minutes)**

* **The Problem:** The packet needs to go to the Router. The Router has a **Firewall** (shield icon).  
* **Experiment 1 (Failure):** Ask students to click **"Forward Packet"** *without* changing the IP.  
  * *Result:* The Router flashes **RED**. The log shows "Access Denied".  
  * *Reason:* The Router sees the source IP is 192.168.1.15 (The Attacker), which is not a trusted device.  
* **Experiment 2 (Success):** Reset the sim. Repeat steps. In the Packet Inspector, change **Source IP** to 192.168.1.5 (The Victim's IP).  
  * *Result:* The Router flashes **GREEN**.  
  * *Reason:* The Router believes the request came directly from the Victim.

### **Plenary (10 Minutes)**

* Review the "System Log" in the tool.  
* Discuss how the firewall was tricked.  
* **Crucial Question:** "Does IP Spoofing fix the return path?" (No—the router will send the reply to the Victim, not the Attacker. This is why this specific attack is often used for Denial of Service or blind injection, rather than two-way communication, unless the attacker controls the local subnet).

## **4\. Differentiation**

### **Support (Lower Ability)**

* **Focus:** Focus on the visual of the "mask." When the packet is spoofed, it gets a blue outline (mask) over the red core.  
* **Analogy:** Explain IP Spoofing like sending a letter with a fake return address. If the receiver replies, the letter goes to the person you pretended to be, not you.

### **Stretch (Higher Ability / A-Level)**

* **Challenge:** Ask students to explain **MAC Address vs. IP Address** in this scenario.  
  * *Prompt:* "We spoofed the IP. Did we spoof the MAC address?"  
  * *Answer:* Yes/No discussion. Technically, for the router to accept the frame at Layer 2, the MAC address usually matches the sender, but the IP header (Layer 3\) is what the firewall rules might be checking in this simplified model.  
* **Extension:** Discuss **HTTPS**.  
  * *Prompt:* "If the payload was encrypted (HTTPS), would this attack still work?"  
  * *Answer:* The *Intercept* would fail (we couldn't read the password), but the *Spoofing* (tricking the router) might still be mechanically possible, though useless for data theft without SSL stripping.

## **5\. Technical Troubleshooting**

* **Files:** Ensure the HTML file is saved locally or on a shared drive. It does not require an internet connection to run (icons are cached or have fallbacks).  
* **Screen Size:** If using tablets/small laptops, ensure the browser is maximized to see the "Hacker Console" footer clearly.