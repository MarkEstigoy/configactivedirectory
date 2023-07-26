# configactivedirectory
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022


<h2>Deployment and Configuration Steps</h2>

Step 1) Create Resources in Azure
Create a resource group with 2 VM's. First VM will be the Domain Controller.  
<br />
<p>
<img src="https://i.ibb.co/8XsRdRJ/step1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we will create the second VM , this will be Client-1 
</p>
<br />
<br />

<p>
<img src="https://i.ibb.co/6w7Bv6J/step1-2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step is too change DC-1's NIC private IP address too "static" 
</p>
<br />

<p>
<img src="https://i.ibb.co/nBgt5s0/step1-3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.ibb.co/QXZzsq7/step1-4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.ibb.co/F7yMTqZ/step1-5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<br />
<br />
Now we connect to DC-1 via remote desktop and install active directory, select "Add roles and features" 
</p>
<br />

<img src="https://i.ibb.co/X3wBTCq/step1-7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Click the "Active Directory Domain Services" option too install 
</p>
<br />
<img src="https://i.ibb.co/gy5G5kK/step1-8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Keep clicking next until you reach the end and press "install" too complete 
</p>
<br />
<img src="https://i.ibb.co/pPRL4tg/step1-9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once it finishes installing, close the window and click on the flag with a yellow warning sign 
</p>
<br />
<img src="https://i.ibb.co/QfS4RGY/step2-0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Click on "Promote this server to a domain controller"
</p>
<br />
<img src="https://i.ibb.co/FsvbW04/step2-1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Click on "Add a new forest" , name your new domain afterwards
</p>
<br />
<img src="https://i.ibb.co/PtkVdPC/step2-2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

