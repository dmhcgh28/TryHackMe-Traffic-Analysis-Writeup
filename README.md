### Interactive Traffic Analysis Simulation

During the practical exercise, we used the simulated static site to analyze network traffic and identify malicious activity.

1. **Observation:** The network animation showed red nodes indicating suspicious traffic. Once the server was compromised, we were tasked with analyzing the logs to restore the network.
<Drag and drop images image_420f1a.png, image_420f19.png, and image_420f18.png here>

2. **Log Analysis & Filtering (Level 1):** By cross-referencing the "Traffic Analyser" with the "IDS/IPS System" logs, we pinpointed the exact sources of the attack:
   - **IP `10.10.99.99`**: Flagged for "Multiple Login Attempts" and "Metasploit Traffic".
   - **IP `10.10.99.62`**: Flagged for "Bad Traffic".
<Drag and drop the logs photo image_420ed7.png here>

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
