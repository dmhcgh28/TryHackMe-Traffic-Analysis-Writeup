### Interactive Traffic Analysis Simulation

During the practical exercise, we used the simulated static site to analyze network traffic and identify malicious activity.

1. **Observation:** The network animation showed red nodes indicating suspicious traffic. Once the server was compromised, we were tasked with analyzing the logs to restore the network.
<img width="675" height="426" alt="image" src="https://github.com/user-attachments/assets/b1deafc8-e272-49ad-a736-afbf2aa739ec" />


### Task 2 Answers & Explanations:
<img width="673" height="678" alt="image" src="https://github.com/user-attachments/assets/110a8f14-e403-4c2e-a8ad-11e282e86ccf" />

* **Which Security Control Level covers contain creating security policies?**
    * **Answer:** `Administrative`
    * **Explanation:** Security controls are generally categorized into three levels: Physical, Technical (or Logical), and Administrative. While physical controls deal with locks and technical controls deal with software/firewalls, Administrative controls focus on the human and organizational element. This includes drafting security policies, compliance regulations, and employee training guidelines.

* **Which Access Control element works with data metrics to manage data flow?**
    * **Answer:** `Load Balancing`
    * **Explanation:** Load balancers act as a traffic cop for network requests. They continuously monitor data metrics (such as server health, current active connections, or response times) to intelligently distribute incoming traffic across multiple servers. This prevents any single server from becoming a bottleneck, ensuring high availability and smooth data flow.

* **Which technology helps correlate different tool outputs and data sources?**
    * **Answer:** `SOAR`
    * **Explanation:** SOAR stands for **Security Orchestration, Automation, and Response**. In a modern Security Operations Center (SOC), analysts use dozens of different tools (firewalls, EDRs, SIEMs, etc.) that generate thousands of alerts. SOAR technologies are designed to integrate (orchestrate) all these disparate tools, automatically correlate their data outputs to filter out false positives, and execute automated response playbooks to contain threats faster.
<img width="670" height="693" alt="image" src="https://github.com/user-attachments/assets/427c9d42-49ed-4bd9-833c-dc42a9011564" />



   We entered these two malicious IP addresses into the IDS/IPS System Filter Table. This action successfully blocked the malicious packets and restored the network, granting us the first flag.
<Drag and drop the filter photo image_420b79.png here>
<Drag and drop the first flag photo image_420b78.png here>


### Task 3 **Port-Based Filtering** 
This task delved into Network Traffic Analysis (NTA), explaining how intercepting and monitoring network data is crucial for detecting anomalies. 

<img width="1279" height="694" alt="image" src="https://github.com/user-attachments/assets/b5aa6498-26f9-4045-a0bf-42518d188790" />


To apply these concepts, a static simulation was provided to restore a compromised network by analyzing logs and configuring an IDS/IPS filter.

### Phase 1: Identifying Malicious IPs (Level 1)
* **Observation:** The network animation showed red nodes indicating suspicious traffic targeting the main server (`10.10.99.199`).

<img width="1362" height="683" alt="image" src="https://github.com/user-attachments/assets/31c8e02c-ff33-4a52-934b-c15221272d9e" />
<img width="619" height="479" alt="image" src="https://github.com/user-attachments/assets/c55a2fac-02f0-4e4d-86c0-c181c67a17f7" />



* **Log Analysis:** By cross-referencing the "Traffic Analyser" logs with the "IDS/IPS System" alerts, the exact sources of the attack were identified:
  * **IP `10.10.99.99`**: Flagged for "Multiple Login Attempts" and "Metasploit Traffic".
  * **IP `10.10.99.62`**: Flagged for "Bad Traffic".

<img width="512" height="644" alt="image" src="https://github.com/user-attachments/assets/f67caaf2-0d64-4b6e-9df2-2b12bb0b0205" />


* **Action & Result:** Adding these two IPs to the IDS/IPS Filter Table successfully blocked the malicious packets, restoring the network and yielding the first flag.
<img width="478" height="385" alt="image" src="https://github.com/user-attachments/assets/81584835-4b21-49f1-8532-937ba403299a" />

<img width="487" height="379" alt="image" src="https://github.com/user-attachments/assets/89e534c3-5b16-427f-b256-47b002d623a9" />


### Phase 2: Port-Based Filtering (Level 2)
* **Observation:** In the second level, the attacker shifted tactics. Instead of relying on specific IP addresses, the malicious traffic came from multiple sources.
* **Log Analysis:** A deeper look at the logs revealed a pattern based on the *destination ports* on the target server (`10.10.99.199`):
  * **Port `4444`**: Frequently associated with Metasploit reverse shells.
  * **Port `7777`** and **Port `2222`**: Showing anomalous inbound connections.
* **Action & Result:** Blocking IP addresses would be ineffective against spoofed or dynamic IPs. The correct mitigation strategy was to filter the traffic based on these specific ports. Adding ports 4444, 7777, and 2222 to the IDS/IPS filter neutralized the threat regardless of its origin, providing the second flag.
[ Drag and drop image_41b51b.png here ]
[ Drag and drop image_41b504.png here ]
[ Drag and drop image_41b502.png here ]

### Final Flags:
* **Level-1 Flag:** `THM{PACKET_MASTER}`
* **Level-2 Flag:** `THM{DETECTION_MASTER}`

   By adding these specific ports to the IDS/IPS filter, we effectively blocked the malicious traffic regardless of the source IP, demonstrating a more robust defense mechanism and earning the second flag.
<Drag and drop image_41b51b.png here>
<Drag and drop image_41b504.png here>
<Drag and drop image_41b502.png here>
