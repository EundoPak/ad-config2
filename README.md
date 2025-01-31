<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" height="40%" width="70%"alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configuring Active Directory (On-Premises) Within Azure, Part 2</h1>
This tutorial is a part 2 for setting up AD.<br />


<!-- <h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com) -->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

**Log into DC-1 and install Active Directory Domain Services**

Select Add Roles and Features and start the AD installation. Click next until you hit "Server Roles", from here select "Active Domain Directory Services". This will contain all the necessary features to use Active Directory. Click next until you're in "Confirmation" and click Install. A pop up will appear asking for an automatic restart, select yes because we will need to restart the server later anyways.
![1](https://github.com/user-attachments/assets/0554de78-228f-40ce-aa30-ec5e7b954048)
![2](https://github.com/user-attachments/assets/89d841dc-549b-433d-b770-90932677e233)

**Promote the server to a Domain Controller**

Click on the flag and select "Promote this server to a domain controller". In "Deployment Configuration", select "Add a new forest" and input a domain name, remember the name as it will be needed to log in later and click next. In "Domain  Controller Options" we can configure our DSRM password, we won't be using this password unless we break something using Active Directory, click next until "Prerequisites Check". Finally click "Install", after the first installation click "Install" again to finalize your Active Directory. (The VM will restart)
![3](https://github.com/user-attachments/assets/0f9348b1-26a8-4f14-a6e3-d97983e236c7)
![4](https://github.com/user-attachments/assets/f3792cc5-0829-4075-ba19-a696822d4540)
![5](https://github.com/user-attachments/assets/c2d7c1b7-efe7-4bf3-aee5-9fb4c4f383ed)
![6](https://github.com/user-attachments/assets/39e28899-2086-491c-a350-c822aead8c1c)

**Creating an Organizational Unit (OU)**

Right click on your domain and click New -> click Organizational Unit, add 2 OUs, "_EMPLOYEES" & "_ADMINS".

![7](https://github.com/user-attachments/assets/c2833a9f-c3df-420b-8202-50e94fecd9bc)

**Creating a user account in OU**

Right click OU "_ADMINS" and click New -> click User and finish creating your user account.

![8](https://github.com/user-attachments/assets/50d8dc0d-18c4-4812-aaf4-3ebfb362634c)

**Adding user to "Domain Admins" Security Group**

Right click on the newly created user and select "Properties". In Properties click "Member Of" and click Add. We can now enter "Domain Admins" and click OK to add our user into the security group. To finalize this configuration first click "Apply" then "OK".

![9](https://github.com/user-attachments/assets/ed3a46d7-7b4a-41b8-8940-c565515597a4)
![10](https://github.com/user-attachments/assets/fd72dcf1-f19e-4e00-aba8-f5e4d215d7a5)

**Join Client-1 VM to DC-1 domain**

Log in to Client-1 VM as the local admin user 



