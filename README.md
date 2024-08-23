<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Rescources in Azure
- Ensure Connectivity between the client and Domain controller
- Install Active Directory 
- Create an Admin and Normal User Accounts in AD

<h1>Deployment and Configuration Steps</h1>

<h3>Create a resoruce group, virtual network and subnet, two VMs named "DC-1 and "Client-1". We will also set the Domain controllers "NIC" Network interface card to be static</h3>

![image](https://github.com/user-attachments/assets/8459f85c-8c17-4e6f-889a-8a52ee8aa702)
![image](https://github.com/user-attachments/assets/d749a179-589d-4b1f-98ed-deb31b209ab1)

<h3>Login into Client-1 and ping DC-1s private address with "ping -t (perpetual ping)". Login to the Domain Controller and enable ICPv4 on the local Firewall. Then check back into Client-1 to observe the changes and establish a conncection to DC-1.</h3>

![image](https://github.com/user-attachments/assets/62796127-a5e0-426f-ac39-3dc6244a2803)
![image](https://github.com/user-attachments/assets/e2f3e0ce-f3ca-496c-b2e5-ed6a8d96284a)
![image](https://github.com/user-attachments/assets/3ced0d78-605d-460b-8323-79197816f272)

<h3>Login to the DC-1 and install Active Directory Domain Services. Promote as the DC (mydomain.com). Restart and log back into the DC-1 as user (mydomain.com\labuser)</h3>

![image](https://github.com/user-attachments/assets/b31f2245-25e6-4801-9d9f-8e9d5fea53aa)
![image](https://github.com/user-attachments/assets/3351ae24-9370-4a64-8e52-af30cbbf1f96)
![image](https://github.com/user-attachments/assets/71d3301b-5b57-4d9e-afbd-c0d6fa377422)
![image](https://github.com/user-attachments/assets/256a4d1f-bdb3-4bdd-9bc6-3a42d3f26450)


<h3>In Active Directory Users and Computers (ADUC), create an Organizational unit (OC) called "_EMPLOYEES", "_ADMINS", new employee named "Jane Doe" same password with "jane_admin".
  Add jane_admin to the "Domain Admins" security group". Logout to then log back in as "mydomain.com\jane_admin".</h3>

![image](https://github.com/user-attachments/assets/ecfcc48b-658b-4404-8f29-2e2303acbfdb)
![image](https://github.com/user-attachments/assets/5486e6d6-66a4-4952-9032-732b0db2abe0)
![image](https://github.com/user-attachments/assets/49e3f3bd-f48c-4227-9ad6-9af037246731)

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
