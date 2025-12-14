# 🛡️ Task 4: Comprehensive Report on Common Network Security Threats

## I. Introduction
Network security threats represent deliberate actions to compromise the confidentiality, integrity, or availability of a network and its resources. This report provides an analysis of three prevalent threats—Denial of Service (DoS), Man-in-the-Middle (MITM), and Spoofing—detailing their mechanisms, impact, and critical mitigation strategies.

## II. Denial of Service (DoS) Attacks

### A. How a DoS Attack Works
A DoS attack aims to make a machine or network resource unavailable to its intended users by temporarily or indefinitely disrupting the services of a host connected to the Internet.
* **Mechanism:** Overwhelming the target system's resources (CPU, memory, network bandwidth) with an immense volume of illegitimate requests or corrupted packets from a single source.
* **DDoS (Distributed DoS):** A far more powerful variation where the attack traffic originates from many different sources (often a 'botnet' of compromised machines), making it harder to block.

### B. Impact
* **Availability Loss:** Website or service downtime, which can last hours or days.
* **Financial Loss:** Direct loss of revenue from sales, recovery costs, and potential regulatory fines.
* **Reputational Damage:** Loss of customer trust due to service failure.

### C. Mitigation and Prevention
| Strategy | Description |
| :--- | :--- |
| **Rate Limiting** | Restricting the number of requests a server will accept over a certain time window to prevent a single IP from overwhelming resources. |
| **Intrusion Prevention Systems (IPS)** | Devices that monitor network traffic for malicious signatures and automatically drop suspect packets. |
| **DDoS Mitigation Services (CDNs)** | Cloud-based services (like Cloudflare or Akamai) that act as a proxy, absorbing large-scale attacks and filtering malicious traffic before it reaches the origin server. |

---

## III. Man-in-the-Middle (MITM) Attacks

### A. How an MITM Attack Works
The attacker secretly intercepts and potentially alters communication between two parties who believe they are communicating directly with each other. The core goal is eavesdropping and data theft.
* **Mechanism:** Common techniques include **ARP Spoofing** (tricking a local network into sending traffic through the attacker's machine) and **DNS Spoofing** (redirecting users to malicious websites).

### B. Impact
* **Data Theft:** Capture of sensitive information, including credentials, bank details, and personal data.
* **Session Hijacking:** Stealing session cookies to impersonate a legitimate user.
* **Data Manipulation:** Modifying the transmitted information without the knowledge of the communicating parties.

### C. Mitigation and Prevention
* **Enforce TLS/SSL (HTTPS):** Encryption makes intercepted data unreadable. **Always** ensure web applications use HTTPS.
* **Strong Authentication:** Implement Multi-Factor Authentication (MFA) to prevent session hijacking from stolen passwords alone.
* **Virtual Private Networks (VPNs):** Encrypting traffic over untrusted public Wi-Fi networks.

---

## IV. Spoofing Attacks

### A. How a Spoofing Attack Works
Spoofing involves an attacker pretending to be a trustworthy source by falsifying data, such as IP addresses or email headers.
* **IP Spoofing:** Changing the source IP address in a network packet to hide the attacker's identity or bypass IP-based filters.
* **Email Spoofing (Phishing):** Changing the sender's address in an email to appear as a legitimate sender (e.g., a bank or a CEO).

### B. Impact
* **Bypass Security:** Tricking firewalls or filtering systems that rely on trusted IP addresses.
* **Successful Phishing:** Leading users to believe a malicious email is legitimate, resulting in credential compromise or malware installation.
* **Repudiation:** Making it difficult to trace the true source of an attack.

### C. Mitigation and Prevention
* **Email Authentication:** Employing standards like **SPF** (Sender Policy Framework), **DKIM** (DomainKeys Identified Mail), and **DMARC** (Domain-based Message Authentication, Reporting, and Conformance) to verify the sender's identity.
* **Packet Filtering:** Implementing ingress and egress filtering on routers and firewalls to block packets with impossible or unauthorized source IP addresses.
* **Network Access Control (NAC):** Strictly controlling which devices are allowed to connect to the network.

---

## V. Conclusion
Effective network security relies on a layered defense strategy. Understanding the mechanisms and impacts of threats like DoS, MITM, and Spoofing is the foundation for implementing appropriate technical and organizational countermeasures to ensure the continued security and availability of network resources.