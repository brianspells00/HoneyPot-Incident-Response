# HoneyPot-Incident-Response
<h2>Description</h2>
In this lab I created a Virtual Honey Pot using Microsoft Azure resources to monitor and analyze Security event logs and use the NIST incident response plan to detect, mitigate, and recover from security breaches.
<br />


<h2>Languages, Utilities and Services Used</h2>

- <b>Microsoft Azurel</b> 
- <b>Remote Desktop Protocol</b>
- <b>Windows Defender Firewall</b> 

<h2>Virtual Environments Used </h2>

- <b>Windows 10</b>


<h2>Project walk-through:</h2>

<p align="center">
First I created a Microsoft Azure account : <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/00MSAzureacct.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
I then made a Resource Group as a place to store the resource I’ll be creating and configuring. Then confirmed it was created properly: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/01%20RG%20creation.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/02RG%20confirm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Then I created a Virtual Network (Vnet-SOC-HP-Lab) ensuring that the region of the Network is the same as the region of my Resource Group. Then confirmed its deployment: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/03Virtual%20network.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/04VN2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/05%20VN%20deploy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Now I’ll be creating a virtual machine to act as a honeypot. I named the VM “ENT-EAST-3” selected Windows 10 as the OS, I created a username and password, selected the disk size and type for the OS. I then created the VM and confirmed the deployment: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/06VM1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/07VM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/08VM3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/09VM4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/10VM5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/11VMConfirm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Now when I navigate to the Resource Group I can see that a Public IP address, Network Security Group, Network Interface, and Disk were added into the group: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/12Resourcecheck.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

