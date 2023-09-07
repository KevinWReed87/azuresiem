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

   <img src="https://i.imgur.com/VAIjndR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

   
  


