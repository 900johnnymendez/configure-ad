<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configuring Active Directory Within Azure Virtual Machines </h1>
This tutorial describes the process for deploying and configuring of on-premises Active Directory within Azure Virtual Machines. It also covers creating and managing user accounts in Active Directory, as well as configuring Group Policy. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (22H2)

<h2>Preparing Active Directory infrastructure</h2>

Create Virtual network

Create Domain Controller virtual machine (Windows server 2022) named DC-1

Username: labuser   Password: Cyberlab123!

Create Client virtual machine (Windows 10) named Client-1

Username: labuser   Password: Cyberlab123!

Set Domain Controller's NIC Private IP address to static

Set Client-1's DNS settings to DC-1's Private IP address

Log into Domain Controller and disable Firewall (to test connectivity)

Restart and login to Client-1 and ping DC-1's Private IP address

Verify the ping succeeded

Within Client-1 use Powershell to run ipconfig /all

Output for DNS settings should show DC-1's Private IP address

<h2>Demonstration</h2>

<img width="662" height="287" alt="Screenshot 2026-08-25 151452" src="https://github.com/user-attachments/assets/59f689b3-893f-45bd-96ba-597982a0da43" />

Clicked on Create Resource Group

<img width="1289" height="1221" alt="Resource Group" src="https://github.com/user-attachments/assets/893a551f-86b6-424c-bde9-9e57410d3b3c" />

Named the Resource Group Active-Directory-Lab, put the region in West US and clicked on review + create

<img width="1392" height="1130" alt="Resource created" src="https://github.com/user-attachments/assets/ae1c8684-1442-4fa4-8156-5159afa17e4f" />

The Resource Group Active-Directory-Lab was created

<img width="661" height="205" alt="Screenshot 2026-08-25 151940" src="https://github.com/user-attachments/assets/0ba74148-a4a5-44a8-931e-ada0505a6dab" />

Clicked on Create Virtual Network

<img width="1292" height="1218" alt="VNET" src="https://github.com/user-attachments/assets/37fc8620-5811-4cf8-87d6-a2a4546869e1" />

Named the Virtual Network Active-Directory-VNet, put it in the Active-Directory-Lab Resource Group and in West US region and then clicked on review + create to create the Virtual Network

<img width="661" height="561" alt="Screenshot 2026-08-25 152523" src="https://github.com/user-attachments/assets/c9a8c24f-e19e-4113-98bd-37b3972d12e8" />

Clicked on Create Azure Virtual Machine

<img width="1444" height="1089" alt="dc-1" src="https://github.com/user-attachments/assets/b25381c1-13f1-4554-8f35-d7510c78eb87" />

Named the Virtual Machine dc-1, put it in Active-Directory-Lab Resource Group and in the same region as the Virtual Network (West US)

<img width="779" height="563" alt="Screenshot 2026-08-25 153005" src="https://github.com/user-attachments/assets/6d8eff2b-9d55-420c-aedd-abed3785f482" />

For the image selected Windows Server 2022 Azure Edition and Standard size

<img width="780" height="565" alt="Screenshot 2026-08-25 153146" src="https://github.com/user-attachments/assets/014c5fce-909e-497d-8b7c-05e98d29954c" />

Username: labuser  Password: Cyberlab123! 

<img width="779" height="625" alt="Screenshot 2026-08-25 153323" src="https://github.com/user-attachments/assets/8eaa35da-9be4-4a5d-b65d-7522c5fcfc43" />

Check to use Server License and click next

<img width="778" height="624" alt="Screenshot 2026-08-25 153443" src="https://github.com/user-attachments/assets/78ac61bb-ec43-487f-a398-05262eb94d70" />

Selected Active-Directory-VNet for the Virtual Network and used the default subnet. Clicked on review + create to create the Virtual Machine

<img width="661" height="561" alt="Screenshot 2026-08-25 152523" src="https://github.com/user-attachments/assets/5647f4c0-f7eb-43fc-aee0-a1df9450a166" />

