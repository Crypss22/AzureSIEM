<h1>Azure Honeypot   <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fhdclipartall.com%2Fimages%2Fhoney-clipart-honey-bank-vector-illustrations-vector-art-illustration-612x516.jpg&f=1&nofb=1&ipt=783ee1997d3312abcdab10930461c1965fc07d1da03794365028bdeb2a8c6898&ipo=images" alt="Image Description" width="150" height="100">
</h1>

   This project consisted of making a SIEM through Microsoft's cloud platform, Azure. Through my vulnerable honeypot, I was able to capture brute-force attacks onto my Virtual Machine and aggregate them through log analytics and plot them through geolocation onto a visual map.

<br /> Below are screenshots of the project and some crucial steps that helped with geolocating and visualizing the brute-force attacks.

<h2>Utilities Used</h2>

- <b>Microsoft Azure</b> 
- <a href="ipgeolocation.io">Ipgeolocation.io's</a> <b>Third-party API</b>


<h2>Environments Used </h2>

- <b>Windows 11 Virtual Machine</b>

<h2>Project walk-through:</h2>

<p align="center">
   <b>This resource provided an API key that granted geolocation via a custom powershell script that can be found <a href="https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1">here</a><br/>
<img src="https://imgur.com/68u14nf.png" height="50%" width="50%" alt="Resource Group"/>
<img src="https://imgur.com/u1zHzb7.png" height="150%" width="150%" alt="Custom Powershell Script"/>
This custom powershell script interacts with Windows Event Viewer and searches for Audit Failures with the Event ID 4625 that signify a failed login attempt
<br />
<br />
<b>This custom inbound rule allowed all incoming traffic from any source on any port</b>  <br/>
<img src="https://imgur.com/yedIVhl.png" height="40%" width="40%" alt="Custom Inbound Rule"/>
<br />
<br />
   <b>In order to allow ICMP echo requests and make the VM discoverable, all profiles on the firewall were disabled</b> 
<br/>
<img src="https://imgur.com/PUo4NVP.png" height="80%" width="80%" alt="VM linked to LAW"/>
<br />
<br />
   <b>The powershell script was run to collect sample brute-force attacks and even some live attacks were caught instantly. These were exported to create a custom log on Azure to familiarize the SIEM</b>  <br/>
<img src="https://imgur.com/eGo2uKc.png" height="250px" width="80%" alt="Failed RDP on Powershell"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
