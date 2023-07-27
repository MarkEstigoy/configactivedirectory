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
</p>
<br />
Give your domain a password 
</p>
<br />
<img src="https://i.ibb.co/rZXQqkh/step2-3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Keep clicking next until you reach "Prerequisites check" and click install. (NOTE- Once it finishes installing the VM will restart)
</p>
<br />
<img src="https://i.ibb.co/Jqr8spw/step2-4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once it restarts, you will want too log back in starting with the root domain name. "mydomain.com\labuser1"
</p>
<br />
<img src="https://i.ibb.co/6v6S6PC/step2-5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once you log back on, click on the tools tab in server manager and click "Active Directory Users and Computers" 
</p>
<br />
<img src="https://i.ibb.co/MMzXt2z/step2-6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Find the "Organizational Unit" tab and create folders "_EMPLOYEES" and "_ADMINS", this is where we will put the new accounts for the domain
</p>
<br />
<img src="https://i.ibb.co/TMD1JRk/step2-7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.ibb.co/r6nLBR3/step2-8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.ibb.co/ctdJ1cJ/step2-9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Next we will create a new user and make it an admin 
</p>
<br />
<img src="https://i.ibb.co/V94y12h/step3-0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Fill in the blanks and create the name you want for the admin. We are going with "Jane Doe" for this lab. Press next once completed
</p>
<br />
<img src="https://i.ibb.co/j6yxZhp/step3-1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Create a new password for the account, check the password never expires box and click next afterwards
</p>
<br />
<img src="https://i.ibb.co/8Bdyr9H/step3-2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once we have created the account, we want too promote it too an admin. To do this, first right click on the name and press "properties"
</p>
<br />
<img src="https://i.ibb.co/3mXht7B/step3-3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once the tab pops up, click on "Member Of" and press "Add" 
</p>
<br />
<img src="https://i.ibb.co/TcQjv4S/step3-4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Type in "Domain admins" and press "Check Names", once it verifies press "OK" too add 
</p>
<br />
<img src="https://i.ibb.co/2NTMT5P/step3-5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
You should now see "Domain Admins" be included in the "Members Of" section. Press apply and click OK afterwards 
</p>
<br />
<img src="https://i.ibb.co/c6YzxN6/step3-6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once thats completed, "Jane Doe" is now an admin. We will now try too login into the domain controller as Jane Doe. 
</p>
<br />
<img src="https://i.ibb.co/rH1dwrJ/step3-7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
We can now see that we have logged into the VM with a new user we have just created! 
</p>
<br />
<img src="https://i.ibb.co/YjGthZw/step3-8.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
The next step is too change Client-1's DNS settings too DC-1's private ip address. First we must find DC's private ip address, it should be under the public ip address
</p>
<br />
<img src="https://i.ibb.co/kgg6n9q/step3-9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once you get DC's private ip address, navigate your way too Client-1's DNS servers settings. Click on the "DNS servers" tab, press custom and copy/paste DC's private ip address onto there. Press Save afterwards too complete the change
</p>
<br />
<img src="https://i.ibb.co/R0PcV1y/step4-0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once thats completed, we must restart Client-1. We can find the restart button by clicking on Client-1 on azure. 
</p>
<br />
<img src="https://i.ibb.co/KVGNtCD/step4-1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Next we will want to log into Client-1. We will do this by using the regular account (labuser1)
</p>
<br />
<img src="https://i.ibb.co/prJxxVW/step4-2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Next we will want too join Client-1 too the domain controller. Press the "Rename this PC (advanced)" settings and press "Change" 
</p>
<br />
<img src="https://i.ibb.co/WH8HD7r/step4-3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Press the "Member Of" option and type in DC's domain name. (mydomain.com) Press OK after
</p>
<br />
<img src="https://i.ibb.co/TPpNRrn/step4-4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
You must now enter an account that has permission to join the domain. Use the account admin that we made previously (mydomain.com\jane_admin)
</p>
<br />
<img src="https://i.ibb.co/DCMpS1H/step4-5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