Clicked on create Azure Virtual Machine to create another Virtual Machine

<img width="1541" height="1021" alt="client-1" src="https://github.com/user-attachments/assets/0f29cd98-71f9-465d-82f9-7c9b106c78f2" />

Named the Virtual Machine client-1 and put in in the same Active-Directory-Lab Resource Group and Region (West US)

<img width="780" height="409" alt="Screenshot 2026-08-25 153810" src="https://github.com/user-attachments/assets/a2c847f5-75e4-4f20-a387-eefcbeead5fa" />

For the image selected Windows 10 Pro, version 22H2 and Standard size

<img width="700" height="630" alt="Screenshot 2026-08-25 153957" src="https://github.com/user-attachments/assets/b918ca8b-c5ac-4605-9bcd-28e3adea9326" />

Username: labuser Password: Cyberlab123! then checked the licensing box and clicked next

<img width="779" height="622" alt="Screenshot 2026-08-25 154212" src="https://github.com/user-attachments/assets/5085323e-6e33-4dc0-9acf-182a2061290d" />

Selected Active Directory-VNet for the Virtual Network and used the default subnet. Clicked on review + create to create to the Virtual Machine

<p>
<img width="860" height="197" alt="Screenshot 2026-06-26 002735" src="https://github.com/user-attachments/assets/46aadd0e-43fc-4eb9-b859-9373af68e3ff" />

</p>
<p>
Created a virtual network named Active-directory-VNET for Windows 10 Pro virtual machine and Windows Server virtual machine to join to.
</p>
<br />

<p>
<img width="852" height="294" alt="Screenshot 2026-06-25 200319" src="https://github.com/user-attachments/assets/fc629dda-ceb1-411b-bdf0-63f866dacd47" />

</p>
<p>
Created two virtual machines, the Domain controller running Windows Server named dc-1 and Windows 10 Pro named client-1. Both VMs were created under the same virtual network (Active-directory-VNET) and the username is labuser and password is Cyberlab123! for both VMs to login.</p>
<br />

<p>

<img width="1015" height="494" alt="Screenshot 2026-06-25 204147" src="https://github.com/user-attachments/assets/9ed2d075-2c88-47bc-a81e-ef99100dad44" />


</p>
<p>
Set the domain controller's (dc-1) NIC private IP address as static so it wont change because in Azure the default private IP address could change. This will make it so that client-1 is able to use dc-1 as the DNS server.
</p>
<br />

<img width="686" height="467" alt="Screenshot 2026-06-25 204639" src="https://github.com/user-attachments/assets/8e64b100-42d9-4100-98ca-baa1d176c226" />

Set client-1's DNS settings to dc-1's private IP address (10.0.0.4) and this will make client-1 look to dc-1 whenever the computer needs to look up anything like google.com for example and for to be able to locate the domain to be able to join it.

<img width="778" height="247" alt="Screenshot 2026-06-26 003017" src="https://github.com/user-attachments/assets/00965886-e0f2-40d6-988e-19fe201ec80e" />

Login to dc-1 vm and disable Windows Firewall to test connectivity. Copied its public IP address to login.

<img width="344" height="74" alt="Screenshot 2026-06-25 222730" src="https://github.com/user-attachments/assets/7f71f318-bd1b-4e42-875b-41b028070a28" />

Used the Remote Desktop Connection application to login and connect to dc-1 virtual machine.

<img width="406" height="247" alt="Screenshot 2026-06-26 003121" src="https://github.com/user-attachments/assets/9c537c99-de4f-4d2e-8be4-0740b9ee48ff" />

Pasted dc-1's public IP address in the box and clicked connect.

<img width="450" height="469" alt="Screenshot 2026-06-26 003244" src="https://github.com/user-attachments/assets/8afd7fe2-904a-4efa-b546-d12dd7ab18e6" />

Entered the credentials that were created with the virtual machines (username: labuser Password: Cyberlab123!)

