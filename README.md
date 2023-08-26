<h1>Azure Honeypot   <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fhdclipartall.com%2Fimages%2Fhoney-clipart-honey-bank-vector-illustrations-vector-art-illustration-612x516.jpg&f=1&nofb=1&ipt=783ee1997d3312abcdab10930461c1965fc07d1da03794365028bdeb2a8c6898&ipo=images" alt="Image Description" width="150" height="100">
</h1>

   This project consisted of utilizing Microsoft Azure's SIEM platform, Sentinel, to monitor brute-force attacks onto a vulnerable virtual machine and further analyze them through log analytics. These attacks were then visualized through the use of a geographical dashboard. <br />

<h2>Utilities Used</h2>

- <b>Microsoft Sentinel</b>

<h2>Environments Used </h2>

- <b>Windows 11 Virtual Machine</b>

<h2>Project walk-through:</h2>

<p align="center">
   <b>A resource group was created, linking the Virtual Machine and the Log Analytics Workspace together.</b>
<img src="https://imgur.com/F3A34ci.png" height="100%" width="100%" alt="Resource Group"/>                                                 
      </p>
   <br />
<p align="center">
<b>After creating the VM, a custom inbound port rule on the firewall was configured to allow all incoming traffic.</b>
<br/>
<img src="https://imgur.com/yedIVhl.png" height="40%" width="40%" alt="Custom Inbound Rule"/>
      </p>
      <p align="center">
      <b>In order to allow ICMP echo requests and make the VM discoverable, the firewall on the VM itself was disabled.</b> 
<br/>
<img src="https://imgur.com/PUo4NVP.png" height="80%" width="80%" alt="VM linked to LAW"/>
      </p>
<br/>
<br/>
      <p align="center">
<b>Following, I created a custom PowerShell script on the virtual machine utilizing AI. The script interacts with the Windows Event Viewer on the VM and specifically targets Audit Failures with Event ID 4625, which indicate failed login attempts. The script collects relevant information from these failed login attempts and exports it to a JSON log file in a format recognized by Azure.
      <p align="center">
The script extracts the collected information from Windows Event Viewer and organizes it into corresponding tables for further analysis. Additionally, the script leverages an API (shown below) that provides geolocation capabilities, allowing the script to determine the latitude and longitude of the attack sources. The log file that is created from this script is then utilized as a sample file in the Log Analytics Workspace for formatting purposes.</b>
</br>   
    <img src="https://imgur.com/LxkZykA.png" height="70%" width="70%" alt="Custom Powershell Script"/>
      </p>
      <p align="center">
<img src="https://imgur.com/68u14nf.png" height="50%" width="50%" alt="Resource Group"/>
      </p>
<br />
<br />
<br />
<p align="center">
<b>Finally, I created a custom workbook and again utilized AI to create a query in order to retrieve the custom log file from the Log Analytics Workspace and extract its valuable tables.
<p align="center">
After successfully pulling the tables, I utilized the world map visualization feature offered by the workbook. By mapping the attack sources based on their latitude and longitude coordinates, I was able to represent the data geographically. To provide a clearer perspective, I adjusted the size of the plotted markers based on the number of attacks originating from each general area and country.
   </b> <br/>
   </p>
<img src="https://imgur.com/Ho9iToa.png" height="80%" width="80%" alt="law query"/>
<br />
<br />
<p align="center">
   <img src="https://i.postimg.cc/G20G3zsc/attacks.png" height="80%" width="80%" alt="world map"/> <br />
<b> Almost instantly an abundance of brute-force attempts were received. Leveraging visualizations to portray attacks by magnitude is crucial and can provide a clear understanding of the threat landscape, trends, and patterns. It is a valuable tool and certainly helps with decisions moving forward.<b>  <br/>
   </p>
   <p></p>
