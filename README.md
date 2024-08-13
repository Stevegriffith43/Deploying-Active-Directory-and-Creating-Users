<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Rescources in Azure
- Ensure Connectivity between the client and Domain controller
- Install Active Directory 
- Create an Admin and Normal User Accounts in AD

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a resoruce group, virtual network and subnet, two VMs named "DC-1 and "Client-1". We will also set the Domanain controllers "NIC" Network interface card to be static.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login into Client-1 and ping DC-1s private address with "ping -t private ip address". Login to the Domain Controller and enable ICPv4 on the local Firewall. Then check back into Client-1 to observe the changes and establish a conncection to DC-1.
</p>
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