<img width="1366" height="768" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/daa075fa-8f15-4f16-897e-2e5b77bdf209" />

Once logged in, clicked start and searched for Windows Defender Firewall with Advanced Secuirty and opened it. Once open, clicked on Windows defender firewall properties. On Domain profile tab where it says firewall state,selected off and did the same for private profile and public profile tab and then clicked apply and okay.

<img width="1084" height="417" alt="Screenshot 2026-06-25 222623" src="https://github.com/user-attachments/assets/9d623448-7ead-4267-baa8-df3340a0e87a" />

Then logged in to client-1 by copying it's Public IP address and opening the Remote Desketop Connection application.

<img width="404" height="250" alt="Screenshot 2026-06-26 003426" src="https://github.com/user-attachments/assets/7a7270de-0a30-43ee-a9a6-8afeea1b8433" />

Pasted client-1's Public IP address and clicked connect.

<img width="453" height="465" alt="Screenshot 2026-06-26 003501" src="https://github.com/user-attachments/assets/0923d154-3423-4382-9681-a1929043784b" />

Logged in with the credentials (Username: labuser Password: Cyberlab123!) and clicked okay to connect. Once in, clicked start and typed Powershell and opened it.

<img width="848" height="695" alt="Annotation 2026-06-26 035726" src="https://github.com/user-attachments/assets/b2bc9a6e-337a-4824-b253-732117de59b1" />

In Powershell, typed ping 10.0.0.4 which is dc-1's private IP address to test connectivity. The ping succeeded, both virtual machines are on the same virtual network. Typed ipconfig /all and under DNS servers it should show 10.0.0.4 (dc-1's private IP address) to make sure client-1 is using dc-1 as the DNS server. If the ping failed it would've said timeout either because both virtual machines aren't on the same virtual network or because Windows Firewall is still on.

<h2> Deploying Active Directory</h2>

Login to DC-1 and install Active Directory Domain Services

Promote DC-1 as a Domain Controller and setup a new forest as mydomain.com

Restart and log back into DC-1 as mydomain.com\labuser

Create Organizational Unit called _EMPLOYEES in Active Directory Users and Computers

Create another Organization Unit called _ADMINS to create a Domain Admin user

Create a new employee in _ADMINS named Jane Doe with username as jane_admin and password Cyberlab123!

Add jane_admin to the Domain Admins Security Group

Log out of DC-1 and log back in as mydomain.com\jane_admin and use it as admin account from this point forward

Login to Client-1 as the original local admin (labuser) and join it to the domain

Login to Domain Controller and verify Client-1 appears in Active Directory Users and Computers

Create new Orginaztional Unit named _CLIENTS and drag Client-1 into there





<h2> Demonstation</h2>

<img width="1366" height="768" alt="Screenshot (4)" src="https://github.com/user-attachments/assets/d8948462-b5f1-4efa-81a3-8ab6c7b420fd" />

To install Active Directory Domain Services, Logged in to dc-1 and clicked start and searched for Server Manager to open it. Clicked add roles and features.

<img width="1366" height="768" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/5c7de25c-1f59-49ba-ae88-5cae77bec1aa" />

Add Roles and Features Wizard appeared on screen to help install Active Directory. Clicked next.

<img width="1366" height="768" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/60ee5d43-4fe7-4283-b489-dcd577c0a605" />

In the server selection, dc-1 is selected and clicked next.

<img width="1366" height="768" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/3dc77ed2-d101-4b66-ae43-819cfb856ddd" />

Selected Active Directory Domain Services to install it and clicked next.

<img width="1366" height="768" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/542af333-90d2-4c24-bd9a-3a1c91270298" />

Checked Restart the destination server automatically if required and clicked install.

<img width="1366" height="768" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/9ddccc19-efcb-46ec-a074-a5aed9e6e652" />

Clicked close after its done installing Active Directory Domain Services and then opened Server Manager.

<img width="1366" height="768" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/7680f2b9-4e0c-4989-a22f-b8ec60cacbfb" />

