<h1>Azure Honeypot   <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fhdclipartall.com%2Fimages%2Fhoney-clipart-honey-bank-vector-illustrations-vector-art-illustration-612x516.jpg&f=1&nofb=1&ipt=783ee1997d3312abcdab10930461c1965fc07d1da03794365028bdeb2a8c6898&ipo=images" alt="Image Description" width="150" height="100">
</h1>
In cybersecurity, threat intelligence is crucial to enhancing the capabilities of security solutions. Threat intelligence resources such as the MITRE ATT&CK framework provide a knowledge base to understand threat actors tactics, techniques, and procedures. In developing an understanding of new exploitation methods, honeypots serve as an invaluable tool in doing so. 
<br>
</br>
In this project, I deploy a virtual machine whose security configurations are weakened and ultimately susceptible to threat actors. I leverage AI and geolocation to create a dashboard and provide a means of visualizing the origin of attacks. Through this, we can conduct further research on indicators of compromise and block network traffic from malicious IP addresses, investigate credentials being used, and more.
 <br />
<h2>Environment Used</h2>

- <b>Windows 11</b>

<h2>Project walk-through:</h2>

<p align="center">
   <b>A resource group was created, linking the Virtual Machine and the Log Analytics Workspace together.</b>
<img src="https://imgur.com/F3A34ci.png" height="100%" width="100%" alt="Resource Group"/>                                                 
      </p>
   <br />
<p align="center">
<b>In the VM's settings on Azure, I configured the firewall to allow traffic on all ports.</b>
<br/>
<img src="https://imgur.com/yedIVhl.png" height="40%" width="40%" alt="Custom Inbound Rule"/>
      </p>
      <p align="center">
      <b>And on the Windows VM itself, disabled the firewall to allow ICMP echo requests, making it discoverable, and baiting all threat actors looking for some low-hanging fruit.</b> 
<br/>
<img src="https://imgur.com/PUo4NVP.png" height="80%" width="80%" alt="VM linked to LAW"/>
      </p>
<br/>
<br/>
      <p align="center">
<b>Following, I created a custom PowerShell script to be used on the virtual machine utilizing AI. The script interacts with the Windows Event Viewer on the VM and specifically targets Audit Failures with Event ID 4625, which indicates a failed login attempt. The script collects relevant information from these failed login attempts and exports it to a JSON file recognized by Azure Sentinel.
      <p align="center">
The script extracts the collected information from Windows Event Viewer and leverages an API to provide geolocation capabilities, determining the latitude and longitude of the attack sources.</b>
</br>   
    <img src="https://imgur.com/LxkZykA.png" height="70%" width="70%" alt="Custom Powershell Script"/>
      </p>
      <p align="center">
<img src="https://imgur.com/68u14nf.png" height="50%" width="50%" alt="API"/>
      </p>
<br />
<br />
<br />
<p align="center">
<b>Finally, I created a custom workbook and once again utilized AI to create a query in order to retrieve the custom log file from the Log Analytics Workspace and extract it's tables.
<p align="center">
After successfully pulling the tables, I utilized the world map visualization feature offered by the workbook. By mapping the attack sources based on their latitude and longitude coordinates, I was able to represent the data geographically. To provide a clearer perspective, I adjusted the size of the plotted markers based on the number of attacks originating from each general area and country.
   </b> <br/>
   </p>
<img src="https://imgur.com/Ho9iToa.png" height="80%" width="80%" alt="law query"/>
<br />
<br />
<p align="center">
   <img src="https://i.postimg.cc/G20G3zsc/attacks.png" height="80%" width="80%" alt="world map"/> <br />
<b> Almost instantly, an abundance of brute-force attempts were received. Leveraging visualizations to portray attacks by magnitude was crucial, and it provided a clear understanding of the threat landscape, trends, and patterns.
   </p>
   <p>Honeypots prove to be a safe, effective way of proactively gathering threat intelligence and analyzing threat actors tactics, techniques, and procedures (TTPs). With the rising implementation of AI into security solutions, this provides an insight into one way AI can be leveraged for data visualization and influence strategic decisions.</p>
