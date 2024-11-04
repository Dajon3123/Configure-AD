<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com/watch?v=ql2fy4voGi4)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 In This Step, I created a resource group to organize all lab resources efficiently. Within this group, I established a virtual network (VNet) to enable secure communication among the resources. I also deployed a virtual machine (VM) in the VNet, which will serve as the main environment for executing lab tasks. This foundational setup ensures proper management and connectivity for the upcoming steps.
- Step 2 In This Step, I created a Windows 10 VM named “Client-1” and ensured it was in the same region and virtual network as DC-1, which I configured with a static private IP address. I set Client-1’s DNS settings to this static IP for DC-1 and restarted the VM. After logging in, I tested connectivity by pinging DC-1, which succeeded. Finally, I ran ipconfig /all in PowerShell to verify that the DNS settings correctly showed DC-1’s private IP.
- Step 3 In This Step, I began by installing Active Directory Domain Services on DC-1 and promoting it to a domain controller with the domain mydomain.com. After restarting, I logged in as mydomain.com\jane_admin and configured Remote Desktop to allow access for domain users on Client-1. Then, I logged into DC-1 again as jane_admin, opened PowerShell ISE as an administrator, and ran a script to create multiple new user accounts, which I confirmed in the "_EMPLOYEES" OU in ADUC. Finally, I tested logging into Client-1 with one of the new accounts, ensuring I had the correct password.
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