At the top right clicked the flag icon and clicked Promote this server to a domain controller because Active Directory is installed but not a domain controller yet.

<img width="1366" height="768" alt="Screenshot (12)" src="https://github.com/user-attachments/assets/9c8b99c7-0327-426a-b2d4-82111a73103b" />

Clicked add a new forest and for the domain name typed in mydomain.com and clicked next.

<img width="1366" height="768" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/df66d537-c051-4a5a-8228-c1e7affbd156" />

For the Directory Services Restore Mode Password typed in password1 and clicked next

<img width="1366" height="768" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/fbaed500-8ad7-478d-bb79-04cacf6f861b" />

Clicked next

<img width="1366" height="768" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/7317e218-f2da-4229-bf70-216db18f1de3" />

Clicked next

<img width="1366" height="768" alt="Screenshot (16)" src="https://github.com/user-attachments/assets/50918345-103e-44cf-bc25-84331032884f" />

Clicked next

<img width="1366" height="768" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/cfa60964-ccd5-493c-8ac7-e3c310b1cfdd" />

Reviewed the selections made and Clicked next

<img width="1366" height="768" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/e0dfa35a-cb73-4b02-a766-85fa8aff8bd0" />

Clicked install for the new Forest to be installed and for the computer (dc-1) to become a domain controller and wait for the computer to automatically restart.

<img width="417" height="244" alt="Screenshot 2026-06-25 215615" src="https://github.com/user-attachments/assets/84c58242-938d-4513-8d49-3cac43edee0b" />

Log back in by pasting dc-1's public IP address.

<img width="451" height="462" alt="Screenshot 2026-06-25 215740" src="https://github.com/user-attachments/assets/580576e5-e214-4bfe-aefe-7f0a4c9702b2" />

To login as a domain user, the username is mydomain.com\labuser and password is Cyberlab123!

<img width="1366" height="768" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/48a7349b-d48b-4815-b497-f05e3100ea0d" />

Once logged in dc-1, clicked start and under Administrative Tools opened Active Directory Users and Computers.

<img width="1366" height="768" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/cf037f6f-13ee-4829-b40f-c7bb7d9573d7" />

Right click mydomain.com and and click on new Organizational Unit

<img width="1366" height="768" alt="Screenshot (21)" src="https://github.com/user-attachments/assets/ca0f1902-7108-4148-85b2-291befd14759" />

Named the Organizational Unit _EMPLOYEES and clicked okay.

<img width="1366" height="768" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/32fa32a2-3b34-497c-861e-4605f7a4ae81" />

Create another Organizational Unit called _ADMINS and click okay.

<img width="1366" height="768" alt="Screenshot (24)" src="https://github.com/user-attachments/assets/4588d23e-0591-4eae-8a25-feeb8c74e812" />

In _ADMINS right click and selected new user.

<img width="1366" height="768" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/9952ee9e-d404-482b-8f80-91fbfcf3a204" />

Create a new user account Jane as first name and Doe as last name. jane_admin is the username and clicked next.

<img width="1366" height="768" alt="Screenshot (26)" src="https://github.com/user-attachments/assets/eb1c4e3a-c216-40f6-9301-7a0754200992" />

Password is Cyberlab123! and selected password never expires.

<img width="1366" height="768" alt="Screenshot (27)" src="https://github.com/user-attachments/assets/45780312-6c25-4781-bc62-fc647f1ae036" />

Shows full name and username of the account being created and clicked finish.

<img width="1366" height="768" alt="Screenshot (29)" src="https://github.com/user-attachments/assets/b980b7d7-3574-4e7c-9637-8717159099c6" />

Even though the account is in the admins folder it is not an admin account. To make the account an admin you have to add it to the domain admins security group. Right clicked on Janes account and clicked properties.

<img width="1366" height="768" alt="Screenshot (30)" src="https://github.com/user-attachments/assets/27ddfeec-bb47-41d5-ab81-36eba2f5509e" />

Under member of, clicked on add

