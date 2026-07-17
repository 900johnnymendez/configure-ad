<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configuring Active Directory Within Azure Virtual Machines </h1>
This tutorial describes the process for deploying and configuring of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Preparing Active Directory infrastructure</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Demonstration</h2>

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

<h2> Deploying active directory</h2>
install active directory and deploy it
<h2> Demonstation</h2>

<img width="1366" height="768" alt="Screenshot (4)" src="https://github.com/user-attachments/assets/d8948462-b5f1-4efa-81a3-8ab6c7b420fd" />

To install Active Directory Domain Services, Logged in to dc-1 and clicked start and searched for Server Manager to open it. Clicked add roles and features.

<img width="1366" height="768" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/5c7de25c-1f59-49ba-ae88-5cae77bec1aa" />

Add Roles and Features Wizard will pop up to help install Active Directory. Click next.

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

Click next

<img width="1366" height="768" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/7317e218-f2da-4229-bf70-216db18f1de3" />

Click next

<img width="1366" height="768" alt="Screenshot (16)" src="https://github.com/user-attachments/assets/50918345-103e-44cf-bc25-84331032884f" />

Click next

<img width="1366" height="768" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/cfa60964-ccd5-493c-8ac7-e3c310b1cfdd" />

Click next

<img width="1366" height="768" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/e0dfa35a-cb73-4b02-a766-85fa8aff8bd0" />

Click install for the new Forest to be installed and for the computer (dc-1) to become a domain controller and wait for the computer to automatically restart.

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

Jane as first name and Doe as last name. jane_admin is the username and clicked next.

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

Logged out of dc-1 and then sign in as jane admin

<img width="405" height="246" alt="Screenshot 2026-06-25 221611" src="https://github.com/user-attachments/assets/0ba10ebb-24b2-4e1c-ab06-ce7e9149ad28" />

Paste dc-1's public IP address

<img width="445" height="461" alt="Screenshot 2026-06-25 221720" src="https://github.com/user-attachments/assets/d79a0e36-cc8c-45ec-8ff2-aaed41c0def6" />

Login to dc-1 as jane admin account, Username is mydomain.com\jane_admin and password is Cyberlab123! and click okay to connect

<img width="395" height="243" alt="Screenshot 2026-06-25 224105" src="https://github.com/user-attachments/assets/349aac30-a0dc-4372-8119-9364335e6893" />

Login to client-1 as local user (labuser) to join the domain.

<img width="787" height="608" alt="image" src="https://github.com/user-attachments/assets/12c10cea-9e55-41da-b3b9-24d410807e43" />

Once logged in, right click start and select system. click on Rename this PC (advanced)

<img width="787" height="612" alt="image" src="https://github.com/user-attachments/assets/46c6cebb-b789-4aa1-a06a-cd745f33d9fd" />

Click change

<img width="786" height="611" alt="image" src="https://github.com/user-attachments/assets/f82d49c0-5032-4b1d-ac5d-c10f7812fda6" />

Select domain and typed mydomain.com and click okay

<img width="786" height="609" alt="image" src="https://github.com/user-attachments/assets/4a1a5f8e-810f-4a28-85fe-4bf316373cdf" />

Its able to locate the domain controller since client-1's DNS settings is set to use dc-1's private IP address. Use jane's admin account to join  the domain. (Username: mydomain.com\jane_admin  Password: Cyberlab123!) and click okay

<img width="1177" height="676" alt="image" src="https://github.com/user-attachments/assets/6237b9b3-5334-4fe5-b75e-3b8abefeaffa" />

Once successfully joined to the domain a pop up window appears saying Welcome to the mydomain.com domain and the client-1 computer will ask to restart now and click restart now.

<img width="1366" height="768" alt="screnshot (1)" src="https://github.com/user-attachments/assets/ec059215-1cf5-4c0b-b09b-42a4c13e7922" />

Now to verify client-1 joined the domain, switched to dc-1 logged in as jane admin account. Searched for Active Directory Users and Computers and opened it.

<img width="1366" height="768" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/e73a4e14-3306-4a96-80db-860cafa6b954" />

Under mydomain.com clicked on Computers, Client-1 is listed, join successfully.

<img width="1366" height="768" alt="screnshot (3)" src="https://github.com/user-attachments/assets/8048295b-ac48-4b70-9b65-60c16ee0933e" />

Right click on mydomain.com and click on New Orginzational Unit called _CLIENTS

<img width="1366" height="768" alt="screnshot (5)" src="https://github.com/user-attachments/assets/6afa1b14-8b22-41c8-a026-1b3aa84f5748" />

In the Computers folder, drag Client-1 to _CLIENTS Orginzational Unit and click yes.

<img width="1366" height="768" alt="screnshot (6)" src="https://github.com/user-attachments/assets/9346dc6a-bf00-4d8e-87f1-ca200c64d3e9" />

Under _CLIENTS client-1 should be listed there
