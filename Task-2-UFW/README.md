# 🔥 Task 2: Basic Firewall Configuration with UFW (Uncomplicated Firewall)

## Objective
The goal of this task was to implement a basic host-based firewall using UFW on a Linux system (Kali VM) to control network traffic, specifically demonstrating the principle of **default denial** while selectively allowing necessary services.

## Configuration Environment
* **Operating System:** Kali Linux (on VMware Fusion)
* **Firewall Tool:** UFW (Uncomplicated Firewall)

## Core Security Strategy
The configuration adheres to the fundamental security principle of **"default deny."** This means all incoming connections are blocked by default, and only explicitly defined services (ports) are allowed access.

## Configuration Steps and Logic
The following commands were executed and saved in the `ufw_configuration.sh` script:

### 1. Reset and Default Policies
The firewall was reset and the default policies were set to ensure a secure baseline:

| Command | Action | Security Implication |
| :--- | :--- | :--- |
| `sudo ufw default deny incoming` | **Blocks ALL incoming traffic.** | This is the most important hardening step, closing all ports by default. |
| `sudo ufw default allow outgoing` | Allows all internal traffic to reach the internet. | Necessary for the host to function normally (e.g., updates, browsing). |

### 2. Service Configuration
Rules were added to explicitly permit or deny specific services as required by the task:

| Command | Action | Protocol/Port | Security Rationale |
| :--- | :--- | :--- | :--- |
| `sudo ufw allow ssh` (or `allow 22/tcp`) | **ALLOWS** incoming SSH traffic. | TCP Port 22 | Necessary for secure remote administration of the system. |
| `sudo ufw deny http` (or `deny 80/tcp`) | **DENIES** incoming HTTP traffic. | TCP Port 80 | Prevents the system from serving unsecured web pages, aligning with the requirement to block general web access. |

### 3. Enabling the Firewall
The firewall was enabled to make the rules active:

* `sudo ufw enable`

### 4. Verification and Status Check
The final step was to verify that the rules were correctly applied before and after enabling the service:

* `sudo ufw status numbered`
    * **Result:** The output confirmed the **Deny** policy for incoming traffic, the **Allow** rule for Port 22/SSH, and the explicit **Deny** rule for Port 80/HTTP.

***Note:** The `ufw_configuration.sh` script contains the exact sequence of commands executed, and the `ufw_status.png` file provides visual verification of the active rules.* 

## Security Impact
* **Reduced Attack Surface:** By setting the default policy to deny incoming traffic, the system's attack surface is drastically reduced. Only the essential administrative port (22) is open.
* **Access Control:** The explicit denial of HTTP (Port 80) ensures that any service attempting to run on that port will be inaccessible from the outside network, acting as a second layer of defense even if a web service is mistakenly launched.

## Deliverables Checklist
* ✅ **`ufw_configuration.sh`:** Script of all UFW commands.
* ✅ **`README.md`:** Explanation of configuration (this file).
* ✅ **`ufw_status.png`:** Screenshot confirming the active firewall rules.

***