<img width="1366" height="768" alt="Screenshot (31)" src="https://github.com/user-attachments/assets/d069c781-cb50-43ef-8157-bd444c2824ae" />

Typed Domain Admins and selected check names to find the admins security group and clicked okay.

<img width="1366" height="768" alt="Screenshot (32)" src="https://github.com/user-attachments/assets/922c9e13-12d5-4733-9f45-ad6f64d351f0" />

Click apply and okay to make Jane's account an actual domain admin.

<img width="1366" height="768" alt="Screenshot (33)" src="https://github.com/user-attachments/assets/19f3dbed-9293-4fd8-9c23-223c2de79894" />

Logged out of dc-1 and then signed in as jane admin

<img width="405" height="246" alt="Screenshot 2026-06-25 221611" src="https://github.com/user-attachments/assets/0ba10ebb-24b2-4e1c-ab06-ce7e9149ad28" />

Paste dc-1's public IP address

<img width="445" height="461" alt="Screenshot 2026-06-25 221720" src="https://github.com/user-attachments/assets/d79a0e36-cc8c-45ec-8ff2-aaed41c0def6" />

Login to dc-1 as jane admin account, Username is mydomain.com\jane_admin and password is Cyberlab123! and clicked okay to connect

<img width="395" height="243" alt="Screenshot 2026-06-25 224105" src="https://github.com/user-attachments/assets/349aac30-a0dc-4372-8119-9364335e6893" />

Login to client-1 as local user (labuser) to join the domain.

<img width="787" height="608" alt="image" src="https://github.com/user-attachments/assets/12c10cea-9e55-41da-b3b9-24d410807e43" />

Once logged in, right click start and select system. click on Rename this PC (advanced)

<img width="787" height="612" alt="image" src="https://github.com/user-attachments/assets/46c6cebb-b789-4aa1-a06a-cd745f33d9fd" />

Under Computer Name tab Clicked change

<img width="786" height="611" alt="image" src="https://github.com/user-attachments/assets/f82d49c0-5032-4b1d-ac5d-c10f7812fda6" />

Selected Member of domain and typed mydomain.com and clicked okay

<img width="786" height="609" alt="image" src="https://github.com/user-attachments/assets/4a1a5f8e-810f-4a28-85fe-4bf316373cdf" />

Its able to locate the domain controller since client-1's DNS settings is set to use dc-1's private IP address. Used jane's admin account to join  the domain. (Username: mydomain.com\jane_admin  Password: Cyberlab123!) and clicked okay

<img width="1177" height="676" alt="image" src="https://github.com/user-attachments/assets/6237b9b3-5334-4fe5-b75e-3b8abefeaffa" />

Once successfully joined to the domain a pop up window appears saying Welcome to the mydomain.com domain and the client-1 computer will ask to restart now.

<img width="1366" height="768" alt="screnshot (1)" src="https://github.com/user-attachments/assets/ec059215-1cf5-4c0b-b09b-42a4c13e7922" />

Now to verify client-1 joined the domain, switched to dc-1 logged in as jane admin account. Searched for Active Directory Users and Computers and opened it.

<img width="1366" height="768" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/e73a4e14-3306-4a96-80db-860cafa6b954" />

Under mydomain.com clicked on Computers, Client-1 is listed, joined the domain successfully.

<img width="1366" height="768" alt="screnshot (3)" src="https://github.com/user-attachments/assets/8048295b-ac48-4b70-9b65-60c16ee0933e" />

Right clicked on mydomain.com and clicked on New Orginzational Unit thats called _CLIENTS

<img width="1366" height="768" alt="screnshot (5)" src="https://github.com/user-attachments/assets/6afa1b14-8b22-41c8-a026-1b3aa84f5748" />

In the Computers folder, drag Client-1 to _CLIENTS Orginzational Unit and clicked yes.

<img width="1366" height="768" alt="screnshot (6)" src="https://github.com/user-attachments/assets/9346dc6a-bf00-4d8e-87f1-ca200c64d3e9" />

