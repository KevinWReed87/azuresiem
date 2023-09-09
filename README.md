 <img src="https://i.imgur.com/REsEWbs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>




<h1>Enhance Security with SIEM: Threat Detection, Analysis, and Mitigation in Azure</h1>

In this lab, we'll begin by creating a secure Windows 10 VM within the Azure environment. We'll intentionally introduce security gaps, so you can get hands-on experience with threat scenarios. A siem sentinel will be created, along with a live attack map and lab analytics in azure.
<br />



<h2>Operating Systems Used </h2>

- Windows 10 Pro</b> 

<h2>List of Prerequisites</h2>

- Computer with the Internet
- Azure Account - May Be Possible to do with a Free Subscription




<h2>Create our Free Azure Account</h2>

- Sign up: https://azure.microsoft.com/en-us/free/
- Login: https://portal.azure.com 



<h2>Prepare Azure Virtual Machine</h2>
  
  - In the search box type virtual machine and click it--> Choose create virtual machine.
  
  <img src="https://i.imgur.com/6QvRNu0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

  - Choose the appropriate settings for your VM, including the region, resource group, VM name and authenyication details.
  - Select an operating system image. (Windows 10 Pro)

  <img src="https://i.imgur.com/L7mz9Rm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

  - Click next and stop at networking.
  - Make sure advanced is checked --> Click create new under network security group

   <img src="https://i.imgur.com/AgKOoeF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

  - Remove the default rule then click add a new inbound rule

   <img src="https://i.imgur.com/3cQE7m3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

   - For destination port range put * for anything --> For protocal any --> For action allow --> Priority - 100 --> Name DANGER_ANY_IN
   - This will allow all traffic from the internet into the virtual machine. Makes the VM very discoverable tp TCP Pings, ICMP Pings and so forth. Don't want the VM to drop any traffic, want it to be very discoverable for for lab purposes.
   - Click add --> OK --> Review+Create-->Create

   <img src="https://i.imgur.com/VAIjndR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
   <img src="https://i.imgur.com/bYJO0Ly.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
   <img src="https://i.imgur.com/ngpGEfi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
   <img src="https://i.imgur.com/rWOHTJC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Create a Log Analytics Workspace</h2>

  - Search log analytics workspace --> Create --> Resource Group (Previous One Created) --> Name (law-honeypot) --> Region (Same as Virtual Machine US West 3) --> Review+Create --> Create.
  <img src="https://i.imgur.com/qUuaxUP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
  <img src="https://i.imgur.com/bffC7jz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Enable Microsoft Defender for Cloud</h2>

  - Search for Microsoft Defender in Azure --> Click on it.
  - On left go to Environment settings.
  - Click on resource group name law-honeypot under Azure Subcriptions.


 <img src="https://i.imgur.com/uFl0baZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
 <img src="https://i.imgur.com/kvUOxoL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

 - Turn on Foundational CSPM and Servers

 <img src="https://i.imgur.com/hDl0CyO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

 - Click save --> Click Data Collection --> All Events --> Save

 <img src="https://i.imgur.com/0MXD6vf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

 - Go back to Log Analytic Workspace to connect it to the Virtual Machine --> Click your workspace --> Then Virtual Machines.

 <img src="https://i.imgur.com/pjj49H9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

 - Click VM name --> Then press connect for the VM

<img src="https://i.imgur.com/uiQh3vM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/9AtpjCM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Configuring Azure Sentinel SIEM</h2>

 - Search for "Azure Sentinal SIEM" and create a new instance.
 - Click the Analytic Workspace you want to add and click add.

<img src="https://i.imgur.com/KF9yj6C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/nxtODXf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Log into Virtual Machine to set up environment</h2>

 - Go to virtual machines --> Click VM name --> Copy public ip address.
<img src="https://i.imgur.com/1KoNc3X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/g6kSDh7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

 - Log into VM with RDP --> Put in public ip --> Use created VM credentials.

<img src="https://i.imgur.com/LbxFvG0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/80gXuAV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- Click start --> Type Event Viewer --> Click Windows Logs --> Then Security

<img src="https://i.imgur.com/gMB8FSk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/8002IAW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- Going to create a failed login attempt to observe on event viewer.

<img src="https://i.imgur.com/8LkzPm2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/M0AAR9x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- General info on log shows username used to try and log into account, domain name which is current VM and failure reason which is unknown username and password.
Workstation name and ip address from login also present.

- Notating this info for when VM goes live for attacks and monitoring the event viewer.

<img src="https://i.imgur.com/D9r4bJi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/x1eZdld.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Turn off Windows Firewall on Virtual Machine</h2>

 - Open Command Line on Local PC and ping public ip address of Virtual Machine to see reply status of VM.

 <img src="https://i.imgur.com/uarnTmA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
 
 - Click start --> Type wf.msc --> Windows defender firewall properties.


<img src="https://i.imgur.com/4RWxj0P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/SuJJpQJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- Domain Profile firwall state off --> Private off --> Public off --> Click apply --> Ok

<img src="https://i.imgur.com/5ehADkc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- Now ping request for ip address of VM. Now getting ping request from VM.

<img src="https://i.imgur.com/ZMiaI5T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Geolocation.io API Key/Powershell Script</h2>

- Will use custom powershell script from a github and download raw script to PC.

<img src="https://i.imgur.com/48tL0SM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/8qaNEBE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- Open up Powershell ISE on Virtual Machine --> Click New --> Paste Script --> Save to Desktop.

<img src="https://i.imgur.com/dEkZ99G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/MGpaiBT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/13I66ON.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/ti6a2IV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

- On browser go to ipgeolocation.io to get new API_KEY --> Sign up for account to recieve API_KEY --> Verify Email --> Log into account --> API_KEY will be shown.

<img src="https://i.imgur.com/uF403BC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<h2>Run Script to get GeoData from attackers</h2>












   






   
  


