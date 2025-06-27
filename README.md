# Task-4 Setup and Use a Firewall on Windows/Linux

A firewall is a security system that monitors and controls incoming and outgoing network traffic based on predetermined rules, acting as a barrier between a trusted internal network and untrusted external networks (like the internet). Its main purpose is to block unauthorized access while allowing legitimate communication.

A firewall operates at different OSI layers:

* **Network Layer (Layer 3):** Inspects IP addresses and protocols; used by packet-filtering firewalls.

* **Transport Layer (Layer 4):** Analyzes TCP/UDP ports and connection types.

* **Application Layer (Layer 7):** Examines application data (e.g., HTTP, FTP); advanced firewalls like NGFWs operate here for deep inspection and threat detection.

## Windows Defender Firewall

Windows Defender Firewall is a built-in security feature in Microsoft Windows that monitors and controls incoming and outgoing network traffic based on predefined or user-defined security rules. It helps protect your computer by blocking unauthorized access while allowing legitimate communication, acting as a barrier between your device and potential threats from local networks or the internet.

## Listing Current Firewall Rules

1. **Open Control Panel**

   * Press `Win + R`, type `control`, and press Enter.

2. Go to:
   **System and Security** → **Windows Defender Firewall**

3. On the left sidebar, click:
   **Advanced settings**

4. This opens the **Windows Defender Firewall with Advanced Security** window.

5. In the left pane, select:

   * **Inbound Rules** → to view rules for incoming traffic
   * **Outbound Rules** → to view rules for outgoing traffic

Here, you can:

* View, enable/disable, or delete existing rules
* Create new rules for programs, ports, IP addresses, etc.

![image](https://raw.githubusercontent.com/lakshaytondwal/task-4/refs/heads/main/img/1.png)

As we can see, our machines can communicate to the Windows FTP server.

![image](https://raw.githubusercontent.com/lakshaytondwal/task-4/refs/heads/main/img/2.png)

## Setting Up a Firewall Rule

Now we can set up a firewall rule on our Windows machine to drop all connections from `192.168.3.4`. To make it short we can use this powershell script or `CMDLET`

```powershell
New-NetFirewallRule -DisplayName "Block FTP from 192.168.3.4" -Direction Inbound -RemoteAddress 192.168.3.4 -Protocol TCP -LocalPort 21 -Action Block
```

![image](https://raw.githubusercontent.com/lakshaytondwal/task-4/refs/heads/main/img/3.png)

As we can see our machine failed to connect to `192.168.3.2` ie or Windows FTP server.

![image](https://raw.githubusercontent.com/lakshaytondwal/task-4/refs/heads/main/img/4.png)

## How does Firewall filters traffic?

A **firewall filters traffic** by inspecting network packets and applying rules based on criteria like:

* **IP address**
* **Port number**
* **Protocol (TCP, UDP, ICMP)**
* **Application or service**

It either **allows**, **blocks**, or **logs** traffic depending on whether the packet matches a defined rule. This helps control access to and from a network, protecting against unauthorized or harmful connections.

---
