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

<h2>Create a Log Abalytics Workspace</h2>

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

- Click VM name --> Then connect

<img src="https://i.imgur.com/uiQh3vM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<img src="https://i.imgur.com/9AtpjCM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>




   
  


