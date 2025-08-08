# Snort IDS/IPS Deployment & Evasion Techniques

## 📌 Project Overview

This project demonstrates the deployment, configuration, and testing of **Snort**, an open-source Intrusion Detection and Prevention System (IDS/IPS), in a controlled lab environment. The goal was to simulate real-world attack patterns, create custom detection rules, and evaluate Snort’s ability to detect and mitigate threats — including attempts to evade detection.

This work was conducted as part of my **MSc in Applied Cyber Security** at **Technological University Dublin**.

---

## 🛠 Technologies & Tools Used

* **Operating Systems:** Ubuntu 22.04 (Detection Machine), Kali Linux (Attacking Machine)
* **Snort** – IDS/IPS configuration and rule creation
* **Wireshark** – Packet capture and analysis
* **VirtualBox** – Lab virtualization
* **Networking:** Bridged network configuration
* **Scripting:** Bash (automation for testing rules)

---

## ⚙️ Lab Setup

**Detection Machine (Snort IDS/IPS):**

* OS: Ubuntu 22.04 LTS
* Snort configured in both **IDS mode** (alert only) and **IPS mode** (active blocking)
* Custom Snort rules created to detect specific attack patterns

**Attacking Machine:**

* OS: Kali Linux
* Tools: Nmap, Metasploit, custom scripts for simulating evasion techniques

**Network Configuration:**

* Bridged networking to simulate real-world packet flow between machines
* Packet capture and logging enabled for post-analysis

---

## 🔧 Implementation Steps

1. **Snort Installation & Configuration**

   ```bash
   sudo apt update
   sudo apt install snort
   snort --version
   ```

   Configured `/etc/snort/snort.conf` to set HOME\_NET and rule paths.

2. **Custom Rule Creation**

   * Wrote Snort rules to detect:

     * Nmap scans
     * Brute-force login attempts
     * Malicious payload patterns
   * Example rule to detect ICMP ping:

     ```
     alert icmp any any -> $HOME_NET any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
     ```

3. **Attack Simulation**

   * Performed Nmap scans (`-sS`, `-A`, `--data-length` to attempt evasion)
   * Launched SSH brute-force attempts
   * Used fragmentation and obfuscation to bypass detection

4. **Evasion Testing**

   * Tested Snort's detection limits with altered packet sizes and timing
   * Logged successful/unsuccessful detections for analysis

5. **Packet Analysis**

   * Used Wireshark to verify packet arrival, rule triggering, and logging accuracy

---

## 📊 Key Results

* Successfully detected and logged multiple attack types:

  * TCP SYN scans
  * ICMP sweeps
  * SSH brute-force attempts
* Implemented **fine-tuning of detection rules** to reduce false positives.
* Identified limitations in default Snort rule sets when facing certain evasion techniques, leading to **improved custom rules**.

---

## 🔍 Lessons Learned

* IDS tuning is critical to balance between **detection coverage** and **false positive rates**.
* Real-world attackers often use **evasion techniques**, making **custom rule creation** essential.
* Combining Snort with tools like **Wireshark** improves visibility and verification of threats.

---

## 🛡 Recommendations

* Regularly update Snort rule sets from sources like Emerging Threats.
* Implement Snort in IPS mode for active mitigation in production environments.
* Integrate with **SIEM platforms** for centralized logging and correlation.

---

## 📂 Project Nature

This was a **lab-based, academic project** — no production networks were involved.
The environment was isolated, and all attack simulations were performed ethically.