Under _CLIENTS client-1 should be listed there

<h2> Creating Users & Setup Remote Desktop for non-admin users</h2>

Log into Client-1 as mydomain.com\jane_admin and open system properties

Click Remote Desktop and allow domain users access to remote desktop

Login to DC-1 as jane_admin and open Powershell ISE as an administrator

Copy the script and paste it in a new script in Powershell ISE

Run the script and when finished check _EMPLOYEES in Active Directory to observe users created

Attempt to log into Client-1 with one of the random user accounts created

<h2>Demonstration</h2>

<img width="405" height="243" alt="Screenshot 2026-06-25 231922" src="https://github.com/user-attachments/assets/ed52a37a-d07e-4735-8f48-629cfffd486f" />

Login to client-1 using its public IP address

<img width="448" height="355" alt="Screenshot 2026-06-25 224348" src="https://github.com/user-attachments/assets/8d1dce04-f0c6-467e-b17e-98836b6b3991" />

Used jane admin account to login. (Username: mydomain.com\jane_admin Password: Cyberlab123!)

<img width="1366" height="768" alt="Screensht (1)" src="https://github.com/user-attachments/assets/466e840c-4f54-46c7-91d3-8d7117fc79cd" />

Once logged in, right clicked start menu and clicked System

<img width="1366" height="768" alt="Screensht (2)" src="https://github.com/user-attachments/assets/385b0dfd-564a-49a3-89f6-102b9545e11b" />

Clicked Remote Desktop

<img width="1366" height="768" alt="Screensht (4)" src="https://github.com/user-attachments/assets/53c743fb-6cc1-42c5-9076-636bcd4b2e08" />

Clicked on Select users that can remotely access this PC

<img width="1366" height="768" alt="Screensht (5)" src="https://github.com/user-attachments/assets/cd2a0789-f348-4c52-af8e-30782fdead64" />

Clicked Add

<img width="1366" height="768" alt="Screensht (6)" src="https://github.com/user-attachments/assets/56f49cd0-e43a-44c9-8907-e86a140bf2ec" />

Typed Domain Users and then clicked Check names. This will make possible for all domain users to have access to remote desktop.

<img width="1366" height="768" alt="Screensht (7)" src="https://github.com/user-attachments/assets/dfac76ec-484a-41af-93b7-5cf59110db8e" />

Clicked okay. Logging in to cliet-1 VM as a non-admin user is now possible.

<img width="1366" height="768" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/f51f7287-6106-4bc5-804d-5823fb634706" />

Logged in to dc-1 as jane_admin. Searched for Powershell ISE and run as administrator.

<img width="971" height="450" alt="Screenshot 2026-06-25 230227" src="https://github.com/user-attachments/assets/d1ed7604-4d73-47d3-943c-e1b01b7e3c2f" />

Copied script

<img width="1366" height="768" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/7f7d40a7-53f6-49a0-b2f1-cdfd6950135b" />

Clicked on New Script in Powershell ISE

<img width="1366" height="768" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/2b2be5be-3d3f-4a45-80a9-7ffcfc2d1eb5" />

Right clicked and pasted the script in Powershell ISE.

<img width="1366" height="768" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/901ad5cb-54a2-49e4-8125-19f5ca6f2aea" />

Clicked on file, Save as.

<img width="1366" height="768" alt="Screenshot (12)" src="https://github.com/user-attachments/assets/a92faf37-41a5-48a6-ab95-4b3e552893ba" />

Named the Powershell file as script and clicked save.

<img width="1366" height="768" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/90a5a099-7909-40bf-997e-d7ae9ff8356e" />

Clicked run script

<img width="1366" height="768" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/1d1b524d-e37e-4568-ac35-63d963419e28" />

Script will create 10,000 random accounts and password by default is Password1 for all accounts.

<img width="1366" height="768" alt="Screenshot (16)" src="https://github.com/user-attachments/assets/7b8c2a66-daad-4334-afe1-06103230d603" />

