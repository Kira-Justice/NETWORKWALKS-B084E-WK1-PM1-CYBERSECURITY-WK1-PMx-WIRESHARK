# NetworkWalks SOC Analyst Internship - Wireshark Threat Hunting Labs

This repository contains my write-ups, methodology, and notes from completing the hands-on Security Operations Center (SOC) packet analysis labs during my **NetworkWalks Internship**. The primary focus of these labs was utilizing **Wireshark** to parse raw packet captures (`.pcap`/`.pcapng`), trace malicious network activity, reconstruct application streams, and investigate indicators of compromise (IoCs).

---

## 🛠️ Skills & Technologies Covered
* **Tools:** Wireshark, Tshark
* **Protocols Analyzed:** TCP, HTTP, SIP, RTP, SMTP
* **Methodologies:** Packet Filtering, Stream Reconstruction, Baseline Anomaly Detection, VoIP Traffic Decoding

---

## 📁 Lab Modules & Objectives

### 1. Identify Attacker IP
* **Objective:** Isolate malicious traffic signatures within a compromised environment to determine the external attacker's source IP address.
* **Key Steps:** Analyzed network baselines, filtered for unusual outbound requests, and flagged suspicious infrastructure endpoints.

### 2. TCP Stream Reconstruction (Stream 1 & Stream 2)
* **Objective:** Follow low-level TCP handshakes and payloads to reconstruct conversations between hosts.
* **Key Steps:** Used Wireshark’s *Follow TCP Stream* feature to isolate directionality (Client-to-Server in red, Server-to-Client in blue) and successfully extracted a hidden metadata note embedded in the server responses.

### 3. Plain Text File Analysis
* **Objective:** Track down unauthorized data exfiltration or file downloads on an internal corporate intranet (`intranet.company.local`).
* **Key Steps:** Filtered for `http.request.method == "GET"`, located an unencrypted file download originating from the `/download/` directory, and reconstructed the stream to uncover a corporate financial report prepared by the company Controller.

### 4. Catch the Brute Forcer
* **Objective:** Detect and isolate an active credential-stuffing or password brute-force attack.
* **Key Steps:** Inspected anomalous authentication traffic patterns, filtered for repeated failed login response codes, and profiled the attacker's automation behavior.

### 5. Catch the Spammer
* **Objective:** Track down an internal asset or external rogue agent using the network to distribute spam emails.
* **Key Steps:** Monitored Mail Exchange signaling anomalies (SMTP traffic) to identify mass-mailing patterns and unauthorized relay abuse.

### 6. VoIP & SIP Traffic Forensics
* **Objective:** Inspect an active voice call traversing the network infrastructure.
* **Key Steps:** 
  * Parsed Session Initiation Protocol (`SIP`) headers (`INVITE`, `180 Ringing`, `200 OK`) to identify the calling extension (**101**).
  * Extracted the Real-time Transport Protocol (`RTP`) voice payload packets (transmitting every 60ms).
  * Used Wireshark's built-in **VoIP Calls Player** to decode and play back the audio stream, confirming the call was answered by the target organization's receptionist.

---

## 🚀 Key Takeaways
Through these labs, I sharpened my ability to translate raw network packets into actionable forensic evidence. Understanding the nuances of protocol behaviors—whether it's the timing of RTP packets or the structure of a SIP header—is essential for any tier-1/tier-2 SOC Analyst defending modern enterprise infrastructures.

***
*Completed as part of my practical training curriculum at Islamic Universit
