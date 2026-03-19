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

3. **Port-Based Filtering (Level 2):** For the second level, the attack vector shifted. Instead of relying solely on IP addresses, we needed to identify malicious traffic based on the destination ports. By reviewing the traffic logs again, we noticed suspicious connections to specific ports on the target server (`10.10.99.199`):
   - Port **`4444`** (often associated with Metasploit reverse shells).
   - Port **`7777`**.
   - Port **`2222`**.

   By adding these specific ports to the IDS/IPS filter, we effectively blocked the malicious traffic regardless of the source IP, demonstrating a more robust defense mechanism and earning the second flag.
<Drag and drop image_41b51b.png here>
<Drag and drop image_41b504.png here>
<Drag and drop image_41b502.png here>