All the users will be created in the Organizational Unit called _EMPLOYEES

<img width="1366" height="768" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/cc9c44f8-b2a6-44c4-8f2f-e2deef21c52a" />

In Active Directory Users and Computers under _EMPLOYEES, thousands of users have been created.

<img width="1366" height="768" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/5cd867c3-6dfa-4c1e-ab60-2c71ef1966eb" />

In _EMPLOYEES, picked a random account that was created to attempt to log into client-1 with it. polo.fam was picked. 

<img width="395" height="243" alt="Screenshot 2026-06-25 224105" src="https://github.com/user-attachments/assets/7eda7f3e-f18a-40aa-937e-585869cc98ad" />

First logged out of jane_admin from client-1. Pasted client-1's Public IP address.

<img width="450" height="464" alt="Screenshot 2026-06-25 232041" src="https://github.com/user-attachments/assets/82bcc2d2-6ff1-4d5e-aa10-da8d9c57e8be" />

Username is mydomain.com\polo.fam and password by default is Password1

<img width="1366" height="768" alt="Screenshot (1)" src="https://github.com/user-attachments/assets/649dbec7-9e75-4a00-acac-4d9779f3b32b" />

Once logged in, opened command prompt to see that polo.fam has a local profile on client-1 VM.

<img width="1366" height="768" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/9041fb25-8900-49b5-9ee8-01794b55b4cc" />

In File Explorer opened C drive, Users folder, polo.fam has its own profile there and jane_admin because also logged in with jane.

<h2> Managing Accounts and Group Policy </h2>

Login to Domain Controller and configure Account Lockout Policy to lockout after 5 attempts with Group Policy Management Console

Update the Group Policy

Pick a random user to attempt to login with the wrong password and observe that the account has been locked out within Active Directory

Unlock the account and attempt to login with it again

Resetting Passwords within Active Directory

Disable the Account in Active Directory and attempt to login and observe

Re-enable the account in Active Directory and attempt to login

<h2>Demonstration</h2>

<img width="1366" height="768" alt="Screenshot (20)" src="https://github.com/user-attachments/assets/828adea2-a1ab-46e9-91f6-0d93553bbd0f" />

Login to dc-1 as jane_admin and right clicked the start menu and clicked run

<img width="1366" height="768" alt="Screenshot (21)" src="https://github.com/user-attachments/assets/dc0b88d1-f8dd-4057-9eb8-2b2d9058eeed" />

Typed gpmc.msc and entered to open Group Policy Management Console

<img width="1366" height="768" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/593e0799-26b1-4776-8af4-30af2a4a0e58" />

Clicked on mydomain.com and then clicked on Linked Group Policy Objects

<img width="1366" height="768" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/3e44cee8-ea9b-41c1-a7c8-524fa75eefd0" />

Right clicked on Default Domain Policy and clicked Edit

<img width="1366" height="768" alt="Screenshot (28)" src="https://github.com/user-attachments/assets/a1427946-bbd6-4e66-955a-8e357798a9ae" />

In Group Policy Management Editor, expanded the following: Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy. Opened Account Lockout duration.

<img width="1366" height="768" alt="Screenshot (29)" src="https://github.com/user-attachments/assets/5759ffa2-230d-4eb7-bf26-6de1cce3ef34" />

Checked Define this Policy settings and set the Lockout duration to 30 minutes and applied.

<img width="1366" height="768" alt="Screenshot (30)" src="https://github.com/user-attachments/assets/abf94dce-05d9-4c68-9479-be43ee71a440" />

Accepted the suggested settings. where the Account will lockout for 30 minutes after 5 invalid attempts

<img width="1366" height="768" alt="Screenshot (32)" src="https://github.com/user-attachments/assets/c4bf75d4-9618-4460-a1c0-b5359bdf5ac6" />

The Account will lockout for 30 minutes after 5 invalid attempts. The Account lockout counter resets after 10 minutes where for example if there is have 2 invalid attempts theres 3 attempts left but after waiting 10 minutes it resets and you get 5 attempts. Can wait some time for the updated settings to roll out or can force it immediately.

