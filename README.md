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
- Step 5
- Step 6

(images from left to right)
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
-------------------------------------------------------------------------------------------------------------------------------------------
<img width="1389" alt="Screenshot 2023-09-29 at 4 40 22 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/f5d17ebc-26b2-47a9-be0f-47872d8e08da">
</p>
<p>
Next we proceed to make an admin and normal user account in Active Directory. We go to Active Directory Users and Computers and under our domain name, which I named 'domainexpansion' we create two new Organizational Units and call one '_EMPLOYEES' and the other '_ADMINS.' Next we decide to make a new user since in the work life environment many if not all accounts are tied to some human identity, which helps idenify who is who as well as keeping things organize. So you'll notice that the we are first logged in as 'labuser', which is just an example user for us to do labs as shown in the Command Prompt and then once we make our new user 'Lucas Flames' we recheck on the Command Prompt and see that we are now 'lucas_admin.' Lastly, once we create our own unique user we are going to add them to the domain admins group, which will allow them make changes to the domain while giving us the lab conductor to see how everything works.
</p>
<br />


Step 5
<p>
<img width="1389" alt="Screenshot 2023-09-29 at 5 34 41 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/fc9052a5-4eac-48e3-8942-77c755bc9967">
-------------------------------------------------------------------------------------------------------------------------------------------
  <img width="1643" alt="Screenshot 2023-09-29 at 5 35 24 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/47ec2979-9e4b-4b4c-9971-b2c6a5de38ac">
</p>
<p>
Next, we are going to join Client 1 to our domain (domainexpansion.com). So the first thing we have to do is go back on Azure and go to Client 1 and set it's DNS settings to the domain controller's private ip address which again is 10.0.0.4. We do this by taking note of DC-1's private IP address, going to Client 1's NIC uder networking, then to DNS servers, switch Inherit from virtual network to custom, typing in DC-1's private IP address, and then saving it. After this, we restart Client 1, which will allow it to flush the DNS cache. Before this, our Client 1's DNS settings were set to the default Vnet that was automatically created when we first created our virtual machine and now we're are manually switching it to join it to our domain controller, which the domain controller recognizes through our domain name. Also, we can check that Client 1 has the new DNS settings by going to command prompt and pinging DC-1's private IP address. To complete the joining process we go to our Client 1 virtual machine and right click start, open up system, click on rename this PC (advanced), click on Change on the bottom right, and make the domain a member of ours through our admin username: domainexpansion.com\lucas_admin and of course a password. Once that's entered, we click on Ok and the computer will restart completing our joining process. 
</p>
<br />

Step 6
<p>
<img width="1109" alt="Screenshot 2023-09-29 at 6 07 27 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/077afd3b-87b9-4c14-b86b-ea6b1b48e7ef">
-------------------------------------------------------------------------------------------------------------------------------------------
<img width="1650" alt="Screenshot 2023-09-29 at 6 07 08 PM" src="https://github.com/lucasfregoso/configure-ad/assets/144977615/04b0b733-5e5c-4a4c-b23e-12968e703701">
</p>
<p>
Finally, we come to the last part of the lab and the first thing we do is allow 'domain users' access to remote desktop, which beforehand only administrative users were allowed to remote desktop. To do this we right click the start menu, click on system, go to Select users that can remotely access this PC, and add 'Domain Users' now allowing any non-adminstrative user to access remote desktop. Now from here, we log into DC-1 as lucas_admin, open PowerShell ISE as administrator, create a new file and paste the script in there that was provided by our instrutor. The script is some coding that is going to create many different users allowing us to see if we can log into Client 1 as a normal user. Once we run the script we can see that a ton of users start being created and if we check our '_EMPLOYEES' section in Active Directory Users and Computers we can now see that all of our users have been placed there. After this, we log out of lucas_admin and log in as one the users that generated by our script and in my case I chose 'bal.ger' and was successfully able to log in, showing us that our lab was executed properly. 
</p>
<br />
