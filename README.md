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

- Windows Server Datacenter 2022 Azure Edition
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

Step 1
<p>
<img width="1577" alt="Screenshot 2023-09-29 at 3 22 54 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/b39546d6-7c85-47bc-b66e-9e05688d6155">
</p>
So before we get into the lab, we first created two virtual machines on Azure simply by going to 'virtual machines', 'create', and then proceed with inputting the right information. Our first virtual machine will be known as 'DC-1' aka domain controller, which essentially acts as a gatekeeper and gives permission to whether or not a user is authorized to access any IT information. The second one is 'Client-1', which will be our user. Next, we must set our domain controller's NIC private ip address to static because it will allow it to be discovered by users across the network making it much easier for schools or companies for example, when their employees or students use the computers they could just log in with their provide username/password allowing the network to recognize it.  
<p>
</p>
<br />

Step 2
<p>
<img width="1389" alt="Screenshot 2023-09-29 at 3 45 44 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/a6a92493-8286-487b-9eac-3e3d93a0524d">
<img width="998" alt="Screenshot 2023-09-29 at 3 42 57 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/439a2600-be1b-48b7-b3e7-34f05c883de2">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
