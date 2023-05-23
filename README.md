<h1>Azure Honeypot   <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fhdclipartall.com%2Fimages%2Fhoney-clipart-honey-bank-vector-illustrations-vector-art-illustration-612x516.jpg&f=1&nofb=1&ipt=783ee1997d3312abcdab10930461c1965fc07d1da03794365028bdeb2a8c6898&ipo=images" alt="Image Description" width="150" height="100">
</h1>

   This project consisted of making a SIEM through Microsoft's cloud platform, Azure. Using my vulnerable honeypot, I captured brute-force attacks on my Virtual Machine, and analyzed them using log analytics. I then plotted the attacks' geolocation data on a visual map.

<br /> Below are screenshots of the project and some crucial steps that helped with geolocating and visualizing the brute-force attacks.

<h2>Utilities Used</h2>
4


<h2>Environments Used </h2>

- <b>Windows 11 Virtual Machine</b>

<h2>Project walk-through:</h2>

<p align="center">
   <b>A resource group was created to link the components of the project together to include the Virtual Machine, the Log Analytics Workspace, and the SIEM, Microsoft Sentinel.<br/>
<img src="https://imgur.com/F3A34ci.png" height=" width="80" alt="Resource Group"/>                                                 
      </p>
   <br />
<p align="center">
      <b>In order to allow ICMP echo requests and make the VM discoverable, all profiles on the firewall were disabled</b> 
<br/>
<img src="https://imgur.com/PUo4NVP.png" height="80%" width="80%" alt="VM linked to LAW"/>
      </p>
<br />
<br />

<p align="center">
This custom inbound rule allowed all incoming traffic from any source on any port
<br/>
<img src="https://imgur.com/yedIVhl.png" height="40%" width="40%" alt="Custom Inbound Rule"/>
      </p>
<br/>
<br/>
<p align="center">
   <b>This resource provided an API key that granted the ability to geolocate attacks via a custom powershell script<br/>
<img src="https://imgur.com/68u14nf.png" height="50%" width="50%" alt="Resource Group"/>
      </p>
      <p align="center">
On the Virtual Machine I created this custom powershell script using AI,  and had it export a .json log file that Azure was familiar with formatting into a custom log. The script interacts with Windows Event Viewer on the VM, and searches for Audit Failures with the Event ID 4625 that signify a failed login attempt.</br>   
    <img src="https://imgur.com/LxkZykA.png" height="70%" width="70%" alt="Custom Powershell Script"/>
      </p>
<br />
<br />
<br />
The log was put into a custom table to familiarize Azure with the format in which it should organize future incoming attacks.  <br/>
<img src="" height="80%" width="80%" alt="tbd"/>
<br />
<br />
tbd  <br/>
<img src="" height="80%" width="80%" alt="tbd"/>
<br />
<br />
Finally, we were able to visualize the attacks on a worldmap. The   <br/>
<img src="" height="80%" width="80%" alt="tbd"/>
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
