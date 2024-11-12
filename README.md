<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>



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
- Step 4 In This Step, I Configured the Account Lockout Threshold in Group Policy to 5 failed attempts. Simulate a lockout by trying 6 failed logins on Client-1. The account should lock after 5 attempts.
Unlock the account in ADUC, reset the password, and verify the login works with the new credentials.



<h2>Deployment and Configuration Steps</h2>

<p>
<img src=https://i.imgur.com/9AitEBd.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I deployed a Windows Server 2022 Datacenter VM on Azure and configured it as a domain controller by installing Active Directory Domain Services (AD DS). I set the server's IP address to static to ensure consistent network connectivity.

Next, I created a Windows 10 client machine in Azure, joined it to the domain, and connected both machines via Remote Desktop. To verify DNS functionality, I ran ipconfig /all on the client machine, confirming that the DNS server pointed to the IP of the domain controller, ensuring proper name resolution and network communication.
</p>
<br />

<p>
<img src=https://i.imgur.com/3Rx4yIt.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I promoted DC-1 to a domain controller with the domain mydomain.com. After a restart, I logged in as mydomain.com\jane_admin and enabled Remote Desktop on Client-1 for domain users.

Next, I logged into DC-1 as jane_admin, opened PowerShell ISE as an administrator, and ran a script to create several user accounts, which I verified in the _EMPLOYEES OU in ADUC. Finally, I tested logging into Client-1 with one of the new accounts, ensuring the correct password worked.


</p>
<br />

<p>
<img src=https://i.imgur.com/4TOwIDx.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly, I simulated a lockout on the Azure VM by configuring Group Policy to allow only 5 login attempts before triggering a lockout. I logged into the Windows 10 VM and opened the Local Group Policy Editor (gpedit.msc). Then, I navigated to Computer Configuration > Windows Settings > Security Settings > Account Lockout Policy and set the Account lockout threshold to 5 invalid attempts, the Account lockout duration to 30 minutes, and the Reset account lockout counter after to 15 minutes. After applying the settings, I ran gpupdate /force in PowerShell to enforce the changes. Finally, I tested the policy by attempting more than 5 incorrect logins, which successfully triggered the account lockout.




</p>
<br />
