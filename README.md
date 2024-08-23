<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Rescources in Azure
- Ensure Connectivity between the client and Domain controller
- Install Active Directory 
- Create an Admin and Normal User Accounts in AD

<h2>Deployment and Configuration Steps</h2>

<h3>Create a resoruce group, virtual network and subnet, two VMs named "DC-1 and "Client-1". We will also set the Domain controllers "NIC" Network interface card to be static</h3>

![image](https://github.com/user-attachments/assets/8459f85c-8c17-4e6f-889a-8a52ee8aa702)
![image](https://github.com/user-attachments/assets/d749a179-589d-4b1f-98ed-deb31b209ab1)

<h3>Login into Client-1 and ping DC-1s private address with "ping -t private ip address". Login to the Domain Controller and enable ICPv4 on the local Firewall. Then check back into Client-1 to observe the changes and establish a conncection to DC-1.</h3>



<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to the DC-1 and install Active Directory Domain Services. Promote as the DC (mydomain.com). Restart and log back into the DC-1 as user (mydomain.com\labuser)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Active Directory Users and Computers (ADUC), create an Organizational unit (OC) called "_EMPLOYEES", "_ADMINS", new employee named "John Doe" same password with "jane_admin".
  Add jane_admin to the "Domain Admins" security group". Logout to then log back in as "mydomain.com\jane_admin".
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup Remote Desktop for non-administrative users on Client-1, Log into Client-1 as mydomain.com\jane_admin and open system properties, Click "Remote Desktop", Allow "domain users" access to remote desktop, You can now log into Client-1 as normal, non-administrative user now. Normally you'd want to do this with Group Policy that allows you to change Many systems at once.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a bunch of additional users and attempt to log into client-1 with one of the users, Login to DC-1 as jane_admin, Open PowerShell_ise as an adminstrator, Create a new file and paste the contents of the script into it, Run the script and observe the accounts in the OU attempt to log into Client-1 with one of the accounts (take note of the passoword in the script).
</p>
<br />
