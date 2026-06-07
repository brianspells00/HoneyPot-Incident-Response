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

<p align="center">
Since my goal is to be discovered I’ll need to modify the Network security rules. First I’ll delete the RDP rule and add a rule to allow all ports to be reached: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/13NSG1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/14NSG2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/15NSG3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Now that all inbound traffic is allowed I now have to disable the firewall on the VM. I’ll be gaining access to the VM via using the public IP address and Remote Desktop Protocol. Once I was logged into the VM I navigated to Windows Defender Firewall properties and turned off the firewall state for the Domain, Private, and Public profiles: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/16RDP1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/17RDP2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/18RDP3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
I opened the Windows cmd and ran the prompt ping 40.76.120.54 to ensure that the machine could be reached: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/19PingVM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
I then disconnected from the VM and purposely entered the wrong login credentials. Then I login and navigate to the Event Viewer, click Windows Logs and then click Security: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/20RDPfail.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/21EV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
I clicked on the code 4652 which is login related and viewed the event. The event was logged as a fail, indicating that the login attempt was unsuccessful: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/22EVloginfail.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Now that I know the logs are active and accurate I’ll create a log repository using Log Analytics workspaces in Azure: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/23LogAgg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Now I’ll add the Log Analytics workspace that I created to Microsoft Sentinel which acts as a SIEM: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/24Sentinel.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Once it has finished being deployed I’ll go to configuration then select Data connectors and select Windows Security Events via AMA to install: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/25Sentinel2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
With that now installed we can set up data collection rules by clicking “Open connector page” Name the collector, select the resource group, ensure the VM is selected and create the collector: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/26WSEAMA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/27WSEMVM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/28DCR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
To confirm the connection I verified that “AzureMonitorWindowsAgent” appeared under Extensions + applications of the VM and also went to the “Log Analytics workspaces” went to the Log tab and ran the command “SecurityEvent” to display the logged events: <br/>
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/29VMverification.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/brianspells00/HoneyPot-Incident-Response/blob/main/Images/30VM%20Verify.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
