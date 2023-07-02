<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Resources in Azure (Virtual Machines | Windows Server 2022)
- Set Connectivity between Domain Controller (DC) with Client 1
- Install Active Directory
- Create Admin and User accounts in AD
- Join client to domain
- Set up Remote Desktop for non-administrative users on client 1

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first step is to create our Resource Group and our VMs (DC-1 and Client-1). Once I have created the Domain Controller I take the following steps:
    
    - Set DC NIC Private IP address to be static
We then create the Client VM on a Windows 10 (Client-1) using the same Resource Group I created for the Domain Controller.
    - Ensure connectivity between Client-1 and DC-1 are the same
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I install Active Directory within our DC-1.  I take a few steps to complete this action as follows:

  - Set up a new forset, ex: mydomain.com and restart then log back into DC-1
  - Create an Admin and Normal User account in Active Directory
      - In Active Directory User and Computers I create an Organizational Unit called "_EMPLOYEES" and "_ADMINS"
      - Created a sample employee as an admin and added to the "Domain Admins" Secuirty Group
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the final steps, I will join Client-1 in the domain I created and set up a remote desktop for non-administrative users on Client-1. Here are the steps I took to complete this action

  - From the Azure portal, I set Client-1's DNS settings to the DC-1 Private IP address
  - I restarted Client-1, I logged in as the original local admin to join the domain
  - Log in to DC-1 to verify Client-1 is active on Active Directory Users and Computers
  - I created a new OU (Organizational Unit) named "_Clients" and dragged Client-1 into this folder
  - Setup Remote Desktop for non-admin users on Client-1
      - Logged into Client-1 as an admin
      - Click “Remote Desktop”
      - Allow “domain users” access to remote desktop
      - You can now log into Client-1 as a normal, non-administrative user now
      - To add a mass amount of users I Opened PowerShell_ise as an Admin
      - Created a new file and pasted the contents of a script
      - Run the script and observed accounts being created
           - Logged in as a newly created user to validate access


</p>
<br />
