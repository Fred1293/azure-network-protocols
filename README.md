# azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/bp6DSLQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Create a Resource Group,
Create a Windows 10 Virtual Machine (VM) -> 
While creating the VM, select the previously created Resource Group -> 
While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet ->
Create a Linux (Ubuntu) VM,
While creating the VM, select the previously created Resource Group and Vnet.

<br />

<p>
<img src="https://i.imgur.com/u71jqj9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Use Remote Desktop to connect to your Windows 10 Virtual Machine -> 
Within your Windows 10 Virtual Machine, Install Wireshark -> 
Open Wireshark and filter for ICMP traffic only -> 
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM ->
Observe ping requests and replies within WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/7gSzghS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark ->
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM ->
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic - >
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity -> 
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using ->
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working),
Stop the ping activity

</p>
<br />

<p>
<img src="https://i.imgur.com/MmwaSvp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Back in Wireshark, filter for SSH traffic only -> 
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address) -> 
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark ->
Exit the SSH connection by typing ‘exit’ and pressing [Enter].

</p>
<br />

<p>
<img src="https://i.imgur.com/t96tsQI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Back in Wireshark, filter for DHCP traffic only -> 
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew) ->
Observe the DHCP traffic appearing in WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/i1xE2xL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6. Back in Wireshark, filter for DNS traffic only ->
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are ->
Observe the DNS traffic being show in WireShark.

</p>
<br />

<p>
<img src="https://i.imgur.com/RxGFO8i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
7. Back in Wireshark, filter for RDP traffic only (tcp.port == 3389) ->
Observe the immediate non-stop spam of traffic, the RDP (protocol) is constantly showing you a live stream from one computer to another, therefore traffic is always being transmitted.