<img width="641" height="332" alt="Screenshot 2026-07-29 160158" src="https://github.com/user-attachments/assets/8858ab7e-19b5-4a3f-98dd-f13feb651456" />

Logged into client-1 as jane_admin and typed gpupdate /force in Command prompt to force the update immediately. Policy update completed successfully so now Account lockout Policy is enforced, logged out of client-1.

<img width="401" height="248" alt="Screenshot 2026-06-26 000043" src="https://github.com/user-attachments/assets/bc017b7a-ba9f-4281-a392-aa3b07afe839" />

Picked a random user from active directory users and computers in _EMPLOYEES (polo.fam) to test Account Lockout. Pasted client-1's Public IP address in Remote desketop connection.

<img width="450" height="466" alt="Screenshot 2026-06-26 000135" src="https://github.com/user-attachments/assets/be9badd4-ccd6-4dba-888b-21bcd69e781f" />

Username is mydomain.com\polo.fam and typed the wrong password 5 times.

<img width="554" height="148" alt="Screenshot 2026-06-26 000239" src="https://github.com/user-attachments/assets/37ee956a-996f-4b44-8c0f-26511fdec882" />

After 5 failed attempts the user account is locked out.

<img width="1366" height="768" alt="Screenshot (33)" src="https://github.com/user-attachments/assets/8017466b-c36a-4a9b-b6a6-8223f208c834" />

To unlock the account go back to dc-1, right clicked on mydomain.com and find.

<img width="1366" height="768" alt="Screenshot (34)" src="https://github.com/user-attachments/assets/dec58cbc-228e-4cf8-8099-1f560f122b36" />

Typed polo.fam and clicked find now

<img width="1366" height="768" alt="Screenshot (35)" src="https://github.com/user-attachments/assets/04036ed5-5851-4ba4-9aa5-0479a1afc59d" />

Double clicked on polo.fam and clicked on Account. Selected unlock account and applied. 

<img width="1366" height="768" alt="Screenshot 0" src="https://github.com/user-attachments/assets/4472d498-43f7-4c6a-aa67-33e99897d98b" />

Since account is unlocked, login to client-1 with polo.fam to test it. Once logged in opened Powershell and typed whoami and it shows mydomain\polo.fam. Logged in successfully.

<img width="1366" height="768" alt="Screenshot (37)" src="https://github.com/user-attachments/assets/dcdc6498-bd0e-4b33-9a7f-258fb60c4f92" />

To reset passwords, in dc-1 search for the account and right clicked and selected reset password.

<img width="1366" height="768" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/d18ff0c2-7bb4-427f-9a5f-78d4c722c355" />

Type new password and check unlock users account if need to and clicked okay.

<img width="1366" height="768" alt="Screenshot (39)" src="https://github.com/user-attachments/assets/0e4ff35a-549e-4150-a788-044462689762" />

To disable an account right click the user and click disable

<img width="1366" height="768" alt="Screenshot (40)" src="https://github.com/user-attachments/assets/032b80fa-642a-4109-a028-3978928b358a" />

polo.fam has been disabled.

<img width="558" height="131" alt="Screenshot 2026-06-26 001745" src="https://github.com/user-attachments/assets/a62f6fd6-a182-45aa-8c11-0d59647ac998" />

Attempting to log into client-1 with the disabled account results in error message saying account is disabled and cannot be used. 

<img width="1366" height="768" alt="Screenshot (41)" src="https://github.com/user-attachments/assets/55b24823-6ec6-447f-8454-3834273e851c" />

To enable account, in dc-1 search for the account and right clicked it and select Enable Account.

<img width="1366" height="768" alt="Screenshot (42)" src="https://github.com/user-attachments/assets/810e3bcf-0a37-477a-bb2b-5ce8c7f8e4f3" />

polo.fam account has been enabled and now able to log in.
