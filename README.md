<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark and experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://youtu.be/P5lYK1DfVC0)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/k2jY9D7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Wireshark and download the Windows x64 Installer. Click Next on everything until Wireshark is downloaded. Choose the Ethernet setting and Filter for ICMP Traffic.
</p>
</p>
<p>
<img src="https://imgur.com/rN8xVO0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After you set the filter to ICMP, open up Windows PowerShell and ping the private address of the Linux virtual machine Private Address. You will now be able to see the ping traffic through Wireshark.
</p>
<p>
<img src="https://imgur.com/KtGhbJT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Using PowerShell ping "google.com", you can now see the traffic through Wireshark.
</p>

</p>

</p>
<br />

<p>
<img src="https://imgur.com/M154OtV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiate a perpetual ping on Windows PowerShell, using (ping "Private IP Address" -t)
</p>
<br />

<p>
<img src="https://imgur.com/rRZLxAH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the Network Security Group that your Ubuntu VM is using, Linux-VM-->Networking-->Network settings-->Rules, and disable incoming (inbound) ICMP traffic

</p>
<br />

<p>
<img src="https://imgur.com/q7gCd3x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the command line Ping activity

</p>
<br />

<p>
<img src="https://imgur.com/yKaTcr7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is on by deleting the security rule, which will allow traffic through the Virtual Network.

</p>
<br />

<p>
<img src="https://imgur.com/MfYk9Kq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p/>
<p>
Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the command line Ping activity (should start working). Ctrl-C through PowerShell to stop the ping.



