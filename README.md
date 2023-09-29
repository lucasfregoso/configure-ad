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
Next, we are going to ensure that there is connectivity between the client and the domain controller. So we log in to client 1 with remote desktop and ping DC-1's private ip address (10.0.0.4) with 'ping -t (private ip address)' and this is known as a perpetual ping. When we first do this we notice that we are getting a 'request timed out' message, which lets us know that DC-1's windows firewall is blocking ICMP traffic. To counter this all we do is go to DC-1's 'Windows Defender Firewall with Advanced Security' and go to Inbound Rules and enable rules with ICMP Echo Request. Once we do that we can go back to client 1 and now see that our ping is working. 
</p>
<br />

Step 3
<p>
<img width="1389" alt="Screenshot 2023-09-29 at 4 08 10 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/237cff7a-ff6c-4002-a12b-07f307e64c20">
</p>
<p>
Next we want to install Active Directory and in IT, it contains critical information about your environment, connect the users to a network that allows them to get their work done, and what users have access to what. First, we go to DC-1 and open up Server Manager, go to add roles and features, click on next until we get to Server Roles, check the Active Directory Domain Services, keep clicking on next until we get to Deploy Configuration. Once there, we add a new forest and this will allow us to create a name for our domain as well as creating our environment for our users. Keep clicking next right after that until we Install and DC-1 will restart after that allowing Active Directory to be fully installed.
</p>
<br />

Step 4
<p>
<img width="1389" alt="Screenshot 2023-09-29 at 4 40 08 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/e3d0d363-4c3f-4164-a892-bb36df70ff81">
------------------------------------------------------------------------------------------------------------------------------------------------------
<img width="1389" alt="Screenshot 2023-09-29 at 4 40 22 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/f5d17ebc-26b2-47a9-be0f-47872d8e08da">
</p>
<p>
Next we proceed to make an admin and normal user account in Active Directory. We go to Active Directory Users and Computers and under our domain name, which I named 'domainexpansion' we create two new Organizational Units and call one '_EMPLOYEES' and the other '_ADMINS.' Next we decide to make a new user since in the work life environment many if not all accounts are tied to some human identity, which helps idenify who is who as well as keeping things organize. So you'll notice that the we are first logged in as 'labuser', which is just an example user for us to do labs as shown in the Command Prompt and then once we make our new user 'Lucas Flames' we recheck on the Command Prompt and see that we are now 'lucas_admin.' Lastly, once we create our own unique user we are going to add them to the domain admins group, which will allow them make changes to the domain while giving us the lab conductor to see how everything works.
</p>
<br />


Step 4
<p>
<img width="1389" alt="Screenshot 2023-09-29 at 4 40 08 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/e3d0d363-4c3f-4164-a892-bb36df70ff81">
---------------------------------------------------------------------------------------------------------------------------------------------
<img width="1389" alt="Screenshot 2023-09-29 at 4 40 22 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/f5d17ebc-26b2-47a9-be0f-47872d8e08da">
</p>
<p>
Next we proceed to make an admin and normal user account in Active Directory. We go to Active Directory Users and Computers and under our domain name, which I named 'domainexpansion' we create two new Organizational Units and call one '_EMPLOYEES' and the other '_ADMINS.' Next we decide to make a new user since in the work life environment many if not all accounts are tied to some human identity, which helps idenify who is who as well as keeping things organize. So you'll notice that the we are first logged in as 'labuser', which is just an example user for us to do labs as shown in the Command Prompt and then once we make our new user 'Lucas Flames' we recheck on the Command Prompt and see that we are now 'lucas_admin.' Lastly, once we create our own unique user we are going to add them to the domain admins group, which will allow them make changes to the domain while giving us the lab conductor to see how everything works.
</p>
<br />






